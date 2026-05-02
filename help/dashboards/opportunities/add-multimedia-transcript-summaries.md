---
title: Ajouter des résumés de transcription multimédia
description: Découvrez comment LLM Optimizer identifie les pages où des informations essentielles sont incorporées dans une vidéo sans texte lisible par ordinateur et comment examiner et déployer des résumés de transcription générés par l’IA avec Optimize sur Edge.
feature: Opportunities
source-git-commit: 36a6836f86b6d31cc4bf4682e881bd127edf66e4
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---


# Ajouter des résumés de transcription multimédia

>[!NOTE]
>
> **Accès anticipé** — Ajouter des résumés de transcription multimédia est disponible dans Accès anticipé. La disponibilité, l’éligibilité et certaines parties du workflow peuvent changer au fur et à mesure que la fonctionnalité se développe. Pour toute question sur l’accès, contactez l’équipe chargée de votre compte Adobe.

L’opportunité Ajouter des résumés de transcription multimédia identifie les pages où des informations importantes se trouvent dans des vidéos ou d’autres médias, sans transcriptions ni courts résumés textuels que les agents d’IA peuvent lire. Il présente des résumés de transcription générés par **IA** ancrés dans le contexte des médias et des pages environnantes. Il permet de récupérer des informations de marque clés qui auraient autrement été manquantes en rendant le contenu multimédia compréhensible pour les agents d’IA.

Pour chaque URL affectée, vous pouvez passer en revue les détails **Correctif de contenu**, **Implémentation** proposés (par exemple, le sélecteur et l’opération CSS de la cible) et **Justification**, puis effectuer le déploiement avec [Optimiser sur Edge](/help/dashboards/optimize-at-edge/overview.md) pour que le trafic agentique reçoive l’HTML enrichie sans les modifications requises du système de gestion de contenu (CMS).

## Comment cela résout le problème

Les correctifs sont appliqués à l’aide de [Optimiser dans Edge](/help/dashboards/optimize-at-edge/overview.md), qui :

- Diffuse un instantané HTML prégénéré aux agents d’IA.
- Enrichit la page avec le texte du résumé de la transcription dans l’HTML qu’ils récupèrent (par exemple, près de la vidéo intégrée appropriée).
- Fonctionne au niveau de la couche CDN (aucune modification de CMS).
- Est uniquement accessible par l’IA : aucun impact sur les visiteurs humains ou les robots d’optimisation du moteur de recherche.
- Déploie en quelques minutes et est **entièrement réversible** à partir de l’interface de LLM Optimizer.

## Fonctionnement

LLM Optimizer signale les pages à trafic élevé pour lesquelles il manque du texte lisible par ordinateur pour les médias incorporés, en fonction de votre configuration et de la structure de la page. Les URL concernées apparaissent dans le tableau **URL avec suggestions** de l’onglet **Suggestions actuelles**, où vous pouvez développer une ligne pour examiner chaque **correctif de contenu**, comment il sera appliqué et pourquoi il est recommandé.

Pour chaque page, vous disposez des éléments suivants :

**Résumé multimédia** - Résumés structurés dérivés de contenu vidéo.
**Aperçu** - Avant et après la comparaison des pages.

![URL avec des suggestions sur les suggestions actuelles, ligne développée avec le correctif de contenu, les détails d’implémentation et la justification](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-expand.png)

Le tableau **URL avec suggestions** répertorie les pages où une transcription ou un texte de résumé aiderait à la découverte automatique. Les suggestions sont organisées en **Suggestions actuelles**, **Suggestions fixes** et **Suggestions ignorées**. Pour chaque URL, vous pouvez :

- **Développez la ligne** pour afficher le texte **Correctif de contenu**, les détails **Implémentation** (y compris l’opération DOM prévue et le sélecteur CSS) et **Justification** de la modification.
- **Aperçu** la comparaison avant et après pour le trafic d’agent.
- **Marquer comme corrigé** si vous avez traité l’opportunité en dehors de LLM Optimizer.
- **Ignorer** les suggestions qui ne sont pas pertinentes.

Vous pouvez modifier le texte de correctif de la ligne, le cas échéant (commande Crayon), puis utiliser les cases à cocher de la ligne pour sélectionner les éléments à déployer. Le pied de page indique le nombre de sélections et fournit **Marquer comme fixe**, **Ignorer les suggestions** et **Déployer les optimisations**.

### Déploiement de l’optimisation

Lorsque vous êtes prêt à publier en périphérie, cliquez sur **Déployer les optimisations**. Une boîte de dialogue **Déployer vers Edge** répertorie les URL, les sélecteurs et les opérations que vous êtes sur le point d’exécuter. Vérifiez la liste, puis choisissez **Déployer** ou **Annuler**.

![Boîte de dialogue Déployer sur Edge pour les correctifs de contenu de résumé de transcription multimédia](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-deploy-dialog.png)

Après un déploiement réussi, **Déploiement terminé** confirme le nombre d’optimisations exécutées. Fermez la boîte de dialogue et ouvrez **Suggestions fixes** pour vérifier le statut.

![Confirmation de fin du déploiement](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-deploy-confirm.png)

>[!NOTE]
>
> Le déploiement des optimisations nécessite l’achèvement du processus d’intégration Optimizer at Edge. Si vous n’avez pas encore intégré, cliquez sur **Déployer les optimisations** pour être redirigé(e) vers le processus d’intégration. Pour plus d’informations sur le fonctionnement d’Optimize at Edge, les fournisseurs de réseau CDN pris en charge et le processus d’intégration, consultez la page [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

### Suggestions fixes et Afficher en direct

Dans **Suggestions fixes**, les URL déployées affichent **Optimisées** dans la colonne de statut. Développez une ligne pour passer en revue les détails **Correctif de contenu**, **Implémentation** et **Justification** en direct. De plus, vous pouvez utiliser **Détails** pour les analyses ou **Afficher en direct** le cas échéant, pour confirmer le trafic agent reçu.

![Correctifs de suggestions avec le statut Optimisé , le correctif de contenu étendu et la restauration](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-fixed.png)

Pour effectuer une restauration en bloc, sélectionnez les lignes optimisées à l’aide des cases à cocher, puis utilisez **Restaurer** dans l’en-tête.

![Suggestions fixes avec des lignes sélectionnées avant la restauration](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-select-in-fixed.png)

## Restauration

Si vous changez d’avis, vous pouvez annuler le déploiement d’une optimisation. Dans **Suggestions fixes**, sélectionnez les lignes à rétablir, puis cliquez sur **Restaurer**.

La boîte de dialogue **Restaurer** répertorie les suggestions qui seront restaurées et avertit que les optimisations déployées seront supprimées du chemin dynamique pour le trafic d’agent. Confirmez, puis cliquez sur **Restaurer** ou **Annuler**.

![Boîte de dialogue Restaurer répertoriant les suggestions à rétablir](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-rollback-dialog.png)

Une fois l’opération terminée, un résumé **Annulé avec succès** s’affiche ; fermez-le pour revenir au tableau de bord.

![Restauration terminée — Restauration réussie](/help/dashboards/opportunities/assets/add-multimedia-transcript-summaries-rollback-confirm.png)

## Faites un essai dans la démonstration

Explorez le workflow Ajouter des résumés de transcription multimédia dans la [démonstration de Frescopa](https://play.llmo.now/org/demo-org).
