---
title: Opportunités d’optimisation
description: Découvrez comment utiliser le tableau de bord des opportunités pour détecter automatiquement comment votre site peut être amélioré afin d’augmenter la visibilité de la marque.
feature: Opportunities
source-git-commit: c6e37395362262eb5fe8366473e76086e36d77e9
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---


# Opportunités d’optimisation

Les opportunités d’optimisation sont des informations automatiquement détectées qui montrent où votre site et votre présence externe peuvent être améliorés pour accroître la visibilité de la marque dans la recherche IA.

Ces optimisations incluent des correctifs sur la page (ajout de contenu structuré, de canoniques ou de résumés), des ajustements techniques (déblocage des robots d’IA ou résolution d’erreurs) et l’influence sur le contenu des sites tiers faisant autorité. La résolution de ces opportunités d’optimisation permet à votre marque d’être représentée avec précision et plus susceptible d’être citée dans les réponses génératives.

![Opportunités d’optimisation](/help/dashboards/assets/oport.png)

## Tableau de bord des opportunités

Les opportunités d’optimisation présentées sur le tableau de bord sont hiérarchisées en fonction des écarts entre les joueurs, des rubriques de tendance et des données de performance et sont présentées sous forme de liste. Vous pouvez rechercher une opportunité spécifique à l’aide du champ de recherche. En outre, les opportunités sont regroupées par balise. Vous pouvez cliquer directement sur une balise pour afficher toutes les opportunités regroupées sous cette balise.

Cliquez sur **Détails** pour ouvrir une fenêtre distincte dans laquelle vous trouverez plus d’informations et des conseils supplémentaires.

## Opportunités prises en charge

Vous trouverez ci-dessous un tableau des opportunités actuellement prises en charge :

| Opportunité | Type | Problèmes Identifiés | Suggestions de correctif |
|---------|----------|----------|----------|
| Résumer les paragraphes longs | Contenu (sur site) | Détecte les paragraphes qui dépassent les seuils de longueur recommandés. Affiche les URL concernées et les fragments de texte surdimensionnés. | Créez des résumés ou divisez du texte long en sections plus courtes et analysables. |
| Recommandations relatives au contenu structuré (FAQ) | Contenu (sur site) | Détecte les invites à forte popularité sans entrées de FAQ correspondantes. Affiche les invites associées, les catégories et les URL concernées. | Ajoutez des blocs de schéma de FAQ avec des réponses concises pour correspondre aux requêtes courantes. |
| Détecter l&#39;absence de Hreflang | Contenu (sur site) | Indique qu’il manque des attributs hreflang aux pages. Fournit les URL affectées et la couverture attendue par langue/région. | Implémentez des balises de redéfinition pour indiquer les versions localisées correctes. |
| Détecter les canoniques manquants | Contenu (sur site) | Recherche les pages sans balises canoniques ou dont les balises sont en conflit. Répertorie les URL concernées et les doublons. | Ajoutez des balises canoniques pointant vers la version préférée de chaque page. Assurer une utilisation cohérente entre les variantes. |
| Détecter les en-têtes vides | Contenu (sur site) | Indique les pages contenant des balises d’en-tête, mais pas de texte. Affiche l’URL et l’emplacement des balises vides. | Ajoutez un texte descriptif aux en-têtes qui reflètent le contenu sous ceux-ci. |
| Détecter les en-têtes en double | Contenu (sur site) | Analyse les en-têtes HTML et marque les en-têtes répétés. Affiche les URL concernées et les fragments de texte dupliqués. | Modifier les en-têtes pour qu’ils soient uniques et maintenir la hiérarchie (H1 → H2 → H3). Fusionner ou renommer les sections en double. |
| Détecter le trafic d’agent bloqué | GÉOLOCALISATION TECHNIQUE | Analyse les journaux du réseau CDN pour les requêtes bloquées provenant d’agents d’IA connus (par exemple, GPTBot, PerplexityBot). Indique les URL et les agents affectés. | Mettez à jour robots.txt ou les configurations de serveur pour autoriser l’accès aux robots d’exploration AI pris en charge, le cas échéant. |
| Détection des problèmes liés aux écrans 404/403/5xx | GÉOLOCALISATION TECHNIQUE | Surveille les journaux CDN pour les réponses d’erreur. Fréquence des rapports, URL affectées et estimation des accès perdus. | Correction de liens rompus, mise à jour des autorisations et résolution des problèmes côté serveur afin que le contenu clé renvoie 200 réponses. |
| Récupérer la visibilité du contenu (accès anticipé) | GÉOLOCALISATION TECHNIQUE | Indique les pages où le contenu critique est masqué aux agents d’IA. Affiche les URL affectées et le contenu attendu qui peut être récupéré. | pré-effectuer le rendu des pages afin que davantage de contenu soit disponible pour les agents d’IA sans exécution de JavaScript. |

### Récupérer l’opportunité de visibilité du contenu {#recover-contet}

Comme indiqué ci-dessus, l’opportunité de visibilité du contenu signale les pages où le contenu clé est perdu pour les agents d’IA en raison du rendu côté client. Pour chaque page identifiée, il vous indique exactement quel contenu est absent de la vue de l’agent d’IA, ce qui vous aide à identifier les écarts de visibilité. Elle est également prise en charge par une fonctionnalité de pré-rendu basée sur les serveurs Edge, qui peut diffuser plus de contenu HTML au trafic de l’agent sans nécessiter de modifications du système de gestion de contenu (CMS). Cette fonctionnalité est actuellement en accès anticipé et nécessite une configuration par l’équipe LLM Optimizer. Veuillez contacter `llmo-at-edge@adobe.com` pour activer l’opportunité de visibilité du contenu.

### Outils supplémentaires

Le [Vérificateur de visibilité LLM](https://chromewebstore.google.com/detail/is-your-webpage-citable/jbjngahjjdgonbeinjlepfamjdmdcbcc) est une extension de Chrome qui vous permet de voir exactement à quelle proportion du contenu de votre page web les LLM peuvent accéder, ainsi que ce qui reste masqué. Conçu comme un outil de diagnostic autonome et gratuit, il ne nécessite aucune licence de produit ni configuration. En un seul clic, les utilisateurs et utilisatrices peuvent évaluer la lisibilité de l’ordinateur de n’importe quel site et afficher côte à côte une comparaison de ce que voient les agents d’IA par rapport à ce que voient les utilisateurs et utilisatrices humains. En outre, estime la quantité de contenu pouvant être récupérée à l’aide de LLM Optimizer.
