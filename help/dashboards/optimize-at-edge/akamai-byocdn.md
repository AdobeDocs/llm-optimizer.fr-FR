---
title: Optimize at Edge - Akamai (BYOCDN)
description: Découvrez comment configurer Akamai BYOCDN pour Optimize at Edge dans LLM Optimizer.
feature: Opportunities
autotag-review: '2026-07-15T17:40:02.356Z'
TQID: 'https://experienceleague.adobe.com/XlHpXbtxqPl-XQQKWeQc3rbsizCT7U0TF1bQkyv0iM8'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3aid: e0828736-236a-487b-a478-5a635455eadc
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 4f0c6d398e2aab337485b7e26cf6f2aba56375fd
workflow-type: tm+mt
source-wordcount: 795
ht-degree: 70%

---


# Akamai (BYOCDN)

Cette configuration achemine le trafic généré par l’IA agentique (demandes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les personnes humaines et les robots d’optimisation du moteur de recherche continuent d’être servis depuis votre origine comme d’habitude. Pour tester la configuration, une fois celle-ci terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Avant de configurer les règles du gestionnaire de propriétés Akamai, vérifiez que vous disposez des éléments suivants :

* Accès au gestionnaire de propriétés Akamai pour votre domaine.
* Clé d’API Edge Optimize récupérée à partir de l’interface d’utilisation de LLM Optimizer. Pour connaître les étapes, voir [Récupération de vos clés API](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#production-api-key).
* (Facultatif) Pour tester le routage de préproduction, consultez [Clé API de préproduction](/help/dashboards/optimize-at-edge/retrieve-api-keys.md#staging-api-key-optional).

**Configuration**

La règle Akamai Property Manager suivante redirige le trafic des pages HTML agentiques vers Edge Optimize. La configuration contient les étapes suivantes :

## &#x200B;1. Définir des critères de routage (correspondance de trafic Agent-utilisateur et HTML)

Définir le routage pour les agents utilisateurs suivants :

```
 *AdobeEdgeOptimize-AI*
 *ChatGPT-User*
 *GPTBot*
 *OAI-SearchBot*
 *PerplexityBot*
 *Perplexity-User*
 *ClaudeBot*
 *Claude-User*
 *Claude-SearchBot*
```

>[!NOTE]
>
>Appliquez la règle de routage Optimize at Edge uniquement au trafic des pages HTML agentiques. Une configuration courante consiste à utiliser des critères côté requête tels que **Extension de fichier** pour faire correspondre `html` et `EMPTY_STRING` pour les URL de page sans extension. Si votre site diffuse HTML à partir d’autres modèles d’URL ou inclut des itinéraires sans extension hors page, tels que des points d’entrée d’API, affinez la règle avec des critères supplémentaires basés sur un chemin d’accès.

![Définir les critères de routage](/help/assets/optimize-at-edge/akamai-step1-routing.png)

## &#x200B;2. Définir l’origine et le comportement SSL

Définir l’origine comme `live.edgeoptimize.net` et faire correspondre le SAN à `*.edgeoptimize.net`

>[!NOTE]
>
>Si l’activation de la propriété échoue après l’ajout de la règle Optimize at Edge, vérifiez si la règle utilise un mode de vérification SSL du serveur d’origine différent de celui de la règle par défaut. Si tel est le cas, mettez à jour la règle Optimize at Edge pour qu’elle corresponde à la règle par défaut. Par exemple, si la règle par défaut utilise **Paramètres de la plateforme**, utilisez **Paramètres de la plateforme** ici également. Si vous ne pouvez pas utiliser le paramètre requis, contactez l’assistance Akamai.

![Définir l’origine et le comportement SSL](/help/assets/optimize-at-edge/akamai-step2-origin.png)

## &#x200B;3. Définir la variable de clé de cache

Définir la variable de clé de cache `PMUSER_EDGE_OPTIMIZE_CACHE_KEY` sur `LLMCLIENT=TRUE;X_FORWARDED_HOST={{builtin.AK_HOST}}`

![Définir la variable de clé de cache](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

## &#x200B;4. Règles de mise en cache

![Règles de mise en cache](/help/assets/optimize-at-edge/akamai-step4-rules.png)

## &#x200B;5. Modifier les en-têtes des demandes entrantes

Définissez les en-têtes de requête entrante suivants :
`x-edgeoptimize-api-key` à la clé API récupérée depuis LLMO
`x-edgeoptimize-config` vers `LLMCLIENT=TRUE;`
`x-edgeoptimize-url` à `{{builtin.AK_URL}}`

![Modifier les en-têtes des requêtes entrantes](/help/assets/optimize-at-edge/akamai-step5-request.png)

## Autoriser l’optimisation sur Edge via des règles de pare-feu (facultatif)

{{waf-allowlist-setup}}

![Définir l’en-tête x-edgeoptimize-fetcher-key dans le Gestionnaire des propriétés](/help/assets/optimize-at-edge/akamai-step10-fetcher-key.png)

>[!NOTE]
>
>Placez également sur la liste autorisée l’agent utilisateur `*AdobeEdgeOptimize/1.0*` et l’en-tête `x-edgeoptimize-fetcher-key` dans Akamai Bot Manager.

## &#x200B;6. Modifier les en-têtes de réponse entrante

![Modifier les en-têtes de réponse entrante](/help/assets/optimize-at-edge/akamai-step6-response.png)

## &#x200B;7. Modification de l’ID de cache

![Modification de l’ID de cache](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

## &#x200B;8. Modifier Les En-Têtes De Requête Sortante

Définir l’en-tête `x-forwarded-host` sur `{{builtin.AK_HOST}}`

![Modifier les en-têtes des requêtes entrantes](/help/assets/optimize-at-edge/akamai-step8-outgoing-request.png)

## &#x200B;9. Basculement de site

La configuration de basculement de site comporte deux parties : un comportement de basculement dans la règle de routage principale Optimiser pour Edge et une règle sœur qui ajoute un en-tête de réponse lorsque le basculement se produit.

### 9 bis. Configuration du comportement de basculement de site

Dans la règle de routage principale Optimiser sur Edge , créez une règle enfant nommée **Comportement de basculement de site**. Définissez-la sur **Ne correspond à aucun** et ajoutez les critères suivants :

* Le **code d’état de réponse** est compris entre `400` et `599`.
* Le **délai d’expiration d’origine** est `Yes`.

![Basculement du site](/help/assets/optimize-at-edge/akamai-step9-failover.png)

![Configuration du comportement de basculement de site](/help/assets/optimize-at-edge/akamai-step9-failover-settings.png)

### 9 ter. Configuration de la règle d’en-tête de réponse de basculement

>[!IMPORTANT]
>
>Créez la règle **Basculement EdgeOptimize - En-tête de test** en tant que règle **sœur** (au même niveau) des règles de routage — **non** imbriquée dans celles-ci. Dans l’arborescence des règles du Gestionnaire de propriétés Akamai, la hiérarchie doit se présenter comme suit :
>
>```
>▼ Optimize at Edge                         ← parent rule group
>   ▼ Optimize at Edge Routing               ← routing child
>       Site Failover Behavior                 ← nested child
>   EdgeOptimize Failover - Test Header      ← sibling of routing child
>```
>
>La règle sœur est évaluée lorsqu’Akamai recrée la requête ayant échoué pour le nom d’hôte d’origine. Le critère de clé API sur la règle de routage empêche cette requête d’être envoyée à nouveau à Edge Optimize.
>
>Assurez-vous également que la règle de **routage Optimize at Edge** n’est pas remplacée par une règle de correspondance ultérieure qui modifie l’origine, le comportement de mise en cache ou l’identifiant de cache pour les mêmes requêtes. Si une autre règle correspondante réinitialise ces comportements, le routage ou la mise en cache de l’option Optimiser à Edge risque de ne pas fonctionner comme prévu.

![Configurer la règle d’en-tête de réponse de basculement](/help/assets/optimize-at-edge/akamai-step9-failover-header.png)

Le basculement de site garantit que si Edge Optimize renvoie une erreur ou expire, Akamai recrée la demande pour votre nom d’hôte d’origine afin que le visiteur reçoive toujours la réponse habituelle du site.

| Scénario | Comportement |
| --- | --- |
| Edge Optimize renvoie `2XX` ou `3XX` | La réponse optimisée est diffusée. `x-edgeoptimize-request-id` est présent. |
| Edge Optimize renvoie `4XX`-`5XX`, ou l’origine expire | La requête est recréée pour le nom d’hôte d’origine. La réponse inclut `x-edgeoptimize-fo: true`. |

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
| `x-edgeoptimize-fo` | Présent uniquement en cas de basculement (valeur : `true`) | Absent |

{{verify-routing-status-in-ui}}

{{return-to-overview}}
