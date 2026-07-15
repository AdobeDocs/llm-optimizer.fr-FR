---
title: Optimize at Edge - CDN géré d’AEM Cloud Service (Fastly)
description: Découvrez comment configurer le CDN géré d’AEM Cloud Service (Fastly) pour Optimize at Edge dans LLM Optimizer.
feature: Opportunities
autotag-review: '2026-07-15T16:49:32.275Z'
TQID: 'https://experienceleague.adobe.com/2-IzfF1iTEzW-gpqPA-t3mffRuhMxaKi1Dp0A62IZ9U'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: d1956731-2adb-4bb7-8301-2b239254ac72id: e0828736-236a-487b-a478-5a635455eadcid: e1b649f0-0a61-46e4-9082-64d5cb2576c6id: ef4e63f5-cb4d-462d-bf9a-1f617edf2a3a
subfeature_v2: id: d23587d6-14d6-4e3f-9ee1-cc18623832e1id: e06fae5f-830b-4222-a469-b5e148d36465
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: c1579802-ddd4-4214-8a91-97b2066abe11id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 836
ht-degree: 100%

---


# Réseau CDN géré par AEM Cloud Service (Fastly)

Cette configuration achemine le trafic généré par l’IA agentique (demandes provenant de robots d’IA et d’agents utilisateurs LLM) vers le service principal Edge Optimize (`live.edgeoptimize.net`). Les personnes humaines et les robots d’optimisation du moteur de recherche continuent d’être servis depuis votre origine comme d’habitude. Pour tester la configuration, une fois celle-ci terminée, recherchez l’en-tête `x-edgeoptimize-request-id` dans la réponse.

## Conditions préalables

Pour accéder à cette fonctionnalité :

- La clientèle payante doit avoir accès au profil de produit IMS **Utilisateurs et utilisatrices Adobe LLM Optimizer**. Contactez l’administration de votre organisation pour demander l’accès.
  ![Ajouter un utilisateur ou une utilisatrice à un profil de produit](/help/assets/optimize-at-edge/cs-fastly-user-product-profiles.png)
- La clientèle en version d’essai doit faire partie du groupe IMS **LLMO Admin**. Si le groupe n’existe pas, l’administration de votre organisation peut le créer et vous ajouter.
  ![Créer un groupe IMS LLMO Admin](/help/assets/optimize-at-edge/cs-fastly-create-ims-group.png)

>[!NOTE]
> Cette fonctionnalité n’est pas prise en charge dans Safari ou dans les modes de navigation incognito/privée.

## Étapes d’activation du routage

Pour commencer à acheminer le trafic généré par l’IA agentique vers Edge Optimizer, procédez comme suit :

1. Dans LLM Optimizer, ouvrez **Configuration cliente** et sélectionnez l’onglet **Configuration du réseau CDN**.

   ![Accéder à Configuration cliente](/help/assets/optimize-at-edge/cs-fastly-prereq-customer-config-nav.png)

2. Repérez la section **Déployer les optimisations vers les agents IA**. Cliquez sur le bouton **Ajouter**.

   ![Déployer des optimisations vers les agents IA - En attente](/help/assets/optimize-at-edge/cs-fastly-enable-button.png)

3. Dans la boîte de dialogue de confirmation, sélectionnez **Activer** pour confirmer que vous souhaitez activer le routage. Si une erreur apparaît, reportez-vous à la section [Dépannage](#troubleshooting) pour la résoudre.

   ![Boîte de dialogue de confirmation Activer le moteur d’optimisation](/help/assets/optimize-at-edge/cs-fastly-enable-dialog.png)

4. Une fois confirmé, le routage prend quelques minutes.

   ![Routage en cours](/help/assets/optimize-at-edge/cs-fastly-enable-button-clicked-routing-in-progress.png)

   Rechargez la page au bout de 5 minutes pour vérifier que le routage est terminé. Une fois le routage configuré et actif, son statut est mis à jour sur **Terminé** pour afficher une coche verte indiquant qu’il a bien été activé. Aucune autre action n’est requise de votre part.

   ![Déployer des optimisations vers les agents IA - Terminé](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

   Pour désactiver le routage à tout moment, revenez à la section **Déployer des optimisations vers les agents IA** de l’onglet **Configuration du réseau CDN** et cliquez sur **Désactiver**.

De plus, si vous avez besoin d’aide pour les étapes ci-dessus, contactez votre équipe Adobe en charge des comptes ou `llmo-at-edge@adobe.com`.

## Dépannage

Si une erreur s’affiche lors de l’activation ou de la désactivation du routage, elle se présente comme suit :

![Boîte de dialogue de confirmation : erreur](/help/assets/optimize-at-edge/cs-fastly-confirmation-dialog-error.png)

Utilisez la liste ci-dessous pour identifier l’erreur et suivre les instructions.

1. **La personne n’a pas accès au produit LLMO**

   **Cause :** le compte d’utilisation ne dispose pas du contexte de produit LLM Optimizer dans votre profil Adobe IMS. Cela est nécessaire pour que la clientèle payante configure le routage du réseau CDN.

   **Recommandation :** vérifiez que le profil de produit **Utilisateurs et utilisatrices Adobe LLM Optimizer** vous a été attribué dans Adobe Admin Console par l’administration de l’organisation.

2. **Seuls les membres du groupe LLMO Admin peuvent configurer le routage du réseau CDN.**

   **Cause :** votre compte n’est pas membre du groupe IMS **LLMO Admin**. Cela est nécessaire pour que la clientèle en version d’essai configure le routage du réseau CDN.

   **Recommandation :** vérifiez que vous avez été ajouté(e) au groupe IMS **LLMO Admin** dans Adobe Admin Console par l’administration de l’organisation.

3. **Le type de réseau CDN demandé aem-cs-fastly ne correspond pas au réseau CDN détecté pour ce domaine.**

   **Cause :** indique que le type de réseau CDN détecté pour votre site n’est pas *AEM Cloud Service Managed CDN (Fastly)*.

   **Recommandation :** vérifiez que votre site est hébergé sur le réseau CDN géré par AEM Cloud Service (Fastly).

4. **Erreur lors de l’exploration du site**

   **Cause :** LLM Optimizer n’a pas pu atteindre votre site lors de la configuration du routage. Cela peut se produire si le site est en panne ou inatteignable, ou encore si la demande a expiré.

   **Recommandation :** vérifiez que votre site est accessible au public et renvoyez une réponse valide, puis réessayez.

5. **Le site n’a pas renvoyé de réponse valide pour la sonde de routage.**

   **Cause :** le site a renvoyé un statut HTTP inattendu (et non 2xx ou 301) lors de l’analyse au moment de la configuration.

   **Recommandation :** vérifiez que votre site renvoie une réponse réussie (2xx) pour l’URL de base enregistrée dans LLM Optimizer, puis réessayez.

6. **Échec de l’authentification avec le service IMS en amont**

   **Cause :** la session a peut-être expiré ou un problème est survenu lors de l’authentification auprès d’Adobe IMS pendant la demande de routage.

   **Recommandation :** déconnectez-vous de LLM Optimizer, reconnectez-vous, puis réessayez d’activer le routage.

Si le problème persiste, contactez l’équipe Adobe en charge des comptes ou `llmo-at-edge@adobe.com`.

## (Facultatif) Vérifier la configuration

Une fois la configuration du routage terminée, vous pouvez éventuellement vérifier que le trafic des robots est acheminé vers Edge Optimize et que le trafic humain n’est pas affecté.

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

2. **Tester le trafic humain (ne devrait PAS être affecté)**

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

   Vous pouvez également confirmer le routage dans l’interface d’utilisation de LLM Optimizer. Ouvrez **Configuration cliente** et sélectionnez l’onglet **Configuration du réseau CDN**. Lorsque le routage est actif, la section **Déployer des optimisations vers les agents IA** indique **Terminé**.

   ![Déployer des optimisations vers les agents IA - Terminé](/help/assets/optimize-at-edge/cs-fastly-disable-button.png)

{{return-to-overview}}
