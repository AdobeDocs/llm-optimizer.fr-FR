---
title: Bonnes pratiques relatives aux catégories, rubriques, invites et autres
description: Optimisez les informations LLM en configurant des catégories, des rubriques, des invites et d'autres marques pour effectuer le suivi, y compris les concurrents, pour une surveillance de marque personnalisée et une analyse de contenu stratégique.
feature: Best Practices, Customer Configuration
source-git-commit: f6d33387337ca097747407099891cbc6b586b9bb
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 2%

---


# Bonnes pratiques relatives à la configuration des catégories, rubriques, invites et autres à suivre

Cette section décrit les bonnes pratiques pour décider de la manière dont vous souhaitez configurer les catégories, rubriques, invites et autres éléments à suivre. En outre, il contient des informations sur la bibliothèque d’invites de l’industrie, qu’Adobe a développée grâce à des recherches approfondies menées avec des experts de l’industrie.

Il s&#39;agit d&#39;une première étape essentielle. Ce que vous décidez maintenant détermine la manière dont les informations sont adaptées au contexte de votre entreprise. Toute modification apportée aux catégories à l’avenir réinitialise les données historiques.

Dans le tableau de bord [[!UICONTROL Configuration du client]](/help/dashboards/customer-configuration.md), vous définissez la manière dont votre marque sera surveillée et analysée au sein de la plateforme LLM Optimizer. Voir [[!UICONTROL Configuration client]](/help/dashboards/customer-configuration.md) pour plus d’informations sur l’utilisation du tableau de bord.

![Fenêtre de configuration du client](/help/assets/best-practices/customer-configuration-best-practices.png)

Dans le tableau de bord [!UICONTROL Configuration du client], vous pouvez personnaliser des catégories (telles que des unités commerciales ou des lignes de produits), effectuer le suivi d’autres marques et ajouter des alias de mention de marque pour capturer toutes les variations de votre marque dans les invites. Cette configuration garantit que la plateforme adapte les informations à votre contexte commercial, ce qui permet une visibilité, un trafic et une analyse des opportunités précis.

## Bibliothèque de prompts sectoriels

Pour faciliter la prise en main des invites et des rubriques, Adobe a créé une bibliothèque d’invites du secteur développée à l’issue de recherches approfondies avec des experts du secteur et d’une analyse du comportement de Recherche optimisée par l&#39;IA auprès de plus de 6 000 clients. Cette bibliothèque identifie les sujets et les prompts les plus pertinents en fonction des tendances spécifiques au secteur, des objectifs commerciaux validés et des modèles concrets de recherche de clientèle.

Pour utiliser la bibliothèque d&#39;invites de secteur :

1. Accédez au tableau de bord **Configuration du client**.
1. Sélectionnez **Télécharger la bibliothèque d’invites** pour télécharger le fichier de bibliothèque à partir de LLM Optimizer.
   ![Téléchargement de bibliothèque d’invite du secteur](/help/assets/best-practices/customer-configuration-prompts-library.png)
1. Examinez les **rubriques** et **invites** suggérées pour le secteur de votre marque dans l’onglet correspondant et choisissez les options les plus pertinentes.
1. Consultez la **colonne Étape du Parcours client** pour afficher les options d’invite tout au long du cycle de vie du client (par exemple, découverte, conversion, rétention). Les invites de funnel à un stade précoce/en haut sont prioritaires, mais elles prennent également en compte les options d’étape ultérieure pour favoriser la rétention, activer le service clientèle, etc.
1. Modifiez les rubriques ou les invites selon les besoins pour mieux prendre en charge vos objectifs avant de charger vos rubriques et invites dans Adobe LLM Optimizer (par exemple, ajouter votre marque/nom de produit, ajouter la terminologie propre à la marque). Les invites peuvent être ajoutées à LLM Optimizer manuellement ou par chargement en masse à l&#39;aide du modèle *.csv* fourni.

>[!TIP]
>
> Utilisez une combinaison d’invites spécifiques au domaine recommandées par LLM Optimizer lors de la configuration initiale et la bibliothèque d’invites du secteur pour traiter votre stratégie d’invites.

### Fondation de recherche de la bibliothèque Prompt

La bibliothèque de l&#39;invitation à l&#39;industrie a été élaborée dans le cadre d&#39;une initiative de recherche exhaustive combinant :

* **Intelligence client :** analyse du comportement et des préférences Recherche optimisée par l&#39;IA sur plus de 6 000 clients
* **Expertise de l’industrie :** points de vue d’experts des secteurs de l’automobile, des services financiers, des soins de santé, des télécommunications et des voyages.
* **Informations axées sur les données :** identification des rubriques à fort impact et des modèles de requête qui stimulent l’engagement et la conversion des clients.

Principales rubriques recherchées par les clients de tous les secteurs d’activité :

* **Auto :** Résolution des problèmes automobiles, Comparaison des véhicules et Financement/Crédit-bail
* **Services financiers :** Recherche de produits financiers
* **Soins de santé :** recherche de symptômes ou de problèmes de santé, comparaison des options de traitement, compréhension des résultats de laboratoire ou des termes médicaux
* **Télécom :** Comparaison des plans, des conditions contractuelles et des promotions, Vérification du service dans la région locale
* **Voyage :** Se préparer pour un voyage, Rechercher et réserver un voyage

Tendances client sur Recherche optimisée par l&#39;IA et comportement d’invite dans les outils LLM :

* Les clients préfèrent poser des questions plutôt que d’utiliser des mots-clés lors de l’utilisation des outils de recherche LLM.
* Ils utilisent principalement des outils de recherche LLM pour les premiers stades de la recherche et de la découverte.
* Les clients ont tendance à mentionner une marque ou un nom de produit spécifique dans leurs invites.

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

![Ajout de catégories dans LLM Optimizer](/help/assets/best-practices/add-category.png)

>[!IMPORTANT]
>
> * Choisissez une approche et respectez-la.
> * Vous ne pouvez avoir qu’un seul modèle de catégorie **one** par compte/marque. Ne mélangez pas **SBU** et **URL_DIR** en même temps.
<!--Can you mix Product/Service with these?-->

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

![Ajout de rubriques dans LLM Optimizer](/help/assets/best-practices/add-topic.png)

Lors de la création de la liste, tenez compte des points suivants :

* Un éditeur peut-il comprendre le sujet en 5 secondes à partir du texte d’invite ? Si ce n’est pas le cas, renommez/simplifiez.
* Une autre équipe sera-t-elle propriétaire du correctif pour différents sujets ? Si oui, vous avez choisi des sujets utiles.
  <!-- Last bullet point does not make sense. Clarification needed. Also not sure what is meant by "editor"?-->

Quelques conseils utiles supplémentaires :

* Utilisez vos connaissances de votre entreprise ou de votre site pour définir des sujets qui correspondent aux objectifs stratégiques de votre marque
* Comparez votre marque à d’autres marques sur des sujets spécifiques.

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

## Bonnes pratiques de tracking des autres marques

Suivi Les autres vous permettent de surveiller la visibilité et les mentions dans les réponses LLM pour les invites et les sujets importants pour votre entreprise.

L’onglet [!UICONTROL **Suivi d’autres utilisateurs**] vous permet d’ajouter d’autres utilisateurs, y compris des concurrents, pour suivre leur visibilité pour des invites et des rubriques spécifiques.

Avec le suivi d’autres marques, vous pouvez voir à quelle fréquence d’autres marques sont mentionnées à côté de votre marque dans différentes régions et catégories et comparer leur visibilité à la vôtre.

>[!TIP]
>
>Examinez régulièrement les mentions et les citations des concurrents ou d&#39;autres entreprises afin de déterminer les domaines où votre marque peut s&#39;améliorer.

## En savoir plus

* Le [tableau de bord de configuration du client](/help/dashboards/customer-configuration.md) vous permet de configurer le suivi des catégories, rubriques, invites et autres.
* [Bonnes pratiques relatives à LLM Optimizer](/help/tutorials/best-practices.md) décrit les bonnes pratiques concernant l’optimisation de LLM

