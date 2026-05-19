---
title: Vue d’ensemble du transfert de journaux avec BYOCDN
description: Découvrez comment transférer les journaux du CDN de votre fournisseur vers le compartiment S3 d’Adobe pour la collecte de données du trafic généré par l’IA agentique dans LLM Optimizer.
feature: Agentic Traffic
autotag-review: '2026-05-15T17:53:26.846Z'
TQID: 'https://experienceleague.adobe.com/EPQ6GBjNXpIwYTuzj1xDKkIzuFLOWFPmu0lqSGUAX3I'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: d23587d6-14d6-4e3f-9ee1-cc18623832e1
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 215
ht-degree: 100%

---


# Vue d’ensemble du transfert de journaux avec BYOCDN {#cdn-log-forwarding}

Le transfert de journaux pour un CDN géré par le client ou la cliente (BYOCDN) est le processus d’envoi de vos journaux d’accès du CDN au compartiment Amazon S3 d’Adobe afin que LLM Optimizer puisse collecter et analyser les données de trafic généré par l’IA agentique. Sans transfert des journaux du CDN, le tableau de bord du [trafic généré par l’IA agentique](/help/dashboards/agentic-traffic.md) reste vide.

Les guides fournis ci-dessous suivent le même processus en deux phases :

1. **Intégration dans LLM Optimizer** - Enregistrez votre CDN sur la page [Configuration du CDN](/help/dashboards/customer-configuration.md) pour générer les informations d’identification S3 et les détails du chemin requis.
2. **Configurez votre CDN** - Utilisez ces détails pour créer une tâche de transfert de journaux (ou chargez les journaux manuellement) dans la console de votre fournisseur de CDN. Pour CloudFront, vous pouvez utiliser la console ou effectuer la configuration en utilisant uniquement **l’interface de ligne de commande AWS** ; voir [CloudFront (interface de ligne de commande AWS)](/help/overview/log-forwarding/cloudfront-cli.md).

## Fournisseurs de CDN {#cdn-providers}

Suivez le guide correspondant en fonction de votre fournisseur de CDN.

| Fournisseur de CDN | Guide |
|---|---|
| Akamai | [Afficher le guide](/help/overview/log-forwarding/akamai.md) |
| Cloudflare | [Afficher le guide](/help/overview/log-forwarding/cloudflare.md) |
| CloudFront (console) | [Afficher le guide](/help/overview/log-forwarding/cloudfront.md) |
| CloudFront (AWS CLI) | [Afficher le guide](/help/overview/log-forwarding/cloudfront-cli.md) |
| Fastly | [Afficher le guide](/help/overview/log-forwarding/fastly.md) |
| Imperva | [Afficher le guide](/help/overview/log-forwarding/imperva.md) |
| Autre (CDN manuel / non pris en charge) | [Afficher le guide](/help/overview/log-forwarding/other.md) |

>[!NOTE]
>
>Si votre fournisseur de CDN n’est pas répertorié ci-dessus, utilisez le guide **Autre (CDN manuel / non pris en charge)** qui concerne les téléchargements manuels, les scripts ad hoc et tout CDN qui n’est pas pris en charge nativement.
