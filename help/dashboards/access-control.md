---
title: Contrôle d’accès
description: Découvrez les différences entre les utilisateurs affectés au produit et les utilisateurs de l’organisation dans Adobe LLM Optimizer, ce que les utilisateurs en lecture seule voient dans l’interface utilisateur et comment les administrateurs attribuent l’accès dans Adobe Admin Console.
feature: Customer Configuration
autotag-review: '2026-05-15T17:26:43.837Z'
TQID: 'https://experienceleague.adobe.com/hJpQQpuHBRMdKT5oKA9z0Y8H3d3p6To-n2hWKrXgZsQ'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: b704f6a0-b2fb-4df0-9177-9753751004f5
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 7a92587197cf6a9eec6b01bd4eaeeaf1194d3088
workflow-type: tm+mt
source-wordcount: 618
ht-degree: 4%

---


# Contrôle d’accès

Adobe LLM Optimizer prend en charge le contrôle d’accès de base, basé sur les rôles des utilisateurs. Cette fonctionnalité est disponible uniquement pour les **clients payants** et est activée sur demande. Il n’est pas disponible pour les clients en version d’évaluation.

>[!IMPORTANT]
>
>Pour demander l’accès à cette fonctionnalité, les clients payants doivent contacter leur gestionnaire de compte Adobe.

## Utilisateurs affectés au produit {#product-assigned-users}

Si vous êtes affecté au produit, vous disposez des mêmes fonctionnalités qu’un utilisateur organisationnel standard, en plus des autorisations suivantes :

* Accédez en écriture à [Configuration du client](/help/dashboards/customer-configuration.md) pour les invites, les catégories, les rubriques et les paramètres associés.
* Déployez des optimisations [Optimisez sur Edge](/help/dashboards/optimize-at-edge/overview.md) et gérez les suggestions.
* Gérez les configurations de la console de recherche de Google.
* Gérez l’optimisation au niveau des configurations Edge et CDN.
* Intégrez un nouveau site.

## Utilisateurs de l’organisation {#organizational-users}

Les utilisateurs organisationnels sont des utilisateurs standard qui ne sont **pas** affectés au produit. Si vous êtes un utilisateur de l’entreprise, vous disposez d’un accès **lecture seule** aux tableaux de bord [LLM Optimizer](/help/dashboards/dashboards-overview.md) et aux vues associées. Les restrictions suivantes s’appliquent.

### Configuration cliente {#customer-configuration-restrictions}

* Le **invite de chargement** est désactivé.
* La gestion et la modification des invites, des catégories, des rubriques et des zones géographiques sont désactivées.

  ![Restrictions de configuration du client pour les utilisateurs en lecture seule](/help/dashboards/assets/access-control-customer-configuration.png)

### Configuration du réseau CDN (configuration du client) {#cdn-configuration-restrictions}

* Le **réseau CDN intégré** est désactivé (les utilisateurs en lecture seule ne peuvent pas ajouter de fournisseur de réseau CDN).
* La fonction **Supprimer le réseau de diffusion de contenu** est désactivée (les utilisateurs en lecture seule ne peuvent pas supprimer une configuration de réseau de diffusion de contenu existante).
* Le bouton **Envoyer** de la boîte de dialogue intégrée au réseau CDN est désactivé (les utilisateurs en lecture seule ne peuvent pas terminer la configuration du réseau CDN).

  ![Restrictions de configuration du réseau CDN pour les utilisateurs en lecture seule](/help/dashboards/assets/access-control-cdn-configuration.png)

### Présence des marques — informations sur les données {#brand-presence-restrictions}

* Les boutons **Supprimer** en regard des rubriques sont masqués (les utilisateurs en lecture seule ne peuvent pas supprimer de rubriques du suivi).
* Les boutons **Supprimer** en regard des invites sont masqués (les utilisateurs en lecture seule ne peuvent pas supprimer les invites du suivi).

  ![Actions de Présence des marques masquées pour les utilisateurs en lecture seule](/help/dashboards/assets/access-control-brand-presence.png)

### Opportunités de trafic agent (opportunités de page d’erreur) {#agentic-opportunities}

Pour les opportunités telles que les pages d’erreur 404, 403 et 503 :

* **Optimisation du déploiement** est masqué.
* Une alerte informative explique que l’accès au déploiement est requis.

  ![Optimisation du déploiement cachée dans les opportunités de trafic sur les agents](/help/dashboards/assets/access-control-agentic-deploy.png)

### Autres pages d’opportunité {#other-opportunities}

Le comportement en lecture seule s’applique également aux types d’opportunité tels que :

* Table des matières
* Synthèse
* Lisibilité
* Effectuer le pré-rendu
* Titres
* Questions fréquentes
* Données structurées manquantes
* Opportunité de correctif générique

Pour ces pages :

* Le paramètre **Optimisation du déploiement** est masqué lorsque l’utilisateur ne dispose pas d’un accès de déploiement.
* Une alerte intégrée explique que l’accès au déploiement est requis. Le message est similaire au suivant : *Accès au déploiement requis — Vous n’avez pas l’autorisation de déployer des optimisations ou de gérer des suggestions. Contactez votre administrateur pour demander l’accès.*
* La barre inférieure persistante avec les actions de déploiement est masquée.

  ![Alerte intégrée lorsque l’accès au déploiement est requis](/help/dashboards/assets/access-control-deploy-alert.png)

  ![Optimiser pour les actions de déploiement Edge masquées pour les utilisateurs en lecture seule](/help/dashboards/assets/access-control-optimize-at-edge.png)

### Configuration de l’invite de la console de recherche de Google {#gsc-restrictions}

* Les actions Gérer et Connecter sont désactivées ou masquées.
* La colonne d’actions utilisée pour ajouter des invites est masquée.

  ![Restrictions de configuration de Google Search Console](/help/dashboards/assets/access-control-gsc.png)

### Intégration d’un nouveau site {#onboarding-restrictions}

* L’intégration d’un nouveau site est désactivée pour les utilisateurs sans contrôle d’accès.

  ![Site intégré désactivé](/help/dashboards/assets/access-control-onboarding.png)

## Affecter le produit à un utilisateur ou à un groupe {#assign-product}

Un **administrateur système** de votre organisation peut utiliser [Adobe Admin Console](https://adminconsole.adobe.com/) pour affecter Adobe LLM Optimizer à un utilisateur ou à un groupe.

1. Connectez-vous à [&#128279;](https://adminconsole.adobe.com/) avec un compte disposant de droits d’administration pour votre organisation.
1. Attribuez le profil de produit Adobe LLM Optimizer (ou le droit de produit équivalent de votre organisation) à l’utilisateur ou au groupe qui doit recevoir les fonctionnalités attribuées au produit.

Pour obtenir des instructions détaillées, voir [Gestion des produits dans Admin Console](https://helpx.adobe.com/fr/enterprise/using/manage-products.html) et [Gestion des groupes d’utilisateurs](https://helpx.adobe.com/fr/enterprise/using/user-groups.html).

>[!NOTE]
>
>Les flux d’écran dans le Adobe Admin Console peuvent changer d’une version à l’autre. Si les options ci-dessus ne correspondent pas à votre console, utilisez les liens d’aide intégrés au produit dans Adobe Admin Console ou contactez l’équipe de votre compte Adobe.
