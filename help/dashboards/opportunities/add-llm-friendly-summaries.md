---
title: Ajouter des résumés compatibles avec LLM
description: Découvrez comment LLM Optimizer identifie les pages à trafic élevé qui ne disposent pas de résumés concis et d’éléments clés pour les agents d’IA, et comment les examiner et les déployer avec Optimize sur Edge.
feature: Opportunities
autotag-review: '2026-07-15T16:47:03.003Z'
TQID: 'https://experienceleague.adobe.com/InOzeT7WlDaACpB-WT0F-JqI1nopOJewihCP9eUQnNY'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
  - id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2:
  - id: bbfc1b77-44c5-4fe8-b65f-ec160fe0d021
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 793
ht-degree: 9%

---


# Ajouter des résumés compatibles avec LLM

L’opportunité Ajouter des résumés compatibles avec LLM identifie les pages à trafic élevé qui manquent de résumés structurés concis, ce qui rend plus difficile pour les agents d’IA de comprendre rapidement les informations clés de la page. Il présente des résumés clairs et des points clés fondés sur le contenu de votre page existante. Cela permet aux agents d’interpréter et de capturer plus efficacement les revendications de marque importantes et augmente la probabilité que votre contenu soit inclus avec précision dans les réponses de l’IA.

Pour chaque URL affectée, vous pouvez passer en revue les suggestions générées par l’IA, puis les déployer avec [Optimiser sur Edge](/help/dashboards/optimize-at-edge/overview.md) afin que le trafic agentic soit plus clair et analysable, sans nécessiter de modifications du système de gestion de contenu (CMS).

## Comment cela résout le problème

Les correctifs sont appliqués à l’aide de [Optimiser dans Edge](/help/dashboards/optimize-at-edge/overview.md), qui :

- Diffuse un instantané HTML prégénéré aux agents d’IA.
- Enrichit la page avec des résumés et/ou des points importants dans l’HTML qu’ils récupèrent.
- Fonctionne au niveau de la couche CDN (aucune modification de CMS).
- Est uniquement accessible par l’IA : aucun impact sur les visiteurs humains ou les robots d’optimisation du moteur de recherche.
- Déploie en quelques minutes et est **entièrement réversible** à partir de l’interface de LLM Optimizer.

## Fonctionnement

LLM Optimizer identifie les pages à trafic élevé où des **résumés** et **points clés** au niveau des pages ou des sections peuvent aider à la compréhension de l’IA. Les URL concernées apparaissent dans le tableau **URL avec suggestions** de l’onglet **Suggestions actuelles**, où vous pouvez développer une ligne pour examiner chaque recommandation.

![URL avec suggestions sur les suggestions actuelles, ligne développée avec suggestions de résumé de page et de section](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-expand.png)

Le tableau **URL avec suggestions** répertorie les pages où des résumés aideraient à la découverte agentique. Les suggestions sont organisées en **Suggestions actuelles**, **Suggestions fixes** et **Suggestions ignorées**. Pour chaque URL, vous pouvez effectuer les opérations suivantes :

- **Développez la ligne** pour afficher l’analyse et le texte du résumé proposé (et les points clés, le cas échéant).
- **Aperçu** la comparaison avant et après pour le trafic d’agent.
- **Marquer comme corrigé** si vous avez traité l’opportunité en dehors de LLM Optimizer.
- **Ignorer** les suggestions qui ne sont pas pertinentes.

Chaque entrée développée affiche des instructions récapitulatives au niveau de la page et de la section, **générées par l’IA** une copie, des contrôles de modification et un contexte lié à la page active.

Cliquez sur **Aperçu** dans la colonne **Actions** pour ouvrir l’aperçu de l’optimisation. Il compare l’aspect actuel de votre page en matière de trafic d’agent avec la vue de post-optimisation (par exemple, le contenu injecté **résumé** et **point clé** aligné sur les emplacements suggérés). Vous pouvez ouvrir ou ignorer cet aperçu à tout moment avant le déploiement.

Lorsque vous êtes prêt à publier, cochez les cases pour sélectionner les éléments de ligne de résumé et de point clé. Le pied de page indique le nombre de sélections et fournit **Marquer comme fixe**, **Ignorer les suggestions** et **Déployer les optimisations**.

![Suggestions actuelles avec éléments de ligne de résumé sélectionnés et déployer des optimisations dans le pied de page](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-select-url.png)

### Déploiement de l’optimisation

Lorsque vous êtes prêt à publier en périphérie, cliquez sur **Déployer les optimisations**. Une boîte de dialogue **Déployer vers Edge** répertorie les URL sélectionnées et les détails d’optimisation. Vérifiez la liste, puis choisissez **Déployer** ou **Annuler**.

Boîte de dialogue ![Déployer sur Edge](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-deploy-dialog.png)

Après un déploiement réussi, le **Déploiement terminé** confirme le nombre d’optimisations activées et note que les agents d’IA peuvent prendre du temps pour indexer la mise à jour. Fermez la boîte de dialogue et ouvrez **Suggestions fixes** pour vérifier le statut.

![Confirmation de fin du déploiement](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-deploy-confirm.png)

>[!NOTE]
>
>Le processus d’intégration à Optimize at Edge doit être terminé pour pouvoir déployer des optimisations. Si vous n’avez pas encore effectué l’intégration, cliquer sur **Déployer des optimisations** vous redirigera vers le processus d’intégration. Pour plus d’informations sur le fonctionnement d’Optimize at Edge, les fournisseurs de réseau CDN pris en charge et le processus d’intégration, consultez la page [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

### Suggestions fixes et Afficher en direct

Dans **Suggestions fixes**, les URL déployées affichent **Optimisées** dans la colonne de statut. Développez une ligne pour passer en revue la copie de résumé déployée et les instructions.

![Onglet Suggestions fixes avec statut Optimisé, résumés déployés étendus, Afficher en direct et Détails](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-fixed.png)

Cliquez sur **Afficher en direct** sur la ligne pour ouvrir une vue en lecture seule du **contenu actuel de la page** diffusé à des fins de vérification (y compris les blocs **résumé** et **point clé** injectés, le cas échéant). Utilisez **Details** pour les analyses. Lorsque vous devez annuler des modifications de périphérie en bloc, sélectionnez les lignes optimisées à l’aide des cases à cocher, puis utilisez **Restaurer** dans l’en-tête.

![Suggestions fixes avec cases à cocher pour la sélection en bloc avant la restauration](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-select-in-fixed.png)

## Restauration

Si vous changez d’avis, vous pouvez annuler toute optimisation déployée. Dans la vue **Suggestions fixes**, sélectionnez les lignes optimisées à rétablir, puis cliquez sur **Restaurer** dans l’en-tête.

La boîte de dialogue **Restaurer** répertorie les suggestions qui seront restaurées, avec un court avertissement indiquant que les optimisations déployées seront rétablies. Confirmez la liste, puis cliquez sur **Restaurer** ou **Annuler**.

![Boîte de dialogue Restaurer répertoriant les suggestions à rétablir](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-rollback-dialog.png)

Une fois l’opération terminée, un résumé **Annulé avec succès** s’affiche ; fermez-le pour revenir au tableau de bord.

![Restauration terminée — Restauration réussie](/help/dashboards/opportunities/assets/add-llm-friendly-summaries-rollback-confirm.png)

## Tester l’opportunité avec la démo

Explorez le workflow Ajouter des résumés compatibles avec LLM dans la [démonstration de Frescopa](https://play.llmo.now/org/demo-org).
