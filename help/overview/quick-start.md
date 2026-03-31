---
title: Démarrage rapide
description: Découvrez comment intégrer votre nom de marque et votre domaine, activer votre version d’essai à partir d’Experience Hub ou d’Experience Cloud et terminer la configuration pour Adobe LLM Optimizer.
feature: Quickstart, Onboarding
source-git-commit: dcbeb1c61dd9dcefd83908f65f8303d36c0fb78e
workflow-type: tm+mt
source-wordcount: '1208'
ht-degree: 47%

---


# Démarrage rapide

Pour commencer à utiliser LLM Optimizer, vous devez terminer le processus d’intégration. Après l’intégration, vous pourrez personnaliser les catégories, les rubriques, les invites et configurer le transfert du journal pour obtenir des informations plus précises et un accès complet aux [tableaux de bord de &#x200B;](/help/dashboards/dashboards-overview.md) ainsi qu’à d’autres fonctionnalités.

## Vue d’ensemble de l’intégration

Le processus d’intégration commence par l’intégration de votre domaine et de votre nom de marque. Chaque partie du parcours d’intégration est détaillée ci-dessous, avec des conseils utiles pour commencer à utiliser LLM Optimizer dès que possible.

### Autoriser Adobe LLM Optimizer à accéder aux pages publiques

Pour fournir un contenu précis et des recommandations techniques, Adobe LLM Optimizer doit pouvoir accéder à vos pages destinées au public. Pour ce faire, un robot d’exploration interne sécurisé (agent utilisateur Spacecat/1.0) est utilisé.

Configuration requise :

* Ajoutez l’agent utilisateur Spacecat/1.0 à la Liste autorisée dans le fichier robots.txt de votre site ou dans les règles de gestion du trafic de robots.
* Assurez-vous que les pages ne sont pas bloquées au niveau du domaine ou du réseau CDN. Les pages bloquées ne peuvent pas être indexées, ce qui signifie que les tâches d’optimisation et les informations ne peuvent pas être générées pour elles.

Si la visibilité du contenu semble faible dans le tableau de bord, vérifiez que le robot d’exploration a accès à vos domaines. L’accès restreint est une cause courante d’indexation incomplète.

## Étape 1 : intégrer votre nom de marque et votre domaine {#step-1-onboard-your-domain}

Pour commencer à utiliser LLM Optimizer, commencez par activer votre version d’évaluation (si éligible) et intégrez votre nom de marque et votre domaine.

### Activer votre version d’évaluation

Le flux d’activation diffère en fonction de votre produit Adobe.

#### Clients AEM Cloud

Pour activer votre version d’évaluation, en tant que client AEM Cloud, vous pouvez effectuer l’une des opérations suivantes :

* Accédez à [&#128279;](https://experienceleague.adobe.com/fr/docs/experience-manager-cloud-service/content/experience-hub/experience-hub) et utilisez la carte Annonce de produit pour activer LLM Optimizer. Après avoir sélectionné **Essayer LLM Optimizer**, vous êtes redirigé vers [https://llmo.now](https://llmo.now). Connectez-vous via IMS, puis saisissez un domaine et un nom de marque pour démarrer le processus d’intégration.
* Ou accédez directement à [&#128279;](https://llmo.now) et connectez-vous.

![Version d’évaluation de LLM Optimizer](/help/overview/assets/llm-trial.png)

#### clients Adobe Analytics

Si vous êtes client Adobe Analytics, une bannière s’affiche sur la page d’accueil d’Experience Cloud.

![Page d’accueil d’Experience Cloud avec la bannière Démarrer la version d’évaluation de Adobe LLM Optimizer &#x200B;](/help/overview/assets/experience-cloud-llmo-trial-banner.png)

Vous pouvez activer votre version d’évaluation de l’une des façons suivantes :

* Sélectionnez **Démarrer la version d’évaluation de Adobe LLM Optimizer** dans la bannière.
* Accédez directement à [&#128279;](https://llmo.now) et connectez-vous.

Une fois l’essai actif, continuez à intégrer votre nom de marque et votre domaine.

>[!NOTE]
>
> * **Version d’essai gratuite** les clients AEM Cloud et Adobe Analytics peuvent utiliser la version d’essai gratuite de LLM Optimizer.
> * **Les clients qui activent l’évaluation le ou après le 1er avril 2026** peuvent utiliser jusqu’à 100 invites, un domaine, et peuvent déployer des optimisations sur jusqu’à 10 URL pour un seul type d’opportunité.
> * **Les clients qui ont activé l’évaluation avant le 1er avril 2026** continuent d’avoir accès à jusqu’à 200 invites en vertu de leurs conditions actuelles.
>
>L’utilisation au-delà des limites incluses nécessite un contrat de licence distinct. L’accès est fourni « en l’état » et « en fonction de la disponibilité », et peut être modifié, limité ou supprimé à tout moment. Contactez votre représentant de compte pour plus d’informations.

#### Intégrez votre nom de marque et votre domaine

Intégrez votre nom de marque et votre domaine pour commencer à utiliser LLM Optimizer.

1. Saisissez votre nom de marque et le domaine associé.

   * Il doit s’agir du domaine principal dans lequel vous souhaitez analyser et optimiser le contenu.

1. Intégration terminée.

   * Une fois envoyé, LLM Optimizer commence à analyser votre domaine et à générer des informations.

![Domaine LLM Optimizer](/help/overview/assets/domain.png)

>[!NOTE]
>Les nouveaux prompts n’apparaîtront pas dans le [tableau de bord Présence de la marque](/help/dashboards/brand-presence.md) tant que le traitement ne sera pas terminé.

>[!NOTE]
>Le domaine fourni sera utilisé par toutes les personnes membres de votre organisation et ne peut pas être modifié.

Un petit ensemble de catégories, de rubriques et de prompts sera généré pendant la phase d’intégration. L’analyse de présence de la marque sur ces prompts sera disponible peu de temps après l’intégration de votre site.

La possibilité de déployer des optimisations sur le serveur Edge est également disponible. Pour en savoir plus, consultez [Optimisation sur Edge - Questions fréquentes](https://experienceleague.adobe.com/en/docs/llm-optimizer/using/resources/optimize-at-edge/overview#frequently-asked-questions).

Configurez également le [transfert de journal CDN](#step-4) pour l’analyse du trafic. LLM Optimizer a besoin des données et des informations de Présence des marques des agences et du trafic de recommandation pour identifier les opportunités et fournir des recommandations prescriptives qui augmentent la visibilité de l&#39;IA.

### Clients cloud non AEM

Une fois que votre organisation a finalisé l’accord commercial, vous êtes intégré à LLM Optimizer avec le domaine sélectionné par votre organisation. Une fois l’intégration terminée, connectez-vous à [&#128279;](https://llmo.now).

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

Pour déverrouiller les informations sur le trafic et le Trafic de recommandation Agentic, ajoutez les informations de transfert de journal CDN depuis le tableau de bord [configuration du client](/help/dashboards/customer-configuration.md#cdn-configuration). Ouvrez l’onglet **Configuration du réseau CDN** et sélectionnez **Réseau CDN intégré**.

![Configuration cliente du CDN](/help/overview/assets/cc-cdn.png)

Si aucun fournisseur de réseau CDN n’a été ajouté au préalable (comme décrit ci-dessus), vous serez invité à ajouter le transfert de journal CDN lors de l’accès initial aux tableaux de bord du trafic généré par l’IA agentique et du trafic de recommandation. Pour plus d’informations, consultez :

* [Trafic généré par l’IA agentique](/help/dashboards/agentic-traffic.md#cdn-setup)
* [Trafic de recommandation](/help/dashboards/referral-traffic.md#setup)

>[!NOTE]
>Pour plus d’informations sur le transfert de journal lors de l’utilisation d’un réseau CDN géré par le client (BYOCDN), consultez [Présentation du transfert de journal BYOCDN](/help/overview/log-forwarding/log-forwarding-overview.md)

## Étape 5 : explorer les tableaux de bord et prendre des mesures

Après avoir fourni des informations pour le transfert du journal CDN, vous pouvez :

* afficher le tableau de bord de la [présence de la marque](/help/dashboards/brand-presence.md), visualiser votre score de visibilité et suivre vos performances par rapport aux autres marques ;
* Explorez les tableaux de bord [Agentic](/help/dashboards/agentic-traffic.md) et [Trafic de recommandation &#x200B;](/help/dashboards/referral-traffic.md), si le transfert du journal CDN a été configuré.
* Utiliser les [opportunités](/help/dashboards/opportunities.md) pour identifier les améliorations de contenu et techniques ;
* exporter des données et collaborer avec votre équipe ou inviter vos collègues à utiliser le produit.

Enfin, pour comprendre pleinement les fonctionnalités de LLM Optimizer, vous devez explorer tous les [tableaux de bord](/help/dashboards/dashboards-overview.md) disponibles.
