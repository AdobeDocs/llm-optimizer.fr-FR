---
title: Bonnes pratiques relatives aux catégories, rubriques, prompts et autres
description: Optimisez les informations des LLM en configurant des catégories, des rubriques, des prompts et d’autres marques pour effectuer le suivi, y compris de la concurrence, pour une surveillance de marque personnalisée et une analyse de contenu stratégique.
feature: Best Practices, Customer Configuration
autotag-review: '2026-07-15T17:42:20.391Z'
TQID: 'https://experienceleague.adobe.com/nnLohajbU-fogbmBfGE5PUzdsoTJ5fjwW-ruVTjOWtM'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: c898dfb2-0885-42fb-b2af-b2d756752646
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: e69d5a42-0217-4ca5-9396-a9a826a170da
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: addf009e-030a-4310-8534-776a3e62ed48
  - id: b5520579-b31f-4df7-9281-f0d9f91e2edc
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d00e9f03-e50b-4162-b143-0c0817c937c2
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
  - id: f8667931-f646-4dd3-af2a-b9d0cb8098ad
source-git-commit: 74484901cba1f054070673f2d706b26b6360aacb
workflow-type: tm+mt
source-wordcount: 1482
ht-degree: 77%

---

# Bonnes pratiques de configuration des catégories, rubriques, invites et autres marques à suivre

Cette section décrit les bonnes pratiques pour décider de la manière dont vous souhaitez configurer les catégories, rubriques, invites et autres marques à suivre. En outre, elle contient des informations sur la bibliothèque de prompts sectoriels, qu’Adobe a développée grâce à des recherches approfondies menées avec des spécialistes de chaque secteur.

Cette configuration est une première étape essentielle. Ce que vous décidez maintenant détermine la manière dont les informations sont adaptées au contexte de votre entreprise. Toute modification apportée aux catégories à l’avenir réinitialise les données historiques.

Dans le tableau de bord [[!UICONTROL Gestion des marques]](/help/dashboards/customer-configuration.md), vous définissez la manière dont votre marque est surveillée et analysée au sein de la plateforme LLM Optimizer.

Vous pouvez personnaliser les catégories (telles que les unités commerciales ou les lignes de produits), effectuer le suivi d’autres marques et ajouter des alias de mention de marque pour capturer toutes les variations de votre marque dans les invites. Cette configuration garantit que la plateforme adapte les informations à votre contexte commercial, ce qui permet une visibilité, un trafic et une analyse des opportunités précis.

Par défaut, chaque organisation commence par une marque active et d’autres marques suggérées parmi lesquelles choisir.

![Brand Management : navigation dans l’application (expérience orientée marque)](/help/assets/brand-centric-experience/llmo-app-shell.png)

![Gestion des marques - Présentation de la configuration](/help/assets/brand-centric-experience/brands-management-configuration.png)

Pour configurer des rubriques et des invites pour une marque spécifique, utilisez le tableau de bord **Bibliothèque d&#39;invites**.

<!-- Add link to Prompt Library page when available-->

![Gestion des prompts](/help/assets/brand-centric-experience/prompts-management.png)

## Bibliothèque de prompts sectoriels

Pour faciliter la prise en main des prompts et des rubriques, Adobe a créé une bibliothèque de prompts sectoriels développée à l’issue de recherches approfondies avec des spécialistes des différents secteurs et d’une analyse du comportement de recherche optimisée par l’IA auprès de plus de 6 000 clients et clientes. Cette bibliothèque identifie les sujets et les prompts les plus pertinents en fonction des tendances spécifiques au secteur, des objectifs commerciaux validés et des modèles concrets de recherche de clientèle.

Pour utiliser la bibliothèque de prompts sectoriels :

1. Accédez au tableau de bord **Bibliothèque d’invites**.
1. Sélectionnez **Télécharger la bibliothèque d’invites** pour télécharger le fichier de bibliothèque à partir de LLM Optimizer.
1. Examinez les **rubriques** et **prompts** suggérés pour le secteur de votre marque dans l’onglet correspondant et choisissez les options les plus pertinentes.
1. Consultez la **colonne Étape du parcours client** pour afficher les options de prompts tout au long du cycle de vie du client ou de la cliente (par exemple, découverte, conversion, rétention). Les prompts destinés aux premières étapes/au haut du tunnel sont hautement prioritaires, mais envisagez également des options pour les étapes ultérieures afin de favoriser la fidélisation, d’assurer le service clientèle, etc.
1. Modifiez les rubriques ou les prompts selon les besoins pour mieux prendre en charge vos objectifs avant de charger vos rubriques et prompts dans Adobe LLM Optimizer (par exemple, ajoutez votre marque/nom de produit, ajoutez la terminologie propre à la marque). Les prompts peuvent être ajoutés à LLM Optimizer manuellement ou par chargement en masse à l’aide du modèle *.csv* fourni.

<!--![Industry prompt library download](/help/assets/best-practices/download-prompts.png) - add screenshot to steps-->

>[!TIP]
>
> Utilisez une combinaison de prompts spécifiques au domaine recommandés par LLM Optimizer lors de la configuration initiale et la bibliothèque de prompts sectoriels pour élaborer votre stratégie relative aux prompts.

### Bases de la recherche de la bibliothèque de prompts

La bibliothèque de prompts sectoriels a été élaborée dans le cadre d’une initiative de recherche exhaustive combinant les éléments suivants :

* **Intelligence client :** analyse du comportement et des préférences de recherche optimisée par l’IA sur plus de 6 000 clients et clientes.
* **Expertise de l’industrie :** points de vue de spécialistes des secteurs de l’automobile, des services financiers, des soins de santé, des télécommunications et des voyages.
* **Informations axées sur les données :** identification des rubriques à fort impact et des modèles de requête qui stimulent l’engagement et la conversion des clients et des clientes.

Principales rubriques recherchées par les clients et les clientes de tous les secteurs d’activité :

* **Auto :** résolution des problèmes automobiles, comparaison des véhicules et financement/crédit-bail
* **Services financiers :** recherche de produits financiers.
* **Soins de santé :** recherche des symptômes ou des problèmes de santé, comparaison des options de traitement et compréhension des résultats de laboratoire ou des termes médicaux
* **Télécom :** Comparaison des plans, des conditions contractuelles et des promotions, et vérification du service dans la région locale
* **AirlineTravel :** Préparation d&#39;un voyage, recherche et réservation de voyages

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

<!--How do you pick a region? Or is that handled differently?-->

![Ajouter des catégories dans LLM Optimizer](/help/assets/best-practices/create-category1.png)

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

![Ajouter des rubriques dans LLM Optimizer](/help/assets/best-practices/add-new-topic1.png)

Lors de la création de la liste, tenez compte des points suivants :

* Quelqu&#39;un peut-il comprendre le sujet en 5 secondes à partir du texte de l&#39;invite ? Si ce n’est pas le cas, renommez/simplifiez.
* Une autre équipe sera-t-elle chargée de la correction des différentes rubriques ? Si oui, vous avez choisi des rubriques utiles.

<!-- Last bullet point does not make sense. Clarification needed. Also not sure what is meant by "editor"?-->

Quelques conseils utiles supplémentaires :

* Utilisez les connaissances de votre entreprise ou de votre site pour définir des rubriques qui correspondent aux objectifs stratégiques de votre marque.
* Comparez votre marque à d’autres marques sur des sujets spécifiques.

>[!IMPORTANT]
>
> * Conservez les rubriques basées sur l’intention, et non sur l’organisation.
> * N’ajoutez pas de catégories/filtres pour les marques/non-marques/zones géographiques, car vous pouvez les filtrer spécifiquement dans le tableau de bord **[!UICONTROL Présence des marques]**.
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

Le suivi d’autres marques vous permet de surveiller la visibilité et les mentions dans les réponses LLM pour les invites et les sujets importants pour votre entreprise.

[!UICONTROL **Autres marques à suivre**] est disponible dans **Gestion des marques** > **Suivi des marchés** et vous permet d’en ajouter d’autres, y compris des concurrents, pour suivre leur visibilité pour des invites et des sujets spécifiques.

Avec d’autres marques à suivre, vous pouvez voir à quelle fréquence d’autres marques sont mentionnées aux côtés de votre marque dans différentes régions et catégories et comparer leur visibilité à la vôtre.

>[!TIP]
>
>Examinez régulièrement les mentions et les citations de la concurrence ou d’autres entreprises afin de déterminer les domaines où votre marque peut s’améliorer.

## En savoir plus

* [Brands Management](/help/dashboards/customer-configuration.md) permet de configurer les catégories et les autres marques à suivre.
* [Bibliothèque d&#39;invites](/help/dashboards/customer-configuration.md) est l&#39;endroit où vous configurez vos rubriques et invites.
* Les [bonnes pratiques relatives à LLM Optimizer](/help/tutorials/best-practices.md) décrivent les bonnes pratiques concernant l’optimisation des LLM.

