---
title: Opportunités d’optimisation
description: Découvrez comment utiliser le tableau de bord des opportunités pour détecter automatiquement comment votre site peut être amélioré afin d’augmenter la visibilité de la marque.
feature: Opportunities
source-git-commit: 82830e66d43ddd9741617cdf6daab63cd259554b
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 100%

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
| Résumer les paragraphes longs | Contenu (sur site) | Détecte les paragraphes qui dépassent les seuils de longueur recommandés. Affiche les URL concernées et les fragments de texte surdimensionnés. | Créez des résumés ou divisez du texte long en sections plus courtes et analysables. |
| Recommander du contenu structuré (questions fréquentes) | Contenu (sur site) | Détecte les prompts très populaires sans correspondance avec les entrées de questions fréquentes. Affiche les prompts associés, les catégories et les URL concernées. | Ajoutez des blocs de schéma de questions fréquentes avec des réponses concises pour correspondre aux requêtes courantes. |
| Détecter l’absence d’attributs hreflang | Contenu (sur site) | Indique les pages sans attributs hreflang. Fournit les URL affectées et la couverture attendue par langue/région. | Implémentez des balises hreflang pour indiquer les versions localisées correctes. |
| Détecter les balises canoniques manquantes | Contenu (sur site) | Recherche les pages sans balises canoniques ou avec des balises conflictuelles. Répertorie les URL concernées et les doublons. | Ajoutez des balises canoniques pointant vers la version préférée de chaque page. Assurez une utilisation cohérente entre les variantes. |
| Détecter le trafic bloqué généré par l’IA agentique | Géolocalisation technique | Analyse les journaux CDN pour les requêtes bloquées provenant d’agents d’IA connus (par exemple, GPTBot, PerplexityBot). Indique les URL et les agents affectés. | Mettez à jour robots.txt ou les configurations de serveur pour autoriser l’accès aux robots d’exploration d’IA pris en charge, le cas échéant. |
| Détecter les problèmes 404/403/5xx | Géolocalisation technique | Surveille les journaux CDN pour les réponses d’erreur. Indique la fréquence, les URL affectées et l’estimation des accès perdus. | Corrigez les liens rompus, mettez à jour des autorisations et résolvez les problèmes côté serveur afin que le contenu clé renvoie 200 réponses. |
| Récupérer la visibilité du contenu (accès anticipé) | Géolocalisation technique | Indique les pages où le contenu critique est masqué aux agents d’IA. Affiche les URL affectées et le contenu attendu qui peut être récupéré. | Effectuez un pré-rendu des pages afin que davantage de contenu soit disponible pour les agents d’IA sans exécution de JavaScript. |

## Optimisation automatique {#auto-optimization}

L’optimisation automatique permet le déploiement en un clic des optimisations recommandées, ce qui réduit l’effort manuel et le délai de rentabilité. Les optimisations peuvent être appliquées à la source de contenu ou au niveau du CDN. L’optimisation automatique basée sur Edge est actuellement disponible en accès anticipé pour certaines opportunités. Pour plus d’informations, consultez la page [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

<!--### Recover Content Visibility Opportunity {#recover-contet}

As stated above, the content visibility opportunity, flags pages where key content is lost for AI agents due to client-side rendering. For each identified page, it shows you exactly which content is missing from the AI agent view, helping you pinpoint visibility gaps. It's also supported by an edge-based pre-rendering capability that can serve more HTML content to agentic traffic without requiring Content Management System (CMS) changes. This functionality is currently in Early Access and requires setup from the LLM Optimizer team. Please contact `llmo-at-edge@adobe.com` to activate the content visibility opportunity.-->

### Outils supplémentaires

Le [vérificateur de visibilité LLM](https://chromewebstore.google.com/detail/is-your-webpage-citable/jbjngahjjdgonbeinjlepfamjdmdcbcc) est une extension de Chrome qui vous permet de voir exactement à quelle proportion du contenu de votre page web les LLM peuvent accéder, ainsi que ce qui reste masqué. Conçu comme un outil de diagnostic autonome et gratuit, il ne nécessite aucune licence de produit ni configuration. En un seul clic, les utilisateurs et utilisatrices peuvent évaluer la lisibilité de n’importe quel site et afficher côte à côte une comparaison de ce que voient les agents d’IA par rapport à ce que voient les utilisateurs et utilisatrices humains. En outre, il estime la quantité de contenu pouvant être récupérée à l’aide de LLM Optimizer.
