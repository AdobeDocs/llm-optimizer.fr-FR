---
source-git-commit: da789100d814004687de2f46e18a295671dec4b8
workflow-type: tm+mt
source-wordcount: '363'
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

## Clé API du domaine d’évaluation (facultatif) {#retrieve-staging-edge-optimize-api-key}

Utilisez un nom d’hôte d’évaluation lorsque vous souhaitez tester l’optimisation sur Edge dans un environnement inférieur avant que le trafic de production n’utilise les règles de routage.

**Conditions préalables**

* Le nom d’hôte d’évaluation doit appartenir au **même domaine enregistrable** que votre site de production (par exemple, `https://staging.example.com` lorsque la production est `https://www.example.com`).
* Un seul domaine d **évaluation** peut être configuré pour le site. Une fois enregistré, il ne peut pas être modifié sans assistance.

**Étapes**

1. Dans LLM Optimizer, ouvrez **Configuration du client** et sélectionnez l’onglet **Configuration du réseau de diffusion de contenu**.

2. Dans la section **Déployer les optimisations sur les agents d’IA** , sélectionnez **Ajouter un domaine d’évaluation** (ou **Domaine d’évaluation** si un domaine d’évaluation est déjà configuré).

3. Dans la boîte de dialogue **Domaine d’évaluation**, saisissez l’URL d’évaluation complète, y compris `https://`, puis sélectionnez **Définir le domaine**.

   ![ Boîte de dialogue d’entrée du domaine d’évaluation ](/help/assets/optimize-at-edge/byocdn-staging-domain-input.png)

4. Confirmez le domaine dans l’invite suivante. Une fois le workflow terminé, la boîte de dialogue **Domaines d’évaluation** affiche le domaine configuré et sa clé **API**. Sélectionnez **Copier** pour copier la clé API intermédiaire.

   ![Clé API du domaine d’évaluation](/help/assets/optimize-at-edge/byocdn-staging-domain-api-key.png)

Si vous avez besoin d&#39;aide, contactez `llmo-at-edge@adobe.com`.

## Vérification du statut du routage dans LLM Optimizer {#verify-routing-status-in-ui}

Le statut du routage du trafic peut également être vérifié dans l’interface utilisateur de LLM Optimizer. Accédez à **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**.

![Déploiement des optimisations sur les agents d’IA - terminé](/help/assets/optimize-at-edge/byocdn-CDN-traffic-routed-tick.png)

## Revenir à l’aperçu {#return-to-overview}

Pour en savoir plus sur l’optimisation sur Edge, y compris sur les opportunités disponibles, les workflows d’optimisation automatique et les questions fréquentes, revenez à la [ Présentation de l’optimisation sur Edge ](/help/dashboards/optimize-at-edge/overview.md).
