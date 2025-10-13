---
title: Démarrage rapide
description: Prise en main de Adobe LLM Optimizer - Intégrez votre marque, déverrouillez les informations de visibilité de l’IA et explorez les tableaux de bord pour améliorer les performances des recherches.
source-git-commit: 5e8efde82c10c9afa09d51ec9ef20fc006363210
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---


# Démarrage rapide

Pour commencer à utiliser l’optimiseur LLM, vous devez terminer le processus d’intégration comme décrit dans les étapes présentées ci-dessous. Une fois le processus terminé[&#x200B; vous disposerez d’un accès complet aux tableaux de bord de LLM Optimizer &#x200B;](/help/dashboards/dashboards-overview.md)et à d’autres fonctionnalités.

## Présentation de l’intégration

Le processus d’intégration commence par l’intégration de votre domaine. Le processus est différent selon que vous êtes un client AEM Cloud ou non. Une fois le processus terminé, vous devrez fournir des informations pour le transfert du journal CDN et enfin personnaliser les catégories, les rubriques et les invites. Chaque partie du processus est détaillée ci-dessous, ainsi que des conseils utiles sur la manière de commencer à utiliser LLM Optimizer dès que possible.

## Étape 1 : intégration de votre domaine

### Essayer Avant d&#39;acheter

Les clients AEM Cloud (Cloud Service, Managed Services, Edge Delivery Service) ont la possibilité d’utiliser l’offre **Essayer avant d’acheter**. Il s’agit d’une version d’évaluation gratuite de LLM Optimizer avec jusqu’à 200 invites gratuites. L’utilisation de plus de 200 invites nécessite un contrat de licence séparé. L’accès est fourni « en l’état » et « selon disponibilité », et peut être modifié, limité ou supprimé par Adobe à tout moment.

Certaines fonctionnalités du produit ne sont pas disponibles dans la version gratuite :

* La version d’essai est limitée à un domaine. Une fois la configuration terminée, vous ne pourrez plus modifier le domaine que vous avez fourni.
* La prise en charge du déploiement des optimisations ne sera pas disponible.

Consultez la section ci-dessous pour plus d’informations sur l’activation de la version d’évaluation gratuite et l’intégration à votre domaine.

### Clients AEM Cloud

Si vous êtes un client AEM Cloud, vous avez la possibilité d’essayer LLM Optimizer à l’aide de la carte Annonce de produit dans [Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/experience-hub/experience-hub).

>[!NOTE]
>Les invites nouvellement ajoutées n&#39;apparaîtront pas dans le [tableau de bord de présence de la marque](/help/dashboards/brand-presence.md) tant que le traitement n&#39;est pas terminé. Les clients AEM Cloud peuvent utiliser la version d’évaluation gratuite de LLM Optimizer. L’utilisation de plus de 200 invites nécessite un contrat de licence séparé. L’accès est fourni « en l’état » et « selon disponibilité », et peut être modifié, limité ou supprimé par Adobe à tout moment. Veuillez contacter votre représentant de compte pour plus d’informations.

![Version d&#39;évaluation de LLM Optimizer](/help/overview/assets/llm-trial.png)

Une fois que vous avez cliqué sur le bouton **Essayer LLM Optimizer**, vous êtes redirigé vers [https://llmo.now](https://llmo.now). Vous devrez alors vous connecter via IMS. Une fois connecté, vous démarrez le processus d’intégration en fournissant un domaine et le nom de la marque.

![domaine LLM Optimizer](/help/overview/assets/domain.png)

>[!NOTE]
>Le domaine que vous avez fourni sera utilisé par tous les membres de votre organisation et ne peut pas être modifié.

Pour déclencher l’analyse de la présence de la marque, vous devez fournir les catégories, les rubriques et les invites.

![Analyse de la présence des marques](/help/overview/assets/bp-analysis.png)

En outre, vous devez également configurer le [transfert de journal CDN](#step-4) pour l’analyse du trafic. LLM Optimizer a besoin des données sur la présence de la marque et des informations provenant du trafic des agences et des recommandations pour identifier les opportunités et fournir des recommandations prescriptives afin d’accroître la visibilité de l’IA.

### Clients cloud non AEM

Une fois l’accord commercial finalisé, vous serez intégré via la commande slackbot avec le domaine que vous souhaitez intégrer sur LLM Optimizer. Une fois cette intégration terminée, vous pourrez vous connecter à LLM Optimizer via [https://llmo.now](https://llmo.now).

### Étape 2 : personnalisation des catégories, des rubriques et des invites

Pour déclencher l’analyse de la présence de la marque et renseigner le tableau de bord avec des informations sur la visibilité de votre marque, vous devez personnaliser les catégories, les rubriques et les invites. Cette configuration est créée dans le [tableau de bord de configuration du client](/help/dashboards/customer-configuration.md).

![Tableau de bord de configuration du client](/help/overview/assets/prompt-creation.png)

À partir de ce tableau de bord, vous pouvez :

* Ajoutez **nouvelles catégories** qui correspondent aux priorités de votre entreprise. Les catégories peuvent être de larges zones de contenu pertinentes pour votre domaine.
* Saisissez **rubriques personnalisées** ou sous-rubriques dont vous souhaitez effectuer le suivi. Les rubriques peuvent être des thèmes spécifiques liés à un volume élevé de mots-clés sans marque associés à votre domaine.
* Créez **vos invites** pour surveiller la visibilité dans des requêtes spécifiques. Les invites sont des requêtes (avec et sans marque) qui fournissent une visibilité de base. Seul un nombre limité d’invites sera généré automatiquement en fonction des catégories et des rubriques que vous avez fournies.
* Définissez la mention **alias** pour vous assurer que toutes les mentions d’une marque sont capturées et prises en compte.
* Définissez **autres alias** pour suivre précisément d’autres marques.

>[!NOTE]
>Les invites exactes que vous demandez aux LLM ne sont pas disponibles publiquement car elles ne sont pas divulguées par les LLM.

>[!NOTE]
>
> Pour plus d’informations sur la configuration des catégories, rubriques et invites, reportez-vous à la page [Bonnes pratiques pour la configuration des catégories, rubriques, invites](/help/overview/best-practices-topics-prompts.md).

### Étape 3 : préremplissage automatique des informations

Une fois votre domaine intégré et que vous avez fourni les catégories et les rubriques, LLM Optimizer déclenche automatiquement l’analyse de présence de la marque.

### Étape 4 : fournir des informations pour le transfert du journal CDN {#step-4}

Pour déverrouiller les informations sur le trafic d’agence et le trafic de référence, vous devez fournir des informations pour le transfert des journaux CDN. Elle peut être ajoutée à partir du [tableau de bord de configuration du client](/help/dashboards/customer-configuration.md) en accédant à l’onglet **Configuration du réseau CDN** et en cliquant sur **Intégrer le réseau CDN**.

![Réseau CDN de configuration du client](/help/overview/assets/cc-cdn.png)

Si aucun fournisseur de réseau CDN n’a été ajouté au préalable comme dans l’exemple ci-dessus, vous serez invité à ajouter le transfert de journal CDN lors de l’accès initial aux tableaux de bord du trafic d’agence et de référence. Pour plus d’informations, consultez :

* [Trafic d’agent](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Trafic de référence](/help/dashboards/referral-traffic.md#setup#setup)

### Étape 5 : Explorer les tableaux de bord et prendre des mesures

Après avoir fourni des informations pour le transfert du journal CDN, vous pouvez :

* Affichez le tableau de bord [Présence de la marque](/help/dashboards/brand-presence.md) et visualisez votre score de visibilité et suivez vos performances par rapport aux autres marques.
* Explorez les tableaux de bord [Agentic](/help/dashboards/agentic-traffic.md) et [Referral Traffic](/help/dashboards/referral-traffic.md), si le transfert du journal CDN a été configuré.
* Utilisez [Opportunités](/help/dashboards/opportunities.md) pour identifier les améliorations de contenu et techniques.
* Exportez des données et collaborez avec votre équipe ou invitez votre collègue à utiliser le produit.

Enfin, pour comprendre pleinement les fonctionnalités de LLM Optimizer, vous devez explorer tous les [tableaux de bord](/help/dashboards/dashboards-overview.md) disponibles.
