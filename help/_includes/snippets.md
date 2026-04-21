---
source-git-commit: b13f91d144d4899198891c4dcd841de8cfbb2355
workflow-type: tm+mt
source-wordcount: '157'
ht-degree: 0%

---
# Fragments de code

## Vérification du statut du routage dans LLM Optimizer {#verify-routing-status-in-ui}

Le statut du routage du trafic peut également être vérifié dans l’interface utilisateur de LLM Optimizer. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

![Déploiement des optimisations sur les agents d’IA - terminé](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

## Autorisation de l’optimisation sur Edge via des règles de pare-feu (facultatif) {#waf-allowlist-setup}

Si votre réseau CDN utilise un WAF ou un gestionnaire de robots :

* Placez sur la liste autorisée l’agent utilisateur `*AdobeEdgeOptimize/1.0*` dans votre WAF ou Gestionnaire de robots afin que le service Optimize at Edge puisse récupérer votre contenu d’origine.
* Si votre pare-feu nécessite une vérification supplémentaire au-delà de l’agent utilisateur, générez un secret (par exemple, `openssl rand -hex 32`) et :
   * Ajoutez des `x-edgeoptimize-fetcher-key` avec le secret dans vos règles de routage à côté des autres en-têtes `x-edgeoptimize-*`.
   * Ajoutez une règle WAF ou Gestionnaire de robots pour autoriser les requêtes où `x-edgeoptimize-fetcher-key` correspond au même secret.
* Optimiser dans Edge transmet cet en-tête en l’état : vous êtes propriétaire du cycle de vie complet des clés.

## Revenir à l’aperçu {#return-to-overview}

Pour en savoir plus sur l’optimisation sur Edge, y compris sur les opportunités disponibles, les workflows d’optimisation automatique et les questions fréquentes, revenez à la [ Présentation de l’optimisation sur Edge ](/help/dashboards/optimize-at-edge/overview.md).
