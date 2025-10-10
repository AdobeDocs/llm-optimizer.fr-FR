---
title: Configuration du client
description: Voici la présentation de l’article.
source-git-commit: e35ddb9b055d2f974fd94b3a21e13e92d05c8799
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 1%

---


# Configuration du client

La configuration client est l’endroit où vous définissez la manière dont votre marque sera surveillée et analysée au sein de la plateforme. Vous pouvez personnaliser des catégories (telles que des unités commerciales ou des lignes de produits), suivre les concurrents et ajouter des alias de mention de marque pour capturer toutes les variations de votre marque dans les invites. Cette configuration garantit que la plateforme adapte les informations à votre contexte commercial, ce qui permet une visibilité, un trafic et une analyse des opportunités précis.

![URL de tendance en concurrence pour les citations](/help/dashboards/assets/customer-config.png)

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

