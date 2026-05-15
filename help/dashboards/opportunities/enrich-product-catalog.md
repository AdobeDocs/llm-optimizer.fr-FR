---
title: Enrichissement du catalogue de produits
description: Découvrez comment LLM Optimizer identifie les produits dotés de descriptions génériques ou techniquement denses et comment les améliorer à l’aide d’enrichissements narratifs générés par l’IA optimisés par Adobe Commerce.
feature: Opportunities
autotag-review: '2026-05-15T17:45:51.619Z'
TQID: 'https://experienceleague.adobe.com/5ihGQ8L-37uWsZSDo4TVCUPBPqsqqQ5waGbH3VKPIig'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: c0713b97-4af8-4c41-b742-5afcc6ced468
subfeature_v2:
  - id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 1266
ht-degree: 0%

---


# Enrichissement du catalogue de produits

Les LLM tentent de connecter les attributs de produit à la valeur réelle, aux cas d’utilisation et à l’intention d’achat. Lorsque les noms et descriptions de produits ne communiquent pas clairement cette valeur, vos produits sont moins susceptibles d’être cités, recommandés ou faire l’objet d’une découverte pilotée par l’IA. En effet, les agents d’IA raisonnent par le biais de relations, et non de champs de données brutes. Liste de produits portant le nom de « Coffee Grinder X200 » et description énumérant les caractéristiques techniques (puissance du moteur, paramètres de meulage, etc.) Donne très peu à un LLM quand un client demande « le meilleur moulin à expresso pour un barista maison ».

L’opportunité d’enrichissement du catalogue de produits identifie les produits de votre catalogue Commerce dont les noms et descriptions sont trop génériques, trop denses sur le plan technique ou trop ambigus pour être interprétés avec précision par les ILM. Optimisé par Adobe Commerce, il génère des enrichissements narratifs et riches en intentions pour les noms et descriptions de vos produits et les applique directement à votre catalogue Commerce en un seul clic.

Il fait apparaître deux mesures clés en un coup d’œil :

- **URLs** — Liste des pages Détails du produit (produits de votre catalogue) dont la qualité d&#39;enrichissement a été évaluée.
- **Trafic des agents** — Nombre total de visites et d’interactions sur un site qui sont initiées et dirigées par des agents d’IA autonomes (tels que des assistants ou des robots optimisés par LLM) agissant au nom des utilisateurs pour découvrir, récupérer ou interagir avec du contenu.

![Tableau de bord d’enrichissement du catalogue de produits](/help/dashboards/opportunities/assets/enrich-product-catalog-overview.png)

>[!NOTE]
>
>Cette opportunité est actuellement dans Beta et peut être activée par les clients Adobe Commerce. Contactez votre gestionnaire de compte pour accéder à la version bêta.

## Fonctionnement

L’agent de catalogue Adobe Commerce lit les données de votre catalogue de produits et analyse chaque SKU de produit, y compris tous ses attributs techniques, le contexte de la catégorie, les variantes, le nom et la description existants. Il identifie les produits pour lesquels le nom ou la description actuels ne communiquent pas de valeur pertinente pour l’acheteur et génère une alternative enrichie qui traduit les détails techniques dans un langage clair et aligné sur l’intention.

Par exemple, un produit appelé *« Meuleuse à café X200 »* avec une description énumérant « 18 réglages de meulage, moteur de 450 W » peut être enrichi pour expliquer que « Le X200 offre une consistance espresso au niveau du café parce que son système de meulage à 18 étapes est couplé à un moteur à couple élevé pour des résultats répétables à la maison ». Les attributs tels que le prix et l’inventaire sont délibérément exclus de l’enrichissement. L’agent de catalogue se concentre sur les attributs générateurs de valeur qui expliquent ce qu’est le produit, comment il est utilisé et pourquoi il est important pour un acheteur.

Les produits contenant des suggestions d’enrichissement sont affichés dans le tableau **URL avec des suggestions** hiérarchisé par impact d’enrichissement. Pour chaque produit identifié, LLM Optimizer fournit :

- **Nom actuel** — Nom du produit tel qu&#39;il apparaît dans votre catalogue Adobe Commerce.
- **Nom mis à jour** : nom de produit généré par l’IA et axé sur la valeur, qui communique le contexte et l’intention relatifs à l’acheteur aux LLM.
- **Description actuelle** — Description du produit tel qu&#39;il apparaît dans votre catalogue Adobe Commerce.
- **Description suggérée** - Description générée par l’IA qui traduit les attributs techniques de votre produit en un récit qui aide les ILM à comprendre ce qu’est le produit, la valeur narrative et pourquoi il est important.

![Tableau des produits avec suggestions](/help/dashboards/opportunities/assets/enrich-product-catalog-suggestions.png)

## Produits avec suggestions

Le tableau **URL avec suggestions** répertorie tous les produits présentant des opportunités d’enrichissement. Pour chaque produit, vous pouvez :

- **Développez la ligne** pour afficher l’analyse IA et l’enrichissement proposé.
- **Modifier** le nom ou la description du produit proposé avant la demande, afin de vous conformer aux directives de votre marque en matière de voix et de marchandisage.
- **Déployez l’optimisation** pour les produits que vous souhaitez enrichir et publiez-la directement dans votre catalogue Adobe Commerce.
- **Marquer comme corrigé** une fois que l’enrichissement a été révisé et appliqué.
- **Ignorer** les suggestions qui ne sont pas pertinentes pour votre stratégie de catalogue.

Les suggestions sont organisées en trois vues : **Suggestions actuelles**, **Suggestions fixes** et **Suggestions ignorées**. Une fois qu’un enrichissement est appliqué, il passe aux Suggestions fixes avec le statut **Appliqué** et une action **Afficher dans le catalogue** pour vérifier la mise à jour dans Adobe Commerce. Les enrichissements appliqués peuvent être restaurés à tout moment, en restaurant le nom et la description d’origine du produit.

<!--[Fixed suggestions with Applied status](/help/dashboards/opportunities/assets/enrich-product-catalog-fixed.png)-->

## Déploiement de l’optimisation

Une fois que vous avez révisé et éventuellement modifié les suggestions de vos produits sélectionnés, cliquez sur **Déployer les optimisations** pour publier le nom et la description du produit mis à jour dans votre catalogue Adobe Commerce. Une boîte de dialogue de confirmation affiche les produits sélectionnés et les modifications appliquées. Après confirmation, un écran de résultats confirme quels produits ont été correctement mis à jour.

Les enrichissements étant directement appliqués au catalogue Adobe Commerce, les noms et descriptions de produits mis à jour sont immédiatement disponibles sur tous les canaux qui utilisent votre catalogue, y compris vos storefronts, vos flux de publicités et toutes les intégrations directes de produits LLM. Cela garantit que chaque surface sur laquelle apparaît votre produit communique des informations cohérentes et de haute qualité.

>[!NOTE]
>
>L’enrichissement du catalogue nécessite la connexion de LLM Optimizer à Adobe Commerce. Si votre instance Commerce n’est pas encore connectée à LLM Optimizer, vous serez redirigé vers la configuration de la connexion avant que les enrichissements puissent être appliqués.

![Boîte de dialogue Appliquer les enrichissements](/help/dashboards/opportunities/assets/enrich-product-catalog-deploy.png)

## Faites un essai dans la démonstration

Consultez l’opportunité d’enrichissement du catalogue de produits en action à l’aide de l’environnement de démonstration Frescopa.

[Afficher le catalogue de produits enrichi dans la démonstration de Frescopa](https://play.llmo.now/org/demo-org/opportunities/commerce-product-catalog-enrichment/e5f2a854-7477-421c-820f-74d5dd595647?siteId=9ae8877a-bbf3-407d-9adb-d6a72ce3c5e3)

## Questions fréquentes

**Pourquoi les noms et descriptions de produits génériques nuisent-ils à la découvrabilité de l’IA ?**

Les LLM ne correspondent pas aux produits aux requêtes d’acheteurs en recherchant le chevauchement des mots-clés. Ils réfléchissent aux relations, en établissant un lien entre ce qu’un acheteur a l’intention de trouver et ce que fait réellement un produit, à qui il est destiné et comment il se compare aux autres produits. Un nom ou une description de produit qui répertorie les spécifications techniques sans communiquer de valeur réelle donne très peu de contexte à un LLM. Le résultat est que votre produit est moins susceptible d&#39;être cité lorsqu&#39;un acheteur pose une question pertinente, même si votre produit correspond le mieux à ses besoins.

**Quels attributs de produit l’agent de catalogue utilise-t-il pour générer des enrichissements ?**

L’agent de catalogue utilise des attributs orientés valeur dans votre catalogue Commerce qui aident les gestionnaires de sites à comprendre ce qu’est un produit, comment il est utilisé et pourquoi il est important. Attributs qui génèrent de la valeur, tels que les fonctionnalités du produit, les cas d’utilisation, les propriétés de matériau, le contexte de catégorie et les détails de compatibilité. Les attributs tels que le prix et les niveaux de stock sont délibérément exclus, car ils ne contribuent pas à la compréhension sémantique du produit et peuvent rendre les descriptions moins durables à mesure que les conditions changent.

**Puis-je modifier l’enrichissement généré par l’IA avant de l’appliquer ?**

Oui. Chaque suggestion comprend un aperçu modifiable du nom et de la description du produit proposé. Vous pouvez modifier l’enrichissement pour qu’il corresponde à la voix de votre marque, corriger les inexactitudes ou incorporer du contexte supplémentaire avant de l’appliquer à votre catalogue.

**L&#39;enrichissement va-t-il changer ce que les visiteurs humains voient sur ma vitrine ?**

Oui, les visiteurs humains verront le nom et la description du produit mis à jour sur le storefront, ainsi que tous les autres canaux provenant de votre catalogue Commerce. C&#39;est intentionnel : l&#39;objectif est d&#39;améliorer la façon dont votre produit est compris partout, pas seulement par les agents de l&#39;IA et aussi d&#39;éviter les risques d&#39;occultation.

**Que se passe-t-il dans mes autres canaux de vente lorsque j’applique un enrichissement ?**

Comme l’enrichissement est écrit directement dans votre catalogue Adobe Commerce, il se propage automatiquement à tous les canaux qui utilisent votre catalogue de commerce comme source de vérité, y compris plusieurs storefronts, pipelines de publicité et tous flux directs de produits LLM. Cela permet d’assurer la cohérence de la marque et des informations cohérentes sur les produits pour les LLM explorant à Internet pour vos produits.

**Puis-je annuler un enrichissement si le résultat ne me satisfait pas ?**

Oui. Les enrichissements appliqués peuvent être restaurés à tout moment à partir de la vue Suggestions fixes , en restaurant le nom et la description d’origine du produit dans votre catalogue Adobe Commerce.
