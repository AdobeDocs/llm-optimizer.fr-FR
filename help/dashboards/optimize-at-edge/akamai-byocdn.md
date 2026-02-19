---
title: Optimiser sur Edge - Akamai (BYOCDN)
description: Découvrez comment configurer Akamai BYOCDN pour l’optimisation sur Edge dans LLM Optimizer.
feature: Opportunities
source-git-commit: 9230e525340bb951fcd9f2ae1f88bad557d5b7d7
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 14%

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

La configuration de basculement de site comporte deux parties : le comportement de basculement (configuré dans la règle principale de routage Optimisation à la périphérie) et une règle d’en-tête de test de basculement distincte.

**9 bis. Comportement de basculement de site (dans la règle principale de routage d’optimisation à la périphérie)**

Dans la règle de routage principale, configurez le comportement de basculement de site et le fragment de code XML avancé comme suit :

![Basculement du site](/help/assets/optimize-at-edge/akamai-step9-failover.png)

Ajoutez le `x-edgeoptimize-request` d’en-tête de requête avec la valeur `fo` via le code XML avancé :

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

9 ter **. Règle d’en-tête du test de basculement (règle sœur)**

>[!IMPORTANT]
>
>Créez la règle **Basculement EdgeOptimize - En-tête de test** en tant que règle **sœur** (au même niveau) des règles de routage — **pas** imbriquée dans celles-ci. Dans l’arborescence des règles du Gestionnaire de propriétés Akamai, la hiérarchie doit se présenter comme suit :
>
>```
>▼ Parent Rule
>   ▶ Optimize at Edge Routing     ← routing rule
>       EdgeOptimize Failover - Test Header       ← sibling, same level
>```
>
>Cela permet de s’assurer que la règle d’en-tête du test de basculement évalue **toutes** les règles de routage, pas seulement une.

Si la valeur du `x-edgeoptimize-request` d’en-tête de requête est `fo`, définissez le `x-edgeoptimize-fo` d’en-tête de réponse sortante sur `true`.

![Règles de basculement](/help/assets/optimize-at-edge/akamai-step9-failover-rules.png)

Le basculement de site garantit que si Edge Optimize renvoie une erreur `4XX` ou `5XX`, la requête est automatiquement renvoyée à votre origine par défaut, de sorte que l’utilisateur final reçoive toujours une réponse.

| Scénario | Comportement |
| --- | --- |
| Edge Optimize renvoie `2XX` | La réponse optimisée est transmise au client. |
| Edge Optimize renvoie `4XX` ou `5XX` | La demande est routée vers l’origine par défaut. |

**Vérifier la configuration**

Une fois la configuration terminée, vérifiez que le trafic des robots est acheminé vers Edge Optimize et que le trafic humain n’est pas affecté.

**1. Tester le trafic de robots (doit être optimisé)**

Simulez une requête de robot d’IA à l’aide d’une chaîne agent-utilisateur :

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Une réponse réussie inclut l’en-tête `x-edgeoptimize-request-id`, confirmant que la requête a été acheminée via Edge Optimize :

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

**2. Tester le trafic humain (ne devrait PAS être affecté)**

Simulez une requête régulière de navigateur humain :

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
```

La réponse ne doit **pas** contenir l’en-tête `x-edgeoptimize-request-id`. Le contenu de la page et le temps de réponse doivent rester identiques à avant l’activation de l’option Optimiser dans Edge.

**3. Comment différencier les deux scénarios**

| En-tête | Trafic de robots (optimisé) | Trafic humain (non affecté) |
|---|---|---|
| `x-edgeoptimize-request-id` | Présent : contient un ID de requête unique | Absent |
| `x-edgeoptimize-fo` | Présent uniquement en cas de basculement (valeur : `1`) | Absent |

Le statut du routage du trafic peut également être vérifié dans l’interface utilisateur de LLM Optimizer. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

![Statut du routage du trafic AI avec routage activé](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

{{return-to-overview}}
