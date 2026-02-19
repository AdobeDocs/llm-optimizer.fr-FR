---
title: Démarrage rapide
description: 'Prise en main d’Adobe LLM Optimizer : intégrez votre marque, exploitez les informations de visibilité de l’IA et explorez les tableaux de bord pour améliorer les performances des recherches.'
feature: Quickstart, Onboarding
source-git-commit: 82830e66d43ddd9741617cdf6daab63cd259554b
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 93%

---


# Démarrage rapide

Pour commencer à utiliser LLM Optimizer, vous devez terminer le processus d’intégration comme décrit dans les étapes présentées ci-dessous. Une fois le processus terminé, vous disposerez d’un accès complet aux ](/help/dashboards/dashboards-overview.md)tableaux de bord de LLM Optimizer[ et à d’autres fonctionnalités.

## Vue d’ensemble de l’intégration

Le processus d’intégration commence par votre domaine. Le processus est différent si vous êtes client ou cliente d’AEM Cloud. Une fois le processus terminé, vous devrez fournir des informations pour le transfert du journal CDN et enfin personnaliser les catégories, les rubriques et les prompts. Chaque partie du processus est détaillée ci-dessous, ainsi que des conseils utiles sur la manière de commencer à utiliser LLM Optimizer dès que possible.

### Autoriser Adobe LLM Optimizer à accéder aux pages publiques

Pour fournir un contenu précis et des recommandations techniques, Adobe LLM Optimizer doit pouvoir accéder à vos pages destinées au public. Pour ce faire, un robot d’exploration interne sécurisé (agent utilisateur Spacecat/1.0) est utilisé.

Configuration requise :

* Ajoutez l’agent utilisateur Spacecat/1.0 à la liste autorisée dans le fichier robots.txt de votre site ou dans les règles de gestion du trafic de robots.
* Assurez-vous que les pages ne sont pas bloquées au niveau du domaine ou du réseau CDN. Les pages bloquées ne peuvent pas être indexées, ce qui signifie que les tâches d’optimisation et les informations ne peuvent pas être générées pour elles.

Si la visibilité du contenu semble faible dans le tableau de bord, vérifiez que le robot d’exploration a accès à vos domaines. L’accès restreint est une cause courante d’indexation incomplète.

## Étape 1 : intégration de votre domaine

### Essayer avant d’acheter

Les clients AEM Cloud (Cloud Service, Managed Services, Edge Delivery Service) ont la possibilité d’utiliser l’offre **Essayer avant d’acheter**. Il s’agit d’une version d’évaluation gratuite de LLM Optimizer avec jusqu’à 200 prompts gratuits. L’utilisation de plus de 200 prompts nécessite un contrat de licence séparé. L’accès est fourni en l’état et selon la disponibilité, et peut être modifié, limité ou supprimé par Adobe à tout moment.

Certaines fonctionnalités du produit ne sont pas disponibles dans la version gratuite :

* La version d’essai est limitée à un domaine. Une fois la configuration terminée, vous ne pourrez plus modifier le domaine fourni.
* La possibilité de déployer des optimisations est disponible en accès anticipé. Pour en savoir plus, consultez le [Forum aux questions sur l’optimisation pour Edge](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/resources/optimize-at-edge/overview#frequently-asked-questions).

Consultez la section ci-dessous pour plus d’informations sur l’activation de la version d’évaluation gratuite et l’intégration à votre domaine.

### Clients et clientes AEM Cloud

Si vous êtes client ou cliente d’AEM Cloud, vous avez la possibilité d’essayer LLM Optimizer à l’aide de la carte Annonce de produit dans [Experience Hub](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/experience-hub/experience-hub).

>[!NOTE]
>Les nouveaux prompts n’apparaîtront pas dans le [tableau de bord Présence de la marque](/help/dashboards/brand-presence.md) tant que le traitement ne sera pas terminé. Les clients et les clientes d’AEM Cloud peuvent utiliser la version d’évaluation gratuite de LLM Optimizer. L’utilisation de plus de 200 prompts nécessite un contrat de licence séparé. L’accès est fourni en l’état et selon la disponibilité, et peut être modifié, limité ou supprimé par Adobe à tout moment. Contactez votre gestionnaire de compte pour plus d’informations.

![Version d’évaluation de LLM Optimizer](/help/overview/assets/llm-trial.png)

Cliquer sur le bouton **Essayer LLM Optimizer** vous redirigera vers [https://llmo.now](https://llmo.now). Vous devrez alors vous connecter via IMS. Une fois la connexion établie, vous démarrez le processus d’intégration en fournissant un domaine et le nom de la marque.

![Domaine LLM Optimizer](/help/overview/assets/domain.png)

>[!NOTE]
>Le domaine fourni sera utilisé par toutes les personnes membres de votre organisation et ne peut pas être modifié.

Un petit ensemble de catégories, de rubriques et de prompts sera généré pendant la phase d’intégration. L’analyse de présence de la marque sur ces prompts sera disponible peu de temps après l’intégration de votre site.

<!--![Brand Presence Analysis](/help/overview/assets/bp-analysis.png)-->

De plus, vous devez également configurer le [transfert des journaux CDN](#step-4) pour l’analyse du trafic. LLM Optimizer a besoin des données et des informations de présence de la marque issues du trafic généré par l’IA agentique et du trafic de recommandation pour identifier les opportunités et fournir des conseils afin de renforcer la visibilité de l’IA.

### Personnes non clientes d’AEM Cloud

Une fois l’accord commercial finalisé, vous serez intégré au domaine que vous souhaitez intégrer à LLM Optimizer. Une fois cette intégration terminée, vous pourrez vous connecter à LLM Optimizer via [https://llmo.now](https://llmo.now).

## Étape 2 : personnalisation des catégories, des rubriques et des prompts

Une fois votre site intégré, vous pouvez afficher l’analyse de présence de la marque en fonction du petit ensemble de propts qui ont été générés automatiquement pendant la phase d’intégration. À l’avenir, vous pourrez personnaliser les catégories, les rubriques et les pompts de votre marque. Cette configuration est créée dans le [tableau de bord de configuration cliente](/help/dashboards/customer-configuration.md).

![Tableau de bord de configuration cliente](/help/overview/assets/prompt-creation.png)

À partir de ce tableau de bord, vous pouvez :

* ajouter de **nouvelles catégories** qui correspondent aux priorités de votre entreprise ; Les catégories peuvent être de larges zones de contenu pertinentes pour votre domaine.
* saisir des **rubriques ou sous-rubriques personnalisées** dont vous souhaitez effectuer le suivi ; Les rubriques peuvent être des thèmes spécifiques liés à un volume élevé de mots-clés sans marque associés à votre domaine.
* créer **vos prompts** pour surveiller la visibilité dans des requêtes spécifiques ; Les prompts sont des requêtes (avec et sans marque) qui fournissent une visibilité de base. Seul un nombre limité de prompts sera généré automatiquement en fonction des catégories et des rubriques que vous avez fournies.
* définir la mention **alias** pour vous assurer que toutes les mentions d’une marque sont capturées et prises en compte ;
* définir d’**autres alias** pour suivre précisément d’autres marques.

>[!NOTE]
>Les prompts exacts que vous demandez aux LLM ne sont pas disponibles publiquement car ils ne sont pas divulgués par les LLM.

>[!NOTE]
>
> Pour plus d’informations sur la configuration des catégories, rubriques et prompts, reportez-vous à la page [Bonnes pratiques pour la configuration des catégories, rubriques, prompts](/help/overview/best-practices-topics-prompts.md).

## Étape 3 : informations sur la présence de la marque

Une fois votre domaine intégré, des informations initiales s’affichent dans la vue Présence de la marque en fonction des prompts qui ont été générés automatiquement lors de l’intégration. Une fois que vous avez personnalisé vos propres catégories, rubriques et prompts, LLM Optimizer déclenche automatiquement l’analyse de présence de la marque sur les prompts que vous avez fournis et les résultats seront disponibles sous 24 heures.

## Étape 4 : fournir des informations pour le transfert du journal CDN {#step-4}

Pour déverrouiller les informations sur le trafic généré par l’IA agentique et le trafic de recommandation, vous devez fournir des informations pour le transfert du journal CDN. Elles peuvent être ajoutées à partir du [tableau de bord de configuration cliente](/help/dashboards/customer-configuration.md#cdn-configuration) en accédant à l’onglet **Configuration du réseau CDN** et en cliquant sur **Intégrer le réseau CDN**.

![Configuration cliente du CDN](/help/overview/assets/cc-cdn.png)

Si aucun fournisseur de réseau CDN n’a été ajouté au préalable (comme décrit ci-dessus), vous serez invité à ajouter le transfert de journal CDN lors de l’accès initial aux tableaux de bord du trafic généré par l’IA agentique et du trafic de recommandation. Pour plus d’informations, consultez :

* [Trafic généré par l’IA agentique](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Trafic de recommandation](/help/dashboards/referral-traffic.md#setup#setup)

## Étape 5 : explorer les tableaux de bord et prendre des mesures

Après avoir fourni des informations pour le transfert du journal CDN, vous pouvez :

* afficher le tableau de bord de la [présence de la marque](/help/dashboards/brand-presence.md), visualiser votre score de visibilité et suivre vos performances par rapport aux autres marques ;
* explorer les tableaux de bord du [trafic généré par l’IA agentique](/help/dashboards/agentic-traffic.md) et du [trafic de recommandation](/help/dashboards/referral-traffic.md), si le transfert de journal CDN a été configuré ;
* Utiliser les [opportunités](/help/dashboards/opportunities.md) pour identifier les améliorations de contenu et techniques ;
* exporter des données et collaborer avec votre équipe ou inviter vos collègues à utiliser le produit.

Enfin, pour comprendre pleinement les fonctionnalités de LLM Optimizer, vous devez explorer tous les [tableaux de bord](/help/dashboards/dashboards-overview.md) disponibles.
