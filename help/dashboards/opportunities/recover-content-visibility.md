---
title: Restauration de la visibilité du contenu
description: Découvrez comment LLM Optimizer identifie les pages où le contenu critique est masqué pour les agents IA et comment récupérer cette visibilité à l’aide de l’optimisation en périphérie.
feature: Opportunities
autotag-review: '2026-05-15T17:56:37.098Z'
TQID: 'https://experienceleague.adobe.com/rHqJL4RrJr1ghsy4fhXe-JLDrWruNSZgVhXQeRN-iyA'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 928
ht-degree: 100%

---


# Restauration de la visibilité du contenu

Les agents IA ne peuvent citer que le contenu auquel ils ont accès. Lorsque le contenu clé de vos pages est masqué par un rendu côté client et des chargements dynamiques (tels que les descriptions de produits, les évaluations des utilisateurs et utilisatrices, les recettes et les commentaires), les agents IA passent à côté et ne peuvent donc pas le citer.

L’opportunité Récupérer la visibilité du contenu identifie les pages de votre site concernées par cet écart de visibilité. Pour chaque page identifiée, elle vous indique exactement quel contenu est masqué pour les agents IA, met en évidence l’écart de visibilité, et vous permet d’effectuer des corrections sans modifier le CMS pour récupérer le contenu masqué.

Elle présente trois mesures clés en un coup d’œil :

- **URL** — Nombre de pages identifiées par un écart de visibilité du contenu.
- **Contenu récupérable estimé** — Estimation du contenu qui peut être récupéré grâce à l’optimisation.
- **Visibilité moyenne du contenu** — Pourcentage moyen de contenu actuellement visible par les agents d’IA sur les pages affectées.

![Tableau de bord Récupérer la visibilité du contenu](/help/dashboards/opportunities/assets/recover-content-visibility-overview.png)

Pour une présentation vidéo de cette opportunité, vous pouvez regarder [Récupérer la Visibilité du contenu ](https://www.youtube.com/watch?v=BigPyJssFCw).

Cette opportunité peut être optimisée à l’aide d’[Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md). Les optimisations sont destinées exclusivement aux agents d’IA et n’ont pas d’impact sur les visiteurs humains (diffusion uniquement aux robots). Les optimisations sont ensuite appliquées à la couche CDN sans modification du CMS et peuvent être effectives en quelques minutes sans intervention des équipes de développement, ce qui en fait un déploiement rapide et à faible risque.

## Fonctionnement

LLM Optimizer analyse vos pages en comparant ce à quoi les agents d’IA peuvent accéder à ce qui est réellement présent sur la page. Les pages qui reçoivent un fort trafic généré par l’IA agentique, mais qui ont une faible visibilité du contenu sont affichées dans le tableau **URL avec des suggestions**, classées par volume de trafic agentique.

Pour chaque URL affectée, LLM Optimizer donne les informations suivantes :

- **Analyse de l’IA** — Description du contenu manquant et des raisons pour lesquelles il est important qu’il soit citable par le LLM, ainsi qu’une liste des références de contenu pouvant être récupérées.
- **Visibilité du contenu** — Pourcentage du contenu actuellement visible par les agents d’IA sur cette page.
- **Contenu récupérable estimé** : estimation du contenu qui peut être récupéré avec l’optimisation.
- **Aperçu** — Comparaison HTML côte à côte de l’apparence actuelle de la page par rapport à sa version post-optimisation, afin que vous puissiez valider les modifications avant le déploiement.

Le correctif est appliqué à l’aide de la fonctionnalité [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md) — Capacité de déploiement en périphérie d’Adobe qui fournit, au niveau de la couche CDN, un instantané HTML pré-généré et optimisé pour l’IA aux agents utilisateurs LLM, et qui récupère le contenu précédemment masqué sans modifier votre CMS.

<!-- [URLs with suggestions](/help/dashboards/opportunities/assets/recover-content-visibility-urls.png)-->

## URL avec suggestions

Le tableau **URL avec des suggestions** répertorie toutes les pages affectées et peut être filtré par classification. Pour chaque URL, vous pouvez effectuer les opérations suivantes :

- **Développer la ligne** pour afficher l’analyse de l’IA, y compris le contenu manquant et son importance pour le LLM.
- **Prévisualiser** la comparaison HTML côte à côte de la page active par rapport à la version post-optimisation.
- **Marquer comme résolu** une fois le problème résolu.
- **Ignorer** les suggestions qui ne sont pas pertinentes.

Les suggestions sont organisées en trois vues : **Suggestions actuelles**, **Suggestions fixes** et **Suggestions ignorées**. Une fois qu’une suggestion est déployée, elle passe à la catégorie Suggestions fixes avec un statut **Optimisé** et une action **Afficher en direct** pour vérifier que l’optimisation est active pour le trafic généré par l’IA agentique. Les suggestions fixes peuvent également être restaurées à tout moment.

![Suggestions fixes avec statut Optimisé](/help/dashboards/opportunities/assets/recover-content-visibility-fixed.png)

## Déploiement de l’optimisation

Une fois que vous avez examiné les suggestions et sélectionné les URL à optimiser, cliquez sur **Déployer les optimisations** pour publier le correctif sur le réseau CDN Edge. Une boîte de dialogue de confirmation **Déployer vers Edge** affiche les URL sélectionnées, leur type (pré-rendu) et la suggestion appliquée. Après le déploiement, un écran de confirmation affiche les URL qui ont été optimisées.

>[!NOTE]
>
>Le processus d’intégration à Optimize at Edge doit être terminé pour pouvoir déployer des optimisations. Si vous n’avez pas encore effectué l’intégration, cliquer sur **Déployer des optimisations** vous redirigera vers le processus d’intégration. Pour plus d’informations sur le fonctionnement d’Optimize at Edge, les fournisseurs de réseau CDN pris en charge et le processus d’intégration, consultez la page [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md).

Boîte de dialogue ![Déployer sur Edge](/help/dashboards/opportunities/assets/recover-content-visibility-deploy.png)

## Tester l’opportunité avec la démo

Découvrez l’opportunité Récupérer la visibilité du contenu dans l’environnement de démo Frescopa.

[Voir l’opportunité Récupérer la visibilité du contenu dans la démo Frescopa](https://play.llmo.now/org/demo-org/opportunities/prerender/75729489-756a-4c2b-9905-155b1715da5c)

## Questions fréquentes

**Pourquoi le contenu de ma page est-il masqué pour les agents d’IA ?**

La plupart des sites web modernes reposent sur JavaScript pour charger le contenu de manière dynamique après la demande de page initiale. Les agents d’IA n’exécutent généralement pas JavaScript, de sorte que le contenu généré côté client (listes de produits, avis d’utilisateurs et d’utilisatrices, liens vers des articles de blog, etc.) n’est jamais visible pour l’agent d’IA, même s’il est entièrement visible par les visiteurs humains.

**Cette optimisation a-t-elle un impact sur les visiteurs humains ou les robots de SEO ?**

Non. Optimize at Edge cible uniquement les agents utilisateurs d’IA. Les visiteurs humains et les robots de SEO voient la page d’origine, sans impact sur leur expérience ni leurs performances.

**Dois-je modifier mon CMS ou faire appel à l’équipe de développement ?**

Non. L’optimisation est appliquée à la périphérie du réseau CDN et ne nécessite aucune modification du contenu, aucun déploiement de code ni aucune intervention de l’équipe de développement. Une fois l’intégration à Optimize at Edge effectuée, vous pouvez déployer et annuler les modifications en quelques minutes directement à partir de l’interface de LLM Optimizer.

**Que se passe-t-il si le contenu de ma page change après le déploiement ?**

Pour l’opportunité Récupérer la visibilité du contenu, LLM Optimizer définit une courte durée de vie du cache afin que toute mise à jour de contenu sur votre site déclenche une actualisation en quelques minutes. Les agents d’IA recevront toujours la version la plus récente de votre contenu.

**Comment démarrer avec Optimize at Edge ?**

Consultez la page[Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md) pour en savoir plus sur le processus d’intégration, consulter les guides de configuration CDN et connaître les conditions préalables.
