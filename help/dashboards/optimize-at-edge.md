---
title: Optimiser dans Edge
description: Découvrez comment diffuser des optimisations dans LLM Optimizer à la périphérie du réseau CDN sans apporter de modifications de création requises.
feature: Opportunities
source-git-commit: eb8bdf9144aebb85171a529a3cc25034be5b076e
workflow-type: tm+mt
source-wordcount: '2291'
ht-degree: 1%

---


# Optimiser dans Edge

Cette page fournit un aperçu détaillé sur la manière de fournir des optimisations à la périphérie du réseau CDN sans aucune modification de création. Elle couvre le processus d’intégration, les opportunités d’optimisation disponibles et comment optimiser automatiquement à la périphérie.

>[!NOTE]
>Cette fonctionnalité est actuellement en accès anticipé. Vous pouvez en savoir plus sur les programmes d’accès anticipé [ici](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current#aem-beta-programs).

## Qu’est-ce que l’optimisation chez Edge ?

Optimize at Edge est une fonctionnalité de déploiement Edge dans LLM Optimizer qui apporte des modifications conviviales pour l’IA aux agents utilisateurs LLM. Dans le contexte actuel, « Edge » signifie que l’optimisation est appliquée au niveau de la couche CDN. Comme il fournit des optimisations au niveau de la couche CDN, aucune modification de création dans le système de gestion de contenu (CMS) n’est nécessaire afin que votre CMS d’origine reste inchangé. Cette séparation vous permet d’améliorer la visibilité de LLM sans modifier vos workflows de publication existants. Il cible uniquement le trafic d’agents et n’a aucune incidence sur les utilisateurs humains ou les robots SEO. Lorsque LLM Optimizer détecte des opportunités d’optimisation d’une page, les utilisateurs peuvent déployer des correctifs directement sur le réseau de diffusion de contenu.

Optimize chez Edge est une alternative plus rapide et plus épurée aux correctifs traditionnels qui nécessitent des efforts d’ingénierie complexes. Comme mentionné, une fois une configuration unique terminée, aucune modification de plateforme ni aucun long cycle de développement ne sont nécessaires pour appliquer les modifications. Vous pouvez publier des améliorations en quelques minutes sans nécessiter l’engagement des développeurs. Il s’agit d’une méthode sans code permettant d’optimiser votre site web pour les agents d’IA.

Optimize at Edge est conçu pour les utilisateurs professionnels des équipes de marketing, d’optimisation du référencement, de contenu et de stratégie numérique. Il peut permettre aux utilisateurs professionnels d’effectuer l’ensemble du parcours dans LLM Optimizer : identification des opportunités, compréhension des suggestions et déploiement facile des correctifs. Avec Optimiser sur Edge, les utilisateurs et utilisatrices peuvent prévisualiser les modifications, les déployer rapidement à l’extrémité du réseau CDN et vérifier que les optimisations sont actives. Les performances peuvent être suivies dans l’écosystème LLM Optimizer.

### Principaux avantages

* Diffusion **IA uniquement) :** diffuse HTML optimisé uniquement aux agents d’IA, sans impact sur les visiteurs humains ou les robots d’optimisation du moteur de recherche (SEO).
* **Cycles plus rapides :** publiez les modifications en quelques minutes et non en quelques semaines. Aucune modification de la plateforme ou de longs cycles d’ingénierie n’est nécessaire.
* **Réversible :** pris en charge avec une fonctionnalité de restauration en un clic qui peut rétablir la page en quelques minutes.
* **Aucun impact sur les performances :** les optimisations et la mise en cache basées sur Edge n’affectent pas la latence du site.
* **Indépendant du réseau de diffusion de contenu et de CMS :** fonctionne avec n’importe quelle configuration de réseau CDN et configuration front-end, quel que soit le système de gestion de contenu.

### Quelles sont les opportunités prises en charge avec Optimize chez Edge ?

Les opportunités qui peuvent améliorer l’expérience web agentique sont prises en charge avec Optimizer sur Edge. Pour en savoir plus sur chaque opportunité, consultez la page [Tableau de bord des opportunités](/help/dashboards/opportunities.md) et la section des opportunités de la page active.

## Intégration

Contactez l’équipe de votre compte Adobe ou l’équipe FDE pour démarrer le processus d’intégration. Votre équipe informatique ou réseau CDN doit également terminer le processus de configuration et les conditions préalables. Vous pouvez également contacter `llmo-at-edge@adobe.com` pour obtenir une aide supplémentaire à l’intégration.

Conditions préalables à l’intégration d’Optimize à Edge :

* Terminez le processus d’intégration à LLM Optimizer.
* Terminez le processus de transfert des journaux pour vos journaux CDN.

Conditions requises pour votre équipe informatique/réseau CDN :

* Générez une clé API.
* Ajoutez Optimiser au niveau des règles de routage Edge dans le réseau CDN.
* Placez sur la liste autorisée les chemins définis par l’utilisateur pour l’ensemble du domaine.
* Ajoutez une liste définie par l’utilisateur d’agents utilisateur LLM à cibler.
* Assurez-vous `robots.txt`’il ne bloque aucun agent utilisateur destiné à cibler.
* Confirmez l’optimisation au niveau du routage Edge dans l’interface LLM Optimizer.

Pour guider le processus de configuration, vous trouverez ci-dessous des exemples de configuration pour un certain nombre de configurations de réseau CDN. Gardez à l’esprit que ces exemples doivent être adaptés à votre configuration active réelle. Nous vous recommandons d’appliquer d’abord les modifications dans les environnements inférieurs.

>[!BEGINTABS]

>[!TAB Réseau CDN géré par Adobe]

**Réseau CDN géré par Adobe**

L’objectif de cette configuration est de configurer des requêtes avec des agents utilisateurs et utilisatrices authentiques qui seront acheminés vers le service Optimizer (serveur principal `live.edgeoptimize.net`). Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

```
curl -svo page.html https://frescopa.coffee/about-us --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

La configuration du routage est effectuée à l’aide d’une règle [originSelector CDN](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic#origin-selectors). Les prérequis sont les suivants :

* décider du domaine à acheminer
* décidez des chemins à acheminer
* décidez des agents utilisateur à acheminer (regex recommandée)

Pour déployer la règle, vous devez effectuer les opérations suivantes :

* créez un [pipeline de configuration](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/operations/config-pipeline)
* validez le fichier de configuration `cdn.yaml` dans votre référentiel
* exécution du pipeline de configuration


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

Pour tester la configuration, exécutez une curl et attendez-vous aux éléments suivants :

```
curl -svo page.html https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

>[!TAB Fastly (BYOCDN)]

**Edge Optimize BYOCDN - Fastly - VCL**

![Fastly VCL](/help/assets/optimize-at-edge/fastly-vcl.png)

![Ajouter des fragments de code VCL](/help/assets/optimize-at-edge/add-vcl-snippets.png)

**fragment de code vcl_recv**

```
unset req.http.x-edgeoptimize-url;
unset req.http.x-edgeoptimize-config;
unset req.http.x-edgeoptimize-api-key;

if (!req.http.x-edgeoptimize-request
    && req.http.user-agent ~ "(?i)(AdobeEdgeOptimize-AI|ChatGPT-User|GPTBot|OAI-SearchBot|PerplexityBot|Perplexity-User)") {
  set req.http.x-fowarded-host = req.http.host; # required for identifying the original host
  set req.http.x-edgeoptimize-url = req.url; # required for identifying the original url
  set req.http.x-edgeoptimize-config = "LLMCLIENT=true"; # required for cache key
  set req.http.x-edgeoptimize-api-key = "<YOUR API KEY>"; # required for identifying the client
  set req.backend = F_EDGE_OPTIMIZE;
}
```

**fragment de code vcl_hash**

```
if (req.http.x-edgeoptimize-config) {
  set req.hash += "edge-optimize";
  set req.hash += req.http.x-edgeoptimize-config;
}
```

**fragment de code vcl_delivery**

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

>[!TAB Akamai (BYOCDN)]

**Edge Optimize BYOCDN - Akamai**

L’objectif de cette configuration est d’acheminer les requêtes des agents utilisateurs de l’agent vers le service Edge Optimize (serveur principal `live.edgeoptimize.net`). Pour tester la configuration, une fois la configuration terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.


**La règle JSON Akamai Property Manager suivante achemine les agents utilisateur LLM vers Edge Optimize :**

La configuration comprend les étapes suivantes :

**1. Définissez les critères de routage (correspondance Utilisateur-Agent)**

![Définir des critères de routage](/help/assets/optimize-at-edge/akamai-step1-routing.png)

**2. Définissez l’origine et le comportement SSL**

![Définir l’origine et le comportement SSL](/help/assets/optimize-at-edge/akamai-step2-origin.png)

**3. Définissez La Variable Clé De Cache**

![Définir la variable de clé de cache](/help/assets/optimize-at-edge/akamai-step3-cachekey.png)

**4. Règles de mise en cache**

![&#x200B; Règles de mise en cache &#x200B;](/help/assets/optimize-at-edge/akamai-step4-rules.png)

**5. Modifiez Les En-Têtes Des Requêtes Entrantes**

![Modifier les en-têtes des demandes entrantes](/help/assets/optimize-at-edge/akamai-step5-request.png)

6 **. Modifier les en-têtes de réponse entrante**

![Modifier les en-têtes de réponse entrante](/help/assets/optimize-at-edge/akamai-step6-response.png)

7 **. Modification de l’ID de cache**

![Modification de l’ID de cache](/help/assets/optimize-at-edge/akamai-step7-cacheid.png)

8 **. Basculement de site**

![Basculement de site](/help/assets/optimize-at-edge/akamai-step8-failover.png)

![Comportements de basculement](/help/assets/optimize-at-edge/akamai-step8-failover-behaviors.png)

![&#x200B; Règles de basculement &#x200B;](/help/assets/optimize-at-edge/akamai-step8-failover-rules.png)

![Réponse des comportements](/help/assets/optimize-at-edge/akamai-step8-behaviors-response.png)

Pour tester la configuration, exécutez une curl et attendez-vous aux éléments suivants :

```
curl -svo page.html https://www.example.com/page.html --header "user-agent: chatgpt-user"
< HTTP/2 200
< x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
```

>[!ENDTABS]

>[!NOTE]
>Pour les autres fournisseurs de réseau CDN, contactez `llmo-at-edge@adobe.com` pour aider vos équipes informatiques/CDN à l’intégration. Une fois les configurations de configuration terminées, vous pouvez déployer des suggestions d’optimisation sur les opportunités Edge dans LLM Optimizer.

## Opportunités

Le tableau suivant présente les opportunités qui peuvent améliorer l’expérience web de l’agent et qui sont prises en charge par Optimiser dans Edge.

| Opportunité | Type | Auto-identification | Suggestion automatique | Optimiser automatiquement |
|---------|----------|----------|----------|----------|
| Restaurer la visibilité du contenu | Géolocalisation technique | Détecte les pages où le contenu critique est masqué aux agents d’IA. Affiche les URL affectées et le contenu attendu qui peut être récupéré. | Met en évidence le contenu qui peut être rendu disponible pour les agents d’IA et recommande d’activer le pré-rendu pour ces pages. | Fournit un instantané d’HTML complet et convivial pour l’IA au trafic d’agents qui récupère le contenu précédemment masqué. |
| Optimiser les en-têtes pour les LLM | Optimisation du contenu | Analyse les en-têtes pour détecter les en-têtes vides, en double, manquants ou ambigus qui peuvent réduire la lisibilité de la machine. | Propose une hiérarchie d’en-têtes plus épurée et des libellés améliorés, et affiche un aperçu de la structure mise à jour pour chaque page. | Injecte la structure d’en-tête améliorée pour les agents d’IA, préservant votre conception visuelle tout en rendant la page plus lisible pour les LLM. |
| Ajouter des résumés compatibles avec LLM | Optimisation du contenu | Identifie les pages longues ou complexes qui ne disposent pas de résumés concis au niveau de la page ou de la section, ce qui les rend plus difficiles à analyser et à comprendre rapidement par l’IA. | Recommande des résumés courts générés par l’IA au niveau des pages et des sections qui capturent le contenu clé. | Insère les résumés dans les sections HTML appropriées, améliorant la façon dont les modèles interprètent et décrivent le contenu de la page. |
| Ajout de questions fréquentes pertinentes | Optimisation du contenu | Détecte les trous d’intention dans le contenu de page existant qui pourraient tirer parti des questions fréquentes. | Suggère le contenu des FAQ générées par l’IA en fonction des intentions de l’utilisateur et des rubriques existantes. | Injecte le contenu des FAQ dans HTML, ce qui rend les pages plus détectables et pertinentes dans les réponses pilotées par l’IA. |
| Simplification des contenus complexes | Optimisation du contenu | Indique les pages avec du texte complexe qui peut entraver la compréhension de l’IA. | Fournit des versions simplifiées de texte complexe générées par l’IA tout en préservant la signification d’origine. | Réécrit des sections complexes dans la page, améliorant ainsi la lisibilité de l’IA. |

### Outils supplémentaires

Le [Adobe LLM Optimizer : votre page web est-elle accessible ?](https://chromewebstore.google.com/detail/adobe-llm-optimizer-is-yo/jbjngahjjdgonbeinjlepfamjdmdcbcc) extension Chrome indique la proportion de contenu de page web auquel les LLM peuvent accéder et ce qui reste masqué. Conçu comme un outil de diagnostic autonome et gratuit, il ne nécessite aucune licence de produit ni configuration.

En un seul clic, vous pouvez évaluer la lisibilité de la machine de n’importe quel site. Vous pouvez comparer côte à côte ce que voient les agents d’IA et ce que voient les utilisateurs et utilisatrices, et estimer la quantité de contenu pouvant être récupérée à l’aide de LLM Optimizer. Consultez le [L’IA peut-elle lire votre site web ?](https://business.adobe.com/fr/blog/introducing-the-llm-optimizer-chrome-extension) plus d’informations.

## Opportunités détaillées

Dans les sections qui suivent, vous pouvez afficher des détails supplémentaires pour chaque opportunité prise en charge par Optimizer dans Edge.

### Restaurer la visibilité du contenu

Cette opportunité signale les pages où le contenu clé est masqué pour les agents d’IA en raison du rendu côté client. Pour chaque page identifiée, il vous indique exactement quel contenu est absent de la vue de l’agent d’IA, met en évidence les écarts de visibilité et vous permet d’appliquer directement des modifications pour récupérer le contenu masqué. Lorsque vous déployez cette opportunité avec Optimize sur Edge, une version pré-générée et optimisée par l’IA de la page est diffusée aux agents utilisateurs LLM afin qu’ils puissent accéder au contexte complet sans exécuter Javascript.
Cela permet de s’assurer que la page est d’abord entièrement visible par les agents d’IA. Des améliorations supplémentaires sont apportées en plus de ce rendu HTML prédéfini.

>[!IMPORTANT]
>Cette fonctionnalité de pré-rendu s’applique automatiquement à toutes les opportunités présentées ci-dessous lorsqu’elles sont déployées avec Optimiser sur Edge afin de s’assurer que la page est entièrement visible par les agents d’IA.

### Optimiser les en-têtes pour les LLM

Cette opportunité détecte les pages où la structure des en-têtes rend difficile, pour les agents d’IA, la compréhension de la page en raison de titres vides, en double, manquants ou ambigus. Pour chaque page affectée, l’opportunité fait apparaître les en-têtes sous-optimaux et recommande une hiérarchie plus claire. Lorsqu’ils sont déployés avec Optimize sur Edge, les en-têtes améliorés sont appliqués au trafic d’agent dans HTML diffusé. Cela permet une meilleure lisibilité de la machine tout en conservant la même disposition pour votre visage.

### Ajouter des résumés compatibles avec LLM

Cette opportunité identifie les pages qui peuvent bénéficier de résumés concis pour aider les gestionnaires de contenu à comprendre rapidement à quoi correspond le contenu de la page. Pour chaque page, l’opportunité détecte où un résumé est le plus nécessaire et crée des résumés générés par l’IA au niveau de la page ou de la section. Lorsque vous effectuez un déploiement avec Optimize sur Edge, ces résumés sont insérés dans l’HTML que les agents d’IA récupèrent, ce qui améliore les chances de voir votre contenu décrit plus précisément.

### Ajout de questions fréquentes pertinentes

Cette opportunité signale les pages où un contenu de questions/réponses supplémentaire pourrait mieux correspondre à l’intention de l’utilisateur et aux invites dans la découverte pilotée par l’IA. Pour chaque page, il propose des blocs de FAQ générés par l’IA liés à l’intention de l’utilisateur et au contenu de la page. Avec Optimize sur Edge, ces questions fréquentes sont insérées dans HTML, ce qui rend votre page plus conviviale pour l’IA et augmente la probabilité que les réponses de l’IA reflètent directement vos conseils.

### Simplification des contenus complexes

Cette opportunité trouve des pages avec des paragraphes longs et complexes qui peuvent réduire la compréhension de l’IA. Pour chaque page qui dépasse les seuils de lisibilité, il crée un contenu généré par l’IA plus simple et plus facile à analyser tout en préservant sa signification d’origine. Lorsqu’il est déployé en périphérie, le contenu simplifié diffusé au trafic d’agence aide les gestionnaires de contenu de terrain à interpréter et résumer votre contenu plus fidèlement.

## Optimisation automatique dans Edge

Pour chaque opportunité, vous pouvez prévisualiser, modifier, déployer, afficher en direct et restaurer les optimisations en périphérie.

>[!VIDEO](https://video.tv.adobe.com/v/3477983/?learn=on&enablevpops)

### Prévisualiser

La **Prévisualisation** vous permet de voir l’impact d’une suggestion avant sa mise en ligne. Elle fait apparaître une différence côte à côte entre la page active et la version optimisée pour l’IA attendue après l’application de la suggestion. Cette vue utilise la même logique Optimiser pour Edge qui alimentera le trafic en direct, mais dans un mode d’aperçu isolé. Cela n’a aucune incidence sur le trafic en direct, car il s’agit d’une simulation en lecture seule pour révision.

![Aperçu](/help/assets/optimize-at-edge/preview.png)

### Modifier

**Modifier** permet d’affiner ou de réécrire complètement la suggestion générée automatiquement avant de la déployer. Au lieu d’accepter la suggestion, vous conservez un contrôle total via le workflow de modification. La vue affiche les modifications proposées dans un éditeur structuré, où vous pouvez modifier le texte pour mieux correspondre à votre intention d’origine. La version modifiée sera ensuite diffusée aux agents d’IA une fois déployée.

![Modifier](/help/assets/optimize-at-edge/edit.png)

### Déployer

**Déployer** publie les suggestions sélectionnées afin que les expériences optimisées puissent être diffusées de la périphérie aux agents d’IA. Si le réseau CDN est entièrement routé, toutes les pages du domaine sont généralement mises en ligne avec les nouvelles modifications en quelques minutes. Placer sur la liste autorisée Si le routage a été configuré pour des chemins sélectionnés uniquement, seules les pages sélectionnées sont mises en ligne avec les optimisations.

![Déployer](/help/assets/optimize-at-edge/deploy.png)

### Afficher en direct

**Afficher en direct** vous permet de vérifier que l’optimisation est en ligne et se comporte comme prévu pour le trafic d’agent, une vue à laquelle il serait autrement difficile d’accéder. Vous pouvez afficher la page active sous Suggestions fixes , ce qui effectue le rendu de la page comme indiqué aux agents d’IA.

![Afficher en direct](/help/assets/optimize-at-edge/view-live.png)

### Restauration

La restauration en toute sécurité rétablit une optimisation précédemment déployée. La version AI uniquement de la page est généralement renvoyée à son état précédent en quelques minutes, ce qui permet de tester en toute sécurité les optimisations si nécessaire.

![Restaurer](/help/assets/optimize-at-edge/rollback.png)

## Questions fréquentes

Q. Quels types de gestion du cycle de vie ciblez-vous avec Optimize chez Edge ?

Vous définissez la liste des agents utilisateur à cibler lors du processus d’intégration.

<!--Q. What does "Edge" in Optimize at Edge mean?

In our context, "Edge" means that the optimization is applied at the CDN layer and not inside your CMS.

Q. Why does this optimization require a CDN?

The CDN is where the optimized version of the page is assembled and delivered to AI agents. We leverage the CDN to ensure your origin CMS remains unchanged. This separation lets you improve LLM visibility without altering your existing publishing workflows.-->

Q. Que se passe-t-il si je ne suis pas encore intégré à Optimize sur Edge ?

Si vous cliquez sur **Déployer les optimisations** avant d’avoir terminé la configuration requise, rien ne sera appliqué à votre site. Au lieu de cela, une boîte de dialogue contextuelle vous invite à contacter notre équipe à l’adresse `llmo-at-edge@adobe.com` pour obtenir de l’aide sur l’intégration. Jusqu’à ce que l’intégration soit terminée, vous pouvez toujours explorer les opportunités et les suggestions détectées, mais le workflow de déploiement en un clic restera inactif.

Q : Que se passe-t-il lorsque le contenu est mis à jour à la source ?

Nous diffusons la version optimisée de la page à partir du cache tant que la page source sous-jacente n’a pas changé. Cependant, lorsque la source change, notre système s’actualise automatiquement afin que les agents d’IA reçoivent toujours le contenu le plus récent. En effet, nous utilisons les paramètres de durée de vie (TTL) du cache réduits (par ordre de minutes) afin que toute mise à jour de contenu sur votre site déclenche une nouvelle optimisation dans cette fenêtre. <!--As there is no universal TTL that fits every site, we can configure this TTL based on your cache invalidation rules to ensure both systems stay in sync.-->

Q. L’optimisation sur Edge est-elle réservée aux sites qui utilisent Adobe Edge Delivery Service (EDS) ?

Nombre Le service Optimize at Edge est compatible avec le réseau CDN et fonctionne avec n’importe quelle architecture front-end, et pas seulement avec celles déployées sur la pile Adobe EDS.

Q. En quoi le pré-rendu d’Optimisation sur Edge diffère-t-il du rendu côté serveur (SSR) traditionnel ?

Les deux résolvent différents problèmes et peuvent fonctionner ensemble. Le rendu côté serveur traditionnel effectue le rendu du contenu côté serveur, mais n’inclut pas le contenu chargé ultérieurement dans le navigateur. Le pré-rendu Optimiser sur Edge capture la page après le chargement des données côté client et JavaScript, produisant ainsi la version entièrement assemblée à la périphérie du réseau CDN. Le rendu côté serveur se concentre sur l’amélioration de l’expérience humaine et Optimiser chez Edge améliore l’expérience web pour les LLM.
