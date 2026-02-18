---
title: Optimiser sur Edge - Akamai (BYOCDN)
description: Découvrez comment configurer Akamai BYOCDN pour l’optimisation sur Edge dans LLM Optimizer.
feature: Opportunities
source-git-commit: 23752b30294c3d467ca477b085aa521cad0f72ca
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 26%

---


# Akamai (BYOCDN)

Cette configuration achemine le trafic dynamique (requêtes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les visiteurs humains et les robots d&#39;optimisation du moteur de recherche continuent d&#39;être servis depuis votre origine comme d&#39;habitude. Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Avant de configurer les règles du gestionnaire de propriétés Akamai, vérifiez que vous disposez des éléments suivants :

* Accès au gestionnaire de propriétés Akamai pour votre domaine.
* Fin du processus d’intégration de LLM Optimizer.
* Transfert du journal CDN vers LLM Optimizer terminé.
* Clé d’API Edge Optimize récupérée à partir de l’interface utilisateur de LLM Optimizer.

{{retrieve-byocdn-api-key}}

**Configuration**

La règle Akamai Property Manager suivante achemine les agents utilisateur LLM vers Edge Optimize. La configuration contient les étapes suivantes :

**1. Définir les critères de routage (correspondance Utilisateur-Agent)**

Définissez le routage pour les user-agents:image.png suivants

```
 *AdobeEdgeOptimize-AI*,
 *ChatGPT-User*,
 *GPTBot*,
 *OAI-SearchBot*,
 *PerplexityBot*,
 *Perplexity-User*
```

![Définir les critères de routage](/help/assets/optimize-at-edge/akamai-step1-routing.png)

**2. Définir l’origine et le comportement SSL**

Définissez l’origine comme `live.edgeoptimize.net` et faites correspondre le SAN à `*.edgeoptimize.net`

![Définir l’origine et le comportement SSL](/help/assets/optimize-at-edge/akamai-step2-origin.png)

**3. Définir la variable de clé de cache**

Définissez la variable de cache `PMUSER_EDGE_OPTIMIZE_CACHE_KEY` sur `LLMCLIENT=TRUE;X_FORWARDED_HOST={{builtin.AK_HOST}}`

![Définir la variable de clé de cache](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

**4. Règles de mise en cache**

![Règles de mise en cache](/help/assets/optimize-at-edge/akamai-step4-rules.png)

**5. Modifier les en-têtes des requêtes entrantes**

Définissez les en-têtes de requête entrante suivants :
`x-edgeoptimize-api-key` à la clé API extraite de LLMO
`x-edgeoptimize-config` à `LLMCLIENT=TRUE;`
`x-edgeoptimize-url` à `{{builtin.AK_URL}}`

![Modifier les en-têtes des requêtes entrantes](/help/assets/optimize-at-edge/akamai-step5-request.png)

**6. Modifier les en-têtes de réponse entrante**

![Modifier les en-têtes de réponse entrante](/help/assets/optimize-at-edge/akamai-step6-response.png)

**7. Modification de l’ID de cache**

![Modification de l’ID de cache](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

**8. Modifiez Les En-Têtes Des Requêtes Sortantes**

Définir `x-forwarded-host`’en-tête sur `{{builtin.AK_HOST}}`

![Modifier les en-têtes de requête sortante](/help/assets/optimize-at-edge/akamai-step8-outgoing-request.png)

**9. Basculement du site**

![Basculement du site](/help/assets/optimize-at-edge/akamai-step9-failover.png)

![Comportements de basculement](/help/assets/optimize-at-edge/akamai-step9-failover-behaviors.png)

![Règles de basculement](/help/assets/optimize-at-edge/akamai-step9-failover-rules.png)

Le basculement de site garantit que si Edge Optimize renvoie une erreur `4XX` ou `5XX`, la requête est automatiquement renvoyée à votre origine par défaut, de sorte que l’utilisateur final reçoive toujours une réponse.

| Scénario | Comportement |
| --- | --- |
| Edge Optimize renvoie `2XX` | La réponse optimisée est transmise au client. |
| Edge Optimize renvoie `4XX` ou `5XX` | La demande est routée vers l’origine par défaut. |

{{verify-setup-byocdn}}

{{return-to-overview}}
