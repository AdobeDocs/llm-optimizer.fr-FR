---
title: Optimize at Edge - CDN géré d’AEM Cloud Service (Fastly)
description: Découvrez comment configurer le CDN géré d’AEM Cloud Service (Fastly) pour Optimize at Edge dans LLM Optimizer.
feature: Opportunities
source-git-commit: 184d6008c2579014c6ff453e8bfff4bb898f4b82
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 20%

---


# Réseau CDN géré par AEM Cloud Service (Fastly)

Cette configuration achemine le trafic généré par l’IA agentique (demandes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les personnes humaines et les robots d’optimisation du moteur de recherche continuent d’être servis depuis votre origine comme d’habitude. Pour tester la configuration, une fois l’installation terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

## Conditions préalables

Pour accéder à cette fonctionnalité :

- Les clients payants doivent avoir accès au profil de produit IMS **Utilisateurs de**. Contactez l’administrateur de votre organisation pour demander l’accès.
  ![Ajout d’un utilisateur à un profil de produit](/help/assets/optimize-at-edge/cs-fastly-user-product-profiles.png)
- Les clients en version d&#39;essai doivent faire partie du groupe IMS **LLMO Admin**. Si le groupe n’existe pas, l’administrateur de votre organisation peut le créer et vous ajouter.
  ![Créer un groupe IMS d&#39;administration LLMO](/help/assets/optimize-at-edge/cs-fastly-create-ims-group.png)

>[!NOTE]
> Cette fonctionnalité n’est pas prise en charge dans Safari ou dans les modes de navigation incognito/privée.

## Étapes pour activer le routage

Pour commencer à acheminer le trafic généré par l’IA agentique vers Edge Optimizer :

1. Dans LLM Optimizer, ouvrez **Configuration du client** et sélectionnez l’onglet **Configuration du réseau de diffusion de contenu**.

   ![Accédez à Configuration cliente](/help/assets/optimize-at-edge/cs-fastly-prereq-customer-config-nav.png)

2. Recherchez la section **Déployer des optimisations sur des agents d’IA**. Cliquez sur le bouton **Activer**.

   ![Déploiement des optimisations sur les agents d’IA - en attente](/help/assets/optimize-at-edge/cs-fastly-enable-button.png)

3. Dans la boîte de dialogue de confirmation, sélectionnez **Activer** pour confirmer que vous souhaitez activer le routage. Si une erreur apparaît, reportez-vous à la section [Dépannage](#troubleshooting) pour la résoudre.

   ![Boîte de dialogue de confirmation Activer le moteur d’optimisation](/help/assets/optimize-at-edge/cs-fastly-enable-dialog.png)

4. Une fois confirmé, le routage prend quelques minutes.

   ![Routage en cours](/help/assets/optimize-at-edge/cs-fastly-enable-button-clicked-routing-in-progress.png)

   Rechargez la page au bout de 5 minutes pour vérifier que le routage est terminé. Une fois le routage configuré et actif, son statut passe à **Terminé** avec une coche verte confirmant qu&#39;il est activé. Aucune autre action n’est requise de votre part.

   ![Déploiement des optimisations sur les agents d’IA - terminé](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

   Pour désactiver le routage à tout moment, revenez à la section **Déployer les optimisations sur les agents d’IA** de l’onglet **Configuration du réseau CDN** et cliquez sur **Désactiver**.

De plus, si vous avez besoin d’aide pour les étapes ci-dessus, contactez votre équipe de compte Adobe ou `llmo-at-edge@adobe.com`.

## Dépannage

Si une erreur s’affiche lors de l’activation ou de la désactivation du routage, elle se présente comme suit :

![Erreur de la boîte de dialogue de confirmation](/help/assets/optimize-at-edge/cs-fastly-confirmation-dialog-error.png)

Utilisez la liste ci-dessous pour identifier l’erreur et suivre les instructions.

1. **L&#39;utilisateur n&#39;a pas accès au produit LLMO**

   **Cause :** le compte utilisateur ne dispose pas du contexte de produit LLM Optimizer dans votre profil Adobe IMS. Cela est nécessaire pour que les clients payants configurent le routage CDN.

   **Recommandation :** vérifiez que le profil de produit **Utilisateurs Adobe LLM Optimizer** vous a été attribué dans Adobe Admin Console par l’administrateur de l’organisation.

2. **Seuls les membres du groupe d’administrateurs LLMO peuvent configurer le routage CDN**

   **Cause :** votre compte n’est pas membre du groupe IMS **LLMO Admin**. Cela est nécessaire pour que les clients d’évaluation configurent le routage CDN.

   **Recommandation :** Vérifiez que vous avez été ajouté au groupe IMS **LLMO Admin** dans Adobe Admin Console par l’administrateur de l’organisation.

3. **Le type de réseau CDN demandé aem-cs-fastly ne correspond pas au réseau CDN détecté pour ce domaine**

   **Cause :** indique que le type de réseau CDN détecté pour votre site n’est pas *AEM Cloud Service Managed CDN (Fastly)*.

   **Recommandation :** vérifiez que votre site est hébergé sur le réseau CDN géré par AEM Cloud Service (Fastly).

4. **Erreur lors de l&#39;exploration du site**

   **Cause :** LLM Optimizer n’a pas pu atteindre votre site lors de la configuration du routage. Cela peut se produire si le site est en panne, inatteignable ou si la demande a expiré.

   **Recommandation :** vérifiez que votre site est accessible au public et renvoyez une réponse valide, puis réessayez.

5. **Le site n’a pas renvoyé de réponse valide pour la sonde de routage**

   **Cause :** le site a renvoyé un statut HTTP inattendu (et non 2xx ou 301) lors de l’analyse lors de la configuration.

   **Recommandation :** vérifiez que votre site renvoie une réponse réussie (2xx) pour l’URL de base enregistrée dans LLM Optimizer, puis réessayez.

6. **Échec de l’authentification avec le service IMS en amont**

   **Cause :** la session a peut-être expiré ou un problème est survenu lors de l’authentification auprès d’Adobe IMS pendant la demande de routage.

   **Recommandation :** déconnectez-vous de LLM Optimizer, reconnectez-vous, puis réessayez d’activer le routage.

Si le problème persiste, contactez l’équipe ou l’`llmo-at-edge@adobe.com` de votre compte Adobe.

## (Facultatif) Vérification de la configuration

Une fois la configuration du routage terminée, vous pouvez éventuellement vérifier que le trafic de robots d’IA est acheminé vers Edge Optimize et que le trafic humain n’est pas affecté.

1. **Tester le trafic de robots (doit être optimisé)**

   Simulez une requête de robot d’IA à l’aide d’une chaîne utilisateur-agent :

   ```
   curl -svo /dev/null https://www.example.com/page.html \
     --header "user-agent: chatgpt-user"
   ```

   Une réponse réussie inclut l’en-tête `x-edgeoptimize-request-id`, confirmant que la requête a été acheminée via Edge Optimize :

   ```
   < HTTP/2 200
   < x-edgeoptimize-request-id: 50fce12d-0519-4fc6-af78-d928785c1b85
   ```

2. **Tester le trafic humain (ne doit PAS être affecté)**

   Simulez une requête régulière de navigateur humain :

   ```
   curl -svo /dev/null https://www.example.com/page.html \
     --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36"
   ```

   La réponse ne doit pas contenir l’en-tête `x-edgeoptimize-request-id`. Le contenu de la page et le temps de réponse doivent rester identiques à avant l’activation de l’option Optimize at Edge.

3. **Comment différencier les deux scénarios**

   | En-tête | Trafic de robots (optimisé) | Trafic humain (non affecté) |
   |---|---|---|
   | `x-edgeoptimize-request-id` | Présent : contient un ID de requête unique | Absent |
   | `x-edgeoptimize-fo` | Présent uniquement en cas de basculement (valeur : `1`) | Absent |

4. **Vérifier le statut du routage dans LLM Optimizer**

   Vous pouvez également confirmer le routage dans l’interface utilisateur de LLM Optimizer. Ouvrez **Configuration du client** et sélectionnez l’onglet **Configuration du réseau CDN**. Lorsque le routage est actif, la section **Déployer les optimisations sur les agents d’IA** indique **Terminé**.

   ![Déploiement des optimisations sur les agents d’IA - terminé](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

{{return-to-overview}}
