---
source-git-commit: e9309dc8f8d1d81b953483f17dcb424e46d5cd3b
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---
# Fragments de code

## Étapes de récupération des clés API {#retrieve-byocdn-api-key}

**Procédure de récupération de votre clé API d’optimisation d’Edge de production :**

1. Dans LLM Optimizer, ouvrez **Configuration du client** et sélectionnez l’onglet **Configuration du réseau de diffusion de contenu**.

   ![Accéder à la configuration du client](/help/assets/optimize-at-edge/prereq-customer-config-nav.png)

2. Recherchez la section **Déployer des optimisations sur des agents d’IA**. Cochez la case **Activer le moteur d’optimisation**.

   ![Déploiement des optimisations sur les agents d’IA - en attente](/help/assets/optimize-at-edge/byocdn-deploy-optimizations-pending.png)

3. Dans la boîte de dialogue de confirmation, sélectionnez **Activer**.

   ![Boîte de dialogue de confirmation Activer le moteur d’optimisation](/help/assets/optimize-at-edge/byocdn-enable-optimization-engine-dialog.png)

4. Sélectionnez **Afficher les détails**. Dans la boîte de dialogue **Déployer les détails des optimisations**, copiez la **Clé API de production** (utilisez **Copier** en regard du champ).

   ![Clé de l’API de production dans les détails des optimisations du déploiement](/help/assets/optimize-at-edge/byocdn-production-api-key-details.png)

   >[!NOTE]
   >La boîte de dialogue peut indiquer que la configuration n’est pas terminée. Cela est attendu jusqu’à ce que le routage soit vérifié. Vous pouvez toujours copier la clé API afin que votre équipe informatique ou réseau CDN puisse terminer la configuration.

De plus, si vous avez besoin d’aide pour les étapes ci-dessus, contactez votre équipe de compte Adobe ou votre `llmo-at-edge@adobe.com`.

## Facultatif : test du routage sur un nom d’hôte d’évaluation {#retrieve-staging-edge-optimize-api-key}

**Facultatif : test du routage sur un nom d’hôte d’évaluation**

Si vous souhaitez valider le routage dans un environnement inférieur avant d’activer le routage de production, vous pouvez configurer un nom d’hôte d’évaluation.

**Conditions requises**

* Le nom d’hôte d’évaluation doit se trouver sur le **même domaine enregistrable** que la production (par exemple, `https://staging.example.com` lorsque la production est `https://www.example.com`).
* Un seul domaine **’évaluation** par site. Une fois enregistré, il ne peut pas être modifié sans contacter Adobe.

**Obtention de votre clé API intermédiaire**

1. Ouvrez **Configuration du client** et sélectionnez **Configuration du réseau CDN**.
2. Sous **Déployer les optimisations sur les agents d’IA**, sélectionnez **Ajouter un domaine intermédiaire** (ou **Domaine d’évaluation** si un domaine d’évaluation est déjà configuré).
3. Saisissez l’URL d’évaluation complète, y compris `https://`, puis sélectionnez **Définir le domaine**.
4. Copiez la clé API **staging** à partir de la boîte de dialogue de confirmation.

![Clé API du domaine d’évaluation](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Déployez les mêmes règles de routage sur votre environnement d’évaluation à l’aide de la clé API d’évaluation.

**Test du trafic de robots d’évaluation**

Remplacez `https://staging.example.com/page.html` par l’URL et le chemin d’accès d’évaluation réels. **Succès :** la réponse inclut l’en-tête `x-edgeoptimize-request-id`.

Si vous avez besoin d&#39;aide, contactez `llmo-at-edge@adobe.com`.

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

Pour en savoir plus sur l’optimisation sur Edge, y compris sur les opportunités disponibles, les workflows d’optimisation automatique et les questions fréquentes, revenez à la [&#x200B; Présentation de l’optimisation sur Edge &#x200B;](/help/dashboards/optimize-at-edge/overview.md).
