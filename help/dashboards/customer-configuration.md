---
title: Configuration cliente
description: Utilisez la configuration cliente pour définir comment votre marque sera surveillée et analysée sur la plateforme LLM Optimizer.
feature: Customer Configuration
source-git-commit: 3fab5f21311a741e51e7a31cd3a26de79fcbff95
workflow-type: tm+mt
source-wordcount: '2100'
ht-degree: 40%

---


# Configuration cliente {#customer-configuration}

Le tableau de bord de la configuration cliente est un outil puissant qui fournit des informations sur la visibilité de votre marque dans les LLM. En configurant correctement des catégories, des rubriques et des prompts, vous pouvez vous assurer que votre marque est bien positionnée pour apparaître dans les réponses générées par les LLM. Cette configuration garantit que la plateforme adapte les informations à votre contexte commercial, ce qui permet une visibilité, un trafic et une analyse des opportunités précis.

![Tableau de bord de la configuration cliente](/help/dashboards/assets/customer-config.png)

Pour configurer la manière dont LLM Optimizer surveille et analyse la présence de votre marque sur différents marchés et paysages concurrentiels, vous avez accès aux onglets suivants :

* [Prompts](#prompts-brand)
* [Catégories](#categories)
* [Autres marques](#other-brands)
* [Alias de marque](#brand-aliases)
* [Configuration du CDN](#agentic-cdn)
* [Google Search Console](#google-console)

>[!IMPORTANT]
>
> Pour plus d’informations sur la configuration des catégories, rubriques et prompts, reportez-vous à la page [Bonnes pratiques pour la configuration des catégories, rubriques, prompts](/help/overview/best-practices-topics-prompts.md).

## Prompts {#prompts-brand}

Dans cet onglet, vous pouvez vérifier, gérer et personnaliser les prompts. Vous pouvez charger un fichier CSV [Analyse de présence de la marque](/help/dashboards/brand-presence.md) et la liste sera remplie avec les prompts et les rubriques de cette analyse ou [télécharger une bibliothèque de prompts](/help/overview/best-practices-topics-prompts.md) créée par Adobe. Vous pouvez également supprimer, modifier et ajouter des rubriques et leurs prompts associés selon vos besoins.

Pour importer un fichier CSV d’informations de données, vous devez d’abord exporter un fichier à partir du tableau de bord Présence de la marque. Voir la section [Données](/help/dashboards/brand-presence.md#data-insights) pour savoir comment faire. Une fois que vous avez le fichier :

1. Dans le tableau de bord, cliquez sur **Charger le fichier CSV**.
2. Dans la fenêtre Importer des données, effectuez un glisser-déposer ou choisissez manuellement le fichier.
3. Cliquez sur **Charger des données**.

Vous pouvez également créer un fichier CSV en téléchargeant le modèle depuis la fenêtre **Importer des données**. Une fois que vous avez le modèle, ouvrez-le et saisissez vos rubriques ainsi que les prompts, catégories et régions associés, chacun dans une nouvelle ligne.

Pour savoir comment télécharger et utiliser la bibliothèque de prompts sectoriels créée par Adobe, consultez la section Bibliothèque de prompts sectoriels sur [cette page](/help/overview/best-practices-topics-prompts.md).

En outre, vous pouvez également ajouter des rubriques/prompts à la liste, sans passer par un fichier CSV ou une bibliothèque de prompts. Pour ce faire, sur le tableau de bord, vous devez suivre ces étapes :

1. Cliquez sur le bouton **Ajouter une rubrique**.
2. Dans la nouvelle fenêtre de configuration, sélectionnez la **catégorie**. Les catégories créées précédemment apparaîtront ici.
3. Saisissez le nom de la rubrique.
4. Ajoutez le texte de prompt.
5. Sélectionnez la région.
6. Cliquez sur **Ajouter un prompt** et la rubrique contenant le prompt s’affiche dans la liste.

>[!NOTE]
>Les prompts nouvellement ajoutés n’apparaîtront pas dans Présence de la marque tant que le traitement ne sera pas terminé.

Sur la liste, vous pouvez cliquer sur chaque rubrique et le ou les prompts associés apparaîtront. Pour supprimer la rubrique et ses prompts associés, cliquez sur l’icône de suppression dans la liste.

## Catégories {#categories}

Dans l’onglet Catégories, vous pouvez définir les catégories commerciales ou les gammes de produits que vous souhaitez suivre et les associer à des régions spécifiques. Dans l’ensemble, l’onglet Catégories correspond à presque toutes les autres personnalisations de cette page, car les catégories apparaissent dans le champ Catégorie pour les autres personnalisations (suivi des autres, alias, etc.). Pour ajouter une nouvelle catégorie :

1. Cliquez sur le bouton **Ajouter**.
2. Dans la nouvelle fenêtre de configuration, ajoutez le **nom de la catégorie**.
3. Personnalisez la **région associée** où la catégorie sera surveillée.
4. Cliquez sur **Enregistrer** pour que la nouvelle catégorie apparaisse dans la liste des catégories.

L’ajout de nouvelles catégories ne génère pas automatiquement de rubriques et de prompts. Ceux-ci doivent être ajoutés manuellement à partir de l’onglet [Données](#data-insights).

Pour supprimer une catégorie, cliquez sur l’icône de suppression dans la liste des catégories. Attention : **supprimer une catégorie supprimera également les éléments associés** comme les alias de marque liés à cette catégorie spécifique.

## Autres marques {#others-tracking}

En utilisant cet onglet, vous pouvez suivre la manière dont les autres marques sont mentionnées par rapport à la vôtre dans différentes catégories et régions. Surveillez leur présence et leurs performances dans vos segments de marché. Pour personnaliser le suivi :

1. Cliquez sur le bouton **Ajouter**.
2. Dans la nouvelle fenêtre de configuration, sélectionnez la **catégorie**. Les catégories créées précédemment apparaîtront ici.
3. Ajoutez le nom de l’autre.
4. Personnalisez l’alias et les domaines de l’autre si nécessaire.
5. Cliquez sur **Enregistrer**.

Pour supprimer une entrée dans la liste, cliquez sur l’icône de suppression.

## Alias de marque {#brand-aliases}

L’utilisation d’alias de marque vous permet de configurer d’autres noms et variations de votre marque qui doivent faire l’objet d’un suivi dans différentes catégories et régions. Cela permet d’assurer une surveillance complète de toutes les mentions de la marque. Pour ajouter un alias de la marque :

1. Cliquez sur le bouton **Ajouter**.
2. Dans la nouvelle fenêtre de configuration, sélectionnez la **catégorie**. Les catégories créées précédemment apparaîtront ici.
3. Sélectionnez la **région** où l’alias sera surveillé.
4. Ajoutez l’alias de la marque.
5. Cliquez sur **Enregistrer** et l’alias de la marque apparaît dans la liste.

Pour supprimer un alias de marque, cliquez sur l’icône **Supprimer** dans la liste des alias.

## Configuration du CDN {#cdn-configuration}

Dans cet onglet, vous pouvez configurer vos flux CDN pour permettre à Adobe LLM Optimizer d’analyser vos données CDN. Ces données seront utilisées pour alimenter les tableaux de bord (comme le trafic généré par l’IA agentique), fournissant des informations sur les modèles de trafic, les mesures de performances et les opportunités d’optimisation. Pour intégrer votre fournisseur de CDN, cliquez sur **Intégrer le CDN**.

![Configuration cliente du CDN](/help/overview/assets/cc-cdn.png)

Dans la fenêtre **Intégrer le fournisseur du CDN** :

1. Sélectionnez votre fournisseur de CDN.
2. Cliquez sur **Intégration** pour activer le transfert des journaux.

Si vous sélectionnez **Autre**, vous devrez contacter llmo-now@adobe.com pour obtenir de l’aide.

## Google Search Console {#google-console}

Adobe LLM Optimizer vous permet d’intégrer votre compte Google Search Console pour importer des requêtes de recherche réelles directement dans l’interface. En affichant les requêtes réelles de la Search Console Google, vous pouvez créer des jeux d’invites basés sur le comportement réel de la recherche et les modèles de découverte à haute intention. Cela vous permet de hiérarchiser les invites en fonction de la demande éprouvée et d&#39;aligner les efforts d&#39;optimisation LLM sur la manière dont les utilisateurs effectuent actuellement des recherches. De plus, vous conservez le contrôle total, car les requêtes ne sont jamais ajoutées automatiquement et doivent être explicitement sélectionnées avant de devenir des invites actives.

### Fonctionnement {#how-it-works}

La principale chose à retenir à propos de l’intégration entre LLM Optimizer et la Search Console Google est la suivante : au lieu de deviner manuellement ce que les clients pourraient demander à un assistant d’IA, nous regardons ce qu’ils **recherchent déjà** et transformons ces requêtes réelles en invites conversationnelles naturelles. Ce processus de déplacement des requêtes de recherche vers les invites d’IA est illustré dans le diagramme ci-dessous.

![Flux de processus](/help/dashboards/assets/diagram-flow.png)

En général, le processus comporte cinq étapes :

#### Étape 1 — Collecter vos données de recherche réelles {#gsc-one}

Le processus commence par les mots-clés que votre audience utilise réellement lorsqu’elle trouve votre site web via Google. Ce jeu de données brut (souvent des milliers de requêtes uniques) est la base de tout ce qui suit.

#### Étape 2 — Analyser la signification et filtrer pour la sécurité {#gsc-two}

Chaque requête est analysée pour sa signification sémantique (ce sur quoi l’utilisateur interroge réellement) et filtrée à l’aide d’un filtre de sécurité qui supprime le contenu inapproprié ou hors marque. Cela permet de s’assurer que seuls les mots-clés propres et pertinents avancent.

#### Étape 3 — Regrouper en catégories et sujets {#gsc-three}

Les requêtes associées sont automatiquement regroupées en **catégories** (thèmes commerciaux généraux) et **sujets** (sous-sujets ciblés dans chaque catégorie). Le système donne la priorité aux catégories déjà configurées dans votre configuration de LLM Optimizer. En outre, il peut également faire apparaître de nouvelles catégories que vos données de recherche révèlent, mais qui ne sont pas encore surveillées. Le diagramme suivant est un exemple de catégories et de sujets pour une marque de meubles :

![Marque de meubles](/help/dashboards/assets/diagram-example.png)

#### Étape 4 — Générer des invites ancrées dans des mots-clés réels {#gsc-four}

Pour chaque sujet, le système génère des invites similaires à la façon dont les vraies personnes parlent avec les assistants d&#39;IA. Chaque invite est directement influencée par des mots-clés de recherche réels de votre console de recherche Google, transformant l’intention du mot-clé en questions conversationnelles naturelles.

Cette approche (fondée sur des mots-clés) signifie :

* Les invites reflètent une demande réelle, pas des questions hypothétiques.
* La langue reflète la manière dont vos clients formulent les choses.
* La couverture couvre tout ce que les gens recherchent sur votre site.

La génération d’invites prend également en compte votre profil de marque (y compris les produits, les concurrents, le positionnement du secteur et le public cible) pour s’assurer que les invites sont adaptées au contexte.

#### Etape 5 - Assurance qualité et diffusion {#gsc-five}

Avant la diffusion, chaque invite fait l’objet de plusieurs contrôles qualité automatisés :

* Déduplication : les invites quasi identiques sont supprimées.
* Équilibrage du ratio de marque — assure un mélange réaliste (~75 % sans marque, ~25 % avec marque).
* Qualité de la langue — supprime les phrases robotisées pour que le son soit naturel.
* Contrôles de cohérence — valide les dates, supprime les phrases de remplissage, assure une longueur concise.

En outre, chaque invite est balisée avec sa catégorie, son sujet, son type d’intention et sa classification de marque/sans marque, prête pour que LLM Optimizer puisse commencer la surveillance.

#### Invite Anatomy {#prompt-anatomy}

Une fois le processus ci-dessus terminé, chaque invite transmise à LLM Optimizer possède les attributs suivants :

| Champ | Description |
|---------|----------|
| Texte | L’invite, semblable à la façon dont un utilisateur la saisirait dans un assistant d’IA |
| Catégorie | Thème commercial général affecté à cette invite. |
| Rubrique | Sous-rubrique spécifique dans la catégorie. |
| Zone géographique | Le marché cible (par exemple, États-Unis, Royaume-Uni, etc.). |
| Intention | État d’esprit de l’utilisateur : informationnel, comparatif, transactionnel, didactique, planification ou délégation. |
| Type | Le type peut être de marque (mentionne la marque/les produits) ou sans marque (question générique du secteur). |

### Utilisation {#how-to-use}

Suivez les étapes présentées ci-dessous pour intégrer et utiliser les requêtes de la console de recherche Google avec LLM Optimizer.

#### Connexion à la console de recherche Google {#connect-console}

Avant d’utiliser cette fonctionnalité, vous devez intégrer votre compte Google Search Console à l’optimiseur LLM.

1. Ouvrez le tableau de bord de configuration du client.
1. Accédez à l’onglet Search Console de Google et cliquez sur **Connect Account**.
   ![Console de recherche Google](/help/dashboards/assets/google-console.png)
1. Connectez-vous avec un compte Google ayant accès à la propriété de Search Console souhaitée.
   ![Compte Google](/help/dashboards/assets/google-account.png)
1. Sélectionnez la propriété à connecter.
   ![Propriété de console](/help/dashboards/assets/console-property.png)
1. Une fois la connexion établie, LLM Optimizer commence à récupérer les requêtes de recherche pertinentes.
   ![Récupération des données](/help/dashboards/assets/console-complete.png)

#### Requêtes de révision et de recherche {#search-query}

Après avoir intégré le compte de la console de recherche Google à l’optimiseur LLM, vous pouvez consulter la liste des rubriques et des invites provenant de la console de recherche et ajouter les invites de la liste.

1. Dans l’onglet Search Console de Google, passez en revue la liste des rubriques et des invites provenant de la Search Console.
   ![Liste des invites](/help/dashboards/assets/prompts-list.png)
1. Cliquez sur la catégorie de rubrique/invite de votre choix pour développer la liste.
1. Utilisez le bouton **Ajouter** pour ajouter des invites de la liste. Vous pouvez également ajouter des invites et des catégories en bloc à l&#39;aide de **Ajouter tout**.
   ![Ajouter des invites](/help/dashboards/assets/add-prompts.png)
1. Une fois la sélection effectuée, cliquez sur **Enregistrer** dans le message de notification.

#### Afficher les requêtes ajoutées à la liste des invites {#prompts-list}

Une fois une requête ajoutée, elle apparaît dans l’onglet [Invites](#prompts-brand) du tableau de bord de la configuration client. Les invites provenant de la Search Console Google sont marquées d&#39;une icône de la Search Console Google dans la colonne **Origin**. L’icône vous permet de distinguer les invites basées sur le comportement réel de la recherche utilisateur de celles ajoutées manuellement ou d’autres sources.

### Questions fréquentes {#gsc-faq}

Q : À quelle fréquence les invites sont-elles mises à jour dans le tableau de bord de la console de recherche Google ?

Les invites provenant de la Search Console Google sont généralement actualisées une fois par mois. Chaque actualisation extrait les dernières données de requête de recherche de votre console de recherche Google, réexécute le pipeline de génération et met à jour votre ensemble d’invites. Cela garantit que vos invites restent alignées sur les tendances de recherche actuelles et les changements saisonniers du comportement des utilisateurs.

Q : Combien d’invites sont généralement sourcées depuis la console de recherche de Google ?

Le nombre dépend de la taille de votre déploiement et du nombre de catégories suivies. Par exemple :

| Catégories | Total des rubriques | Invites diffusées |
|---------|----------|----------|
| 1-2 | 3-8 | ~65-180 |
| 4-5 | 12-20 | ~270-450 |
| 10 | 30-40 | ~675-900 |

Notre objectif est de fournir des ensembles d’invites qui répondent aux objectifs de qualité communiqués lors de l’évaluation et de l’intégration : au moins 20 invites par sujet, avec 3 à 4 sujets par catégorie, et un équilibre sain entre les marques et les marques.

Q : Dans combien de temps les invites provenant de la Search Console Google apparaîtront-elles après ma connexion à la Search Console Google ?

Les invites sont généralement disponibles **en quelques heures** une fois la connexion à la console de recherche Google établie. Le pipeline extrait automatiquement vos données de recherche, les traite par le biais des étapes de génération et d’assurance qualité et diffuse l’invite finale définie sur LLM Optimizer.

Q : Qui peut se connecter à la console de recherche de Google ?

Toute personne disposant des droits **Propriétaire** ou **Autorisation complète** sur la propriété de la console de recherche Google peut autoriser la connexion. Il s’agit des niveaux d’autorisation qui accordent l’accès en lecture aux données de requête de recherche. Si vous n’êtes pas sûr de votre niveau d’autorisation, vous pouvez le vérifier sous **Paramètres>Utilisateurs** et autorisations dans votre console de recherche Google.

Q : Puis-je marquer les invites comme ignorées ou ignorées afin de ne pas les voir dans la liste des invites de la console de recherche Google ?

Oui, vous pouvez supprimer toute invite que vous ne souhaitez pas surveiller. Les invites supprimées sont supprimées de votre liste d&#39;invites active et n&#39;apparaîtront pas dans les rapports futurs. Si une invite supprimée est régénérée lors d’une actualisation mensuelle ultérieure, vous pouvez la supprimer à nouveau.

Q : Une fois que j’ajoute des invites de la console de recherche Google à ma liste d’invites, combien de temps vais-je voir les données de Présence des marques pour ces invites ?

Les données de présence des marques des nouvelles invites ajoutées apparaîtront lors de la prochaine actualisation planifiée des données, qui s&#39;exécute généralement au début de chaque semaine. Selon le moment où vous ajoutez les invites, vous pouvez voir les résultats sous quelques jours.
