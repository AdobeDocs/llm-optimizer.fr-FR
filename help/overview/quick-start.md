---
title: Démarrage rapide
description: Prise en main de Adobe LLM Optimizer - Intégrez votre marque, déverrouillez les informations de visibilité de l’IA et explorez les tableaux de bord pour améliorer les performances des recherches.
feature: Quickstart, Onboarding
source-git-commit: 24183fbe2577bb9402f8b6aaaf1e46c75403383d
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 0%

---


# Démarrage rapide

Pour commencer à utiliser l’optimiseur LLM, vous devez terminer le processus d’intégration comme décrit dans les étapes présentées ci-dessous. Une fois le processus terminé[&#x200B; vous disposerez d’un accès complet aux tableaux de bord de LLM Optimizer &#x200B;](/help/dashboards/dashboards-overview.md)et à d’autres fonctionnalités.

## Présentation de l’intégration

Le processus d’intégration commence par l’intégration de votre domaine. Le processus est différent selon que vous êtes un client AEM Cloud ou non. Une fois le processus terminé, vous devrez fournir des informations pour le transfert du journal CDN et enfin personnaliser les catégories, les rubriques et les invites. Chaque partie du processus est détaillée ci-dessous, ainsi que des conseils utiles sur la manière de commencer à utiliser LLM Optimizer dès que possible.

### Autoriser Adobe LLM Optimizer à accéder aux pages publiques

Pour fournir un contenu précis et des recommandations techniques, Adobe LLM Optimizer doit pouvoir accéder à vos pages destinées au public. Pour ce faire, vous devez utiliser un robot d’exploration interne sécurisé (agent utilisateur Spacecat/1.0).

Configuration requise :

* Ajoutez l’agent utilisateur Spacecat/1.0 à la Liste autorisée dans le fichier robots.txt de votre site ou dans les règles de gestion du trafic de robots
* Assurez-vous que les pages ne sont pas bloquées au niveau du domaine ou du réseau CDN. Les pages bloquées ne peuvent pas être indexées, ce qui signifie que les tâches d’optimisation et les informations ne peuvent pas être générées pour elles.

Si la visibilité du contenu apparaît faible dans le tableau de bord, vérifiez que le robot d’exploration a accès à vos domaines. L’accès restreint est une cause courante d’indexation incomplète.

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

Un petit ensemble de catégories, de rubriques et d’invites sera généré pendant la phase d’intégration. L’analyse de la présence de la marque sur ces invites sera disponible peu de temps après l’intégration de votre site.

<!--![Brand Presence Analysis](/help/overview/assets/bp-analysis.png)-->

En outre, vous devez également configurer le [transfert de journal CDN](#step-4) pour l’analyse du trafic. LLM Optimizer a besoin des données sur la présence de la marque et des informations provenant du trafic des agences et des recommandations pour identifier les opportunités et fournir des recommandations prescriptives afin d’accroître la visibilité de l’IA.

### Clients cloud non AEM

Une fois l’accord commercial finalisé, vous serez intégré au domaine que vous souhaitez intégrer à LLM Optimizer. Une fois cette intégration terminée, vous pourrez vous connecter à LLM Optimizer via [https://llmo.now](https://llmo.now).

### Étape 2 : personnalisation des catégories, des rubriques et des invites

Une fois votre site intégré, vous pouvez afficher l’analyse de la présence de la marque en fonction du petit ensemble d’invites qui ont été générées automatiquement pendant la phase d’intégration. À l’avenir, vous pourrez personnaliser les catégories, les rubriques et les invites de votre marque. Cette configuration est créée dans le [tableau de bord de configuration du client](/help/dashboards/customer-configuration.md).

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

### Étape 3 : Informations sur la présence de la marque

Une fois votre domaine intégré, des informations initiales s’affichent dans la vue de présence de la marque en fonction des invites qui ont été générées automatiquement lors de l’intégration. Une fois que vous avez personnalisé vos propres catégories, rubriques et invites, LLM Optimizer déclenche automatiquement l&#39;analyse de la présence de la marque sur les invites que vous avez fournies et les résultats seront disponibles dans 24 heures.

### Étape 4 : fournir des informations pour le transfert du journal CDN {#step-4}

Pour déverrouiller les informations sur le trafic d’agence et le trafic de référence, vous devez fournir des informations pour le transfert des journaux CDN. Elle peut être ajoutée à partir du [tableau de bord de configuration du client](/help/dashboards/customer-configuration.md#cdn-configuration) en accédant à l’onglet **Configuration du réseau CDN** et en cliquant sur **Intégrer le réseau CDN**.

![Réseau CDN de configuration du client](/help/overview/assets/cc-cdn.png)

Si aucun fournisseur de réseau CDN n’a été ajouté au préalable (comme décrit ci-dessus), vous serez invité à ajouter le transfert de journal CDN lors de l’accès initial aux tableaux de bord du trafic d’agence et de référence. Pour plus d’informations, consultez :

* [Trafic d’agent](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Trafic de référence](/help/dashboards/referral-traffic.md#setup#setup)

### Étape 5 : Explorer les tableaux de bord et prendre des mesures

Après avoir fourni des informations pour le transfert du journal CDN, vous pouvez :

* Affichez le tableau de bord [Présence de la marque](/help/dashboards/brand-presence.md) et visualisez votre score de visibilité et suivez vos performances par rapport aux autres marques.
* Explorez les tableaux de bord [Agentic](/help/dashboards/agentic-traffic.md) et [Referral Traffic](/help/dashboards/referral-traffic.md), si le transfert du journal CDN a été configuré.
* Utilisez [Opportunités](/help/dashboards/opportunities.md) pour identifier les améliorations de contenu et techniques.
* Exportez des données et collaborez avec votre équipe ou invitez votre collègue à utiliser le produit.

Enfin, pour comprendre pleinement les fonctionnalités de LLM Optimizer, vous devez explorer tous les [tableaux de bord](/help/dashboards/dashboards-overview.md) disponibles.
