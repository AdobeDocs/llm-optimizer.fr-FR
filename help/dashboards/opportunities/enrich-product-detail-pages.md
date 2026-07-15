---
title: Enrichissement de la page des détails du produit
description: Découvrez comment LLM Optimizer identifie les pages de produits où les données de catalogue sont masquées aux agents d’IA et comment récupérer cette visibilité à l’aide de l’optimisation basée sur les périphériques et des informations sur les catalogues de produits optimisées par Adobe Commerce.
feature: Opportunities
autotag-review: '2026-07-15T17:50:18.330Z'
TQID: 'https://experienceleague.adobe.com/UINqU57uqqbNJE3cV6zK56hxCcAmRrMMv-esNEfxqKI'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2: id: a6256a78-8814-462c-9627-86699b39cee1
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 1210
ht-degree: 7%

---


# Enrichissement des pages de détails du produit

Les agents d’IA peuvent uniquement recommander des produits qu’ils peuvent comprendre entièrement. Sur la plupart des vitrines commerciales, les pages de produits sont conçues pour les acheteurs humains. Par conséquent, ces produits reposent sur des onglets rendus par JavaScript, des panneaux extensibles, des assistants d’achat, des modèles interactifs et des liens vers des variantes de produits de surface, des spécifications et des fonctionnalités. Les agents d’IA n’analysent pas les détails de la page Produit, ce qui signifie que ces données riches sur les produits ne sont jamais vues par les robots d&#39;exploration LLM qui alimentent les découvertes pilotées par l’IA, même lorsqu’elles sont entièrement visibles par les visiteurs humains.

L’opportunité Enrichir les pages de détails du produit identifie les pages de produits de votre catalogue Adobe Commerce où existe cet écart de visibilité. Optimisé par le catalogue Adobe Commerce, il compare ce à quoi les agents d’IA peuvent accéder sur le storefront par rapport aux données complètes des produits disponibles dans votre catalogue et fait apparaître tous les attributs, variantes et profondeurs de vos caractéristiques de produit qui sont absents de la vue de l’agent d’IA.

Il présente en un coup d’œil les mesures clés suivantes :

- **Pages de produits** — Liste de toutes les pages de détails de produits identifiées avec un écart de visibilité des données de catalogue.
- **Trafic des agents** — Nombre total de visites et d’interactions sur un site qui sont initiées et dirigées par des agents d’IA autonomes (tels que des assistants ou des robots optimisés par LLM) agissant au nom des utilisateurs pour découvrir, récupérer ou interagir avec du contenu.

![Tableau de bord Enrichir les pages de détails du produit](/help/dashboards/opportunities/assets/enrich-product-detail-pages-overview.png)

Cette opportunité peut être optimisée à l’aide d’[Optimize at Edge](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/resources/optimize-at-edge/overview#what-is-optimize-at-edge). Les optimisations sont diffusées exclusivement aux agents d’IA sans impact sur les visiteurs humains (diffusion en robots uniquement), appliquées au niveau de la couche CDN sans CMS ni modifications de catalogue requises, et peuvent prendre effet en quelques minutes sans engagement des développeurs, ce qui en fait un chemin de déploiement rapide et à faible risque pour les catalogues de produits volumineux.

## Fonctionnement

L’agent de catalogue Adobe Commerce lit l’ensemble des données de votre catalogue de produits, notamment les variantes, les relations de produits approfondies, les attributs, les facettes, les métadonnées des catégories et toutes les caractéristiques des produits. Il compare ensuite les données à ce qui est réellement accessible aux agents d’IA sur le PDP de storefront correspondant. Les pages où les données de catalogue sont masquées dans les robots d&#39;exploration d’IA sont affichées dans le tableau **URL avec des suggestions**, hiérarchisé par volume de trafic d’agent.

Pour chaque page de produit affectée, LLM Optimizer fournit :

- **Aperçu de l’analyse de l’IA** — Liste complète des informations de catalogue manquantes dans la vue de l’agent d’IA et des raisons pour lesquelles elles sont importantes pour la découverte de produits pilotée par LLM, y compris une liste de points de données récupérables tels que les variantes de produits, les options de taille, les spécifications du matériau et les détails de compatibilité, entre autres.

Le correctif est appliqué à l’aide de la fonctionnalité de déploiement Edge d’Adobe [Optimize at Edge](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/resources/optimize-at-edge/overview#what-is-optimize-at-edge), qui fournit un instantané d’HTML entièrement prégénéré et convivial par l’IA aux agents utilisateurs de LLM au niveau de la couche CDN. Cela récupère toutes les données de catalogue précédemment masquées (y compris les variantes de produits, les spécifications techniques et les détails de fonctionnalités) sans toucher votre catalogue Commerce ou l’interface utilisateur de storefront visible par l’homme.

![URL avec tableau de suggestions](/help/dashboards/opportunities/assets/enrich-product-detail-pages-suggestions.png)

## URL avec suggestions

Le tableau **URL avec suggestions** répertorie toutes les pages de produits identifiées qui bénéficient d’une optimisation. Pour chaque URL de produit, vous pouvez :

- **Aperçu** pour afficher l’analyse de l’IA, y compris les informations de catalogue manquantes et la raison pour laquelle elles sont importantes pour la découvrabilité pilotée par l’IA.
- **Marquer comme fixe** une fois l’optimisation déployée et validée
- **Ignorer** suggestions qui ne sont pas pertinentes pour votre stratégie de marchandisage.

Les suggestions sont organisées en trois vues : **Suggestions actuelles**, **Suggestions fixes** et **Suggestions ignorées**. Une fois qu’une suggestion est déployée, elle passe aux suggestions fixes avec un statut **Optimisé** et une action **Afficher en direct** pour vérifier que l’enrichissement est en direct pour le trafic d’agents. Les suggestions fixes peuvent être annulées à tout moment.

## Déploiement de l’optimisation

Une fois que vous avez examiné les suggestions et sélectionné les pages de produit à optimiser, cliquez sur **Déployer les optimisations** pour publier l’enrichissement sur le réseau CDN Edge. Une boîte de dialogue de confirmation **Déployer vers Edge** affiche les URL de produit sélectionnées, le type d’optimisation et l’enrichissement appliqué. Après le déploiement, un écran de confirmation confirme quelles pages de produits ont été optimisées avec succès.

L’optimisation est diffusée exclusivement aux agents utilisateurs de l’IA via la couche de périphérie du réseau CDN. Les visiteurs humains continuent à voir votre expérience de storefront existante exactement comme auparavant, sans modifications de la conception de votre PDP, des performances de la page ou de l’expérience de votre marque.

>[!NOTE]
>
>Le déploiement des optimisations nécessite (1) la connexion de LLM Optimizer à Adobe Commerce et (2) l’achèvement du processus d’intégration d’Optimisation lors de l’utilisation d’Edge.

Si votre instance Commerce n’est pas encore connectée à LLM Optimizer, vous serez redirigé vers la configuration de la connexion avant que les enrichissements puissent être appliqués.

Si vous n’avez pas encore effectué l’intégration, cliquer sur **Déployer des optimisations** vous redirigera vers le processus d’intégration. Pour plus d’informations sur le fonctionnement d’Optimize at Edge, les fournisseurs de réseau CDN pris en charge et le processus d’intégration, consultez la page [Optimize at Edge](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/resources/optimize-at-edge/overview#what-is-optimize-at-edge).

Boîte de dialogue ![Déployer sur Edge](/help/dashboards/opportunities/assets/enrich-product-detail-pages-deploy.png)

## Tester l’opportunité avec la démo

Consultez l’opportunité Enrichir les pages de détails du produit en action à l’aide de l’environnement de démonstration Frescopa.

[Afficher les pages Enrichir les détails du produit dans la démonstration de Frescopa](https://play.llmo.now/org/demo-org/opportunities/commerce-product-page-enrichment/4e8b0428-0893-4864-a00e-fc1d77fb3372?siteId=9ae8877a-bbf3-407d-9adb-d6a72ce3c5e3)

## Questions fréquentes

**Pourquoi les données de mon catalogue de produits sont-elles masquées aux agents d’IA ?**

Les vitrines Commerce sont conçues pour les acheteurs humains. Les caractéristiques des produits, leurs variantes, les options de taille, les détails des matériaux et d’autres spécifications techniques sont souvent traités dans le cadre d’interactions pilotées par JavaScript, telles que des onglets, des panneaux réductibles, des modèles de pop-up, des liens et des assistants d’achat. Les agents d’IA n’analysent pas les détails de la page Produit. De ce fait, toutes ces données sont invisibles pour les robots d&#39;exploration LLM, même lorsqu’elles sont entièrement présentes dans votre catalogue de produits. Il en résulte que les agents d’IA formulent des recommandations de produits en fonction d’une fraction des informations réellement disponibles sur les produits.

**Quels types de données de produit cette optimisation récupère-t-elle ?**

L’agent de catalogue récupère toutes les informations sur les produits disponibles dans votre catalogue Adobe Commerce qui ne sont actuellement pas accessibles sur le storefront pour les agents d’IA. Cela inclut les caractères du produit, les relations, les variantes (tailles, couleurs, configurations), les spécifications et attributs techniques, les détails de compatibilité, les métadonnées de catégorie et les valeurs de facette.

**Cette optimisation affectera-t-elle mes visiteurs humains, mes robots d’optimisation du moteur de recherche ou les performances de storefront ?**

Non. Optimize at Edge cible uniquement les agents utilisateurs d’IA. Les visiteurs humains et les robots d’optimisation du moteur de recherche reçoivent la page de produit originale exactement comme auparavant, sans modifications de leur expérience, des performances de chargement de page ou de la conception de storefront.

**Dois-je modifier mon catalogue Commerce, CMS ou impliquer des développeurs ?**

Non. L’optimisation est appliquée au niveau de la couche de périphérie du réseau CDN et ne nécessite aucune modification de votre catalogue Adobe Commerce, aucun déploiement de code et aucun engagement des développeurs. Une fois l’intégration à Optimize dans Edge effectuée, vous pouvez déployer et restaurer des enrichissements en quelques minutes directement depuis l’interface de LLM Optimizer.

**Que se passe-t-il si mes données produit changent après le déploiement ?**

Pour l’opportunité Enrichir les pages de détails du produit , LLM Optimizer utilise des paramètres de TTL à faible cache afin que toute mise à jour de produit de votre catalogue Commerce déclenche une actualisation en quelques minutes. Les agents d’IA recevront toujours les données de produit les plus récentes disponibles.
