---
title: Configuration cliente
description: Utilisez la configuration cliente pour définir comment votre marque sera surveillée et analysée sur la plateforme LLM Optimizer.
feature: Customer Configuration
source-git-commit: 5d8b59ea4281c88bb42dc48096c07a3faaeb2e88
workflow-type: ht
source-wordcount: '836'
ht-degree: 100%

---


# Configuration cliente {#customer-configuration}

Le tableau de bord de la configuration cliente est un outil puissant qui fournit des informations sur la visibilité de votre marque dans les LLM. En configurant correctement des catégories, des rubriques et des prompts, vous pouvez vous assurer que votre marque est bien positionnée pour apparaître dans les réponses générées par les LLM. Cette configuration garantit que la plateforme adapte les informations à votre contexte commercial, ce qui permet une visibilité, un trafic et une analyse des opportunités précis.

![Tableau de bord de la configuration cliente](/help/dashboards/assets/customer-config.png)

Pour configurer la manière dont LLM Optimizer surveille et analyse la présence de votre marque sur différents marchés et paysages concurrentiels, vous avez accès aux onglets suivants :

* [Prompts](#prompts-brand)
* [Catégories](#categories)
* [Autres marques](#other-brands)
* [Alias de marque](#brand-aliases)
* [Configuration du CDN](#agentic-cdn)

>[!IMPORTANT]
>
> Pour plus d’informations sur la configuration des catégories, rubriques et prompts, reportez-vous à la page [Bonnes pratiques pour la configuration des catégories, rubriques, prompts](/help/overview/best-practices-topics-prompts.md).

## Prompts {#prompts-brand}

Dans cet onglet, vous pouvez vérifier, gérer et personnaliser les prompts. Vous pouvez charger un fichier CSV [Analyse de présence de la marque](/help/dashboards/brand-presence.md) et la liste sera remplie avec les prompts et les rubriques de cette analyse ou [télécharger une bibliothèque de prompts](/help/overview/best-practices-topics-prompts.md) créée par Adobe. Vous pouvez également supprimer, modifier et ajouter des rubriques et leurs prompts associés selon vos besoins.

Pour importer un fichier CSV d’informations de données, vous devez d’abord exporter un fichier à partir du tableau de bord Présence de la marque. Voir la section [Données](/help/dashboards/brand-presence.md#data-insights) pour savoir comment faire. Une fois que vous avez le fichier :

1. Dans le tableau de bord, cliquez sur **Charger le fichier CSV**.
2. Dans la fenêtre Importer des données, effectuez un glisser-déposer ou choisissez manuellement le fichier.
3. Cliquez sur **Charger des données**.

Vous pouvez également créer un fichier CSV en téléchargeant le modèle depuis la fenêtre **Importer des données**. Une fois que vous avez le modèle, ouvrez-le et saisissez vos rubriques ainsi que les prompts, catégories et régions associés, chacun dans une nouvelle ligne.

Pour savoir comment télécharger et utiliser la bibliothèque de prompts sectoriels créée par Adobe, consultez la section Bibliothèque de prompts sectoriels sur [cette page](/help/overview/best-practices-topics-prompts.md).

En outre, vous pouvez également ajouter des rubriques/prompts à la liste, sans passer par un fichier CSV ou une bibliothèque de prompts. Pour ce faire, sur le tableau de bord, vous devez suivre ces étapes :

1. Cliquez sur le bouton **Ajouter une rubrique**.
2. Dans la nouvelle fenêtre de configuration, sélectionnez la **catégorie**. Les catégories créées précédemment apparaîtront ici.
3. Saisissez le nom de la rubrique.
4. Ajoutez le texte de prompt.
5. Sélectionnez la région.
6. Cliquez sur **Ajouter un prompt** et la rubrique contenant le prompt s’affiche dans la liste.

>[!NOTE]
>Les prompts nouvellement ajoutés n’apparaîtront pas dans Présence de la marque tant que le traitement ne sera pas terminé.

Sur la liste, vous pouvez cliquer sur chaque rubrique et le ou les prompts associés apparaîtront. Pour supprimer la rubrique et ses prompts associés, cliquez sur l’icône de suppression dans la liste.

## Catégories {#categories}

Dans l’onglet Catégories, vous pouvez définir les catégories commerciales ou les gammes de produits que vous souhaitez suivre et les associer à des régions spécifiques. Dans l’ensemble, l’onglet Catégories correspond à presque toutes les autres personnalisations de cette page, car les catégories apparaissent dans le champ Catégorie pour les autres personnalisations (suivi des autres, alias, etc.). Pour ajouter une nouvelle catégorie :

1. Cliquez sur le bouton **Ajouter**.
2. Dans la nouvelle fenêtre de configuration, ajoutez le **nom de la catégorie**.
3. Personnalisez la **région associée** où la catégorie sera surveillée.
4. Cliquez sur **Enregistrer** pour que la nouvelle catégorie apparaisse dans la liste des catégories.

L’ajout de nouvelles catégories ne génère pas automatiquement de rubriques et de prompts. Ceux-ci doivent être ajoutés manuellement à partir de l’onglet [Données](#data-insights).

Pour supprimer une catégorie, cliquez sur l’icône de suppression dans la liste des catégories. Attention : **supprimer une catégorie supprimera également les éléments associés** comme les alias de marque liés à cette catégorie spécifique.

## Autres marques {#others-tracking}

En utilisant cet onglet, vous pouvez suivre la manière dont les autres marques sont mentionnées par rapport à la vôtre dans différentes catégories et régions. Surveillez leur présence et leurs performances dans vos segments de marché. Pour personnaliser le suivi :

1. Cliquez sur le bouton **Ajouter**.
2. Dans la nouvelle fenêtre de configuration, sélectionnez la **catégorie**. Les catégories créées précédemment apparaîtront ici.
3. Ajoutez le nom de l’autre.
4. Personnalisez l’alias et les domaines de l’autre si nécessaire.
5. Cliquez sur **Enregistrer**.

Pour supprimer une entrée dans la liste, cliquez sur l’icône de suppression.

## Alias de marque {#brand-aliases}

L’utilisation d’alias de marque vous permet de configurer d’autres noms et variations de votre marque qui doivent faire l’objet d’un suivi dans différentes catégories et régions. Cela permet d’assurer une surveillance complète de toutes les mentions de la marque. Pour ajouter un alias de la marque :

1. Cliquez sur le bouton **Ajouter**.
2. Dans la nouvelle fenêtre de configuration, sélectionnez la **catégorie**. Les catégories créées précédemment apparaîtront ici.
3. Sélectionnez la **région** où l’alias sera surveillé.
4. Ajoutez l’alias de la marque.
5. Cliquez sur **Enregistrer** et l’alias de la marque apparaît dans la liste.

Pour supprimer un alias de marque, cliquez sur l’icône de suppression dans la liste des alias.

## Configuration du CDN {#cdn-configuration}

Dans cet onglet, vous pouvez configurer vos flux CDN pour permettre à Adobe LLM Optimizer d’analyser vos données CDN. Ces données seront utilisées pour alimenter les tableaux de bord (comme le trafic généré par l’IA agentique), fournissant des informations sur les modèles de trafic, les mesures de performances et les opportunités d’optimisation. Pour intégrer votre fournisseur de CDN, cliquez sur **Intégrer le CDN**.

![Configuration cliente du CDN](/help/overview/assets/cc-cdn.png)

Dans la fenêtre **Intégrer le fournisseur du CDN** :

1. Sélectionnez votre fournisseur de CDN.
2. Cliquez sur **Intégration** pour activer le transfert des journaux.

Si vous sélectionnez **Autre**, vous devrez contacter llmo-now@adobe.com pour obtenir de l’aide.
