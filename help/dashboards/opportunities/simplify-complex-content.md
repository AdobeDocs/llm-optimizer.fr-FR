---
title: Simplifier les contenus complexes
description: Découvrez comment LLM Optimizer identifie les pages à trafic élevé avec une copie dense difficile à interpréter pour les agents d’IA, et comment réviser et déployer du texte simplifié avec Optimize sur Edge.
feature: Opportunities
autotag-review: '2026-05-15T17:58:39.879Z'
TQID: 'https://experienceleague.adobe.com/wO3ZY-fEgOi7cD4dq0kCltk-YJSD431bkA6-9PW42Lo'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 785
ht-degree: 1%

---


# Simplifier les contenus complexes

L’opportunité Simplifier le contenu complexe identifie les pages à trafic élevé où le texte dense ou complexe rend plus difficile, pour les agents de l’IA, l’interprétation des informations clés. Il introduit des versions plus claires et plus faciles à analyser de la copie existante tout en préservant la signification originale. Cela permet aux agents d’analyser, de résumer et d’extraire des informations importantes de manière plus fiable.

Pour chaque URL affectée, vous pouvez examiner les suggestions **Texte amélioré**, les comparer avec **Aperçu**, puis les déployer avec [Optimiser dans Edge](/help/dashboards/optimize-at-edge/overview.md) afin que le trafic agentic reçoive un HTML plus clair sans aucune modification du système de gestion de contenu (CMS) requise.

## Comment cela résout le problème

Les correctifs sont appliqués à l’aide de [Optimiser dans Edge](/help/dashboards/optimize-at-edge/overview.md), qui :

- Diffuse un instantané HTML prégénéré aux agents d’IA.
- Met à jour la page visible par l’agent afin que les passages complexes soient remplacés ou augmentés avec **Texte amélioré** aligné sur la page active.
- Fonctionne au niveau de la couche CDN (aucune modification de CMS).
- Est uniquement accessible par l’IA : aucun impact sur les visiteurs humains ou les robots d’optimisation du moteur de recherche.
- Déploie en quelques minutes et est **entièrement réversible** à partir de l’interface de LLM Optimizer.

## Fonctionnement

LLM Optimizer identifie les pages qui reçoivent un trafic d’agent élevé et où le contenu a un score inférieur aux seuils de lisibilité, puis suggère des réécritures de la copie. Pour chaque page, vous avez :

**Texte amélioré** - contenu simplifié, fondé sur ce qui se trouve déjà sur la page.
**Aperçu** - une comparaison avant et après pour le trafic d’agent.

Les URL concernées apparaissent dans le tableau **URL avec suggestions** de l’onglet **Suggestions actuelles**, où vous pouvez développer une ligne pour examiner chaque recommandation.

![URL avec suggestions sur les suggestions actuelles, ligne développée avec texte et aperçu améliorés](/help/dashboards/opportunities/assets/simplify-complex-content-expand.png)

Le tableau **URL avec suggestions** répertorie les pages où un contenu simplifié aiderait à la compréhension des agents. Les suggestions sont organisées en **Suggestions actuelles**, **Suggestions fixes** et **Suggestions ignorées**. Pour chaque URL, vous pouvez :

- **Développez la ligne** pour afficher les suggestions **Texte amélioré** de cette page.
- **Aperçu** la comparaison avant et après pour le trafic d’agent.
- **Marquer comme corrigé** si vous avez traité l’opportunité en dehors de LLM Optimizer.
- **Ignorer** les suggestions qui ne sont pas pertinentes.

**Vues** incluent **Suggestions actuelles**, **Suggestions fixes** (statut **Optimisé** lors du déploiement) et **Suggestions ignorées**. Vous pouvez vérifier le déploiement en direct à l’aide de **Afficher en direct** sur **Suggestions fixes** et effectuer une restauration à tout moment.

Sélectionnez les URL ou les éléments de ligne avec **Texte amélioré** que vous souhaitez expédier à l’aide des cases à cocher, puis utilisez **Marquer comme fixe**, **Ignorer les suggestions** ou **Déployer les optimisations** dans l’en-tête **Plan d’opportunité**. L’interface utilisateur de démonstration affiche également un nombre de sélections et les actions associées avec la liste.

![Plan d’opportunité, suggestions actuelles, ligne développée et déployer des optimisations dans l’en-tête du plan](/help/dashboards/opportunities/assets/simplify-complex-content-select.png)

### Déploiement de l’optimisation

Lorsque vous êtes prêt à publier en périphérie, cliquez sur **Déployer les optimisations**. Une boîte de dialogue **Déployer vers Edge** répertorie les URL sélectionnées et les détails d’optimisation. Vérifiez la liste, puis choisissez **Déployer** ou **Annuler**.

![ Boîte de dialogue Déployer sur Edge ](/help/dashboards/opportunities/assets/simplify-complex-content-deploy-dialog.png)

Après un déploiement réussi, le **Déploiement terminé** confirme le nombre d’optimisations activées et note que les agents d’IA peuvent prendre du temps pour indexer la mise à jour. Fermez la boîte de dialogue et ouvrez **Suggestions fixes** pour vérifier le statut.

![Confirmation de fin du déploiement](/help/dashboards/opportunities/assets/simplify-complex-content-deploy-confirm.png)

>[!NOTE]
>
>Le déploiement des optimisations nécessite l’achèvement du processus d’intégration Optimizer at Edge. Si vous n’avez pas encore intégré, cliquez sur **Déployer les optimisations** pour être redirigé(e) vers le processus d’intégration. Pour plus d’informations sur le fonctionnement d’Optimize at Edge, les fournisseurs de réseau CDN pris en charge et le processus d’intégration, consultez la page [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

### Suggestions fixes et Afficher en direct

Dans **Suggestions fixes**, les URL déployées affichent **Optimisées** dans la colonne de statut. Développez une ligne pour passer en revue le **texte amélioré** déployé et les instructions.

![Onglet Suggestions fixes avec statut Optimisé, copie simplifiée développée, Afficher en direct et Détails](/help/dashboards/opportunities/assets/simplify-complex-content-fixed.png)

Cliquez sur **Afficher en direct** sur la ligne pour ouvrir une vue en lecture seule du **contenu actuel de la page** diffusé à des fins de vérification (y compris des passages simplifiés, le cas échéant). Utilisez **Details** pour les analyses.

![Afficher en direct : contenu actuel de la page, y compris texte simplifié pour les agents](/help/dashboards/opportunities/assets/simplify-complex-content-view-live.png)

Lorsque vous devez annuler des modifications de périphérie en bloc, sélectionnez les lignes optimisées à l’aide des cases à cocher, puis utilisez **Restaurer** dans l’en-tête.

![Correction des suggestions avec la ligne déployée développée, le statut Optimisé et l’option Restaurer dans l’en-tête](/help/dashboards/opportunities/assets/simplify-complex-content-rollback.png)

## Restauration

Si vous changez d’avis, vous pouvez annuler toute optimisation déployée. Dans la vue **Suggestions fixes**, sélectionnez les lignes optimisées à rétablir, puis cliquez sur **Restaurer** dans l’en-tête.

La boîte de dialogue **Restaurer** répertorie les suggestions qui seront restaurées, avec un court avertissement indiquant que les optimisations déployées seront rétablies. Confirmez la liste, puis cliquez sur **Restaurer** ou **Annuler**.

![Boîte de dialogue Restaurer répertoriant les suggestions à rétablir](/help/dashboards/opportunities/assets/simplify-complex-content-rollback-dialog.png)

Une fois l’opération terminée, un résumé **Annulé avec succès** s’affiche ; fermez-le pour revenir au tableau de bord.

![Restauration terminée — Restauration réussie](/help/dashboards/opportunities/assets/simplify-complex-content-rollback-confirm.png)

## Faites un essai dans la démonstration

Explorez le workflow Simplifier le contenu complexe dans la [démonstration de Frescopa](https://play.llmo.now/org/demo-org).
