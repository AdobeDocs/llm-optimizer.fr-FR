---
title: Contrôle d’accès
description: Découvrez les différences entre les utilisateurs et utilisatrices affectés au produit et les utilisateurs et utilisatrices de l’organisation dans Adobe LLM Optimizer, ce que les utilisateurs en lecture seule peuvent voir dans l’interface d’utilisation et comment les équipes d’administration attribuent les accès dans Adobe Admin Console.
feature: Customer Configuration
autotag-review: '2026-07-15T16:44:26.227Z'
TQID: 'https://experienceleague.adobe.com/km1BB-gqTl1U92LhHxbXtoH4MTA2tLXS3mPx5u9rEoQ'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d622681e-b12a-44e4-b49f-91c12f18b52b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e1e0219c-f879-479f-8427-888ed2a6e9c2
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 618
ht-degree: 100%

---


# Contrôle d’accès

Adobe LLM Optimizer prend en charge le contrôle d’accès de base, basé sur les rôles des utilisateurs et utilisatrices. Cette fonctionnalité est disponible uniquement pour la **version payante** et est activée sur demande. Elle n’est pas disponible pour les clientes et clients qui utilisent la version d’évaluation.

>[!IMPORTANT]
>
>Pour solliciter l’accès à cette fonctionnalité, les clients et clientes de la version payante doivent contacter leur gestionnaire de compte Adobe.

## Utilisateurs et utilisatrices affectés au produit {#product-assigned-users}

Si vous êtes affecté au produit, vous disposez des mêmes fonctionnalités qu’un utilisateur standard de l’organisation, ainsi que des autorisations suivantes :

* Accéder en écriture à la [configuration du client](/help/dashboards/customer-configuration.md) pour les invites, les catégories, les sujets et les paramètres associés
* Déployer des optimisations [Optimize at Edge](/help/dashboards/optimize-at-edge/overview.md) et gérer les suggestions.
* Gérer les configurations de Google Search Console.
* Gérer les configurations Optimize at Edge et CDN.
* Intégrer un nouveau site.

## Utilisateurs et utilisatrices de l’organisation {#organizational-users}

Les utilisateurs et utilisatrices de l’organisation sont des utilisateurs et utilisatrices standard qui ne sont **pas** affectés au produit. Les utilisateurs et utilisatrices de l’organisation disposent d’un accès en **lecture seule** aux [tableaux de bord LLM Optimizer](/help/dashboards/dashboards-overview.md) et aux vues associées. Les restrictions suivantes s’appliquent.

### Configuration cliente {#customer-configuration-restrictions}

* Le **chargement d’invites** est désactivé.
* La gestion et la modification des invites, des catégories, des sujets et des régions sont désactivées.

  ![Restrictions de configuration du client ou de la cliente pour les utilisateurs et utilisatrices en lecture seule](/help/dashboards/assets/access-control-customer-configuration.png)

### Configuration du CDN (configuration du client ou de la cliente) {#cdn-configuration-restrictions}

* L’**intégration de réseau CDN** est désactivée (les utilisateurs et utilisatrices en lecture seule ne peuvent pas ajouter de fournisseur de réseau CDN).
* La **suppression de réseau CDN** est désactivée (les utilisateurs et utilisatrices en lecture seule ne peuvent pas supprimer les configurations de réseau CDN existantes).
* Le bouton **Envoyer** de la boîte de dialogue Intégration CDN est désactivé (les utilisateurs et utilisatrices en lecture seule ne peuvent pas valider la configuration du réseau CDN).

  ![Restrictions de configuration du réseau CDN pour les utilisateurs et utilisatrices en lecture seule](/help/dashboards/assets/access-control-cdn-configuration.png)

### Présence de la marque — Analyses de données {#brand-presence-restrictions}

* Les boutons **Supprimer** à côté des sujets sont masqués (les utilisateurs et utilisatrices en lecture seule ne peuvent pas supprimer les sujets du suivi).
* Les boutons **Supprimer** à côté des invites sont masqués (les utilisateurs et utilisatrices en lecture seule ne peuvent pas supprimer les invites du suivi).

  ![Actions de Présence de la marque masquées pour les utilisateurs et utilisatrices en lecture seule](/help/dashboards/assets/access-control-brand-presence.png)

### Opportunités de trafic généré par l’IA agentique (opportunités de page d’erreur) {#agentic-opportunities}

Pour les opportunités telles que les pages d’erreur 404, 403 et 503 :

* L’option **Optimisation du déploiement** est masquée.
* Une alerte informative explique que l’accès au déploiement est requis.

  ![L’option Optimisation du déploiement est masquée dans les opportunités de trafic généré par l’IA agentique](/help/dashboards/assets/access-control-agentic-deploy.png)

### Autres pages d’opportunité {#other-opportunities}

Le comportement en lecture seule s’applique également aux types d’opportunité suivants :

* Table des matières
* Synthèse
* Lisibilité
* Effectuer le pré-rendu
* Titres
* Questions fréquentes
* Données structurées manquantes
* Opportunité de correctif générique

Pour les pages suivantes :

* L’option **Optimisation du déploiement** est masquée lorsque l’utilisateur ou l’utilisatrice ne dispose pas d’un accès au déploiement.
* Une alerte intégrée explique que l’accès au déploiement est requis. Le message ressemble à ce qui suit : *Accès au déploiement requis — Vous n’avez pas l’autorisation de déployer des optimisations ni de gérer les suggestions. Contactez l’administrateur ou l’administratrice pour demander l’accès.*
* La barre inférieure persistante avec les actions de déploiement est masquée.

  ![Alerte intégrée lorsque l’accès au déploiement est requis](/help/dashboards/assets/access-control-deploy-alert.png)

  ![Actions de déploiement Optimize at Edge masquées pour les utilisateurs et utilisatrices en lecture seule](/help/dashboards/assets/access-control-optimize-at-edge.png)

### Configuration des invites Google Search Console {#gsc-restrictions}

* Les actions Gérer et Connecter sont désactivées ou masquées.
* La colonne d’actions utilisée pour ajouter des invites est masquée.

  ![Restrictions de configuration de Google Search Console](/help/dashboards/assets/access-control-gsc.png)

### Intégrer un nouveau site {#onboarding-restrictions}

* L’intégration d’un nouveau site est désactivée pour les utilisateurs et utilisatrices sans contrôle d’accès.

  ![Intégration d’un nouveau site désactivée](/help/dashboards/assets/access-control-onboarding.png)

## Affecter le produit à un utilisateur ou une utilisatrice, ou à un groupe {#assign-product}

L’**administrateur ou administratrice système** de votre organisation peut utiliser [Adobe Admin Console](https://adminconsole.adobe.com/) pour affecter Adobe LLM Optimizer à un utilisateur ou une utilisatrice, ou à un groupe.

1. Connectez-vous à [Adobe Admin Console](https://adminconsole.adobe.com/) avec un compte disposant de droits d’administration pour votre organisation.
1. Attribuez le profil de produit Adobe LLM Optimizer (ou l’équivalent dans votre organisation) à l’utilisateur ou l’utilisatrice ou au groupe qui doit bénéficier des autorisations correspondantes.

Pour obtenir des instructions détaillées, voir [Gestion des produits dans Admin Console](https://helpx.adobe.com/fr/enterprise/using/manage-products.html) et [Gestion des groupes d’utilisateurs](https://helpx.adobe.com/fr/enterprise/using/user-groups.html).

>[!NOTE]
>
>Les enchaînements d’écrans dans Adobe Admin Console peuvent changer d’une version à l’autre. Si les options ci-dessus ne correspondent pas à votre console, utilisez les liens d’aide intégrés au produit dans Adobe Admin Console ou contactez l’équipe Adobe en charge des comptes.
