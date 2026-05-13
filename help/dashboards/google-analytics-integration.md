---
title: Intégration de Google Analytics
description: Découvrez comment connecter Google Analytics 4 à LLM Optimizer pour mesurer les résultats commerciaux, l’engagement sur le site et les découvertes pilotées par l’IA dans le tableau de bord du Trafic de recommandation.
feature: Referral Traffic
source-git-commit: abf88fc3e141e12d6b5c826e35d4590ae6407c9b
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 1%

---


# Intégration de Google Analytics

L’intégration de Google Analytics 4 (GA4) connecte LLM Optimizer aux données GA4 de votre entreprise afin que vous puissiez mesurer la manière dont la découverte pilotée par l’IA sur des plateformes telles que ChatGPT, Gemini, Copilot, Claude et Perplexity se traduit en engagement réel sur le site web et en résultats commerciaux. Après avoir connecté une propriété GA4, LLM Optimizer extrait les mesures de trafic de recommandation, d’engagement et de conversion que GA4 attribue à ces sources et les fait apparaître dans le tableau de bord **Trafic de recommandation** sous l’onglet **Impact commercial**.

## Disponibilité {#availability}

>[!IMPORTANT]
>
>L’intégration de GA4 est incluse dans l’offre LLM Optimizer payante. Les clients qui utilisent la version d’évaluation gratuite ne pourront pas se connecter à GA4 tant qu’ils n’auront pas effectué la mise à niveau vers une offre payante.

## Avant de commencer {#before-you-begin}

Pour établir la connexion, vous avez besoin des éléments suivants :

* Compte Google disposant d’au moins un accès **Visionneuse** sur la propriété GA4 à laquelle vous souhaitez vous connecter. L’accès au niveau de la propriété est géré dans Google Analytics sous **Admin > Gestion des accès aux propriétés**.
* Autorisation de gérer la configuration dans LLM Optimizer (sinon le bouton Se connecter est visible mais désactivé).
* Un navigateur qui autorise les fenêtres pop-up à partir de l’origine de LLM Optimizer : l’étape de connexion à Google s’ouvre dans un nouvel onglet.

Il n’est **nécessaire** créer un projet Google Cloud, de générer un compte de service, de charger une clé JSON ou de saisir un identifiant de propriété. LLM Optimizer négocie la connexion via l’écran de consentement OAuth standard de Google.

## Connexion de GA4 au tableau de bord du Trafic de recommandation {#connect}

Le flux de connexion commence à partir du tableau de bord du Trafic de recommandation [&#128279;](/help/dashboards/referral-traffic.md) comme suit :

1. Ouvrez le Trafic de recommandation **&#x200B;**&#x200B;dans LLM Optimizer.

1. Ouvrez l’onglet **Impact commercial**.

   Tableau de bord du Trafic de recommandation ![](/help/dashboards/assets/ga4-integration-01-business-impact-tab.png)

1. Sélectionnez **Connexion à Analytics**. LLM Optimizer vous dirige vers **Configuration du client > Analytics**. Dans le sélecteur de fournisseur Analytics, sélectionnez **Google Analytics 4**.

   ![Configuration du client, onglet Analytics avec GA4 sélectionné](/help/dashboards/assets/ga4-integration-02-analytics-ga4-picker.png)

1. Sélectionnez **Connexion**. Un nouvel onglet du navigateur s’ouvre sur l’écran de connexion de Google.

   ![Connexion à Google pour la connexion GA4](/help/dashboards/assets/ga4-integration-03-google-sign-in.png)

1. Connectez-vous avec le compte Google ayant accès à la propriété GA4 à laquelle vous souhaitez vous connecter. Approuvez l’autorisation `See and download your Google Analytics data` (étendue `analytics.readonly`) lorsque Google vous y invite.

1. Google vous renvoie à LLM Optimizer, qui répertorie les propriétés GA4 auxquelles votre compte peut accéder. Sélectionnez la propriété à connecter et à envoyer.

1. Revenez à l’onglet LLM Optimizer . L’onglet Analytics détecte automatiquement la connexion terminée et la carte GA4 affiche un statut **Connecté**.

### Après la connexion {#after-connect}

Une fois GA4 connecté à LLM Optimizer, voici ce qui se passe :

* LLM Optimizer renvoie les **quatre dernières semaines calendaires complètes** et la **semaine calendaire en cours à ce jour**.
* Après le renvoi, les données sont actualisées **quotidiennement** avec une extraction de la **journée complète précédente**.

>[!NOTE]
>
>Le renvoi peut prendre quelques heures. Le tableau de bord de l’impact commercial commence à se remplir progressivement au fur et à mesure que les données arrivent ; aucune action n’est requise de votre part pendant l’exécution du renvoi.

Si vous vous reconnectez (par exemple, pour changer de compte Google ou de propriété GA4), seule la semaine calendaire en cours est renvoyée, les semaines précédentes déjà chargées étant conservées.

## Fonctionnement {#how-it-works}

### Modèle de connexion

L’intégration utilise le flux OAuth 2.0 standard de Google délégué par l’utilisateur. LLM Optimizer stocke un jeton d’actualisation défini sur la propriété GA4 sélectionnée et ce jeton permet à LLM Optimizer d’appeler l’API Data GA4 en votre nom (avec un accès en lecture seule) jusqu’à ce que vous le révoquiez de votre compte Google.

### Comment le trafic LLM est identifié

LLM Optimizer ne demande GA4 que pour les sessions GA4 lui-même attribuées à une plateforme LLM. Aujourd’hui, il s’agit de sessions dont le `sessionSourceMedium` correspond à l’un des formats `chatgpt`, `gemini.google.com`, `copilot.microsoft.com`, `claude` ou `perplexity`. La liste des sources LLM prises en charge est gérée par Adobe et peut s’étendre au fil du temps.

### Données ingérées {#data-ingested}

Chaque extraction quotidienne récupère un rapport agrégé contenant les éléments suivants :

**Dimensions**

| Dimension GA4 | Ce qu’il représente |
| --- | --- |
| `date` | Le jour où la session a eu lieu. |
| `landingPage` | Première page que le visiteur a vue sur votre site. |
| `countryId` | Le pays du visiteur, tel que déterminé par la géolocalisation de l’adresse IP de GA4. |
| `deviceCategory` | Mobile / ordinateur de bureau / tablette. |
| `sessionSourceMedium` | La source/support LLM attribuée par GA4. |

**Mesures**

| Mesure GA4 | Ce qu’il représente |
| --- | --- |
| `sessions` | Nombre de sessions dans l’intervalle. |
| `screenPageViews` | Pages vues dans le compartiment. |
| `bounceRate` | Fraction de sessions ayant rebondi. |
| `totalPurchasers` | Acheteurs distincts (si le commerce électronique est configuré dans GA4). |
| `transactions` | Nombre de transactions (si le commerce électronique est configuré). |
| `purchaseRevenue` | Chiffre d’affaires d’achat (USD). |
| `totalRevenue` | Chiffre d’affaires total (USD). |

### Utilisation de ces données par LLM Optimizer

LLM Optimizer utilise ces données pour renseigner les performances au niveau des pages, les répartitions des sources, les divisions par pays et par appareil et les tendances temporelles du tableau de bord de l’impact sur l’entreprise. Aucune donnée n’est utilisée pour entraîner des modèles ou partagés en dehors de votre client.

### Ce qui n’est pas ingéré

Aucun identifiant d’utilisateur (identifiant client Google, adresse IP, identifiant d’appareil), aucune ligne au niveau de la session, aucune ligne au niveau de l’événement, aucune dimension ou mesure personnalisée au-delà de celles répertoriées ci-dessus et aucune définition d’audience ou de segment GA4.

## Questions fréquentes {#faq}

Q : L’intégration GA4 est-elle disponible pendant l’essai ?

Non. L’intégration est disponible uniquement pour les clients LLM Optimizer payants.

Q : Dois-je créer un projet Google Cloud ou un compte de service ?

Non. La connexion est une connexion Google standard. LLM Optimizer gère le client OAuth Google côté Adobe ; vous n’avez besoin que d’un compte Google avec un accès Observateur sur la propriété GA4.

Q : Quelles données sont collectées ou stockées ?

LLM Optimizer fonctionne avec des mesures agrégées provenant de l’API de données GA4 autorisée par votre organisation, et non avec des données brutes au niveau de l’événement.

Q : Comment les données sont-elles ingérées ?

Votre entreprise autorise LLM Optimizer à interroger l’API Data GA4 pour la propriété sélectionnée. Le trafic de recommandation aligné sur les sources LLM est consommé via cette API.

Q : À quelle fréquence les données sont-elles actualisées ?

Les données sont actualisées **tous les jours** (le jour précédent complet une fois le renvoi terminé).

Q : Les données brutes au niveau de l’événement sont-elles stockées dans LLM Optimizer ?

Non. Seules les mesures **agrégées** sont utilisées pour comprendre les modèles et les tendances de trafic.

Q : Les URL complètes, les chaînes de requête ou le contenu des pages sont-ils stockés ?

Les chemins d’accès aux pages de destination sont ingérés dans le cadre du rapport standard ; les chaînes de requête et le contenu des pages ne sont pas ingérés pour cette intégration.

Q : Les identifiants d’utilisateur (identifiant client Google, adresse IP, identifiant de l’appareil) sont-ils stockés ?

Non.

Q : Combien de temps les données sont-elles conservées ?

Actuellement, les données sont stockées indéfiniment.

Q : Les données sont-elles chiffrées en transit et au repos ?

Actuellement, les données sont chiffrées en transit, et non au repos. Cela peut changer dans les futures mises à jour.

Q : Les données historiques sont-elles renvoyées ?

Oui. Après une configuration réussie, les quatre dernières semaines calendaires complètes et la semaine calendaire en cours sont renvoyées. Voir aussi [Après la connexion](#after-connect).

Q : Puis-je me déconnecter ou révoquer l’accès ?

Oui, à tout moment. Vous pouvez vous reconnecter à un compte ou une propriété différent(e) à partir de la carte GA4 dans LLM Optimizer ou révoquer l’accès au LLM Optimizer entièrement à partir de votre compte Google à l’adresse [https://myaccount.google.com/permissions](https://myaccount.google.com/permissions). La révocation de l’accès arrête les nouvelles extractions de données ; les données agrégées précédemment ingérées restent dans LLM Optimizer.

Q : Ma propriété GA4 est connectée mais l&#39;impact commercial est vide - pourquoi ?

LLM Optimizer extrait uniquement les sessions que GA4 lui-même attribue à une source/un support LLM pris en charge (aujourd’hui : ChatGPT, Gemini, Copilot, Claude, Perplexity). Si votre propriété GA4 n’a pas encore enregistré de sessions de référence provenant de l’une de ces sources dans la fenêtre temporelle affichée, le tableau de bord sera vide même si la connexion est saine.
