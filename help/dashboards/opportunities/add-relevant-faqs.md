---
title: Ajouter des FAQ pertinentes
description: Découvrez comment LLM Optimizer identifie les pages à trafic élevé qui ne disposent pas de contenu de questions/réponses structuré pour les agents d’IA et comment examiner et déployer des questions fréquentes générées par l’IA avec Optimize sur Edge.
feature: Opportunities
source-git-commit: 7f0729839d761ca57236da935c8c7638dd92f32a
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 1%

---


# Ajouter des FAQ pertinentes

L’opportunité Ajouter des questions fréquentes pertinentes identifie les pages à trafic élevé qui ne disposent pas de contenu de questions/réponses structuré sur lequel les agents d’IA s’appuient souvent lors de la génération de réponses. Il présente un contenu pertinent, **FAQ alignée sur l’intention** ancré dans vos documents de page existants. Cela permet aux agents de faire correspondre plus directement les questions des utilisateurs et utilisatrices à votre contenu.

Pour chaque URL affectée, vous pouvez passer en revue les suggestions de FAQ générées par l’IA, puis les déployer avec [Optimiser sur Edge](/help/dashboards/optimize-at-edge/overview.md) afin que le trafic agentic reçoive un contexte de questions-réponses plus clair sans aucune modification requise du système de gestion de contenu (CMS).

## Comment cela résout le problème

Les correctifs sont appliqués à l’aide de [Optimiser dans Edge](/help/dashboards/optimize-at-edge/overview.md), qui :

- Diffuse un instantané HTML prégénéré aux agents d’IA.
- Enrichit la page avec le contenu des FAQ dans l’HTML qu’elles récupèrent.
- Fonctionne au niveau de la couche CDN (aucune modification de CMS).
- Est uniquement accessible par l’IA : aucun impact sur les visiteurs humains ou les robots d’optimisation du moteur de recherche.
- Déploie en quelques minutes et est **entièrement réversible** à partir de l’interface de LLM Optimizer.

## Fonctionnement

LLM Optimizer identifie les pages à trafic élevé où le contenu des questions/réponses est manquant ou mince, en fonction de l’invite de votre marque. Les URL concernées apparaissent dans le tableau **URL avec suggestions** de l’onglet **Suggestions actuelles**, où vous pouvez développer une ligne pour examiner chaque recommandation.

![URL avec des suggestions sur les suggestions actuelles, ligne développée avec des invites de FAQ et des réponses générées par l’IA](/help/dashboards/opportunities/assets/add-relevant-faqs-expand.png)

Le tableau **URL avec suggestions** répertorie les pages où les questions fréquentes peuvent aider à la découverte pilotée par l’IA. Les suggestions sont organisées en **Suggestions actuelles**, **Suggestions fixes** et **Suggestions ignorées**. Pour chaque URL, vous pouvez :

- **Développez la ligne** pour afficher le contenu de la FAQ proposée pour cette page.
- **Aperçu** la comparaison avant et après pour le trafic d’agent.
- **Marquer comme corrigé** si vous avez traité l’opportunité en dehors de LLM Optimizer.
- **Ignorer** les suggestions qui ne sont pas pertinentes.

Chaque entrée développée répertorie les questions fréquentes **invites**, **générées par l’IA** les réponses suggérées, les **raisonnements** et les **sources** liées à la page. Le tableau indique également le nombre de questions fréquentes suggérées par URL et **trafic Agentic (4 semaines)** pour vous aider à établir des priorités.

Cliquez sur **Aperçu** sur une ligne pour ouvrir l’aperçu de l’optimisation. Il compare l’aspect actuel de votre page en matière de trafic d’agent avec la vue de post-optimisation (par exemple, le nouveau bloc **FAQ**).

![Aperçu des optimisations comparant la vue actuelle de l’agent par rapport à la vue post-optimisation avec les questions fréquentes](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-01.png)

Cochez les cases des lignes pour indiquer les suggestions de questions fréquentes à envoyer. Le pied de page indique le nombre de sélections et fournit **Marquer comme fixe**, **Ignorer les suggestions** et **Déployer les optimisations**.

![Suggestions de FAQ sélectionnées sur les suggestions actuelles avec les optimisations de déploiement](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-02.png)

### Déploiement de l’optimisation

Lorsque vous êtes prêt à publier en périphérie, cliquez sur **Déployer les optimisations**. Une boîte de dialogue **Déployer vers Edge** répertorie les URL, les questions et les réponses que vous êtes sur le point de transmettre. Vérifiez la liste, puis choisissez **Déployer** ou **Annuler**.

![ Boîte de dialogue Déployer sur Edge ](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-03.png)

Après un déploiement réussi, **Déploiement terminé** confirme le nombre d’optimisations exécutées. Fermez la boîte de dialogue et ouvrez **Suggestions fixes** pour vérifier le statut.

![Confirmation de fin du déploiement](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-04.png)

>[!NOTE]
>
>Le déploiement des optimisations nécessite l’achèvement du processus d’intégration Optimizer at Edge. Si vous n’avez pas encore intégré, cliquez sur **Déployer les optimisations** pour être redirigé(e) vers le processus d’intégration. Pour plus d’informations sur le fonctionnement d’Optimize at Edge, les fournisseurs de réseau CDN pris en charge et le processus d’intégration, consultez la page [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

### Suggestions fixes et Afficher en direct

Dans **Suggestions fixes**, les URL déployées affichent **Optimisées** dans la colonne de statut. Développez une ligne pour passer en revue le contenu de la FAQ en direct, utilisez **Détails** pour les analyses ou cliquez sur **Afficher en direct** pour ouvrir une vue en lecture seule du **contenu de la page en cours** diffusé à des fins de vérification (y compris la section **FAQ** injectée).

![Suggestions fixes avec statut Optimisé, Affichage dynamique et Restauration](/help/dashboards/opportunities/assets/add-relevant-faqs-fixed.png)

La fenêtre **Afficher en direct** affiche la structure de la page et la copie de la FAQ, telles qu’elles sont présentées dans ce contrôle.

![Afficher en direct : contenu actuel de la page, y compris les questions fréquentes](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-05.png)

## Restauration

Si vous changez d’avis, vous pouvez annuler toute optimisation déployée. Dans la vue **Suggestions fixes**, sélectionnez les lignes optimisées à rétablir, puis cliquez sur **Restaurer** dans l’en-tête.

La boîte de dialogue **Restaurer** répertorie les suggestions qui seront restaurées, avec un court avertissement indiquant que les optimisations déployées seront rétablies. Confirmez la liste, puis cliquez sur **Restaurer** ou **Annuler**.

![Boîte de dialogue Restaurer répertoriant les suggestions à rétablir](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-07.png)

Une fois l’opération terminée, un résumé **Annulé avec succès** s’affiche ; fermez-le pour revenir au tableau de bord.

![Restauration terminée — Restauration réussie](/help/dashboards/opportunities/assets/add-relevant-faqs-ui-08.png)

## Faites un essai dans la démonstration

Explorez le workflow Ajouter des questions fréquentes pertinentes dans la [démonstration de Frescopa](https://play.llmo.now/org/demo-org).
