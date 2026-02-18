---
title: Optimize at Edge
description: Découvrez comment diffuser des optimisations dans LLM Optimizer à la périphérie du réseau CDN sans apporter de modifications.
feature: Opportunities
source-git-commit: 23752b30294c3d467ca477b085aa521cad0f72ca
workflow-type: tm+mt
source-wordcount: '2172'
ht-degree: 85%

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

Pour guider le processus de configuration, sélectionnez votre fournisseur de réseau CDN ci-dessous et suivez le guide de configuration correspondant. Gardez à l’esprit que ces exemples doivent être adaptés à votre configuration active réelle. Nous vous recommandons d’appliquer d’abord les modifications dans les environnements inférieurs.

### Guides de configuration du réseau CDN

| Fournisseur de CDN | Type | Guide |
|---|---|---|
| Réseau CDN géré par AEM Cloud Service (Fastly) | Géré par Adobe | [Afficher le guide de configuration](/help/dashboards/optimize-at-edge-aem-managed-cdn.md) |
| Fastly (BYOCDN) | Apporter votre propre réseau CDN | [Afficher le guide de configuration](/help/dashboards/optimize-at-edge-fastly-byocdn.md) |
| Akamai (BYOCDN) | Apporter votre propre réseau CDN | [Afficher le guide de configuration](/help/dashboards/optimize-at-edge-akamai-byocdn.md) |
| Cloudflare (BYOCDN) | Apporter votre propre réseau CDN | [Afficher le guide de configuration](/help/dashboards/optimize-at-edge-cloudflare-byocdn.md) |

>[!NOTE]
>Si votre fournisseur de réseau CDN n’est pas répertorié ci-dessus ou si vous ne trouvez pas votre domaine ou votre adresse e-mail dans l’interface utilisateur de LLM Optimizer, contactez `llmo-at-edge@adobe.com` pour obtenir de l’aide sur l’intégration. Une fois les configurations terminées, vous pouvez déployer des suggestions d’Optimize at Edge dans LLM Optimizer.

Chaque guide de configuration du réseau CDN ci-dessus comprend des étapes de vérification détaillées à la fin pour confirmer que le trafic agent est correctement acheminé et que le trafic humain n’est pas affecté.

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

En un seul clic, vous pouvez évaluer la lisibilité de n’importe quel site. Vous pouvez comparer côte à côte ce que voient les agents d’IA et ce que voient les utilisateurs et utilisatrices, et estimer la quantité de contenu pouvant être récupérée à l’aide de LLM Optimizer. Consultez la page [L’IA peut-elle lire votre site web ?](https://business.adobe.com/fr/blog/introducing-the-llm-optimizer-chrome-extension) pour avoir plus d’informations.

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

>[!VIDEO](https://video.tv.adobe.com/v/3477986/?captions=fre_fr&learn=on&enablevpops)

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
