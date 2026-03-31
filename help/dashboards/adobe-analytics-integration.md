---
title: Intégration d’Adobe Analytics
description: Découvrez comment connecter Adobe Analytics à LLM Optimizer pour mesurer les résultats commerciaux, l’engagement sur le site et les découvertes pilotées par l’IA dans le tableau de bord du Trafic de recommandation.
feature: Referral Traffic
source-git-commit: e7c9bc1d40267dc92608baa005f85f4be21cfda1
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 4%

---


# Intégration d’Adobe Analytics

L’intégration d’Adobe Analytics connecte LLM Optimizer aux données Adobe Analytics de votre entreprise afin que vous puissiez mesurer la manière dont les découvertes pilotées par l’IA se traduisent par un engagement réel sur le site web et des résultats commerciaux. Une fois le processus d&#39;intégration terminé, les données seront disponibles dans le tableau de bord **Trafic de recommandation** sous l&#39;onglet **Impact commercial**.

En liant les données d’analyse aux informations de visibilité de l’IA, LLM Optimizer vous permet de suivre :

* Interaction client sur les pages consultées par l’IA.
* Signaux de conversion liés aux parcours de découverte de l’IA.
* Impact des optimisations GEO sur les performances.

Cette intégration permet de combler le fossé entre la mesure de visibilité de l’IA et l’analyse des performances commerciales. Les équipes peuvent désormais voir non seulement où la marque apparaît dans les réponses de l’IA, mais aussi ce qui se passe après l’arrivée des utilisateurs.

## Disponibilité {#availability}

>[!IMPORTANT]
>
>L’intégration d’Adobe Analytics est incluse dans l’offre LLM Optimizer payante. Les clients qui utilisent l’évaluation gratuite ne pourront pas connecter Adobe Analytics tant qu’ils n’auront pas effectué la mise à niveau vers une offre payante.

## Connexion d’Adobe Analytics au tableau de bord du Trafic de recommandation {#connect}

Le flux de connexion commence à partir du tableau de bord du Trafic de recommandation [&#128279;](/help/dashboards/referral-traffic.md) comme suit :

1. Ouvrez le tableau de bord du Trafic de recommandation [&#128279;](/help/dashboards/referral-traffic.md). La vue par défaut est **informations sur le trafic**.

   ![Tableau de bord de Trafic de recommandation, onglet Informations de trafic](/help/dashboards/assets/aa-integration-01-referral-traffic-traffic-insights.png)

1. Sélectionnez l’onglet **Impact commercial**. Si aucun fournisseur Analytics n’est connecté, une bannière s’affiche : **Se connecter pour voir l’impact commercial**, avec **Se connecter à Analytics**.

   ![Onglet Impact commercial avec Se connecter à Analytics](/help/dashboards/assets/aa-integration-02-business-impact-connect.png)

1. Sélectionnez **Connexion à Analytics**. Le tableau de bord [Configuration du client](/help/dashboards/customer-configuration.md) s’ouvre alors dans l’onglet **Analytics**.

   ![Configuration du client, onglet Analytics](/help/dashboards/assets/aa-integration-03-analytics-tab.png)

1. Sous **Informations d’identification**, saisissez l’**ID client** et le **Secret client**, puis sélectionnez **Vérifier et continuer**. Veuillez noter les points suivants :

   * L’option **Vérifier et continuer** n’est disponible que lorsque les deux champs sont remplis.
   * Après une vérification réussie, les suites de rapports sont chargées.
   * Utilisez l’**ID client** et le **Secret client** d’un [compte technique](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/) qui a accès à la suite de rapports dont vous avez besoin.

   ![Informations d’identification Analytics et Vérifier et continuer](/help/dashboards/assets/aa-integration-04-credentials.png)

1. Sous **Configuration**, choisissez une **Suite de rapports**.

   Lorsqu’une suite de rapports est sélectionnée, LLM Optimizer charge les options **Dimension d’URL de page** disponibles pour cette suite.

   ![Suite de rapports sélectionnée et chargement des dimensions](/help/dashboards/assets/aa-integration-05-report-suite.png)

1. Choisissez un Dimension d’URL de page **(liste de dimensions spécifique à la suite), puis sélectionnez** Enregistrer et activer **.**

   * Le Dimension d’URL de page **reste désactivé jusqu’à ce qu’une suite de rapports soit sélectionnée et que les dimensions soient chargées.**
   * L’option **Enregistrer et activer** n’est disponible qu’après avoir sélectionné une dimension d’URL de page.

   ![Dimension URL de la page et Enregistrer et activer](/help/dashboards/assets/aa-integration-06-page-url-dimension.png)

1. Après l’enregistrement, la configuration doit afficher le statut **Connecté**. Vous pouvez revenir au tableau de bord du Trafic de recommandation avec **Accéder au tableau de bord du Trafic de recommandation**. Dans **Trafic de recommandation** dans l’onglet **Impact commercial**, le statut doit apparaître comme **Connecté à Adobe Analytics**.

   ![Connecté à Adobe Analytics en configuration et impact commercial](/help/dashboards/assets/aa-integration-07-connected.png)

### Après la connexion {#after-connect}

* LLM Optimizer renvoie les **quatre dernières semaines calendaires complètes** et la **semaine calendaire en cours à ce jour**.
* Après le renvoi, les données sont actualisées **quotidiennement** avec une extraction de la **journée complète précédente**.

>[!NOTE]
>
>Le renvoi peut prendre quelques heures.

## Fonctionnement {#how-it-works}

### Configuration

Lors de la configuration, vous définissez la suite de rapports et la dimension de page que LLM Optimizer utilise pour l’ingestion Adobe Analytics. La dimension de page peut être le mappage de `variables/page` standard ou un `eVar` personnalisé, selon votre suite de rapports.

### Comment le trafic LLM est identifié

Le trafic provenant de LLM est identifié à l’aide d’Adobe Analytics [Type de référent : outils d’IA dédiée à la conversation](https://experienceleague.adobe.com/en/docs/analytics/components/dimensions/referrer-type#conversational-ai-tools).

### Données ingérées {#data-ingested}

Les données suivantes sont ingérées par LLM Optimizer :

**Dimensions**

* Domaine du parrain
* Type de référent
* Pays
* Type d’appareil
* Dimension de page sélectionnée

**Mesures**

* Pages vues
* Visites
* Visiteurs et visiteuses
* Entrées
* Sorties
* Rebonds
* Visites sur une seule page
* Temps passé
* Paniers
* Ajouts au panier
* Retraits du panier
* Consultations du panier
* Passages en caisse
* Commandes
* Revenu
* Unités

### Utilisation de ces données par LLM Optimizer

Ce jeu de données alimente les informations LLM Optimizer pour :

* Performances du trafic LLM au niveau de la page.
* Performances des référents entre les sources LLM.
* Tendances régionales et au niveau des appareils.
* Résultats commerciaux en aval.

## Questions fréquentes {#faq}

Q : L’intégration d’Adobe Analytics est-elle disponible pendant la période d’évaluation ?

Non. L’intégration est disponible uniquement pour les clients LLM Optimizer payants.

Q : Quelles données sont collectées ou stockées ?

Consultez le chapitre [Données ingérées](#data-ingested) ci-dessus. LLM Optimizer fonctionne avec des mesures agrégées issues des API Adobe Analytics autorisées par votre organisation, et non avec les données brutes au niveau de l’accès.

Q : Comment les données sont-elles ingérées ?

Votre entreprise autorise LLM Optimizer à interroger les API Adobe Analytics. Le trafic de recommandation aligné sur les sources LLM est consommé via ces API.

Q : À quelle fréquence les données sont-elles actualisées ?

Les données sont actualisées **tous les jours** (le jour précédent complet une fois le renvoi terminé).

Q : Les données brutes au niveau de l’accès sont-elles stockées dans LLM Optimizer ?

Non. Seules les mesures **agrégées** sont utilisées pour comprendre les modèles et les tendances de trafic.

Q : Les URL complètes, les chaînes de requête ou le contenu des pages sont-ils stockés ?

Les URL complètes utilisées pour la dimension de page sélectionnée peuvent être ingérées ; les chaînes de requête et le contenu de page ne sont pas ingérés pour cette intégration.

Q : Les identifiants d’utilisateur (ECID, adresse IP, ID de cookie) sont-ils stockés ?

Non.

Q : Combien de temps les données sont-elles conservées ?

Gardez à l’esprit que les politiques de conservation peuvent évoluer. Actuellement, les données sont stockées indéfiniment.

Q : Les données sont-elles chiffrées en transit et au repos ?

Actuellement, les données sont chiffrées en transit et non au repos. Cela peut changer dans les futures mises à jour.

Q : Les données historiques sont-elles renvoyées ?

Oui. Après une configuration réussie, les quatre dernières semaines calendaires complètes et la semaine calendaire en cours sont renvoyées. Voir aussi [Après la connexion](#after-connect).
