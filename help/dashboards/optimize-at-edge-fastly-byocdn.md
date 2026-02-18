---
title: Optimisation d’Edge - Fastly (BYOCDN)
description: Découvrez comment configurer Fastly BYOCDN pour optimiser sur Edge dans LLM Optimizer.
feature: Opportunities
source-git-commit: 8cdd15413555057165f69ea4d5a15b243ab9098d
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 6%

---


# Fastly (BYOCDN)

Cette configuration achemine le trafic dynamique (requêtes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les visiteurs humains et les robots d&#39;optimisation du moteur de recherche continuent d&#39;être servis depuis votre origine comme d&#39;habitude. Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Avant de configurer les règles Fastly VCL, vérifiez que vous disposez des éléments suivants :

* Accès à Fastly pour votre domaine.
* Fin du processus d’intégration de LLM Optimizer.
* Transfert du journal CDN vers LLM Optimizer terminé.
* Clé d’API Edge Optimize récupérée à partir de l’interface utilisateur de LLM Optimizer.

{{retrieve-byocdn-api-key}}

**Configuration**

Ajoutez les trois fragments de code VCL suivants à votre service Fastly. Ces fragments de code gèrent les requêtes d’agent de routage vers Edge Optimize, la séparation des clés de cache et le basculement vers votre origine par défaut.

![Fastly VCL](/help/assets/optimize-at-edge/fastly-vcl.png)

![Ajouter des fragments de code VCL](/help/assets/optimize-at-edge/add-vcl-snippets.png)

**Fragment de code vcl_recv**

```
unset req.http.x-edgeoptimize-url;
unset req.http.x-edgeoptimize-config;
unset req.http.x-edgeoptimize-api-key;

if (!req.http.x-edgeoptimize-request
    && req.http.user-agent ~ "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)") {
  set req.http.x-forwarded-host = req.http.host; # required for identifying the original host
  set req.http.x-edgeoptimize-url = req.url; # required for identifying the original url
  set req.http.x-edgeoptimize-config = "LLMCLIENT=TRUE;"; # required for cache key
  set req.http.x-edgeoptimize-api-key = "<YOUR API KEY>"; # required for identifying the client
  set req.backend = F_EDGE_OPTIMIZE;
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
  set req.backend = F_Default_Origin;
  restart;
}

if (!req.http.x-edgeoptimize-config && req.http.x-edgeoptimize-request == "failover") {
  set resp.http.x-edgeoptimize-fo = "1";
}
```

**Basculement**

Le fragment de code `vcl_deliver` gère automatiquement le basculement. Si Edge Optimize renvoie une erreur `4XX` ou `5XX`, la requête est redémarrée et routée vers votre origine par défaut, de sorte que l’utilisateur final reçoive toujours une réponse. Les réponses de basculement incluent l’en-tête `x-edgeoptimize-fo: 1`.

| Scénario | Comportement |
| --- | --- |
| Edge Optimize renvoie `2XX` | La réponse optimisée est transmise au client. |
| Edge Optimize renvoie `4XX` ou `5XX` | La requête est redémarrée et diffusée à partir de l’origine par défaut. |
| Réponse de basculement | Inclut le `x-edgeoptimize-fo: 1` d’en-tête. |

{{verify-setup-byocdn}}

{{return-to-overview}}
