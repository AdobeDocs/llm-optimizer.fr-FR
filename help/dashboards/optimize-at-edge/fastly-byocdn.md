---
title: Optimize at Edge - Fastly (BYOCDN)
description: Découvrez comment configurer Fastly BYOCDN pour Optimize at Edge dans LLM Optimizer.
feature: Opportunities
autotag-review: '2026-05-15T17:51:24.924Z'
TQID: 'https://experienceleague.adobe.com/qXp1pbmZrxahHFOUzIuo-WEawdgNWIIQKDyy0yL2MLA'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 349
ht-degree: 92%

---


# Fastly (BYOCDN)

Cette configuration achemine le trafic généré par l’IA agentique (demandes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les personnes humaines et les robots d’optimisation du moteur de recherche continuent d’être servis depuis votre origine comme d’habitude. Pour tester la configuration, une fois celle-ci terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Avant de configurer les règles Fastly VCL, vérifiez que vous disposez des éléments suivants :

* Accès à Fastly pour votre domaine.
* Clé d’API Edge Optimize récupérée à partir de l’interface d’utilisation de LLM Optimizer. Pour connaître les étapes, voir [Récupération de vos clés API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facultatif) Pour tester le routage d’évaluation, consultez [Clé API d’évaluation](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Configuration**

Ajoutez les trois fragments de code VCL suivants à votre service Fastly. Ces fragments de code gèrent les requêtes d’agent de routage vers Edge Optimize, la séparation des clés de cache et le basculement vers votre origine par défaut.

![Configuration du serveur principal Fastly](/help/assets/optimize-at-edge/fastly-backend-config.png)

![Ajouter des fragments de code VCL](/help/assets/optimize-at-edge/add-vcl-snippets.png)

**Fragment de code vcl_recv**

```
unset req.http.x-edgeoptimize-url;
unset req.http.x-edgeoptimize-config;
unset req.http.x-edgeoptimize-api-key;
unset req.http.x-edgeoptimize-fetcher-key; # Optional (required only in case of WAF)

if (!req.http.x-edgeoptimize-request
    && req.http.user-agent ~ "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)") {
  set req.http.x-forwarded-host = req.http.host; # required for identifying the original host
  set req.http.x-edgeoptimize-url = req.url; # required for identifying the original url
  set req.http.x-edgeoptimize-config = "LLMCLIENT=TRUE;"; # required for cache key
  set req.http.x-edgeoptimize-api-key = "<YOUR API KEY>"; # required for identifying the client
  set req.http.x-edgeoptimize-fetcher-key = "<YOUR FETCHER KEY>"; # Optional (required only in case of WAF)
  set req.backend = F_EDGE_OPTIMIZE;
  return(lookup);
}
```

**Fragment de code vcl_hash**

```
if (req.http.x-edgeoptimize-config) {
  set req.hash += "edge-optimize";
  set req.hash += req.http.x-edgeoptimize-config;
}
```

**Fragment de code vcl_delivery**

```
if (req.http.x-edgeoptimize-config && resp.status >= 400) {
  set req.http.x-edgeoptimize-request = "failover";
  restart;
}

if (req.http.x-edgeoptimize-config) {
  return(deliver);
}

if (!req.http.x-edgeoptimize-config && req.http.x-edgeoptimize-request == "failover") {
  set resp.http.x-edgeoptimize-fo = "1";
}
```

**Basculement**

Le fragment de code `vcl_deliver` gère automatiquement le basculement. Si Edge Optimize renvoie une erreur `4XX` ou `5XX`, la demande est redémarrée et routée vers votre origine par défaut, de sorte que l’utilisateur final ou l’utilisatrice finale reçoive toujours une réponse. Les réponses de basculement incluent l’en-tête `x-edgeoptimize-fo: 1`.

| Scénario | Comportement |
| --- | --- |
| Edge Optimize renvoie `2XX` | La réponse optimisée est transmise à la clientèle. |
| Edge Optimize renvoie `4XX` ou `5XX` | La requête est redémarrée et diffusée à partir de l’origine par défaut. |
| Réponse de basculement | Inclut l’en-tête `x-edgeoptimize-fo: 1`. |

**Autoriser l’optimisation sur Edge via des règles de pare-feu (facultatif)**

{{waf-allowlist-setup}}

**Vérifier la configuration**

Une fois la configuration terminée, vérifiez que le trafic des robots est acheminé vers Edge Optimize et que le trafic humain n’est pas affecté.

**1. Tester le trafic de robots (doit être optimisé)**

Simulez une requête de robot d’IA à l’aide d’une chaîne utilisateur-agent :

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Une réponse réussie inclut l’en-tête `x-edgeoptimize-request-id`, confirmant que la requête a été acheminée via Edge Optimize :

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

**2. Tester le trafic humain (ne devrait PAS être affecté)**

Simulez une requête régulière de navigateur humain :

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
```

La réponse ne doit **pas** contenir l’en-tête `x-edgeoptimize-request-id`. Le contenu de la page et le temps de réponse doivent rester identiques à avant l’activation de l’option Optimize at Edge.

**3. Comment différencier les deux scénarios**

| En-tête | Trafic de robots (optimisé) | Trafic humain (non affecté) |
|---|---|---|
| `x-edgeoptimize-request-id` | Présent : contient un ID de requête unique | Absent |
| `x-edgeoptimize-fo` | Présent uniquement en cas de basculement (valeur : `1`) | Absent |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
