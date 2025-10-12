---
title: Bonnes pratiques relatives aux catégories, rubriques et invites
description: Optimisez les informations LLM en configurant les catégories, les rubriques, les invites et les concurrents pour une surveillance de marque personnalisée et une analyse de contenu stratégique.
source-git-commit: c7c66566137ad1f5bda89f55748b9d81ddf36f76
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 0%

---


# Bonnes pratiques relatives à la configuration des catégories, rubriques, invites et concurrents

Cette section décrit les bonnes pratiques pour décider de la manière dont vous souhaitez configurer vos catégories, rubriques, invites et concurrents.

Il s&#39;agit d&#39;une première étape essentielle. Ce que vous décidez maintenant détermine la manière dont les informations sont adaptées au contexte de votre entreprise. Toute modification apportée aux catégories à l’avenir réinitialise les données historiques.

Dans le tableau de bord [[!UICONTROL Configuration du client]](/help/dashboards/customer-configuration.md), vous définissez la manière dont votre marque sera surveillée et analysée au sein de la plateforme LLM Optimizer. Voir [[!UICONTROL Configuration client]](/help/dashboards/customer-configuration.md) pour plus d’informations sur l’utilisation du tableau de bord.

![Fenêtre de configuration du client](/help/assets/best-practices/customer-configuration-best-practices.png)

Dans le tableau de bord [!UICONTROL Configuration du client], vous pouvez personnaliser des catégories (telles que des unités commerciales ou des lignes de produits), effectuer le suivi des concurrents et ajouter des alias de mention de marque pour capturer toutes les variations de votre marque dans les invites. Cette configuration garantit que la plateforme adapte les informations à votre contexte commercial, ce qui permet une visibilité, un trafic et une analyse des opportunités précis.

## Bonnes pratiques pour les catégories

Les catégories permettent d’organiser votre contenu en unités opérationnelles stratégiques ou en regroupements logiques. Il s’agit du compartiment « comme il se doit » et de la structure organisationnelle de niveau supérieur de votre contenu.

Lorsque vous décidez de la manière de configurer des catégories, vous devez tenir compte de vos objectifs et de qui doit agir sur ce que vous signalez.

>[!IMPORTANT]
>
> Assurez-vous que les catégories sont correctement configurées dès le départ, car les modifications apportées aux catégories réinitialisent les données historiques. Cela signifie que si vous modifiez ces éléments, vous perdez les données historiques antérieures à la modification.

Voici un aperçu des types d’approches que vous pouvez adopter et du moment où vous devez choisir une approche particulière :

| Approche | Description | Avantage |
|---------|----------|---------|
| Unité opérationnelle stratégique (SBU) | Utilisez cette approche si votre organisation est divisée par P&amp;L (par exemple, Consommateur, Entreprise, Services). | Vous obtenez des rapports clairs par secteur d&#39;activité et une responsabilisation plus facile. |
| Répertoire de niveau supérieur du site Web (URL_DIR) | Utilisez si l’architecture des informations de votre site reflète la propriété (/products/, /support/, /docs/, /news/). | Vous obtenez une harmonisation avec la façon dont les équipes publient et gèrent le contenu. |
| Catégorie de produit (ou service) | Utilisez-le si vous vendez un catalogue (SKU/services). | Vous obtenez des vues assorties, une analyse des écarts et des réponses « quelle catégorie a besoin de contenu ». |

La manière de décider de la configuration des catégories repose sur une question : **Qui doit agir sur le rapport ?**

* Si vous êtes un *chef d&#39;entreprise*, choisissez l&#39;approche **SBU**.
* Si vous êtes un *propriétaire de contenu/web*, choisissez l’approche **URL_DIR**.
* Si vous êtes un *responsable du marchandisage/des offres*, choisissez l’approche **Catégorie de produit/service**.

>[!IMPORTANT]
>
> * Choisissez une approche et respectez-la.
> * Vous ne pouvez avoir qu’un seul modèle de catégorie **one** par compte/marque. Ne mélangez pas **SBU** et **URL_DIR** en même temps.
>   <!--Can you mix Product/Service with these?-->

Exemple :

| Type de site | Catégorie | Exemples de taxonomie de rubrique |
|---------|----------|---------|
| Entreprises ayant plusieurs entreprises | SBU | Petit ensemble d’intentions (procédure, dépannage, comparaison, tarification, politique) |
| Site lourd de documentation/support | URL_DIR | Comment, dépannage, référence, notes de mise à jour |
| Catalogue eCommerce/Services | Produit/Service | Comparaison, Avis, Prix/Disponibilité, Comment faire, Dépannage |

## Bonnes pratiques relatives aux rubriques

Les rubriques vous aident à comprendre l’intention de l’utilisateur : elles vous montrent ce que celui-ci souhaite. Ils vous permettent de regrouper les invites avec une intention d&#39;utilisateur similaire. Considérez cela comme un regroupement des invites pertinentes.

>[!IMPORTANT]
>
>Les rubriques sont universelles dans **toutes** les catégories, ce qui signifie qu’elles restent cohérentes quelle que soit la catégorie à laquelle elles sont affectées. Ils représentent des groupes de questions ou d’invites qui partagent une intention commune.

Lorsque vous décidez des sujets, vous souhaitez créer une liste courte et plate (6-12 maximum). Par exemple :

* Produits/Services
* Comment (configuration/utilisation)
* Résolution des problèmes (erreurs/problèmes)
* Comparaison (X contre Y ; « meilleur ... pour ... »)
* Examens et évaluations
* Tarifs et disponibilité
* Politique et garantie
* Contact d’assistance
* Corporate/News (si vous en avez vraiment besoin)

Lors de la création de la liste, tenez compte des points suivants :

* Un éditeur peut-il comprendre le sujet en 5 secondes à partir du texte d’invite ? Si ce n’est pas le cas, renommez/simplifiez.
* Une autre équipe sera-t-elle propriétaire du correctif pour différents sujets ? Si oui, vous avez choisi des sujets utiles.
  <!-- Last bullet point does not make sense. Clarification needed. Also not sure what is meant by "editor"?-->

Quelques conseils utiles supplémentaires :

* Utilisez vos connaissances de votre entreprise ou de votre site pour définir des sujets qui correspondent aux objectifs stratégiques de votre marque
* Examinez comment votre marque se compare à ses concurrents sur des sujets spécifiques.

>[!IMPORTANT]
>
> * Conservez les rubriques basées sur l’intention, et non sur l’organisation.
> * N’ajoutez pas de catégories/filtres pour les marques/non-marques/zones géographiques, car vous pouvez les filtrer spécifiquement dans l’onglet **[!UICONTROL Marques]**.
> * Les sujets sont répartis en plusieurs catégories. Vous **pouvez pas définir** rubriques uniques pour chaque catégorie.
> * Une seule invite **peut** existe dans plusieurs rubriques ou catégories.

## Bonnes pratiques relatives aux invites

Les invites identifient les questions ou requêtes spécifiques que les clients posent, ce qui peut avoir un impact sur votre entreprise. Il s’agit des questions ou requêtes réelles que les utilisateurs saisissent dans les LLM.

Examinez et mettez à jour régulièrement les invites pour vous assurer qu&#39;elles correspondent aux besoins du client et aux objectifs de l&#39;entreprise.

Recommandations relatives aux invites :

* Regroupez les invites similaires en fonction de ce que les utilisateurs demandent.
* Concentrez-vous sur les invites les plus importantes pour vos clients.
* Vérifiez si votre marque a de bonnes chances d’être mentionnée pour certaines invites.

>[!TIP]
>
>* Vous pouvez utiliser des outils tels que Adobe LLM Optimizer et la console de recherche Google avec des filtres RegEx pour identifier les structures de questions courantes (par exemple, « comment », « quoi », « quand », « où ») et découvrir les invites que les personnes utilisent pour visiter votre site.
>* Pour savoir quelles invites sont pertinentes pour votre site/marque, vous pouvez utiliser les données de recherche sur site, les FAQ dans les pages de résultats des moteurs de recherche ou même demander directement aux chatbots LLM quelles questions les clients peuvent poser sur votre marque.

## Bonnes pratiques pour les concurrents

Les concurrents vous permettent de surveiller la visibilité et les mentions dans les réponses LLM pour les invites et les sujets importants pour votre entreprise.

L’onglet [!UICONTROL **Suivi des concurrents**] vous permet d’ajouter des concurrents et de suivre leur visibilité pour des invites et des sujets spécifiques.

Grâce au suivi des concurrents, vous pouvez voir à quelle fréquence les concurrents sont mentionnés aux côtés de votre marque dans différentes régions et catégories et comparer leur visibilité à la vôtre.

>[!TIP]
>
>Examinez régulièrement les mentions et citations des concurrents pour identifier les domaines dans lesquels votre marque peut s&#39;améliorer.

## En savoir plus

* Le [tableau de bord de configuration du client](/help/dashboards/customer-configuration.md) vous permet de configurer vos catégories, rubriques, invites et concurrents.
* [Bonnes pratiques relatives à LLM Optimizer](/help/tutorials/best-practices.md) décrit les bonnes pratiques concernant l’optimisation de LLM

