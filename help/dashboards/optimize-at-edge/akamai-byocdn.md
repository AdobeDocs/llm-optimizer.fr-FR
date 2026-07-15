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
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 810
ht-degree: 98%

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

**1. Définir les critères de routage (correspondance de l’agent utilisateur et du trafic HTML)**

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

**2. Définir l’origine et le comportement SSL**

Définir l’origine comme `live.edgeoptimize.net` et faire correspondre le SAN à `*.edgeoptimize.net`

>[!NOTE]
>
>Si l’activation de la propriété échoue après l’ajout de la règle Optimize at Edge, vérifiez si la règle utilise un mode de vérification SSL du serveur d’origine différent de celui de la règle par défaut. Si tel est le cas, mettez à jour la règle Optimize at Edge pour qu’elle corresponde à la règle par défaut. Par exemple, si la règle par défaut utilise **Paramètres de la plateforme**, utilisez **Paramètres de la plateforme** ici également. Si vous ne pouvez pas utiliser le paramètre requis, contactez l’assistance Akamai.

![Définir l’origine et le comportement SSL](/help/assets/optimize-at-edge/akamai-step2-origin.png)

**3. Définir la variable de clé de cache**

Définir la variable de clé de cache `PMUSER_EDGE_OPTIMIZE_CACHE_KEY` sur `LLMCLIENT=TRUE;X_FORWARDED_HOST={{builtin.AK_HOST}}`

![Définir la variable de clé de cache](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

**4. Règles de mise en cache**

![Règles de mise en cache](/help/assets/optimize-at-edge/akamai-step4-rules.png)

**5. Modifier les en-têtes des requêtes entrantes**

Définissez les en-têtes de requête entrante suivants :
`x-edgeoptimize-api-key` à la clé API récupérée depuis LLMO
`x-edgeoptimize-config` vers `LLMCLIENT=TRUE;`
`x-edgeoptimize-url` à `{{builtin.AK_URL}}`

![Modifier les en-têtes des requêtes entrantes](/help/assets/optimize-at-edge/akamai-step5-request.png)

**Autoriser Optimize at Edge via des règles de pare-feu (facultatif)**

{{waf-allowlist-setup}}

![Définir l’en-tête x-edgeoptimize-fetcher-key dans le Gestionnaire des propriétés](/help/assets/optimize-at-edge/akamai-step10-fetcher-key.png)

>[!NOTE]
>
>Placez également sur la liste autorisée l’agent utilisateur `*AdobeEdgeOptimize/1.0*` et l’en-tête `x-edgeoptimize-fetcher-key` dans Akamai Bot Manager.

**6. Modifier les en-têtes de réponse entrante**

![Modifier les en-têtes de réponse entrante](/help/assets/optimize-at-edge/akamai-step6-response.png)

**7. Modification de l’ID de cache**

![Modification de l’ID de cache](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

**8. Modifier les en-têtes des requêtes sortantes**

Définir l’en-tête `x-forwarded-host` sur `{{builtin.AK_HOST}}`

![Modifier les en-têtes des requêtes entrantes](/help/assets/optimize-at-edge/akamai-step8-outgoing-request.png)

**9. Basculement du site**

La configuration de basculement de site comporte deux parties : le comportement de basculement (configuré dans la règle principale de routage Optimisation à la périphérie) et une règle d’en-tête de test de basculement distincte.

**9a. Comportement de basculement de site (dans la règle principale de routage d’optimisation à la périphérie)**

Dans la règle de routage principale, configurez le comportement de basculement de site et le fragment de code XML avancé comme suit :

>[!IMPORTANT]
>
>Le fragment de code XML de cette étape nécessite le comportement **Avancé**. Dans certains environnements Akamai, ce comportement n’est pas disponible pour la modification en libre-service. Si vous ne voyez pas l’option **Avancé**, contactez votre équipe de compte Akamai ou l’assistance Akamai pour activer la configuration requise.

![Basculement du site](/help/assets/optimize-at-edge/akamai-step9-failover.png)

Ajoutez l’en-tête de requête `x-edgeoptimize-request` avec la valeur `fo` via le code XML avancé :

```
<forward:availability.fail-action2>
<add-header>
<status>on</status>
<name>x-edgeoptimize-request</name>
<value>fo</value>
</add-header>
</forward:availability.fail-action2>
```

![Comportements de basculement](/help/assets/optimize-at-edge/akamai-step9-failover-behaviors.png)

**9b. Règle d’en-tête du test de basculement (règle sœur)**

>[!IMPORTANT]
>
>Créez la règle **Basculement EdgeOptimize - En-tête de test** en tant que règle **sœur** (au même niveau) des règles de routage — **non** imbriquée dans celles-ci. Dans l’arborescence des règles du Gestionnaire de propriétés Akamai, la hiérarchie doit se présenter comme suit :
>
>```
>▼ Parent Rule
>   ▶ Optimize at Edge Routing     ← routing rule
>       EdgeOptimize Failover - Test Header       ← sibling, same level
>```
>
>Cela permet de s’assurer que la règle d’en-tête du test de basculement évalue **toutes** les règles de routage, et pas seulement une.
>
>Assurez-vous également que la règle de **routage Optimize at Edge** n’est pas remplacée par une règle de correspondance ultérieure qui modifie l’origine, le comportement de mise en cache ou l’identifiant de cache pour les mêmes requêtes. Si une autre règle correspondante réinitialise ces comportements, le routage ou la mise en cache de l’option Optimiser à Edge risque de ne pas fonctionner comme prévu.

Si la valeur `x-edgeoptimize-request` d’en-tête de requête est `fo`, définissez l’en-tête de réponse sortante `x-edgeoptimize-fo` sur `true`.

![Règles de basculement](/help/assets/optimize-at-edge/akamai-step9-failover-rules.png)

Le basculement de site garantit que si Edge Optimize renvoie une erreur `4XX` ou `5XX`, la requête est automatiquement renvoyée à votre origine par défaut, de sorte que l’utilisateur final reçoive toujours une réponse.

| Scénario | Comportement |
| --- | --- |
| Edge Optimize renvoie `2XX` | La réponse optimisée est transmise à la clientèle. |
| Edge Optimize renvoie `4XX` ou `5XX` | La demande est routée vers l’origine par défaut. |

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
