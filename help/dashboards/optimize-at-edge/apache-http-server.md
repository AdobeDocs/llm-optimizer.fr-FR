---
title: Optimiser sur Edge - Serveur HTTP Apache
description: Découvrez comment configurer Apache HTTP Server (proxy inverse auto-hébergé) BYOCDN pour une optimisation sur Edge dans LLM Optimizer.
feature: Opportunities
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
source-git-commit: d7e723161836027dcdde931378f5d0f776a1ecfc
workflow-type: tm+mt
source-wordcount: 585
ht-degree: 32%

---


# Serveur HTTP Apache

Cette configuration s’applique lorsque le serveur HTTP Apache agit comme proxy inverse devant votre instance d’origine (une configuration auto-hébergée, **sans** AEM Dispatcher). Il achemine le trafic dynamique (requêtes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les personnes humaines et les robots d’optimisation du moteur de recherche continuent d’être servis depuis votre origine comme d’habitude. Pour tester la configuration, une fois celle-ci terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

L’intégration consiste en un ensemble de fichiers Apache `Include` natifs (aucun code ni programme de travail à déployer). Vous téléchargez trois fichiers, définissez votre clé API et ajoutez deux lignes `Include` à votre hôte virtuel.

**Conditions préalables**

Avant de configurer les règles de routage Apache, vérifiez que vous disposez des éléments suivants :

* Apache HTTP Server 2.4 ou version ultérieure avec ces modules activés : `proxy`, `proxy_http`, `ssl`, `rewrite`, `headers`, `env` et `setenvif`.
* l’accès à la configuration Apache (la `<VirtualHost>` de votre site) et la possibilité de recharger Apache ;
* Clé d’API Edge Optimize récupérée à partir de l’interface d’utilisation de LLM Optimizer. Pour connaître les étapes, voir [Récupération de vos clés API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facultatif) Pour tester le routage de préproduction, consultez [Clé API de préproduction](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

## Configuration

**1. Téléchargez les fichiers de configuration**

Téléchargez les trois fichiers d’inclusion Edge Optimize à partir du [Référentiel d’exemples de code Optimize at Edge](https://github.com/adobe/llmo-code-samples/tree/main/optimize-at-edge/apache) et placez-les dans un répertoire de votre serveur Apache (par exemple, `conf/oae/`) :

| Fichier | Objectif |
|------|---------|
| `oae-routing.conf` | Détecte les robots d’IA, injecte les en-têtes Edge Optimize, achemine les requêtes de page HTML vers le serveur principal et configure l’isolation du cache et le basculement. |
| `oae-failover.conf` | Relit la requête d’origine par rapport à votre origine si Edge Optimize renvoie une erreur. |
| `domains.conf` | Active l’optimisation sur Edge par domaine et contient votre clé API. |

Vous n’avez pas besoin de modifier les `oae-routing.conf` ou les `oae-failover.conf` ; utilisez-les en l’état.

**2. Activez votre domaine et définissez la clé API (`domains.conf`)**

Modifiez le `domains.conf` et ajoutez une ligne par domaine que vous activez. Remplacez l’hôte par votre domaine et `YOUR_API_KEY` par la clé de l’interface utilisateur de LLM Optimizer. Domaines non répertoriés routent vers l’origine inchangé, vous pouvez donc activer un domaine à la fois.

```
SetEnvIfExpr "%{HTTP_HOST} =~ m#(?i)^(www\.)?example\.com(:\d+)?$#" OAE_DOMAIN_ENABLED=1 OAE_API_KEY=YOUR_API_KEY
```

**3. Incluez les fichiers dans votre hôte virtuel**

Ajoutez les deux lignes de `Include` à votre `<VirtualHost *:443>` existant. Le fichier de routage passe **avant** vos règles de réécriture et de `ProxyPass` ; le fichier de basculement passe **après**. Dans l’exemple ci-dessous, les lignes marquées `#NEWLINE` sont les seules lignes que vous ajoutez pour Optimiser dans Edge ; tout le reste (`ServerName`, `ProxyPass` et le reste) fait partie de votre configuration inchangée.

```
Define OAE_CONF_DIR conf/oae                       #NEWLINE  directory holding the OAE include files

<VirtualHost *:443>
    ServerName www.example.com

    Include "${OAE_CONF_DIR}/oae-routing.conf"     #NEWLINE  OAE routing — BEFORE your Rewrite & ProxyPass rules

    # --- your existing rewrite rules and ProxyPass to origin ---
    ProxyPass        "/" "https://www.example.com/"
    ProxyPassReverse "/" "https://www.example.com/"

    Include "${OAE_CONF_DIR}/oae-failover.conf"    #NEWLINE  OAE failover — AFTER your ProxyPass rules
</VirtualHost>
```

**4. Rechargez Apache**

Validez la configuration et rechargez Apache pour appliquer les modifications.

>[!NOTE]
>
>Les réponses humaines et optimisées par les robots sont automatiquement conservées dans des entrées de cache distinctes (les ensembles de fichiers de routage `Vary: x-edgeoptimize-config`). Si votre Apache utilise déjà `mod_cache`, assurez-vous qu’il a `CacheQuickHandler Off` afin que la recherche dans le cache s’exécute une fois les en-têtes Edge Optimize définis.

## Autoriser l’optimisation sur Edge via des règles de pare-feu (facultatif)

{{waf-allowlist-setup}}

## Vérifier la configuration

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
