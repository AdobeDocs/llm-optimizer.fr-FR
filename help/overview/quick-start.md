---
title: Démarrage rapide
description: Voici l’article de démarrage rapide.
source-git-commit: 5dbf794b87df92583daec83ab02063821ee7a412
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 0%

---


# Démarrage rapide

Pour commencer à utiliser l’optimiseur LLM, vous devez passer par le processus d’intégration. Ensuite, vous disposerez d’un accès complet aux tableaux de bord de LLM Optimizer et de fonctionnalités complètes.

## Présentation de l’intégration

Le processus d’intégration commence par l’intégration de votre domaine. Le processus est différent selon que vous êtes un client AEM Cloud ou non. Une fois le processus terminé, vous devrez fournir des informations pour le transfert du journal CDN et enfin personnaliser les catégories, les rubriques et les invites.

### Étape 1 : intégration de votre domaine

### Clients AEM Cloud

Les clients AEM Cloud (Cloud Service/Managed Services/Service Edge Delivery) verront l’option permettant d’essayer LLM Optimizer via la carte d’annonce de produit dans [Experience Hub](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/experience-hub/experience-hub).

>[!NOTE]
>Les invites nouvellement ajoutées n&#39;apparaîtront pas dans Brand Presence tant que le traitement ne sera pas terminé. Les clients AEM Cloud (Cloud Service, Managed Services/Service Edge Delivery) peuvent utiliser la version d’évaluation gratuite de LLM Optimizer. L’utilisation de plus de 200 invites nécessite un contrat de licence séparé. L’accès est fourni « en l’état » et « selon disponibilité », et peut être modifié, limité ou supprimé par Adobe à tout moment. Veuillez contacter votre [représentant de compte] pour plus d’informations.

![Version d&#39;évaluation de LLM Optimizer](/help/overview/assets/llm-trial.png)

Une fois que vous avez cliqué sur le bouton **Essayer LLM Optimizer**, vous êtes redirigé vers [https://llmo.now](https://llmo.now) . Vous devrez alors vous connecter via IMS. Une fois connecté, vous démarrez le processus d’intégration en fournissant un domaine et le nom de la marque.

![domaine LLM Optimizer](/help/overview/assets/domain.png)

>[!NOTE]
>Le domaine que vous avez fourni sera utilisé par tous les membres de votre organisation et ne peut pas être modifié.

Pour déclencher l’analyse de la présence de la marque, vous devez fournir les catégories, les rubriques et les invites.

![Analyse de la présence des marques](/help/overview/assets/bp-analysis.png)

En outre, vous devez également configurer le transfert des journaux du réseau CDN pour l’analyse du trafic. LLM Optimizer a besoin des données sur la présence de la marque et des informations provenant du trafic des agences et des recommandations pour identifier les opportunités et fournir des recommandations prescriptives afin d’aider les clients à accroître leur visibilité sur l’IA.

### Clients cloud non AEM

Après avoir signé le contrat, vous serez intégré via la commande slackbot avec le domaine que vous souhaitez intégrer à LLM Optimizer. Une fois cette intégration terminée, vous pourrez vous connecter à LLM Optimizer via [https://llmo.now](https://llmo.now) .

### Étape 2 : préremplissage automatique des informations

Une fois votre domaine intégré, LLM Optimizer remplit automatiquement les champs suivants :

* **Catégories** - Vastes zones de contenu pertinentes pour votre domaine.
* **Rubriques** - Thèmes spécifiques liés à des mots-clés sans marque à volume élevé associés à votre domaine.
* **Invites** - Requêtes (avec ou sans marque) pour fournir une visibilité de base.

Cela permet de s’assurer que même avant d’ajouter vos configurations et entrées personnalisées, vous obtiendrez des informations initiales sur la visibilité de votre marque.

### Étape 3 : personnalisation des catégories, des rubriques et des invites

Cliquez sur le [tableau de bord de configuration du client](/help/dashboards/customer-configuration.md) pour commencer à personnaliser vos catégories, rubriques et invites.

![Tableau de bord de configuration du client](/help/dashboards/assets/customer-config.png)

À partir de ce tableau de bord, vous pouvez :

* Ajoutez de nouvelles catégories qui correspondent aux priorités de votre entreprise.
* Saisissez les rubriques ou sous-rubriques personnalisées qui doivent faire l&#39;objet d&#39;un suivi.
* Créez vos invites pour surveiller la visibilité dans des requêtes spécifiques.
* Définissez les alias de mention afin que toutes les mentions soient capturées.
* Définissez des alias de concurrents pour suivre précisément les concurrents.

### Étape 4 : fournir des informations pour le transfert du journal CDN

Pour déverrouiller les informations sur le trafic d’agence et le trafic de référence, vous devez fournir des informations pour le transfert des journaux CDN. Voir chaque page spécifique pour plus d’informations sur la configuration du transfert de journal :

* [Trafic d’agent](/help/dashboards/agentic-traffic.md)
* [Trafic de référence](/help/dashboards/referral-traffic.md#setup#cdn-setup)

### Étape 5 : Explorer les tableaux de bord et prendre des mesures

Après avoir fourni des informations pour le transfert du journal CDN, vous pouvez :

* Affichez le tableau de bord [Brand Presence](/help/dashboards/brand-presence.md), visualisez votre score de visibilité et suivez vos performances par rapport à vos concurrents.
* Explorez les tableaux de bord [Agentic](/help/dashboards/agentic-traffic.md) et [Referral Traffic](/help/dashboards/referral-traffic.md).
* Utilisez [Opportunités](/help/dashboards/opportunities.md) pour identifier les améliorations de contenu et techniques.
* Exportez des données et collaborez avec votre équipe ou invitez votre collègue à utiliser le produit.

Pour comprendre pleinement les fonctionnalités de l’optimiseur LLM, explorez tous les [tableaux de bord](/help/dashboards/dashboards-overview.md) disponibles.
