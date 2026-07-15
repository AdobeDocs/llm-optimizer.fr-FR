---
title: Ajouter une table des matières
description: Découvrez comment LLM Optimizer identifie les pages à trafic élevé qui ne disposent pas d’une structure de navigation claire pour les agents d’IA et comment examiner et déployer une table des matières avec Optimize sur Edge.
feature: Opportunities
autotag-review: '2026-07-15T16:47:42.882Z'
TQID: 'https://experienceleague.adobe.com/x-7FiZKCLMmEfm1x2lQNtfOd4su1MyGLrcAtLnjpaqw'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2: id: bbfc1b77-44c5-4fe8-b65f-ec160fe0d021
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 655
ht-degree: 9%

---


# Ajouter une table des matières

>[!NOTE]
>
> **Accès anticipé** — Cette fonctionnalité est disponible en accès anticipé. La disponibilité, l’éligibilité et certaines parties du workflow peuvent changer au fur et à mesure que la fonctionnalité se développe. Pour toute question sur l’accès, contactez l’équipe chargée de votre compte Adobe.

L’opportunité Ajouter une table des matières identifie les pages à trafic élevé qui ne disposent pas d’un guide clair **Table des matières** et structurel, ce qui rend plus difficile, pour les agents d’IA, d’analyser la page et de mapper les requêtes des utilisateurs aux sections appropriées. Il présente une table des matières structurée avec des en-têtes **liés à une ancre** qui reflètent les sections principales de la page. Cette structure permet aux agents d’extraire, de mapper et de citer les passages pertinents de manière plus fiable.

Pour chaque URL affectée, vous pouvez passer en revue les entrées suggérées dans la table des matières, puis les déployer avec [Optimiser dans Edge](/help/dashboards/optimize-at-edge/overview.md) afin que le trafic dynamique reçoive un contexte de navigation plus clair, sans nécessiter de modifications du système de gestion de contenu (CMS).

## Comment cela résout le problème

Les correctifs sont appliqués à l’aide de [Optimiser dans Edge](/help/dashboards/optimize-at-edge/overview.md), qui :

- Diffuse un instantané HTML prégénéré aux agents d’IA.
- Ajoute une table des matières à la page.
- Fonctionne au niveau de la couche CDN (aucune modification de CMS).
- Est uniquement accessible par l’IA : aucun impact sur les visiteurs humains ou les robots d’optimisation du moteur de recherche.
- Déploie en quelques minutes et est **entièrement réversible** à partir de l’interface de LLM Optimizer.

## Fonctionnement

LLM Optimizer identifie les pages à trafic élevé où une **table des matières** améliorerait la façon dont les agents d’IA parcourent les en-têtes et les sections. Pour chaque page, les suggestions sont ancrées dans les en-têtes déjà présents sur la page, de sorte que la table des matières reflète la structure de la page.

Les URL concernées apparaissent dans le tableau **URL avec suggestions** de l’onglet **Suggestions actuelles**.

Dans **Suggestions actuelles**, pour chaque URL vous pouvez :

- **Développez la ligne** pour examiner la table des matières proposée (analysée à partir des en-têtes de page et présentée sous la forme d’entrées liées à une ancre).
- **Aperçu** une comparaison avant et après.
- **Marquer comme corrigé** si vous avez traité l’opportunité en dehors de LLM Optimizer.
- **Ignorer** les suggestions qui ne sont pas pertinentes.

Les suggestions sont organisées en **Suggestions actuelles**, **Suggestions fixes** et **Suggestions ignorées**, conformément aux autres opportunités d’optimisation d’Edge.

### Déploiement de l’optimisation

Lorsque vous êtes prêt à publier sur le serveur Edge, sélectionnez les suggestions de la table des matières à déployer. Le pied de page résume le nombre d’éléments sélectionnés et propose généralement les options **Marquer comme fixe**, **Ignorer les suggestions** et **Déployer les optimisations**.

Cliquez sur **Déployer les optimisations**. Une boîte de dialogue **Déployer vers Edge** répertorie les URL sélectionnées et les détails d’optimisation. Vérifiez la liste, puis choisissez **Déployer** ou **Annuler**.

Après un déploiement réussi, **Déploiement terminé** confirme le nombre d’optimisations exécutées. Fermez la boîte de dialogue et ouvrez **Suggestions fixes** pour vérifier le statut.

>[!NOTE]
>
>Le processus d’intégration à Optimize at Edge doit être terminé pour pouvoir déployer des optimisations. Si vous n’avez pas encore effectué l’intégration, cliquer sur **Déployer des optimisations** vous redirigera vers le processus d’intégration. Pour plus d’informations sur le fonctionnement d’Optimize at Edge, les fournisseurs de réseau CDN pris en charge et le processus d’intégration, consultez la page [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

### Suggestions fixes et Afficher en direct

Dans **Suggestions fixes**, les URL déployées affichent **Optimisées** dans la colonne de statut. Développez une ligne pour passer en revue la table des matières déployée, utilisez **Détails** pour les analyses si disponible, ou cliquez sur **Afficher en direct** pour ouvrir une vue en lecture seule du **contenu actuel de la page** diffusé à des fins de vérification (y compris la **table des matières** injectée).

Lorsque vous devez annuler des modifications de périphérie en bloc, sélectionnez les lignes optimisées à l’aide des cases à cocher, puis utilisez **Restaurer** dans l’en-tête.

## Restauration

Si vous changez d’avis, vous pouvez annuler le déploiement d’une optimisation. Dans la vue **Suggestions fixes**, sélectionnez les lignes optimisées à rétablir, puis cliquez sur **Restaurer** dans l’en-tête.

La boîte de dialogue **Restaurer** répertorie les suggestions qui seront restaurées, avec un court avertissement indiquant que les optimisations déployées seront rétablies. Confirmez la liste, puis cliquez sur **Restaurer** ou **Annuler**.

Une fois l’opération terminée, un résumé **Annulé avec succès** s’affiche ; fermez-le pour revenir au tableau de bord.
