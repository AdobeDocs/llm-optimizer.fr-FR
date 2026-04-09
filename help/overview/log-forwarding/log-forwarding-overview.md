---
title: Présentation du transfert de journal BYOCDN
description: Découvrez comment transférer les journaux CDN de votre fournisseur vers le compartiment S3 Adobe pour la collecte de données de trafic agentic dans LLM Optimizer.
feature: Agentic Traffic
source-git-commit: b6e74e8706c4074a47cc355cb5f3a69a817f8a49
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 2%

---


# Présentation du transfert de journal BYOCDN {#cdn-log-forwarding}

Le transfert de journal pour un réseau CDN géré par le client (BYOCDN) est le processus d’envoi de vos journaux d’accès CDN au compartiment Amazon S3 d’Adobe afin que LLM Optimizer puisse collecter et analyser les données de trafic agentiques. Sans transfert du journal CDN, le tableau de bord [Trafic agent](/help/dashboards/agentic-traffic.md) ne peut pas afficher de mesures.

Les guides fournis ci-dessous suivent le même workflow en deux phases :

1. **Intégration dans LLM Optimizer** — Enregistrez votre réseau CDN sur la page [Configuration du réseau CDN](/help/dashboards/customer-configuration.md) pour générer les informations d’identification S3 et les détails de chemin d’accès nécessaires.
2. **Configurer votre réseau CDN** : utilisez ces détails pour créer une tâche de transfert de journal (ou charger les journaux manuellement) dans la console de votre fournisseur de réseau CDN. Pour CloudFront, vous pouvez utiliser la console ou terminer la configuration de la diffusion avec l’**interface de ligne de commande** uniquement ; voir [CloudFront (interface de ligne de commande AWS)](/help/overview/log-forwarding/cloudfront-cli.md).

## Fournisseurs de réseau CDN {#cdn-providers}

Suivez le guide correspondant à votre fournisseur de réseau CDN.

| Fournisseur de CDN | Guide |
|---|---|
| Akamai | [Afficher le guide](/help/overview/log-forwarding/akamai.md) |
| Cloudflare | [Afficher le guide](/help/overview/log-forwarding/cloudflare.md) |
| CloudFront (console) | [Afficher le guide](/help/overview/log-forwarding/cloudfront.md) |
| CloudFront (interface de ligne de commande AWS) | [Afficher le guide](/help/overview/log-forwarding/cloudfront-cli.md) |
| Fastly | [Afficher le guide](/help/overview/log-forwarding/fastly.md) |
| Imperva | [Afficher le guide](/help/overview/log-forwarding/imperva.md) |
| Autre (réseau CDN manuel/non pris en charge) | [Afficher le guide](/help/overview/log-forwarding/other.md) |

>[!NOTE]
>
>Si votre fournisseur de réseau CDN n’est pas répertorié ci-dessus, utilisez le guide **Autre (réseau CDN manuel/non pris en charge)** qui couvre les chargements manuels, les scripts ad hoc et tout réseau CDN qui n’est pas pris en charge en mode natif.
