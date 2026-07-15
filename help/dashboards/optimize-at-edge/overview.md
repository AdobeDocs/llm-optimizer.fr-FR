---
title: Optimize at Edge
description: Découvrez comment diffuser des optimisations dans LLM Optimizer à la périphérie du réseau CDN sans apporter de modifications.
feature: Opportunities
autotag-review: '2026-07-15T18:10:00.249Z'
TQID: 'https://experienceleague.adobe.com/nRq5punuSnNb4XXIJzkO1NGF66tsyN1rdt-O9dd8tmU'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2:
  - id: bbfc1b77-44c5-4fe8-b65f-ec160fe0d021
  - id: a6256a78-8814-462c-9627-86699b39cee1
  - id: e0ec491f-fe51-42b6-801c-1c0dfcc0e64f
  - id: fe92ae96-fc87-4fea-96a0-adc06310d4f4
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: e9001ce2-5245-4a8e-8601-dd958009072f
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 3147
ht-degree: 67%

---


# Optimize at Edge

Cette page fournit un aperçu détaillé sur la manière de fournir des optimisations à la périphérie du réseau CDN sans aucune modification. Elle couvre le processus d’intégration, les opportunités d’optimisation disponibles et comment optimiser automatiquement à la périphérie.

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

Les opportunités qui peuvent améliorer l’expérience web agentique sont prises en charge avec Optimize at Edge. Pour en savoir plus sur chaque opportunité, consultez la page [Tableau de bord des opportunités](/help/dashboards/opportunities-overview.md) et la section des opportunités de la page active.

## Intégration

<!--You should reach out to either your Adobe account team or the FDE team to start the onboarding process. Your IT or CDN team is also required to complete the pre-requisites and setup process. Additionally, you can also contact `llmo-at-edge@adobe.com` for further onboarding assistance.-->

Démarrez le processus d’intégration dans votre compte LLM Optimizer :

1. Sur le tableau de bord **Configuration cliente**, sélectionnez l’onglet **Configuration du réseau CDN**.
1. Cliquez sur **Intégrer le CDN**.
   ![Onglet Configuration du réseau CDN](/help/overview/assets/cc-cdn.png)
1. Pour la clientèle Fastly gérée par AEM Cloud Service, la configuration du routage est en libre-service et peut être effectuée directement dans l’interface d’utilisation de LLM Optimizer. Pour la clientèle qui utilise d’autres fournisseurs de réseau CDN, votre équipe informatique/réseau CDN doit effectuer la configuration requise et remplir les conditions préalables. Vous pouvez également vous reporter aux exemples de guides CDN fournis ci-dessous pour obtenir des conseils supplémentaires.

>[!NOTE]
>Reportez-vous aux guides détaillés ci-dessous qui couvrent l’ensemble du flux d’intégration. Pour les problèmes non résolus par les guides, vous pouvez contacter `llmo-at-edge@adobe.com`.

Conditions requises pour votre équipe informatique/réseau CDN :

* Ajoutez l’utilisateur-agent `*AdobeEdgeOptimize/1.0*` à la liste autorisée dans le fichier robots.txt de votre site ou dans les règles de gestion du trafic de robots.
* Assurez-vous que les pages ne sont pas bloquées au niveau du domaine ou du réseau CDN.
* Ajoutez les règles de routage d’Optimize at Edge dans le réseau CDN.
* Si votre réseau CDN comporte des règles WAF ou Bot Manager, placez sur la liste autorisée l’agent utilisateur `*AdobeEdgeOptimize/1.0*`. Si une vérification supplémentaire est requise, configurez l’en-tête `x-edgeoptimize-fetcher-key`. Chaque guide BYOCDN ci-dessous comprend les étapes suivantes.
* Confirmez le routage d’Optimize at Edge dans l’interface LLM Optimizer.

Le diagramme suivant illustre le flux des requêtes dans une configuration BYOCDN avec Optimize at Edge :

![Flux de requête BYOCDN](/help/assets/optimize-at-edge/byocdn-request-flow.png)

>[!IMPORTANT]
>Le routage doit être configuré sur le réseau CDN externe (le réseau CDN le plus proche de la clientèle). Si vous disposez de plusieurs réseaux de diffusion de contenu, le routage ne peut être effectué qu’au niveau du réseau CDN externe.

Pour guider le processus de configuration, sélectionnez votre fournisseur de réseau CDN ci-dessous et suivez le guide de configuration correspondant. Gardez à l’esprit que ces exemples doivent être adaptés à votre configuration active réelle. Nous vous recommandons d’appliquer d’abord les modifications dans les environnements inférieurs.

### Guides de configuration du CDN

| Fournisseur de CDN | Type | Guide |
|---|---|---|
| Réseau CDN géré par AEM Cloud Service (Fastly) | Géré par Adobe | [Afficher le guide de configuration](/help/dashboards/optimize-at-edge/aemcs-managed-cdn.md) |
| Fastly (BYOCDN) | Utiliser votre propre CDN | [Afficher le guide de configuration](/help/dashboards/optimize-at-edge/fastly-byocdn.md) |
| Akamai (BYOCDN) | Utiliser votre propre CDN | [Afficher le guide de configuration](/help/dashboards/optimize-at-edge/akamai-byocdn.md) |
| Cloudflare (BYOCDN) | Utiliser votre propre CDN | [Afficher le guide de configuration](/help/dashboards/optimize-at-edge/cloudflare-byocdn.md) |
| CloudFront (BYOCDN) | Utiliser votre propre CDN | [Afficher le guide de configuration](/help/dashboards/optimize-at-edge/cloudfront-byocdn.md) |
| Portail d’Azure (BYOCDN) | Utiliser votre propre CDN | [Afficher le guide de configuration](/help/dashboards/optimize-at-edge/azure-front-door-byocdn.md) |

>[!NOTE]
>
>Si votre fournisseur de réseau CDN n’est pas répertorié ci-dessus ou si vous ne trouvez pas votre domaine ou votre adresse e-mail dans l’interface d’utilisation de LLM Optimizer, contactez `llmo-at-edge@adobe.com` pour obtenir de l’aide sur l’intégration. Une fois les configurations terminées, vous pouvez déployer des suggestions d’Optimize at Edge dans LLM Optimizer.

Chaque guide de configuration du réseau CDN ci-dessus comprend des étapes de vérification détaillées à la fin pour confirmer que le trafic généré par l’IA agentique est correctement acheminé et que le trafic humain n’est pas affecté.

## Opportunités

Le tableau suivant présente les opportunités qui peuvent améliorer l’expérience web de l’agent et qui sont prises en charge par Optimize at Edge.

| Opportunité | Type | Identification automatique | Suggestion automatique | Optimisation automatiquement |
|---------|----------|----------|----------|----------|
| [Restaurer la visibilité du contenu](/help/dashboards/opportunities/recover-content-visibility.md) | Géolocalisation technique | Détecte les pages où le contenu critique est masqué aux agents d’IA. Affiche les URL affectées et le contenu attendu qui peut être récupéré. | Met en évidence le contenu qui peut être rendu disponible pour les agents d’IA et recommande d’activer le pré-rendu pour ces pages. | Fournit un instantané d’HTML complet et convivial pour le trafic généré par l’IA agentique qui récupère le contenu précédemment masqué. |
| [Enrichir les pages de détails du produit](/help/dashboards/opportunities/enrich-product-detail-pages.md) | Géolocalisation technique | Pour les storefronts Adobe Commerce, compare les données de catalogue complètes aux données auxquelles les agents d’IA peuvent accéder sur chaque page de détails du produit. Aperçoit les PDP où les variantes, les spécifications, les attributs et les champs de catalogue associés sont absents de l’HTML visible par l’agent, avec la priorité du trafic de l’agent. | Met en évidence les informations de catalogue récupérables manquantes dans la vue de l’agent et pourquoi elles sont importantes pour la découverte de produits pilotée par LLM. | Diffuse un instantané d’HTML entièrement prégénéré et convivial vers le trafic d’agents à la périphérie du réseau CDN afin que les agents reçoivent un contexte de produit riche de votre catalogue sans CMS ni modifications de catalogue. |
| [Ajout de résumés compatibles avec LLM](/help/dashboards/opportunities/add-llm-friendly-summaries.md) | Optimisation du contenu | identifie les pages à trafic élevé qui ne disposent pas de résumés concis et de points clés structurés au niveau de la page ou de la section, ce qui les rend plus difficiles à analyser et à interpréter par les agents d’IA. | Recommande des résumés courts et générés par l’IA ainsi que des points clés fondés sur le contenu existant. | insère des résumés et des points clés dans les sections HTML appropriées, améliorant la façon dont les modèles interprètent et décrivent le contenu de la page. |
| [Ajout de questions fréquentes pertinentes](/help/dashboards/opportunities/add-relevant-faqs.md) | Optimisation du contenu | Identifie les pages à trafic élevé qui n’ont pas de contenu de questions/réponses structuré aligné sur votre jeu d’invites, ce qui rend plus difficile pour les agents d’IA de faire correspondre les questions des utilisateurs à votre page. | Suggère le contenu des FAQ générées par l’IA en fonction de l’intention des utilisateurs et des rubriques de page existantes. | Injecte le contenu des FAQ en HTML, ce qui rend les pages plus détectables et pertinentes dans les réponses pilotées par l’IA. |
| [Simplifier les contenus complexes](/help/dashboards/opportunities/simplify-complex-content.md) | Optimisation du contenu | Indique les pages avec du texte complexe qui peut entraver la compréhension de l’IA. | Fournit des versions simplifiées de texte complexe générées par l’IA tout en préservant la signification d’origine. | Réécrit des sections complexes dans la page, améliorant ainsi la lisibilité de l’IA. |
| [Ajouter une table des matières](/help/dashboards/opportunities/add-table-of-contents.md) | Géolocalisation technique | Détecte les pages qui ne disposent pas d’une organisation structurelle claire ou de titres de navigation, ce qui rend difficile, pour les agents d’IA, l’analyse et le mappage du contenu aux requêtes des utilisateurs. | Suggère une table des matières structurée avec des en-têtes liés qui reflètent les sections principales de la page. | Injecte une table des matières dans HTML, améliorant la structure des pages afin que les modèles d’IA puissent extraire, mapper et citer plus facilement les sections pertinentes. |
| [Ajouter des résumés de transcription multimédia](/help/dashboards/opportunities/add-multimedia-transcript-summaries.md) | Optimisation du contenu | Identifie les pages où des informations clés sont incorporées dans des vidéos ou d’autres médias sans transcriptions ou résumés lisibles par machine, ce qui rend leur contenu difficile à utiliser pour les agents d’IA. Affiche les URL affectées et le texte recommandé. | Recommande des résumés de transcription générés par l’IA qui soient ancrés dans les médias et les pages. | Insère des résumés de transcription dans HTML afin que le trafic de l’agent reçoive du texte lisible par la machine (par exemple, près de la vidéo appropriée). |

### Outils supplémentaires

L’extension de navigateur [AI Content Visibility Checker](https://chromewebstore.google.com/detail/ai-content-visibility-che/jbjngahjjdgonbeinjlepfamjdmdcbcc) indique quelle part du contenu de votre page web est accessible aux LLM et ce qui reste masqué. Conçue comme un outil de diagnostic autonome et gratuit, elle ne nécessite aucune licence de produit ni configuration.

En un seul clic, vous pouvez évaluer la lisibilité de n’importe quel site. Vous pouvez comparer côte à côte ce que voient les agents d’IA et ce que voient les utilisateurs et utilisatrices, et estimer la quantité de contenu pouvant être récupérée à l’aide de LLM Optimizer. Consultez la page [L’IA peut-elle lire votre site web ?](https://business.adobe.com/fr/blog/introducing-the-llm-optimizer-chrome-extension) pour avoir plus d’informations.

## Opportunités détaillées

Dans les sections qui suivent, vous pouvez afficher des détails supplémentaires pour chaque opportunité prise en charge par Optimize at Edge.

### Restauration de la visibilité du contenu

Cette opportunité signale les pages où le contenu clé est masqué pour les agents d’IA en raison du rendu côté client. Pour chaque page identifiée, elle vous indique exactement quel contenu est absent de la vue de l’agent d’IA, met en évidence les écarts de visibilité et vous permet d’appliquer directement des modifications pour récupérer le contenu masqué. Lorsque vous déployez cette opportunité avec Optimize at Edge, une version pré-générée et optimisée par l’IA de la page est diffusée aux agents utilisateurs LLM afin qu’ils puissent accéder au contexte complet sans exécuter Javascript.
Cela permet de s’assurer que la page est d’abord entièrement visible par les agents d’IA. Des améliorations supplémentaires sont apportées en plus de ce rendu HTML prédéfini.

>[!IMPORTANT]
>Cette fonctionnalité de pré-rendu s’applique automatiquement à toutes les opportunités présentées ci-dessous lorsqu’elles sont déployées avec Optimize at Edge afin de s’assurer que la page est entièrement visible par les agents d’IA.

Consultez la section [Restaurer la visibilité du contenu](/help/dashboards/opportunities/recover-content-visibility.md) pour obtenir une présentation du tableau de bord, les étapes de déploiement et les questions fréquentes.

### Enrichissement des pages de détails du produit

Cette opportunité cible les pages de détails du produit Adobe Commerce où les acheteurs voient le contexte complet du produit grâce à des expériences de storefront interactives, mais où les agents d’IA ne reçoivent qu’un instantané HTML superficiel. L’agent de catalogue compare votre catalogue Commerce faisant autorité au PDP visible par l’agent, répertorie chaque écart significatif (par exemple, les variantes ou les spécifications qui n’apparaissent jamais dans l’HTML statique) et vous permet de déployer une réponse Edge de robot uniquement qui restaure la parité pour les robots d&#39;exploration LLM sans modifier les enregistrements de catalogue ou l’interface utilisateur humaine.

Consultez [Enrichissement des pages Détails du produit](/help/dashboards/opportunities/enrich-product-detail-pages.md) pour une présentation du tableau de bord, les étapes de déploiement et les questions fréquentes.

### Ajouter des résumés compatibles avec les LLM

Cette opportunité identifie les pages à trafic élevé qui peuvent bénéficier de résumés concis et de points clés structurés afin que les gestionnaires de contenu puissent comprendre rapidement les revendications sur la page. Pour chaque page, il détecte où un résumé est le plus nécessaire et propose des résumés générés par l’IA (et des points clés le cas échéant) au niveau de la page ou de la section, sur la base du contenu existant. Lorsque vous effectuez un déploiement avec Optimize sur Edge, ce contenu est inséré dans HTML que les agents d’IA récupèrent, ce qui améliore la précision de la représentation de votre marque dans les réponses de l’IA.

Voir [Ajouter des résumés compatibles avec LLM](/help/dashboards/opportunities/add-llm-friendly-summaries.md) pour plus d’informations sur cette opportunité.

### Ajouter des FAQ pertinentes

Cette opportunité signale les pages à trafic élevé où un contenu de questions/réponses supplémentaire pourrait mieux correspondre à l’intention et aux invites de l’utilisateur dans la découverte pilotée par l’IA. Pour chaque page, il propose des blocs de FAQ générés par l’IA liés à votre jeu d’invites et au contenu de la page. Avec Optimize sur Edge, ces questions fréquentes sont insérées dans HTML, ce qui rend votre page plus conviviale pour l’IA et augmente la probabilité que les réponses de l’IA reflètent directement vos conseils.

Voir [Ajouter des questions fréquentes pertinentes](/help/dashboards/opportunities/add-relevant-faqs.md) pour une présentation du tableau de bord, les étapes de déploiement et les questions fréquentes.

### Simplifier les contenus complexes

Cette opportunité trouve des pages avec des paragraphes longs et complexes qui peuvent réduire la compréhension de l’IA. Pour chaque page qui dépasse les seuils de lisibilité, elle crée un contenu généré par l’IA plus simple et plus facile à analyser tout en préservant sa signification d’origine. Lorsqu’il est déployé en périphérie, le contenu simplifié diffusé au trafic généré par l’IA agentique aide les LLM à interpréter et résumer votre contenu plus fidèlement.

Consultez [Simplifier le contenu complexe](/help/dashboards/opportunities/simplify-complex-content.md) pour une présentation du tableau de bord, les étapes de déploiement et les questions fréquentes.

### Ajouter une table des matières

Cette opportunité détecte les pages difficiles à parcourir pour les agents d’IA, car les en-têtes et la structure des sections sont peu clairs ou manquants. Pour chaque page concernée, il propose une table des matières structurée avec des entrées liées à des ancres alignées sur les sections principales. Lorsque vous effectuez un déploiement avec Optimize sur Edge, cette table des matières est injectée dans HTML afin que les modèles puissent mapper de manière plus fiable les requêtes des utilisateurs aux parties droites de la page et les citer.

Voir [Ajouter la table des matières](/help/dashboards/opportunities/add-table-of-contents.md) pour une présentation du tableau de bord, les étapes de déploiement et les conseils sur l’accès anticipé.

### Ajouter des résumés de transcription multimédia

Cette opportunité cible les pages où les informations importantes ne résident que dans la lecture vidéo, sans transcriptions ni résumés textuels que les agents d’IA peuvent lire. Pour chaque page, il recommande des transcriptions générées par l’IA et de courts résumés des points clés des médias. Avec Optimize sur Edge, ces résumés sont ajoutés à HTML en tant que texte lisible par machine afin que les agents puissent utiliser la même substance que celle que les visiteurs humains obtiennent en regardant la vidéo.

Voir [Ajout de résumés de transcription multimédia](/help/dashboards/opportunities/add-multimedia-transcript-summaries.md) pour une présentation du tableau de bord, les étapes de déploiement et les questions fréquentes.

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

## Ressources supplémentaires

Pour plus d’informations sur la fonctionnalité Optimiser sur Edge , consultez la liste de lecture suivante : [LLM Optimizer — Optimiser sur Edge](https://www.youtube.com/playlist?list=PLzbVcr6JHocVSMWBCaCw4xxjQ_VFVvFh0).

## Questions fréquentes

Q : La clientèle en version d’essai peut-elle essayer Optimize at Edge ?

Oui, la clientèle en version d’essai peut accéder à une opportunité d’optimisation et la déployer sur 10 pages maximum. Par défaut, l’opportunité est Restaurer la visibilité du contenu, qui permet aux agents d’IA d’accéder à la version complète du contenu de votre page.

Q : Quels types de LLM ciblez-vous avec Optimize at Edge ?

Vous définissez la liste des agents utilisateurs à cibler lors du processus d’intégration.

<!--
Q. What does "Edge" in Optimize at Edge mean?

In our context, "Edge" means that the optimization is applied at the CDN layer and not inside your CMS.

Q. Why does this optimization require a CDN?

The CDN is where the optimized version of the page is assembled and delivered to AI agents. We leverage the CDN to ensure your origin CMS remains unchanged. This separation lets you improve LLM visibility without altering your existing publishing workflows.
-->

Q : Que se passe-t-il si je ne suis pas encore intégré à Optimize at Edge ?

Si vous cliquez sur **Déployer les optimisations** avant d’avoir terminé la configuration requise, rien ne sera appliqué à votre site. Au lieu de cela, une boîte de dialogue contextuelle vous invite à contacter notre équipe à l’adresse `llmo-at-edge@adobe.com` pour obtenir de l’aide sur l’intégration. Pendant l’exécution de l’intégration, vous pouvez toujours explorer les opportunités et les suggestions détectées, mais le workflow de déploiement en un clic restera inactif.

Q : Que se passe-t-il lorsque le contenu est mis à jour à la source ?

Nous diffusons la version optimisée de votre page à partir du cache tant que la page source sous-jacente n’a pas changé. Cependant, lorsque la source change pour la **restauration de la visibilité du contenu**, notre système s’actualise automatiquement afin que les agents IA reçoivent toujours le contenu le plus récent. En effet, nous utilisons les paramètres de durée de vie (TTL) du cache réduits (par ordre de minutes) afin que toute mise à jour de contenu sur votre site déclenche une nouvelle optimisation dans cette fenêtre. Pour les opportunités de contenu telles que **Ajouter des résumés compatibles avec LLM**, LLM Optimizer surveille les modifications apportées à la page source. Si une modification est détectée, nous suspendons l’optimisation et la signalons pour révision humaine afin d’éviter toute dérive du contenu entre la page visible par l’agent et la page visible par les personnes.
<!--As there is no universal TTL that fits every site, we can configure this TTL based on your cache invalidation rules to ensure both systems stay in sync.-->

Q : La fonctionnalité Optimize at Edge est-elle réservée aux sites qui utilisent Adobe Edge Delivery Service (EDS) ?

Non. Le service Optimize at Edge est indépendant du réseau CDN et fonctionne avec n’importe quelle architecture front-end, et pas seulement avec celles déployées sur la pile Adobe EDS.

Q : En quoi le pré-rendu d’Optimize at Edge diffère-t-il du rendu côté serveur (SSR) traditionnel ?

Les deux résolvent différents problèmes et peuvent fonctionner ensemble. Le rendu côté serveur traditionnel effectue le rendu du contenu côté serveur, mais n’inclut pas le contenu chargé ultérieurement dans le navigateur. Le pré-rendu d’Optimize at Edge capture la page après le chargement des données côté client et JavaScript, produisant ainsi la version entièrement assemblée à la périphérie du réseau CDN. Le rendu côté serveur se concentre sur l’amélioration de l’expérience humaine et Optimize at Edge améliore l’expérience web pour les LLM.

Q. La Visibilité du contenu de récupération (c’est-à-dire le pré-rendu) est-elle masquée ? Il semble qu’une version différente de la page soit diffusée aux agents d’IA.

Non. Le prérendu permet aux agents d’IA de voir le même contenu que celui déjà visible par les visiteurs humains et les robots d’optimisation du moteur de recherche. De nombreux sites chargent du contenu significatif avec JavaScript, que les agents d’IA classiques n’exécutent pas, de sorte qu’ils peuvent ignorer de grandes parties de la page. Le pré-rendu produit un instantané statique qui capture le texte complet afin que les agents reçoivent les mêmes informations que les humains et les moteurs de recherche. Il **restaure** la parité de contenu pour les LLM ; il n’ajoute ni ne modifie le contenu factuel.

Q. Qu’en est-il des autres possibilités de contenu, telles que l’ajout de résumés compatibles avec LLM, où une nouvelle copie apparaît sur la page diffusée aux agents ? C&#39;est du camouflage ?

Non. L’option Optimiser pour Edge n’introduit pas d’informations auxquelles les utilisateurs humains et les robots d&#39;exploration SEO ne peuvent pas accéder. Le service réorganise ou résume le contenu déjà existant sur la page afin que les agents d’IA puissent l’interpréter plus facilement. Lorsqu’une personne suit un lien à partir d’une réponse de l’IA vers votre site, elle peut toujours trouver les mêmes informations sous-jacentes sur la page active.

Q. Que se passe-t-il si je déploie des optimisations pour certaines URL de mon domaine, mais pas toutes ?

Seules les URL que vous optimisez explicitement sont modifiées. Pour les URL avec des opportunités déployées, les agents d’IA reçoivent la version optimisée. Pour les URL sans opportunités déployées, notre service envoie simplement la page d’origine par proxy en l’état sans appliquer de modifications ni la stocker dans notre couche de cache d’optimisation. Vous pouvez ainsi déployer des optimisations de manière sélective sans affecter le reste de votre site.
