---
title: Bonnes pratiques relatives aux catégories, rubriques, prompts et autres
description: Optimisez les informations des LLM en configurant des catégories, des rubriques, des prompts et d’autres marques pour effectuer le suivi, y compris de la concurrence, pour une surveillance de marque personnalisée et une analyse de contenu stratégique.
feature: Best Practices, Customer Configuration
source-git-commit: f6d33387337ca097747407099891cbc6b586b9bb
workflow-type: ht
source-wordcount: '1435'
ht-degree: 100%

---


# Bonnes pratiques relatives à la configuration des catégories, rubriques, prompts et autres marques à suivre

Cette section décrit les bonnes pratiques pour décider de la manière dont vous souhaitez configurer les catégories, rubriques, prompts et autres marques à suivre. En outre, elle contient des informations sur la bibliothèque de prompts sectoriels, qu’Adobe a développée grâce à des recherches approfondies menées avec des spécialistes de chaque secteur.

Il s’agit d’une première étape essentielle. Ce que vous décidez maintenant détermine la manière dont les informations sont adaptées au contexte de votre entreprise. Toute modification apportée aux catégories à l’avenir réinitialise les données historiques.

Dans le tableau de bord [[!UICONTROL Configuration cliente]](/help/dashboards/customer-configuration.md), vous définissez la manière dont votre marque sera surveillée et analysée au sein de la plateforme LLM Optimizer. Référez-vous à la [[!UICONTROL configuration cliente]](/help/dashboards/customer-configuration.md) pour plus d’informations sur l’utilisation du tableau de bord.

![Fenêtre de configuration cliente](/help/assets/best-practices/customer-configuration-best-practices.png)

Dans le tableau de bord [!UICONTROL Configuration cliente], vous pouvez personnaliser des catégories (telles que des unités commerciales ou des lignes de produits), effectuer le suivi d’autres marques et ajouter des alias de mention de marque pour capturer toutes les variations de votre marque dans les prompts. Cette configuration garantit que la plateforme adapte les informations à votre contexte commercial, ce qui permet une visibilité, un trafic et une analyse des opportunités précis.

## Bibliothèque de prompts sectoriels

Pour faciliter la prise en main des prompts et des rubriques, Adobe a créé une bibliothèque de prompts sectoriels développée à l’issue de recherches approfondies avec des spécialistes des différents secteurs et d’une analyse du comportement de recherche optimisée par l’IA auprès de plus de 6 000 clients et clientes. Cette bibliothèque identifie les sujets et les prompts les plus pertinents en fonction des tendances spécifiques au secteur, des objectifs commerciaux validés et des modèles concrets de recherche de clientèle.

Pour utiliser la bibliothèque de prompts sectoriels :

1. Accédez au tableau de bord **Configuration cliente**.
1. Sélectionnez **Télécharger la bibliothèque de prompts** pour télécharger le fichier de bibliothèque à partir de LLM Optimizer.
   ![Téléchargement de la bibliothèque de prompts sectoriels](/help/assets/best-practices/customer-configuration-prompts-library.png)
1. Examinez les **rubriques** et **prompts** suggérés pour le secteur de votre marque dans l’onglet correspondant et choisissez les options les plus pertinentes.
1. Consultez la **colonne Étape du parcours client** pour afficher les options de prompts tout au long du cycle de vie du client ou de la cliente (par exemple, découverte, conversion, rétention). Les prompts destinés aux premières étapes/au haut du tunnel sont hautement prioritaires, mais envisagez également des options pour les étapes ultérieures afin de favoriser la fidélisation, d’assurer le service clientèle, etc.
1. Modifiez les rubriques ou les prompts selon les besoins pour mieux prendre en charge vos objectifs avant de charger vos rubriques et prompts dans Adobe LLM Optimizer (par exemple, ajoutez votre marque/nom de produit, ajoutez la terminologie propre à la marque). Les prompts peuvent être ajoutés à LLM Optimizer manuellement ou par chargement en masse à l’aide du modèle *.csv* fourni.

>[!TIP]
>
> Utilisez une combinaison de prompts spécifiques au domaine recommandés par LLM Optimizer lors de la configuration initiale et la bibliothèque de prompts sectoriels pour élaborer votre stratégie relative aux prompts.

### Bases de la recherche de la bibliothèque de prompts

La bibliothèque de prompts sectoriels a été élaborée dans le cadre d’une initiative de recherche exhaustive combinant les éléments suivants :

* **Intelligence client :** analyse du comportement et des préférences de recherche optimisée par l’IA sur plus de 6 000 clients et clientes.
* **Expertise de l’industrie :** points de vue de spécialistes des secteurs de l’automobile, des services financiers, des soins de santé, des télécommunications et des voyages.
* **Informations axées sur les données :** identification des rubriques à fort impact et des modèles de requête qui stimulent l’engagement et la conversion des clients et des clientes.

Principales rubriques recherchées par les clients et les clientes de tous les secteurs d’activité :

* **Automobile :** résolution des problèmes automobiles, comparaison des véhicules et financement/crédit-bail.
* **Services financiers :** recherche de produits financiers.
* **Soins de santé :** recherche de symptômes ou de problèmes de santé, comparaison des options de traitement, compréhension des résultats de laboratoire ou des termes médicaux.
* **Télécommunications :** comparaison des plans, des conditions contractuelles et des promotions, vérification du service dans la région locale.
* **Voyage :** se préparer pour un voyage, rechercher et réserver un voyage.

Tendances clientes basées sur la recherche optimisée par l’IA et comportement de prompt dans les outils LLM :

* Les clients et clientes préfèrent poser des questions plutôt que d’utiliser des mots-clés lors de l’utilisation des outils de recherche LLM.
* Ils utilisent principalement des outils de recherche LLM pour les premiers stades de la recherche et de la découverte.
* Les clients et clientes ont tendance à mentionner une marque ou un nom de produit spécifique dans leurs prompts.

## Bonnes pratiques liées aux catégories

Les catégories permettent d’organiser votre contenu en unités opérationnelles stratégiques ou en regroupements logiques. Il s’agit du compartiment le plus adapté et de la structure organisationnelle de niveau supérieur de votre contenu.

Lorsque vous décidez comment configurer les catégories, vous devez tenir compte de vos objectifs et des personnes qui doivent agir en fonction de ce que vous utilisez.

>[!IMPORTANT]
>
> Assurez-vous que les catégories sont correctement configurées dès le départ, car les modifications apportées aux catégories réinitialisent les données historiques. Cela signifie que si vous modifiez ces éléments, vous perdez les données historiques antérieures à la modification.

Voici un aperçu des types d’approches que vous pouvez adopter et du moment où vous devez choisir une approche particulière :

| Approche | Description | Avantage |
|---------|----------|---------|
| Unité commerciale stratégique (SBU) | Utilisez cette approche si votre organisation est divisée en fonction des profits et des pertes (par exemple, Consommateurs, Entreprises, Services). | Vous obtenez des rapports clairs par secteur d’activité et une responsabilisation plus facile. |
| Répertoire de niveau supérieur du site web (URL_DIR) | À utiliser si l’architecture des informations de votre site reflète la propriété (/products/, /support/, /docs/, /news/). | Vous vous alignez sur la manière dont les équipes publient et gèrent le contenu. |
| Catégorie de produit (ou service) | Utilisez-la si vous avez un catalogue de vente (SKU/services). | Vous obtenez des vues regroupées, des analyses des lacunes et des réponses à la question « quelle catégorie a besoin de contenu ». |

La manière de décider de la configuration des catégories repose sur une question : **Qui doit agir sur le rapport ?**

* Si vous avez une *entreprise*, choisissez l’approche **SBU**.
* Si vous êtes *propriétaire de contenu/web*, choisissez l’approche **URL_DIR**.
* Si vous êtes *responsable du marchandisage/des offres*, choisissez l’approche **Catégorie de produit/service**.

![Ajouter des catégories dans LLM Optimizer](/help/assets/best-practices/add-category.png)

>[!IMPORTANT]
>
> * Choisissez une approche et respectez-la.
> * Vous ne pouvez avoir qu’**un seul** modèle de catégorie par compte/marque. Ne mélangez pas **SBU** et **URL_DIR** en même temps.
<!--Can you mix Product/Service with these?-->

Exemple :

| Type de site | Catégorie | Exemples de taxonomie de rubrique |
|---------|----------|---------|
| Entreprises ayant plusieurs activités | SBU | Petit ensemble d’intentions (tutoriel, résolution des problèmes, comparaison, tarification, politique) |
| Site avec beaucoup de documentation/support | URL_DIR | Tutoriel, résolution des problèmes, référence, notes de mise à jour |
| Catalogue eCommerce/Services | Produit/Service | Comparaison, Avis, Prix/Disponibilité, Tutoriel, Dépannage |

## Bonnes pratiques liées aux rubriques

Les rubriques vous aident à comprendre l’intention de l’utilisateur ou l’utilisatrice : elles vous montrent ce que celui-ci ou celle-ci souhaite. Elles vous permettent de regrouper les prompts avec une intention similaire. Considérez-les comme un regroupement des prompts pertinents.

>[!IMPORTANT]
>
>Les rubriques sont universelles dans **toutes** les catégories, ce qui signifie qu’elles restent cohérentes quelle que soit la catégorie à laquelle elles sont affectées. Elles représentent des groupes de questions ou de prompts qui partagent une intention commune.

Lorsque vous établissez des rubriques, créez une liste courte et simple (6-12 maximum). Par exemple :

* Produits/Services
* Tutoriel (configuration/utilisation)
* Résolution des problèmes (erreurs/problèmes)
* Comparaison (X ou Y ; « meilleur … pour … »)
* Examens et évaluations
* Tarifs et disponibilité
* Politique et garantie
* Support/Contact
* Entreprise/Actualités (si vous en avez vraiment besoin)

![Ajouter des rubriques dans LLM Optimizer](/help/assets/best-practices/add-topic.png)

Lors de la création de la liste, tenez compte des points suivants :

* Un éditeur ou une éditrice peut-il comprendre le sujet en 5 secondes à partir du texte du prompt ? Si ce n’est pas le cas, renommez/simplifiez.
* Une autre équipe sera-t-elle chargée de la correction des différentes rubriques ? Si oui, vous avez choisi des rubriques utiles.
  <!-- Last bullet point does not make sense. Clarification needed. Also not sure what is meant by "editor"?-->

Quelques conseils utiles supplémentaires :

* Utilisez les connaissances de votre entreprise ou de votre site pour définir des rubriques qui correspondent aux objectifs stratégiques de votre marque.
* Comparez votre marque à d’autres marques sur des sujets spécifiques.

>[!IMPORTANT]
>
> * Conservez les rubriques basées sur l’intention, et non sur l’organisation.
> * N’ajoutez pas de catégories/filtres pour les marques/non-marques/zones géographiques, car vous pouvez les filtrer spécifiquement dans l’onglet **[!UICONTROL Marques]**.
> * Les rubriques sont réparties en plusieurs catégories. Vous **ne pouvez pas** définir des rubriques uniques pour chaque catégorie.
> * Un seul prompt **peut** exister dans plusieurs rubriques ou catégories.

## Bonnes pratiques liées aux prompts

Les prompts identifient les questions ou requêtes spécifiques que les clients et les clientes posent, ce qui peut avoir un impact sur votre entreprise. Il s’agit des questions ou requêtes réelles que les utilisateurs et les utilisatrices saisissent dans les LLM.

Examinez et mettez à jour régulièrement les prompts pour vous assurer qu’ils correspondent aux besoins des clients ou des clientes et aux objectifs de l’entreprise.

Bonnes pratiques liées aux prompts :

* Regroupez les prompts similaires en fonction de ce que les utilisateurs et les utilisatrices demandent.
* Concentrez-vous sur les prompts les plus importants pour vos clients et clientes.
* Vérifiez si votre marque a de bonnes chances d’être mentionnée dans certains prompts.

>[!TIP]
>
>* Vous pouvez utiliser des outils tels qu’Adobe LLM Optimizer et Google Search Console avec des filtres RegEx pour identifier les structures de questions courantes (par exemple, « comment », « quoi », « quand », « où ») et découvrir les prompts que les personnes utilisent pour visiter votre site.
>* Pour savoir quels prompts sont pertinents pour votre site/marque, vous pouvez utiliser les données de recherche sur site, les FAQ dans les pages de résultats des moteurs de recherche ou même demander directement aux chatbots LLM quelles questions les clients et les clientes peuvent poser sur votre marque.

## Bonnes pratiques de suivi des autres marques

Suivre les autres vous permet de surveiller la visibilité et les mentions dans les réponses LLM pour les prompts et les rubriques importants pour votre entreprise.

L’onglet [!UICONTROL **Suivi des autres**] vous permet d’ajouter d’autres utilisateurs et utilisatrices, y compris de la concurrence, pour suivre leur visibilité pour des prompts et des rubriques spécifiques.

Avec le suivi d’autres marques, vous pouvez voir à quelle fréquence d’autres marques sont mentionnées à côté de votre marque dans différentes régions et catégories et comparer leur visibilité à la vôtre.

>[!TIP]
>
>Examinez régulièrement les mentions et les citations de la concurrence ou d’autres entreprises afin de déterminer les domaines où votre marque peut s’améliorer.

## En savoir plus

* Le [tableau de bord de configuration cliente](/help/dashboards/customer-configuration.md) vous permet de configurer le suivi des catégories, rubriques, prompts et autres marques.
* Les [bonnes pratiques relatives à LLM Optimizer](/help/tutorials/best-practices.md) décrivent les bonnes pratiques concernant l’optimisation des LLM.

