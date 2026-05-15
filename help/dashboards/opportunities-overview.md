---
title: Opportunités d’optimisation
description: Découvrez comment utiliser le tableau de bord des opportunités pour détecter automatiquement comment votre site peut être amélioré afin d’augmenter la visibilité de la marque.
feature: Opportunities
autotag-review: '2026-05-15T17:53:48.623Z'
TQID: 'https://experienceleague.adobe.com/FAbQhzuyT-kIitIaoVQ47dam-TpN-deU5Vbo1nmK5CA'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558
  - id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 1227
ht-degree: 31%

---


# Opportunités d’optimisation

Les opportunités d’optimisation sont des informations automatiquement détectées qui montrent où votre site et votre présence externe peuvent être améliorés afin d’augmenter la visibilité de la marque dans la recherche optimisée par l’IA.

Ces optimisations incluent des correctifs sur la page (ajout de contenu structuré, de balises canoniques ou de résumés), des ajustements techniques (déblocage des robots d’exploration d’IA ou résolution d’erreurs) et l’influence sur le contenu des sites tiers faisant autorité. En tirant parti de ces opportunités d’optimisation, votre marque sera représentée avec précision et aura plus de chance d’être citée dans les réponses issues de l’IA générative.

![Opportunités d’optimisation](/help/dashboards/assets/oport.png)

## Tableau de bord des opportunités

Les opportunités d’optimisation présentées sur le tableau de bord sont hiérarchisées en fonction des écarts avec les autres marques, des rubriques de tendance et des données de performance et sont affichées sous forme de liste. Vous pouvez rechercher une opportunité spécifique à l’aide du champ de recherche. En outre, les opportunités sont regroupées par balise. Vous pouvez cliquer directement sur une balise pour afficher toutes les opportunités regroupées sous cette balise.

Cliquez sur **Détails** pour ouvrir une fenêtre distincte dans laquelle vous trouverez plus d’informations et des conseils supplémentaires.

## Opportunités prises en charge

Vous trouverez ci-dessous un tableau des opportunités actuellement prises en charge :

| Opportunité | Type | Problèmes Identifiés | Suggestions de correction |
|---------|----------|----------|----------|
| [Ajout de résumés compatibles avec LLM](/help/dashboards/opportunities/add-llm-friendly-summaries.md) | Contenu (sur site) | identifie les pages à trafic élevé qui ne disposent pas de résumés concis et de points clés structurés au niveau de la page ou de la section, ce qui les rend plus difficiles pour les agents d’IA à analyser et à interpréter les revendications de marque. Affiche les URL concernées et où des résumés sont recommandés. | Consultez les résumés et les points clés générés par l’IA qui reposent sur le contenu existant, puis déployez-les à la périphérie du réseau CDN avec l’option Optimiser d’Edge afin que les agents reçoivent un contexte plus clair et analysable. |
| [Ajout de questions fréquentes pertinentes](/help/dashboards/opportunities/add-relevant-faqs.md) | Contenu (sur site) | Identifie les pages à trafic élevé qui n’ont pas de contenu de questions/réponses structuré aligné sur votre jeu d’invites, ce qui rend plus difficile pour les agents d’IA de faire correspondre les questions des utilisateurs à votre page. Affiche les URL affectées et l’emplacement dans lequel les questions fréquentes sont recommandées. | Examinez le contenu des FAQ généré par l’IA et aligné sur l’intention, ancré dans les documents de page existants, puis déployez-le à la périphérie du réseau CDN avec l’option Optimiser d’Edge afin que les agents reçoivent un contexte de questions-réponses plus clair. |
| [Ajouter des résumés de transcription multimédia](/help/dashboards/opportunities/add-multimedia-transcript-summaries.md) | Contenu (sur site) | Identifie les pages où des informations clés sont incorporées dans des vidéos ou d’autres médias sans transcriptions ou résumés lisibles par machine, ce qui rend leur contenu difficile à utiliser pour les agents d’IA. Affiche les URL affectées et le texte recommandé. | Passez en revue les résumés de transcription générés par l’IA qui sont ancrés dans le média et la page, puis déployez-les sur le réseau de diffusion de contenu avec l’option Optimiser d’Edge afin que les agents reçoivent du texte lisible par la machine (par exemple, près de la vidéo appropriée). |
| [Trafic bloqué par robots.txt](/help/dashboards/opportunities/traffic-blocked-by-robots.md) | Géolocalisation technique | Analyse votre fichier robots.txt à la recherche de règles qui bloquent de manière sélective les agents d’IA à partir de contenu qui est autrement accessible au public. Indique les URL affectées et les agents bloqués. | Mettez à jour votre fichier robots.txt pour autoriser l’accès aux robots d&#39;exploration d’IA pris en charge, le cas échéant. |
| [Erreurs de trafic agent](/help/dashboards/opportunities/agentic-traffic-errors.md) | Géolocalisation technique | Surveille les journaux CDN pour les réponses d’erreur 404, 403 et 5xx renvoyées aux agents d’IA. Rapports sur les URL affectées et le nombre total d’accès perdus. | Corrigez les liens rompus, mettez à jour des autorisations et résolvez les problèmes côté serveur afin que le contenu clé renvoie 200 réponses. |
| [Simplifier les contenus complexes](/help/dashboards/opportunities/simplify-complex-content.md) | Contenu (sur site) | identifie les pages à trafic élevé où la copie dense ou complexe se trouve en dessous des seuils de lisibilité, ce qui rend plus difficile l’interprétation des informations clés par les agents d’IA. Affiche les URL concernées et l’endroit où un texte simplifié est recommandé. | Examinez le texte amélioré généré par l’IA qui repose sur le contenu de la page existante, puis déployez-le en périphérie du réseau CDN avec l’option Optimiser d’Edge afin que les agents reçoivent des passages plus clairs et plus faciles à analyser. |
| [Récupérer la Visibilité du contenu &#x200B;](/help/dashboards/opportunities/recover-content-visibility.md) | Géolocalisation technique | Indique les pages où le contenu critique est masqué aux agents d’IA. Affiche les URL affectées et le contenu attendu qui peut être récupéré. | Effectuez le pré-rendu des pages au niveau de la couche CDN à l’aide de l’option Optimiser sur Edge afin que davantage de contenu soit disponible pour les agents d’IA sans exécution JavaScript. |
| [Ajouter une table des matières](/help/dashboards/opportunities/add-table-of-contents.md) | Géolocalisation technique | Détecte les pages qui ne disposent pas d’une organisation structurelle claire ou de titres de navigation, ce qui rend difficile, pour les agents d’IA, l’analyse et le mappage du contenu aux requêtes des utilisateurs. Affiche les URL concernées et l’emplacement où une table des matières structurée est recommandée. | Consultez la table des matières structurée suggérée avec des en-têtes liés à une ancre qui reflètent les sections principales de la page, puis déployez-la à l’extrémité du réseau CDN avec Optimiser dans Edge afin qu’une table des matières soit injectée dans HTML, améliorant ainsi la structure de la page afin que les modèles puissent plus facilement extraire, mapper et citer les sections pertinentes. |
| [Analyse Wikipédia](/help/dashboards/opportunities/wikipedia-analysis.md) | Hors site | Analyse la page Wikipédia de votre entreprise par rapport à ses concurrents du secteur en termes de références, de sections, de longueur du contenu, d’images et d’exhaustivité de la boîte de réception. Identifie les écarts spécifiques où votre page se situe en dessous des références du secteur. | Consultez les recommandations stratégiques générées par l’IA pour améliorer votre présence sur Wikipédia, y compris l’ajout de références, l’enrichissement de votre boîte de réception, le développement des sections et l’amélioration de la qualité des articles. |
| [Analyse de Sentiment YouTube (Beta)](/help/dashboards/opportunities/youtube-sentiment-analysis.md) | Hors site, réseaux sociaux et communauté | Analyse les vidéos YouTube citées pour votre invite de Présence des marques définie pour les mentions de marque, le sentiment, la part de voix et les rubriques récurrentes. S’affiche uniquement lorsque des vidéos YouTube sont détectées comme citations pour votre ensemble d’invites. | Examinez les recommandations prioritaires pour améliorer la perception de la marque dans le contenu de YouTube, y compris les actions suggérées et les équipes responsables de leur mise en œuvre. |
| [Reddit Sentiment Analysis (Beta)](/help/dashboards/opportunities/reddit-sentiment-analysis.md) | Hors site, réseaux sociaux et communauté | Analyse les threads Reddit cités pour votre invite de Présence des marques définie pour les mentions de marque, le sentiment, la part de voix et les rubriques récurrentes. S&#39;affiche uniquement lorsque des threads Reddit sont détectés comme citations pour votre ensemble d&#39;invites. | Examiner les recommandations prioritaires pour améliorer la perception de la marque dans le contenu Reddit, y compris les actions suggérées et les équipes responsables de les mettre en œuvre. |
| [Analyse du Sentiment cité (Beta)](/help/dashboards/opportunities/cited-sentiment-analysis.md) | Hors site, réseaux sociaux et communauté | Analyse les URL les plus citées détectées pour votre invite de Présence des marques définie pour les mentions de marque, le sentiment, la part de voix et les rubriques récurrentes. | Examinez les recommandations prioritaires pour améliorer la perception de la marque sur les pages les plus citées par les systèmes d’IA en répondant aux invites sur votre marque. |
| [Enrichissement du catalogue de produits (Beta)](/help/dashboards/opportunities/enrich-product-catalog.md) | Contenu (sur site), Adobe Commerce | Identifie les produits du catalogue Commerce dont les noms ou descriptions sont trop génériques, techniquement denses ou ambigus pour que les LLM puissent les interpréter. Affiche les PDP évalués, le contexte de trafic d’agent et les enrichissements narratifs générés par l’IA. | Passez en revue et modifiez les noms et descriptions de produits proposés, puis déployez des optimisations pour publier des mises à jour directement dans votre catalogue Adobe Commerce (avec restauration à partir de suggestions fixes). |
| [Enrichir les pages de détails du produit](/help/dashboards/opportunities/enrich-product-detail-pages.md) | GÉO technique, Adobe Commerce | Pour les storefronts Adobe Commerce, compare les données de catalogue complètes aux données auxquelles les agents d’IA peuvent accéder sur chaque page de détails du produit. Aperçoit les PDP où les variantes, les spécifications, les attributs et les champs de catalogue associés sont absents de l’HTML visible par l’agent, avec la priorité du trafic de l’agent. | Met en évidence les informations de catalogue récupérables manquantes dans la vue de l’agent et l’importance de celles-ci pour la découverte de produits pilotée par LLM ; déployez avec Optimize sur Edge pour diffuser un instantané d’HTML entièrement prégénéré et convivial vers le trafic d’agent à la périphérie du réseau CDN, afin que les agents reçoivent un contexte de produit riche de votre catalogue sans modifications du catalogue ou de CMS. |

## Optimisation automatique {#auto-optimization}

L’optimisation automatique permet le déploiement en un clic des optimisations recommandées, ce qui réduit l’effort manuel et le délai de rentabilité. Les optimisations peuvent être appliquées à la source de contenu ou au niveau du CDN. L’optimisation automatique basée sur Edge est actuellement disponible en accès anticipé pour certaines opportunités. Pour plus d’informations, consultez la page [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

<!--
### Recover Content Visibility Opportunity {#recover-contet}

As stated above, the content visibility opportunity, flags pages where key content is lost for AI agents due to client-side rendering. For each identified page, it shows you exactly which content is missing from the AI agent view, helping you pinpoint visibility gaps. It's also supported by an edge-based pre-rendering capability that can serve more HTML content to agentic traffic without requiring Content Management System (CMS) changes. This functionality is currently in Early Access and requires setup from the LLM Optimizer team. Please contact `llmo-at-edge@adobe.com` to activate the content visibility opportunity.
-->

### Outils supplémentaires

Le [vérificateur de visibilité LLM](https://chromewebstore.google.com/detail/is-your-webpage-citable/jbjngahjjdgonbeinjlepfamjdmdcbcc) est une extension de Chrome qui vous permet de voir exactement à quelle proportion du contenu de votre page web les LLM peuvent accéder, ainsi que ce qui reste masqué. Conçu comme un outil de diagnostic autonome et gratuit, il ne nécessite aucune licence de produit ni configuration. En un seul clic, les utilisateurs et utilisatrices peuvent évaluer la lisibilité de n’importe quel site et afficher côte à côte une comparaison de ce que voient les agents d’IA par rapport à ce que voient les utilisateurs et utilisatrices humains. En outre, il estime la quantité de contenu pouvant être récupérée à l’aide de LLM Optimizer.

<!--
| Detect Missing Hreflang | Content (Onsite)| Flags pages missing hreflang attributes. Provides affected URLs and expected coverage by language/region.| Implement hreflang tags to indicate correct localized versions. |
| Detect Missing Canonicals | Content (Onsite) | Scans for pages without canonical tags or with conflicting tags. Lists affected URLs and duplicates. | Add canonical tags pointing to the preferred version of each page. Ensure consistent usage across variants. |
-->
