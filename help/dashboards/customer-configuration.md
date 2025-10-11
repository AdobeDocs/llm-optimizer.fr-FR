---
title: Configuration du client
description: Utilisez la configuration client pour définir comment votre marque sera surveillée et analysée sur la plateforme de l’optimiseur LLM.
source-git-commit: b39a6acbcb86c91d23c3aab790266f37b579f651
workflow-type: tm+mt
source-wordcount: '1608'
ht-degree: 1%

---


# Configuration client

La configuration client est l’endroit où vous définissez comment votre marque sera surveillée et analysée sur la plateforme LLM optimizer. Vous pouvez personnaliser des catégories (telles que des unités commerciales ou des lignes de produits), suivre les concurrents et ajouter des alias de mention de marque pour capturer toutes les variations de votre marque dans les invites. Cette configuration garantit que la plateforme adapte les informations à votre contexte commercial, ce qui permet une visibilité, un trafic et une analyse des opportunités précis.

![Tableau de bord de configuration du client](/help/dashboards/assets/customer-config.png)


## Bonnes pratiques relatives à la configuration des catégories, rubriques et invites

Cette section décrit les bonnes pratiques pour décider de la manière dont vous souhaitez configurer vos catégories, rubriques, invites et concurrents.

Il s&#39;agit d&#39;une première étape essentielle. Ce que vous décidez maintenant détermine la manière dont les informations sont adaptées au contexte de votre entreprise. Toute modification apportée aux catégories à l’avenir réinitialise les données historiques.

### Bonnes pratiques pour les catégories

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

Exemple :

| Type de site | Catégorie | Exemples de taxonomie de rubrique |
|---------|----------|---------|
| Entreprises ayant plusieurs entreprises | SBU | Ensemble d’intentions réduit (procédure, dépannage, comparaison, tarification, politique) |
| Site lourd de documentation/support | URL_DIR | Comment, dépannage, référence, notes de mise à jour |
| Catalogue eCommerce/Services | Produit/Service | Comparaison, Avis, Prix/Disponibilité, Comment faire, Dépannage |

### Bonnes pratiques relatives aux rubriques

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
* Entreprise / Actualités (si vous en avez vraiment besoin)

Lors de la création de la liste, tenez compte des points suivants :

* Un éditeur peut-il comprendre le sujet en 5 secondes à partir du texte d’invite ? Si ce n’est pas le cas, renommez/simplifiez.
* Une autre équipe sera-t-elle propriétaire du correctif pour différents sujets ? Si oui, vous avez choisi des sujets utiles.

Quelques conseils utiles supplémentaires :

* Utilisez vos connaissances de votre entreprise ou de votre site pour définir des sujets qui correspondent aux objectifs stratégiques de votre marque
* Examinez comment votre marque se compare à ses concurrents sur des sujets spécifiques.

>[!IMPORTANT]
>
> * Conservez les rubriques basées sur l’intention, et non sur l’organisation.
> * N’ajoutez pas de catégories/filtres pour les marques/non-marques/zones géographiques, car vous pouvez les filtrer spécifiquement dans l’onglet **Marques**.
> * Les rubriques sont réparties dans plusieurs catégories, vous ne pouvez **pas** avoir différentes rubriques par catégorie.
> * Une seule invite peut exister dans plusieurs rubriques ou catégories.

### Bonnes pratiques relatives aux invites

Les invites identifient les questions ou requêtes spécifiques que les clients posent, ce qui peut avoir un impact sur votre entreprise. Il s’agit des questions ou requêtes réelles que les utilisateurs saisissent dans les LLM.

Examinez et mettez à jour régulièrement les invites pour vous assurer qu&#39;elles correspondent aux besoins du client et aux objectifs de l&#39;entreprise.

>[!TIP]
>
>* Vous pouvez utiliser des outils tels que Adobe LLM Optimizer et la console de recherche Google avec des filtres RegEx pour identifier les structures de questions courantes (par exemple, « comment », « quoi », « quand », « où ») et découvrir les invites que les personnes utilisent pour visiter votre site.
>* Pour savoir quelles invites sont pertinentes pour votre site/marque, vous pouvez utiliser les données de recherche sur site, les FAQ dans les pages de résultats des moteurs de recherche ou même demander directement aux chatbots LLM quelles questions les clients peuvent poser sur votre marque.

### Bonnes pratiques pour les concurrents

Les concurrents vous permettent de surveiller la visibilité et les mentions dans les réponses LLM pour les invites et les sujets importants pour votre entreprise.

L’onglet [!UICONTROL **Suivi des concurrents**] vous permet d’ajouter des concurrents et de suivre leur visibilité pour des invites et des sujets spécifiques.

Grâce au suivi des concurrents, vous pouvez voir à quelle fréquence les concurrents sont mentionnés aux côtés de votre marque dans différentes régions et catégories et comparer leur visibilité à la vôtre.

>[!TIP]
>
>Examinez régulièrement les mentions et citations des concurrents pour identifier les domaines dans lesquels votre marque peut s&#39;améliorer.

## Tableau de bord de configuration du client

Le tableau de bord de configuration du client est un outil puissant qui fournit des informations sur la visibilité de votre marque dans les LLM. En configurant correctement des catégories, des rubriques, des invites et des concurrents, vous pouvez vous assurer que votre marque est bien positionnée pour apparaître dans les réponses générées par LLM. Examiner régulièrement des informations telles que Share of Voice, la visibilité du contenu et les opportunités vous aidera à adapter votre stratégie et à garder une longueur d’avance sur vos concurrents.

Pour configurer la manière dont LLM Optimizer surveille et analyse la présence de votre marque sur différents marchés et paysages concurrentiels, vous avez accès aux onglets suivants :

* [Catégories](#categories)
* [Suivi des concurrents](#competitor-tracking)
* [Alias de marque](#brand-aliases)
* [Data Insights](#data-insights)
* [Réseau CDN de l’agence](#agentic-cdn)

## Catégories {#categories}

Dans l’onglet Catégories , vous pouvez définir les catégories métier ou les lignes de produits dont vous souhaitez effectuer le suivi et les associer à des régions spécifiques. Dans l’ensemble, l’onglet Catégories correspond à toutes les autres personnalisations de cette page, car les catégories apparaissent dans le champ Catégorie pour les autres personnalisations (suivi des concurrents, alias, etc.). Pour ajouter une nouvelle catégorie :

1. Cliquez sur le bouton **Ajouter**.
2. Dans la nouvelle fenêtre de configuration, ajoutez le **Nom de la catégorie**.
3. Personnalisez la **Région associée** où la catégorie sera surveillée.
4. Cliquez sur **Enregistrer** pour que la nouvelle catégorie apparaisse dans la liste des catégories.

L’ajout de nouvelles catégories ne génère pas automatiquement de rubriques et d’invites - elles doivent être ajoutées manuellement à partir de l’onglet [Data Insights](#data-insights).

Pour supprimer une catégorie, cliquez sur l’icône de suppression dans la liste des catégories. Attention, car **la suppression d’une catégorie supprimera également les éléments associés** tels que les concurrents que vous avez peut-être configurés ou les alias de marque liés à cette catégorie spécifique.

## Suivi des concurrents {#competitor-tracking}

En utilisant le suivi des concurrents, vous pouvez suivre la manière dont vos concurrents sont mentionnés par rapport à votre marque dans différentes catégories et régions. Surveillez leur présence et leurs performances dans vos segments de marché. Pour personnaliser le tracking des concurrents :

1. Pour ajouter un nouveau concurrent, cliquez sur le bouton **Ajouter**.
2. Dans la nouvelle fenêtre de configuration, sélectionnez la **Catégorie**. Les catégories créées précédemment apparaîtront ici.
3. Ajoutez le nom du concurrent.
4. Personnalisez l’alias et les domaines concurrents si nécessaire.
5. Cliquez sur **Enregistrer** pour que le nouveau concurrent apparaisse dans la liste des concurrents.

Pour supprimer un concurrent, cliquez sur l’icône de suppression dans la liste des concurrents.

## Alias de marque {#brand-aliases}

En utilisant les alias de marque, vous pouvez configurer d’autres noms et variantes de votre marque qui doivent faire l’objet d’un suivi dans différentes catégories et régions. Cela permet une surveillance complète de toutes les mentions de marque. Pour ajouter un alias de marque :

1. Cliquez sur le bouton **Ajouter**.
2. Dans la nouvelle fenêtre de configuration, sélectionnez la **Catégorie**. Les catégories créées précédemment apparaîtront ici.
3. Sélectionnez la **Région** où l’alias sera surveillé.
4. Ajoutez l’alias de la marque.
5. Cliquez sur **Enregistrer** et l’alias de la marque apparaît dans la liste.

Pour supprimer un alias de marque, cliquez sur l’icône de suppression dans la liste des alias.

## Data Insights {#data-insights}

Dans cet onglet, vous pouvez vérifier, gérer et personnaliser les invites. Vous pouvez charger un fichier .csv [informations sur les données de présence de marque](/help/dashboards/brand-presence.md#data-insights) et la liste sera remplie avec des invites et des rubriques issues de cette analyse. Vous pouvez également supprimer, modifier et ajouter des rubriques et leurs invites associées selon vos besoins.

Pour importer un fichier .csv d’informations sur les données, vous devez d’abord exporter un fichier à partir du tableau de bord de la présence de la marque. Consultez la section [informations sur les données](/help/dashboards/brand-presence.md#data-insights) pour savoir comment procéder. Une fois que vous disposez du fichier :

1. Dans le tableau de bord, cliquez sur **Télécharger CSV**.
2. Dans la fenêtre Importer des statistiques sur les données , effectuez un glisser-déposer ou choisissez manuellement le fichier.
3. Cliquez sur **Charger les données**.

Vous pouvez également créer un fichier CSV en téléchargeant le modèle depuis la fenêtre **Importer des informations sur les données**. Une fois que vous disposez du modèle, ouvrez-le et saisissez vos rubriques ainsi que les invites, catégories et régions associées dans une nouvelle ligne.

De plus, vous pouvez également ajouter des rubriques/invites à la liste indépendamment d&#39;un fichier CSV. Pour ce faire, sur le tableau de bord, vous devez :

1. Cliquez sur le bouton **Ajouter une rubrique**.
2. Dans la nouvelle fenêtre de configuration, sélectionnez la **Catégorie**. Les catégories créées précédemment apparaîtront ici.
3. Saisissez le nom de la rubrique.
4. Ajoutez le texte d’invite.
5. Sélectionnez la région.
6. Cliquez sur **Ajouter une invite** et la rubrique contenant l’invite s’affiche dans la liste.

>[!NOTE]
>Les invites nouvellement ajoutées n&#39;apparaîtront pas dans Brand Presence tant que le traitement ne sera pas terminé.

Sur la liste, vous pouvez cliquer sur chaque rubrique et la ou les invites associées apparaîtront. Pour supprimer la rubrique et ses invites associées, cliquez sur l&#39;icône de suppression de la liste.

## Réseau CDN de l’agence {#agentic-cdn}

Non disponible (sera-t-il disponible pour publication ?).

