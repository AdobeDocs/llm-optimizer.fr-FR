---
title: Optimize at Edge
description: Découvrez comment diffuser des optimisations dans LLM Optimizer à la périphérie du réseau CDN sans apporter de modifications.
feature: Opportunities
source-git-commit: 1f665bd14349c15d92f8274742606abcf9b02000
workflow-type: tm+mt
source-wordcount: '4708'
ht-degree: 44%

---


# Optimize at Edge

Cette page fournit un aperçu détaillé sur la manière de fournir des optimisations à la périphérie du réseau CDN sans aucune modification. Elle couvre le processus d’intégration, les opportunités d’optimisation disponibles et comment optimiser automatiquement à la périphérie.

>[!NOTE]
>Cette fonctionnalité est actuellement en accès anticipé. Pour en savoir plus à propos des programmes d’accès anticipé, voir [ici](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current#aem-beta-programs).

## Qu’est-ce qu’Optimize at Edge ?

Optimize at Edge est une fonctionnalité de déploiement en périphérie dans LLM Optimizer qui apporte des modifications conviviales pour l’IA aux agents qui utilisent des LLM. Dans le contexte actuel, « Edge » signifie que l’optimisation est appliquée au niveau de la couche CDN. Comme les optimisations se font au niveau de la couche CDN, aucune modification de création dans le système de gestion de contenu (CMS) n’est nécessaire afin que votre CMS d’origine reste inchangé. Cette séparation vous permet d’améliorer la visibilité dans les LLM sans modifier vos workflows de publication existants. Elle cible uniquement le trafic généré par l’IA agentique et n’a aucune incidence sur les utilisateurs, les utilisatrices ou les robots SEO. Lorsque LLM Optimizer détecte des opportunités d’optimisation d’une page, les utilisateurs et les utilisatrices peuvent déployer des correctifs directement sur le réseau CDN.

Optimize at Edge est une alternative plus rapide et plus épurée aux correctifs traditionnels qui nécessitent des efforts d’ingénierie complexes. Comme mentionné, une fois une configuration unique terminée, aucune modification de plateforme ni aucun long cycle de développement ne sont nécessaires pour appliquer les modifications. Vous pouvez publier des améliorations en quelques minutes sans nécessiter l’engagement de l’équipe de développement. Il s’agit d’une méthode sans code permettant d’optimiser votre site web pour les agents d’IA.

Optimize at Edge est conçu pour les utilisateurs et les utilisatrices des équipes marketing, SEO, de contenu et de stratégie numérique. Cette fonctionnalité peut permettre aux utilisateurs et aux utilisatrices d’effectuer l’ensemble du parcours dans LLM Optimizer : identifier des opportunités, comprendre des suggestions et déployer facilement des correctifs. Avec Optimiser at Edge, les utilisateurs et utilisatrices peuvent prévisualiser les modifications, les déployer rapidement à l’extrémité du réseau CDN et vérifier que les optimisations sont actives. Les performances peuvent être suivies dans l’écosystème LLM Optimizer.

### Principaux avantages

* **Diffusion IA uniquement :** ne fournit du code HTML optimisé qu’aux agents IA, sans impact sur les visites humaines ni sur les robots SEO.
* **Cycles plus rapides :** publiez les modifications en quelques minutes et non en quelques semaines. Aucune modification de la plateforme ou de longs cycles d’ingénierie n’est nécessaire.
* **Réversible :** pris en charge avec une fonctionnalité de restauration en un clic qui peut rétablir la page en quelques minutes.
* **Aucun impact sur les performances :** les optimisations et la mise en cache basées sur Edge n’affectent pas la latence du site.
* **Indépendant du réseau CDN et du système de gestion de contenu :** fonctionne avec n’importe quelle configuration de réseau CDN et configuration front-end, quel que soit le système de gestion de contenu.

### Quelles sont les opportunités prises en charge avec Optimize at Edge ?

Les opportunités qui peuvent améliorer l’expérience web agentique sont prises en charge avec Optimize at Edge. Pour en savoir plus sur chaque opportunité, consultez la page [Tableau de bord des opportunités](/help/dashboards/opportunities.md) et la section des opportunités de la page active.

## Intégration

Contactez l’équipe de votre compte Adobe ou l’équipe FDE pour démarrer le processus d’intégration. Votre équipe informatique ou réseau CDN doit également terminer le processus de configuration et les conditions préalables. Vous pouvez également contacter `llmo-at-edge@adobe.com` pour obtenir une aide supplémentaire à l’intégration.

Conditions préalables à l’intégration d’Optimize at Edge :

* Terminez le processus d’intégration de LLM Optimizer.
* Terminez le processus de transfert des journaux pour vos journaux CDN.

Conditions requises pour votre équipe informatique/réseau CDN :
* Ajoutez `*AdobeEdgeOptimize/1.0*` user-agent à la Liste autorisée dans le fichier robots.txt de votre site ou dans les règles de gestion du trafic de robots.
* Assurez-vous que les pages ne sont pas bloquées au niveau du domaine ou du réseau CDN.
* Ajoutez les règles de routage d’Optimize at Edge dans le réseau CDN.
* Confirmez le routage d’Optimize at Edge dans l’interface LLM Optimizer.

Pour guider le processus de configuration, vous trouverez ci-dessous des exemples pour un certain nombre de configurations de réseau CDN. Gardez à l’esprit que ces exemples doivent être adaptés à votre configuration active réelle. Nous vous recommandons d’appliquer d’abord les modifications dans les environnements inférieurs.

>[!BEGINTABS]

>[!TAB Réseau CDN géré par AEM Cloud Service (Fastly)]

**Edge Optimize - Réseau CDN géré par AEM Cloud Service (Fastly)**

Cette configuration achemine le trafic dynamique (requêtes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les visiteurs humains et les robots d&#39;optimisation du moteur de recherche continuent d&#39;être servis depuis votre origine comme d&#39;habitude. Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Pour commencer à acheminer le trafic d’agent vers Edge Optimizer :

1. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

   ![Accéder à la configuration du client](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Sous **Routage du trafic AI pour déployer des optimisations**, cochez la case **Déployer des optimisations sur des agents AI**. L’équipe d’Adobe s’occupera de la configuration du routage en votre nom.

   ![Cochez la case Déployer les optimisations sur les agents AI](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Après avoir activé la case à cocher, le statut indique que la configuration est en cours. L’équipe d’Adobe terminera la configuration du routage pour vous.

   ![Configuration du routage du trafic AI en cours](/help/assets/optimize-at-edge/prereq-traffic-routing-progress.png)

   Une fois le routage configuré et actif, son état est mis à jour pour afficher une coche verte indiquant qu’il a bien été activé. Aucune autre action n’est requise de votre part.

De plus, si vous avez besoin d’aide pour les étapes ci-dessus, contactez votre équipe de compte Adobe ou votre `llmo-at-edge@adobe.com`.

**Routage en libre-service via le pipeline Cloud Manager**

Si vous préférez configurer le routage vous-même via le pipeline Cloud Manager, procédez comme suit. La configuration du routage est effectuée à l’aide d’une règle [originSelector CDN](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#origin-selectors). Les conditions préalables sont les suivantes :

* Choisissez le domaine à acheminer.
* Choisissez les chemins à acheminer.
* Décidez des agents utilisateur à acheminer (regex recommandée).

Pour déployer la règle, vous devez effectuer les opérations suivantes :

* Créez un [pipeline de configuration](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/config-pipeline).
* Validez le fichier de configuration `cdn.yaml` dans votre référentiel.
* Exécutez le pipeline de configuration.

```
kind: "CDN"
version: "1"
data:
  # Origin selectors to route to Edge Optimize backend
  originSelectors:
    rules:
      - name: route-to-edge-optimize-backend
        when:
          allOf:
            - reqHeader: x-edgeoptimize-request
              exists: false # avoid loops when requests comes from Edge Optimize
            - reqHeader: user-agent
              matches: "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)" # routed user agents
            - reqProperty: domain
              equals: "example.com" # routed domain
            - reqProperty: originalPath
              matches: '(/[^./]+|\.html|/)$' # routed extensions, with .html extension or without extension
            - anyOf:
              - { reqProperty: originalPath, in: [ "/page.html" ] } # routed pages, exact path matching
              - { reqProperty: originalPath, like: "/dir/*" } # routed pages, wildcard path matching
        action:
          type: selectOrigin
          originName: edge-optimize-backend
    origins:
      - name: edge-optimize-backend
        domain: "live.edgeoptimize.net"
```

**Vérifier la configuration**

Pour tester la configuration, exécutez une curl et attendez-vous aux éléments suivants :

```
curl -svo /dev/null https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Le statut du routage du trafic peut également être vérifié dans l’interface utilisateur de LLM Optimizer. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

![Statut du routage du trafic AI avec routage activé](/help/assets/optimize-at-edge/adobe-CDN-traffic-routed-tick.png)

>[!TAB Fastly (BYOCDN)]

**Edge Optimize - Fastly (BYOCDN)**

Cette configuration achemine le trafic dynamique (requêtes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les visiteurs humains et les robots d&#39;optimisation du moteur de recherche continuent d&#39;être servis depuis votre origine comme d&#39;habitude. Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Avant de configurer les règles Fastly VCL, vérifiez que vous disposez des éléments suivants :

* Accès à Fastly pour votre domaine.
* Fin du processus d’intégration de LLM Optimizer.
* Transfert du journal CDN vers LLM Optimizer terminé.
* Clé d’API Edge Optimize récupérée à partir de l’interface utilisateur de LLM Optimizer.

**Procédure de récupération de votre clé API :**

1. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

   ![Accéder à la configuration du client](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Sous **Routage du trafic AI pour déployer des optimisations**, cochez la case **Déployer des optimisations sur des agents AI**.

   ![Cochez la case Déployer les optimisations sur les agents AI](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Copiez la clé API et suivez les étapes de configuration du routage ci-dessous.

   ![Copier la clé API](/help/assets/optimize-at-edge/prereq-copy-api-key.png)

   >[!NOTE]
   >À ce stade, le statut peut afficher une croix rouge indiquant que la configuration n’est pas encore terminée. Cela est attendu : une fois que vous avez terminé la configuration de routage ci-dessous et que le trafic des robots d’IA commence à circuler, le statut se met à jour vers une coche verte confirmant que le routage est activé avec succès.

De plus, si vous avez besoin d’aide pour les étapes ci-dessus, contactez votre équipe de compte Adobe ou votre `llmo-at-edge@adobe.com`.

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

**Vérifier la configuration**

Pour tester la configuration, exécutez une curl et attendez-vous aux éléments suivants :

```
curl -svo /dev/null https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Le statut du routage du trafic peut également être vérifié dans l’interface utilisateur de LLM Optimizer. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

![Statut du routage du trafic AI avec routage activé](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

>[!TAB Akamai (BYOCDN)]

**Edge Optimize - Akamai (BYOCDN)**

Cette configuration achemine le trafic dynamique (requêtes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les visiteurs humains et les robots d&#39;optimisation du moteur de recherche continuent d&#39;être servis depuis votre origine comme d&#39;habitude. Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Avant de configurer les règles du gestionnaire de propriétés Akamai, vérifiez que vous disposez des éléments suivants :

* Accès au gestionnaire de propriétés Akamai pour votre domaine.
* Fin du processus d’intégration de LLM Optimizer.
* Transfert du journal CDN vers LLM Optimizer terminé.
* Clé d’API Edge Optimize récupérée à partir de l’interface utilisateur de LLM Optimizer.

**Procédure de récupération de votre clé API :**

1. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

   ![Accéder à la configuration du client](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Sous **Routage du trafic AI pour déployer des optimisations**, cochez la case **Déployer des optimisations sur des agents AI**.

   ![Cochez la case Déployer les optimisations sur les agents AI](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Copiez la clé API et suivez les étapes de configuration du routage ci-dessous.

   ![Copier la clé API](/help/assets/optimize-at-edge/prereq-copy-api-key.png)

   >[!NOTE]
   >À ce stade, le statut peut afficher une croix rouge indiquant que la configuration n’est pas encore terminée. Cela est attendu : une fois que vous avez terminé la configuration de routage ci-dessous et que le trafic des robots d’IA commence à circuler, le statut se met à jour vers une coche verte confirmant que le routage est activé avec succès.

De plus, si vous avez besoin d’aide pour les étapes ci-dessus, contactez votre équipe de compte Adobe ou votre `llmo-at-edge@adobe.com`.

**Configuration**

La règle Akamai Property Manager suivante achemine les agents utilisateur LLM vers Edge Optimize. La configuration contient les étapes suivantes :

**1. Définir les critères de routage (correspondance Utilisateur-Agent)**

Définissez le routage pour les user-agents suivants :

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

**Vérifier la configuration**

Pour tester la configuration, exécutez une curl et attendez-vous aux éléments suivants :

```
curl -svo /dev/null https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Le statut du routage du trafic peut également être vérifié dans l’interface utilisateur de LLM Optimizer. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

![Statut du routage du trafic AI avec routage activé](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

>[!TAB Cloudflare (BYOCDN)]

**Edge Optimize - Cloudflare (BYOCDN)**

Cette configuration achemine le trafic dynamique (requêtes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les visiteurs humains et les robots d&#39;optimisation du moteur de recherche continuent d&#39;être servis depuis votre origine comme d&#39;habitude. Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

**Conditions préalables**

Avant de configurer les règles de routage de CloudFlare Worker, vérifiez que vous disposez des éléments suivants :

* Un compte Cloudflare avec Workers activé sur votre domaine.
* Accès aux paramètres DNS de votre domaine dans Cloudflare.
* Fin du processus d’intégration de LLM Optimizer.
* Transfert du journal CDN vers LLM Optimizer terminé.
* Clé d’API Edge Optimize récupérée à partir de l’interface utilisateur de LLM Optimizer.

**Procédure de récupération de votre clé API :**

1. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

   ![Accéder à la configuration du client](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Sous **Routage du trafic AI pour déployer des optimisations**, cochez la case **Déployer des optimisations sur des agents AI**.

   ![Cochez la case Déployer les optimisations sur les agents AI](/help/assets/optimize-at-edge/prereq-deploy-checkbox.png)

3. Copiez la clé API et suivez les étapes de configuration du routage ci-dessous.

   ![Copier la clé API](/help/assets/optimize-at-edge/prereq-copy-api-key.png)

   >[!NOTE]
   >À ce stade, le statut peut afficher une croix rouge indiquant que la configuration n’est pas encore terminée. Cela est attendu : une fois que vous avez terminé la configuration de routage ci-dessous et que le trafic des robots d’IA commence à circuler, le statut se met à jour vers une coche verte confirmant que le routage est activé avec succès.

De plus, si vous avez besoin d’aide pour les étapes ci-dessus, contactez votre équipe de compte Adobe ou votre `llmo-at-edge@adobe.com`.

**Fonctionnement du routage**

Lorsque la configuration est correcte, une requête vers votre domaine (par exemple, `www.example.com/page.html`) provenant d’un agent utilisateur agentic est interceptée par le programme de travail Cloudflare et acheminée vers le serveur principal d’Edge Optimize. La requête du serveur principal inclut les en-têtes requis.

**Test de la requête du serveur principal**

Vous pouvez vérifier le routage en adressant une requête directe au serveur principal d’Edge Optimize.

```
curl -svo /dev/null https://live.edgeoptimize.net/page.html \
  -H 'x-forwarded-host: www.example.com' \
  -H 'x-edgeoptimize-url: /page.html' \
  -H 'x-edgeoptimize-api-key: $EDGE_OPTIMIZE_API_KEY' \
  -H 'x-edgeoptimize-config: LLMCLIENT=TRUE;'
```

**En-têtes obligatoires**

Les en-têtes suivants doivent être définis sur les requêtes du serveur principal d’Edge Optimize :

| En-tête | Description | Exemple |
|--------|-------------|---------|
| `x-forwarded-host` | Hôte d’origine de la requête. Obligatoire pour l’identification du domaine du site. | `www.example.com` |
| `x-edgeoptimize-url` | Le chemin d’URL d’origine et la chaîne de requête de la requête. | `/page.html` ou `/products?id=123` |
| `x-edgeoptimize-api-key` | Clé API fournie par Adobe pour votre domaine. | `your-api-key-here` |
| `x-edgeoptimize-config` | Chaîne de configuration pour la différenciation des clés de cache. | `LLMCLIENT=TRUE;` |

**Étape 1 : créer le programme de travail Cloudflare**

1. Connectez-vous à votre tableau de bord Cloudflare.
2. Accédez à **Programmes de travail et pages** dans la barre latérale.
3. Cliquez sur **Créer une application** puis sur **Créer un programme de travail**.
4. Nommez votre programme de travail (par exemple, `edge-optimize-router`).
5. Cliquez sur **Déployer** pour créer le programme de travail avec le code par défaut.

![Tableau de bord Cloudflare Workers](/help/assets/optimize-at-edge/cloudflare-workers-dashboard.png)

**Étape 2 : ajouter le code de programme de travail**

Après avoir créé le programme de travail, cliquez sur **Modifier le code** et remplacez le code par défaut par le suivant :

```javascript
/**
 * Edge Optimize BYOCDN - Cloudflare Worker
 *
 * This worker routes requests from agentic bots (AI/LLM user agents) to the
 * Edge Optimize backend service for optimized content delivery.
 *
 * Features:
 * - Routes agentic bot traffic to Edge Optimize backend
 * - Failover to origin on Edge Optimize errors (any 4XX or 5XX errors)
 * - Loop protection to prevent infinite redirects
 * - Human visitors and SEO bots are served from the origin as usual
 */

// List of agentic bot user agents to route to Edge Optimize
const AGENTIC_BOTS = [
  'AdobeEdgeOptimize-AI',
  'ChatGPT-User',
  'GPTBot',
  'OAI-SearchBot',
  'PerplexityBot',
  'Perplexity-User'
];

// Targeted paths for Edge Optimize routing
// Set to null to route all HTML pages, or specify an array of paths
const TARGETED_PATHS = null; // e.g., ['/', '/page.html', '/products']

// Failover configuration
// Failover on any 4XX client error or 5XX server error from Edge Optimize
const FAILOVER_ON_4XX = true; // Failover on any 4XX error (400-499)
const FAILOVER_ON_5XX = true; // Failover on any 5XX error (500-599)

export default {
  async fetch(request, env, ctx) {
    return await handleRequest(request, env, ctx);
  },
};

async function handleRequest(request, env, ctx) {
  const url = new URL(request.url);
  const userAgent = request.headers.get("user-agent")?.toLowerCase() || "";

  // Check if request is already processed (loop protection)
  const isEdgeOptimizeRequest = !!request.headers.get("x-edgeoptimize-request");

  // Construct the original path and query string
  const pathAndQuery = `${url.pathname}${url.search}`;

  // Check if the path matches HTML pages (no extension or .html extension)
  const isHtmlPage = /(?:\/[^./]+|\.html|\/)$/.test(url.pathname);

  // Check if path is in targeted paths (if specified)
  const isTargetedPath = TARGETED_PATHS === null
    ? isHtmlPage
    : (isHtmlPage && TARGETED_PATHS.includes(url.pathname));

  // Check if user agent is an agentic bot
  const isAgenticBot = AGENTIC_BOTS.some((ua) => userAgent.includes(ua.toLowerCase()));

  // Route to Edge Optimize if:
  // 1. Request is NOT already from Edge Optimize (prevents infinite loops)
  // 2. User agent matches one of the agentic bots
  // 3. Path is targeted for optimization
  if (!isEdgeOptimizeRequest && isAgenticBot && isTargetedPath) {

    // Build the Edge Optimize request URL
    const edgeOptimizeURL = `https://live.edgeoptimize.net${pathAndQuery}`;

    // Clone and modify headers for the Edge Optimize request
    const edgeOptimizeHeaders = new Headers(request.headers);

    // Remove any existing Edge Optimize headers for security
    edgeOptimizeHeaders.delete("x-edgeoptimize-api-key");
    edgeOptimizeHeaders.delete("x-edgeoptimize-url");
    edgeOptimizeHeaders.delete("x-edgeoptimize-config");

    // x-forwarded-host: The original site domain
    // Use environment variable if set, otherwise use the request host
    edgeOptimizeHeaders.set("x-forwarded-host", env.EDGE_OPTIMIZE_TARGET_HOST ?? url.host);

    // x-edgeoptimize-api-key: Your Adobe-provided API key
    edgeOptimizeHeaders.set("x-edgeoptimize-api-key", env.EDGE_OPTIMIZE_API_KEY);

    // x-edgeoptimize-url: The original request URL path and query
    edgeOptimizeHeaders.set("x-edgeoptimize-url", pathAndQuery);

    // x-edgeoptimize-config: Configuration for cache key differentiation
    edgeOptimizeHeaders.set("x-edgeoptimize-config", "LLMCLIENT=TRUE;");

    try {
      // Send request to Edge Optimize backend
      const edgeOptimizeResponse = await fetch(new Request(edgeOptimizeURL, {
        headers: edgeOptimizeHeaders,
        redirect: "manual", // Preserve redirect responses from Edge Optimize
      }), {
        cf: {
          cacheEverything: true, // Enable caching based on origin's cache-control headers
        },
      });

      // Check if we need to failover to origin
      const status = edgeOptimizeResponse.status;
      const is4xxError = FAILOVER_ON_4XX && status >= 400 && status < 500;
      const is5xxError = FAILOVER_ON_5XX && status >= 500 && status < 600;

      if (is4xxError || is5xxError) {
        console.log(`Edge Optimize returned ${status}, failing over to origin`);
        return await failoverToOrigin(request, env, url);
      }

      // Return the Edge Optimize response
      return edgeOptimizeResponse;

    } catch (error) {
      // Network error or timeout - failover to origin
      console.log(`Edge Optimize request failed: ${error.message}, failing over to origin`);
      return await failoverToOrigin(request, env, url);
    }
  }

  // For all other requests (human users, SEO bots), pass through unchanged
  return fetch(request);
}

/**
 * Failover to origin server when Edge Optimize returns an error
 * @param {Request} request - The original request
 * @param {Object} env - Environment variables
 * @param {URL} url - Parsed URL object
 */
async function failoverToOrigin(request, env, url) {
  // Build origin URL
  const originURL = `${url.protocol}//${env.EDGE_OPTIMIZE_TARGET_HOST}${url.pathname}${url.search}`;

  // Prepare headers - clean Edge Optimize headers and add loop protection
  const originHeaders = new Headers(request.headers);
  originHeaders.set("Host", env.EDGE_OPTIMIZE_TARGET_HOST);
  originHeaders.delete("x-edgeoptimize-api-key");
  originHeaders.delete("x-edgeoptimize-url");
  originHeaders.delete("x-edgeoptimize-config");
  originHeaders.delete("x-forwarded-host");
  originHeaders.set("x-edgeoptimize-request", "fo");

  // Create and send origin request
  const originRequest = new Request(originURL, {
    method: request.method,
    headers: originHeaders,
    body: request.body,
    redirect: "manual",
  });

  const originResponse = await fetch(originRequest);

  // Add failover marker header to response
  const modifiedResponse = new Response(originResponse.body, {
    status: originResponse.status,
    statusText: originResponse.statusText,
    headers: originResponse.headers,
  });
  modifiedResponse.headers.set("x-edgeoptimize-fo", "1");
  return modifiedResponse;
}
```

Cliquez sur **Enregistrer et déployer** pour publier le programme de travail.

![Éditeur de code de Cloudflare Worker](/help/assets/optimize-at-edge/cloudflare-worker-editor.png)

**Étape 3 : Configurer les variables d’environnement**

Les variables d’environnement stockent en toute sécurité une configuration sensible telle que votre clé API.

1. Dans les paramètres de votre programme de travail, accédez à **Paramètres** > **Variables**.
2. Sous **Variables d’environnement**, cliquez sur **Ajouter une variable**.
3. Ajoutez les variables suivantes :

   | Nom de variable | Description | Nécessaires |
   |---------------|-------------|----------|
   | `EDGE_OPTIMIZE_API_KEY` | Votre clé API Edge Optimize fournie par Adobe. | Oui |
   | `EDGE_OPTIMIZE_TARGET_HOST` | L’hôte cible des requêtes Edge Optimize (envoyées en tant qu’en-tête `x-forwarded-host`) et le domaine d’origine pour le basculement. Doit être le domaine uniquement sans protocole (par exemple, `www.example.com`, pas `https://www.example.com`). | Oui |

4. Pour la clé API, cliquez sur **Chiffrer** pour la stocker en toute sécurité.
5. Cliquez sur **Enregistrer et déployer**.

![Variables d’environnement Cloudflare](/help/assets/optimize-at-edge/cloudflare-env-variables.png)

**Étape 4 : ajouter un itinéraire à votre domaine**

Pour activer le programme de travail sur votre domaine :

1. Accédez au **Paramètres** > **Triggers** de votre programme de travail.
2. Sous **Itinéraires**, cliquez sur **Ajouter un itinéraire**.
3. Saisissez le modèle de votre domaine (par exemple, `www.example.com/*` ou `example.com/*`).
4. Sélectionnez la zone dans la liste déroulante.
5. Cliquez sur **Enregistrer**.

Vous pouvez également configurer des itinéraires au niveau de la zone :

1. Accédez à votre domaine dans Cloudflare.
2. Accédez à **Itinéraires de travail**.
3. Cliquez sur **Ajouter un itinéraire** et spécifiez le modèle et le programme de travail.

![Itinéraires du programme de travail de Cloudflare](/help/assets/optimize-at-edge/cloudflare-worker-routes.png)

**Étape 5 : vérifier la configuration**

Après le déploiement, testez la configuration en effectuant une requête avec un agent utilisateur.

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: chatgpt-user"
```

Une réponse réussie inclut l’en-tête `x-edgeoptimize-request-id` :

```
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

Le statut du routage du trafic peut également être vérifié dans l’interface utilisateur de LLM Optimizer. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

![Statut du routage du trafic AI avec routage activé](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

Vous pouvez également vérifier que le trafic normal continue de fonctionner :

```
curl -svo /dev/null https://www.example.com/page.html \
  --header "user-agent: Mozilla/5.0"
```

Cette requête doit être diffusée à partir de votre origine sans l’en-tête `x-edgeoptimize-request-id`.

**Vérification du comportement de basculement**

Si Edge Optimize n’est pas disponible ou renvoie une erreur, le programme de travail bascule automatiquement sur votre origine. Les réponses de basculement incluent l’en-tête `x-edgeoptimize-fo` :

```
< HTTP/2 200
< x-edgeoptimize-fo: 1
```

Vous pouvez surveiller les événements de basculement dans les journaux de Cloudflare Workers pour résoudre les problèmes.

**Comprendre la logique du programme de travail**

Le programme de travail de Cloudflare met en œuvre la logique suivante :

1. **Détection de l’agent utilisateur :** vérifie si l’agent utilisateur de la requête entrante correspond à l’un des robots agentic définis (non-respect de la casse).

2. **Ciblage des chemins d’accès :** filtre éventuellement les requêtes en fonction des chemins d’accès ciblés. Par défaut, toutes les pages d’HTML (URL se terminant par `/`, sans extension ou `.html`) sont acheminées. Vous pouvez spécifier des chemins d’accès spécifiques à l’aide du tableau `TARGETED_PATHS` .

3. **Protection contre les boucles :** l’en-tête `x-edgeoptimize-request` empêche les boucles infinies. Lorsqu’Edge Optimize renvoie les requêtes à votre origine, cet en-tête est défini sur `"1"` et le programme de travail transmet la requête sans la renvoyer à Edge Optimize.

4. **Sécurité des en-têtes :** avant de définir les en-têtes Edge Optimize, le programme de travail supprime tous les en-têtes `x-edgeoptimize-*` existants de la requête entrante pour empêcher les attaques par injection d’en-tête.

5. **Mappage des en-têtes :** le programme de travail définit les en-têtes requis pour Edge Optimize :
   * `x-forwarded-host` : identifie le domaine d’origine du site.
   * `x-edgeoptimize-url` - Conserve le chemin d’accès de la requête d’origine et la chaîne de requête.
   * `x-edgeoptimize-api-key` - Authentifie la requête avec Edge Optimize.
   * `x-edgeoptimize-config` - Fournit la configuration de la clé de cache.

6. **Logique de basculement :** si Edge Optimize renvoie un code d’état d’erreur (erreurs client 4XX ou erreurs serveur 5XX) ou si la requête échoue en raison d’une erreur réseau, le programme de travail bascule automatiquement sur votre origine à l’aide de `EDGE_OPTIMIZE_TARGET_HOST`. La réponse de basculement inclut l’en-tête `x-edgeoptimize-fo: 1` pour indiquer que le basculement s’est produit.

7. **Gestion des redirections :** l’option `redirect: "manual"` garantit que les réponses de redirection d’Edge Optimize sont transmises au client sans que le programme de travail ne les suive.

**Personnalisation de la configuration**

Vous pouvez personnaliser le comportement du programme de travail en modifiant les constantes de configuration en haut du code :

**Liste de robots agentiques**

Modifiez le tableau `AGENTIC_BOTS` pour ajouter ou supprimer des agents utilisateur :

```javascript
const AGENTIC_BOTS = [
  'AdobeEdgeOptimize-AI',
  'ChatGPT-User',
  'GPTBot',
  'OAI-SearchBot',
  'PerplexityBot',
  'Perplexity-User',
  // Add additional user agents as needed
  'ClaudeBot',
  'Anthropic-AI'
];
```

**Chemins ciblés**

Par défaut, toutes les pages HTML sont acheminées vers Edge Optimize. Pour limiter le routage à des chemins spécifiques, modifiez le tableau `TARGETED_PATHS` :

```javascript
// Route all HTML pages (default)
const TARGETED_PATHS = null;

// Or specify exact paths to route
const TARGETED_PATHS = ['/', '/page.html', '/products', '/about-us'];
```

**Configuration de basculement**

Par défaut, le programme de travail bascule sur toute erreur 4XX ou 5XX d’Edge Optimize. Personnalisez ce comportement :

```javascript
// Default: failover on any 4XX or 5XX error
const FAILOVER_ON_4XX = true;
const FAILOVER_ON_5XX = true;

// Failover only on 5XX server errors (not 4XX client errors)
const FAILOVER_ON_4XX = false;
const FAILOVER_ON_5XX = true;

// Disable automatic failover (not recommended)
const FAILOVER_ON_4XX = false;
const FAILOVER_ON_5XX = false;
```

**Points importants à prendre en compte**

* **Comportement de basculement :** le programme de travail bascule automatiquement sur votre origine si Edge Optimize renvoie une erreur (codes d’état 4XX ou 5XX) ou si la requête échoue en raison d’une erreur réseau. Le basculement utilise `EDGE_OPTIMIZE_TARGET_HOST` comme domaine d’origine (similaire au `F_Default_Origin` de Fastly ou au `Default_Origin` de CloudFront). Les réponses de basculement incluent l’en-tête `x-edgeoptimize-fo: 1`, que vous pouvez utiliser pour la surveillance et le débogage.

* **Mise en cache :** Cloudflare met en cache les réponses en fonction de l’URL par défaut. Le trafic des agents ne recevant pas le même contenu que le trafic humain, assurez-vous que la configuration du cache en tient compte. Envisagez d’utiliser l’API de cache ou les en-têtes de cache pour différencier le contenu mis en cache. L’en-tête `x-edgeoptimize-config` doit être inclus dans votre clé de cache.

* **Limitation de débit :** Surveillez l’utilisation d’Edge Optimizer et envisagez d’implémenter une limitation de débit pour le trafic agentic, si nécessaire.

* **Tests :** testez toujours la configuration dans un environnement d’évaluation avant de la déployer en production. Vérifiez que le trafic d&#39;agents et de personnes se comporte comme prévu. Testez le comportement de basculement en simulant les erreurs Edge Optimize.

* **Journalisation :** activez la journalisation de Cloudflare Workers pour surveiller les requêtes et résoudre les problèmes. Accédez à **Collaborateurs** > **votre collaborateur** > **Journaux** pour afficher les journaux en temps réel. Le programme de travail consigne les événements de basculement à des fins de débogage.

**Résolution des incidents**

| Problème | Cause possible | Solution |
|-------|----------------|----------|
| Aucun en-tête de `x-edgeoptimize-request-id` dans la réponse | Itinéraire de collaborateur non apparié ou agent utilisateur non présent dans la liste des robots d&#39;agent. | Vérifiez que votre modèle d’itinéraire correspond à l’URL de requête. Vérifiez que l’agent utilisateur se trouve dans le tableau `AGENTIC_BOTS`. |
| Erreurs 401 ou 403 d’Edge Optimize | Clé API non valide ou manquante. | Vérifiez que `EDGE_OPTIMIZE_API_KEY` est correctement défini dans les variables d’environnement. Contactez Adobe pour confirmer que votre clé API est active. |
| Redirections infinies ou boucles | L’en-tête de protection contre les boucles n’est pas défini ou vérifié correctement. | Assurez-vous que la vérification de l’en-tête `x-edgeoptimize-request` est en place. |
| Trafic humain affecté | La logique de routage des collaborateurs est trop large. | Vérifiez que la logique de correspondance de l’agent utilisateur est correcte et ne respecte pas la casse. Vérifiez que `TARGETED_PATHS` est correctement configuré. |
| Temps de réponse lents | Latence réseau vers le serveur principal d’Edge Optimize. | Cela est prévu pour la première requête ; les requêtes suivantes sont mises en cache dans Edge Optimize. |
| En-tête `x-edgeoptimize-fo: 1` en réponse | Edge Optimize a renvoyé une erreur et le basculement vers l’origine s’est produit. | Vérifiez les journaux de Cloudflare Workers pour connaître le code d’erreur spécifique. Vérifiez l’état du service Edge Optimize avec Adobe. |
| Le basculement ne fonctionne pas | Indicateurs de basculement désactivés ou erreur dans la logique de basculement. | Vérifiez que `FAILOVER_ON_4XX` et `FAILOVER_ON_5XX` sont définis sur `true`. Recherchez des messages d&#39;erreur dans les journaux des collaborateurs. |
| Certains chemins ne sont pas optimisés. | Chemin ne correspondant pas aux chemins ciblés ou au modèle de page HTML. | Vérifiez que le chemin d’accès est en `TARGETED_PATHS` (s’il est spécifié) et correspond au modèle RegEx de page HTML. |
| Échec des requêtes avec un hôte non valide | `EDGE_OPTIMIZE_TARGET_HOST` inclut le protocole (par exemple, `https://`). | Utilisez uniquement le nom de domaine sans protocole (par exemple, `example.com`, et non `https://example.com`). |
| Erreur 530 lors du basculement | Cloudflare ne peut pas se connecter à l’origine ou la demande de basculement comporte des en-têtes non valides. | Assurez-vous que la fonction de basculement supprime les en-têtes Edge Optimize. Vérifiez que votre origine est accessible et que le DNS est correctement configuré. |

>[!ENDTABS]

>[!NOTE]
>Pour les autres fournisseurs de réseau CDN, contactez `llmo-at-edge@adobe.com` pour aider l’intégration de vos équipes informatiques/CDN. Une fois les configurations terminées, vous pouvez déployer des suggestions d’Optimize at Edge dans LLM Optimizer.

## Opportunités

Le tableau suivant présente les opportunités qui peuvent améliorer l’expérience web de l’agent et qui sont prises en charge par Optimize at Edge.

| Opportunité | Type | Identification automatique | Suggestion automatique | Optimisation automatiquement |
|---------|----------|----------|----------|----------|
| Restauration de la visibilité du contenu | Géolocalisation technique | Détecte les pages où le contenu critique est masqué aux agents d’IA. Affiche les URL affectées et le contenu attendu qui peut être récupéré. | Met en évidence le contenu qui peut être rendu disponible pour les agents d’IA et recommande d’activer le pré-rendu pour ces pages. | Fournit un instantané d’HTML complet et convivial pour le trafic généré par l’IA agentique qui récupère le contenu précédemment masqué. |
| Ajouter des résumés compatibles avec les LLM | Optimisation du contenu | Identifie les pages longues ou complexes qui ne disposent pas de résumés concis au niveau de la page ou de la section, ce qui les rend plus difficiles à analyser et à comprendre rapidement par l’IA. | Recommande des résumés courts générés par l’IA au niveau des pages et des sections qui capturent le contenu clé. | Insère les résumés dans les sections HTML appropriées, améliorant la façon dont les modèles interprètent et décrivent le contenu de la page. |
| Ajouter des FAQ pertinentes | Optimisation du contenu | Détecte les écarts d’intention dans le contenu de page existant qui pourraient tirer parti des questions fréquentes. | Suggère le contenu des FAQ générées par l’IA en fonction des intentions de l’utilisateur ou de l’utilisatrice et des rubriques existantes. | Injecte le contenu des FAQ en HTML, ce qui rend les pages plus détectables et pertinentes dans les réponses pilotées par l’IA. |
| Simplifier les contenus complexes | Optimisation du contenu | Indique les pages avec du texte complexe qui peut entraver la compréhension de l’IA. | Fournit des versions simplifiées de texte complexe générées par l’IA tout en préservant la signification d’origine. | Réécrit des sections complexes dans la page, améliorant ainsi la lisibilité de l’IA. |

### Outils supplémentaires

[Adobe LLM Optimizer : votre page web est-elle accessible ?](https://chromewebstore.google.com/detail/adobe-llm-optimizer-is-yo/jbjngahjjdgonbeinjlepfamjdmdcbcc) L’extension Chrome indique la proportion de contenu de page web auquel les LLM peuvent accéder et ce qui reste masqué. Conçue comme un outil de diagnostic autonome et gratuit, elle ne nécessite aucune licence de produit ni configuration.

En un seul clic, vous pouvez évaluer la lisibilité de n’importe quel site. Vous pouvez comparer côte à côte ce que voient les agents d’IA et ce que voient les utilisateurs et utilisatrices, et estimer la quantité de contenu pouvant être récupérée à l’aide de LLM Optimizer. Consultez la page [L’IA peut-elle lire votre site web ?](https://business.adobe.com/blog/introducing-the-llm-optimizer-chrome-extension) pour avoir plus d’informations.

## Opportunités détaillées

Dans les sections qui suivent, vous pouvez afficher des détails supplémentaires pour chaque opportunité prise en charge par Optimize at Edge.

### Restauration de la visibilité du contenu

Cette opportunité signale les pages où le contenu clé est masqué pour les agents d’IA en raison du rendu côté client. Pour chaque page identifiée, elle vous indique exactement quel contenu est absent de la vue de l’agent d’IA, met en évidence les écarts de visibilité et vous permet d’appliquer directement des modifications pour récupérer le contenu masqué. Lorsque vous déployez cette opportunité avec Optimize at Edge, une version pré-générée et optimisée par l’IA de la page est diffusée aux agents utilisateurs LLM afin qu’ils puissent accéder au contexte complet sans exécuter Javascript.
Cela permet de s’assurer que la page est d’abord entièrement visible par les agents d’IA. Des améliorations supplémentaires sont apportées en plus de ce rendu HTML prédéfini.

>[!IMPORTANT]
>Cette fonctionnalité de pré-rendu s’applique automatiquement à toutes les opportunités présentées ci-dessous lorsqu’elles sont déployées avec Optimize at Edge afin de s’assurer que la page est entièrement visible par les agents d’IA.

### Ajouter des résumés compatibles avec les LLM

Cette opportunité identifie les pages qui peuvent bénéficier de résumés concis pour aider les LLM à comprendre rapidement à quoi correspond le contenu de la page. Pour chaque page, l’opportunité détecte où un résumé est le plus nécessaire et crée des résumés générés par l’IA au niveau de la page ou de la section. Lorsque vous effectuez un déploiement avec Optimize at Edge, ces résumés sont insérés en HTML que les agents d’IA récupèrent, ce qui améliore les chances de voir votre contenu décrit plus précisément.

### Ajouter des FAQ pertinentes

Cette opportunité signale les pages où un contenu de questions/réponses supplémentaire pourrait mieux correspondre à l’intention de l’utilisateur ou de l’utilisatrice et aux prompts dans la découverte pilotée par l’IA. Pour chaque page, elle propose des blocs de FAQ générés par l’IA liés à l’intention de l’utilisateur ou l’utilisatrice et au contenu de la page. Avec Optimize at Edge, ces questions fréquentes sont insérées en HTML, ce qui rend votre page plus conviviale pour l’IA et augmente la probabilité que les réponses de l’IA reflètent directement vos recommandations.

### Simplifier les contenus complexes

Cette opportunité trouve des pages avec des paragraphes longs et complexes qui peuvent réduire la compréhension de l’IA. Pour chaque page qui dépasse les seuils de lisibilité, elle crée un contenu généré par l’IA plus simple et plus facile à analyser tout en préservant sa signification d’origine. Lorsqu’il est déployé en périphérie, le contenu simplifié diffusé au trafic généré par l’IA agentique aide les LLM à interpréter et résumer votre contenu plus fidèlement.

## Optimize at Edge automatique

Pour chaque opportunité, vous pouvez prévisualiser, modifier, déployer, afficher en direct et restaurer les optimisations en périphérie.

>[!VIDEO](https://video.tv.adobe.com/v/3477983/?learn=on&enablevpops)

### Prévisualiser

La **prévisualisation** vous permet de voir l’impact d’une suggestion avant sa mise en ligne. Elle fait apparaître une différence entre la page active et la version optimisée pour l’IA attendue après l’application de la suggestion. Cette vue utilise la même logique qu’Optimize at Edge qui alimentera le trafic en direct, mais dans un mode de prévisualisation isolé. Cela n’a aucune incidence sur le trafic en direct, car il s’agit d’une simulation en lecture seule pour révision.

![Prévisualisation](/help/assets/optimize-at-edge/preview.png)

### Modifier

**Modifier** permet d’affiner ou de réécrire complètement la suggestion générée automatiquement avant de la déployer. Au lieu d’accepter la suggestion, vous conservez un contrôle total via le workflow de modification. La vue affiche les modifications proposées dans un éditeur structuré, où vous pouvez modifier le texte pour qu’il corresponde mieux à votre intention d’origine. La version modifiée sera ensuite diffusée aux agents d’IA une fois déployée.

![Modifier](/help/assets/optimize-at-edge/edit.png)

### Déployer

**Déployer** publie les suggestions sélectionnées afin que les expériences optimisées puissent être diffusées de la périphérie aux agents d’IA. Si le réseau CDN est entièrement routé, toutes les pages du domaine sont généralement mises en ligne avec les nouvelles modifications en quelques minutes. Si le routage a été configuré pour certains chemins uniquement, seules les pages figurant sur la liste autorisée seront mises en ligne avec les optimisations.

![Déployer](/help/assets/optimize-at-edge/deploy.png)

### Afficher en direct

**Afficher en direct** vous permet de vérifier que l’optimisation est en ligne et se comporte comme prévu pour le trafic généré par l’IA agentique, une vue à laquelle il serait autrement difficile d’accéder. Vous pouvez afficher la page active sous les suggestions appliquées, ce qui effectue le rendu de la page comme indiqué aux agents d’IA.

![Afficher en direct](/help/assets/optimize-at-edge/view-live.png)

### Restauration

La restauration rétablit en toute sécurité une optimisation précédemment déployée. La version IA uniquement de la page est généralement renvoyée à son état précédent en quelques minutes, ce qui permet de tester en toute sécurité les optimisations si nécessaire.

![Restauration](/help/assets/optimize-at-edge/rollback.png)

## Questions fréquentes

Q : Quels types de LLM ciblez-vous avec Optimize at Edge ?

Vous définissez la liste des agents utilisateurs à cibler lors du processus d’intégration.

<!--Q. What does "Edge" in Optimize at Edge mean?

In our context, "Edge" means that the optimization is applied at the CDN layer and not inside your CMS.

Q. Why does this optimization require a CDN?

The CDN is where the optimized version of the page is assembled and delivered to AI agents. We leverage the CDN to ensure your origin CMS remains unchanged. This separation lets you improve LLM visibility without altering your existing publishing workflows.-->

Q : Que se passe-t-il si je ne suis pas encore intégré à Optimize at Edge ?

Si vous cliquez sur **Déployer les optimisations** avant d’avoir terminé la configuration requise, rien ne sera appliqué à votre site. Au lieu de cela, une boîte de dialogue contextuelle vous invite à contacter notre équipe à l’adresse `llmo-at-edge@adobe.com` pour obtenir de l’aide sur l’intégration. Pendant l’exécution de l’intégration, vous pouvez toujours explorer les opportunités et les suggestions détectées, mais le workflow de déploiement en un clic restera inactif.

Q : Que se passe-t-il lorsque le contenu est mis à jour à la source ?

Nous diffusons la version optimisée de votre page à partir du cache tant que la page source sous-jacente n’a pas changé. Cependant, lorsque la source est modifiée pour **Recover Visibilité du contenu**, notre système s’actualise automatiquement afin que les agents d’IA reçoivent toujours le contenu le plus récent. En effet, nous utilisons les paramètres de durée de vie (TTL) du cache réduits (par ordre de minutes) afin que toute mise à jour de contenu sur votre site déclenche une nouvelle optimisation dans cette fenêtre. Pour les opportunités de contenu telles que **Ajouter des résumés compatibles avec LLM**, LLM Optimizer surveille les modifications apportées à la page source. Si une modification est détectée, nous suspendons l’optimisation et la signalons pour révision humaine afin d’éviter toute dérive du contenu entre la page visible par l’agent et la page visible par l’homme.
<!--As there is no universal TTL that fits every site, we can configure this TTL based on your cache invalidation rules to ensure both systems stay in sync.-->

Q : La fonctionnalité Optimize at Edge est-elle réservée aux sites qui utilisent Adobe Edge Delivery Service (EDS) ?

Non. Le service Optimize at Edge est indépendant du réseau CDN et fonctionne avec n’importe quelle architecture front-end, et pas seulement avec celles déployées sur la pile Adobe EDS.

Q : En quoi le pré-rendu d’Optimize at Edge diffère-t-il du rendu côté serveur (SSR) traditionnel ?

Les deux résolvent différents problèmes et peuvent fonctionner ensemble. Le rendu côté serveur traditionnel effectue le rendu du contenu côté serveur, mais n’inclut pas le contenu chargé ultérieurement dans le navigateur. Le pré-rendu d’Optimize at Edge capture la page après le chargement des données côté client et JavaScript, produisant ainsi la version entièrement assemblée à la périphérie du réseau CDN. Le rendu côté serveur se concentre sur l’amélioration de l’expérience humaine et Optimize at Edge améliore l’expérience web pour les LLM.

Q. Que se passe-t-il si je déploie des optimisations pour certaines URL de mon domaine, mais pas toutes ?

Seules les URL que vous optimisez explicitement sont modifiées. Pour les URL avec des opportunités déployées, les agents d’IA reçoivent la version optimisée. Pour les URL sans opportunités déployées, notre service envoie simplement la page d’origine par proxy en l’état sans appliquer de modifications ni la stocker dans notre couche de cache d’optimisation. Vous pouvez ainsi déployer des optimisations de manière sélective sans affecter le reste de votre site.
