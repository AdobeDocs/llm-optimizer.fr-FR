---
title: Configuration cliente
description: Utilisez la configuration cliente pour définir comment votre marque sera surveillée et analysée sur la plateforme LLM Optimizer.
feature: Customer Configuration
autotag-review: '2026-05-15T17:45:12.067Z'
TQID: 'https://experienceleague.adobe.com/qa7zk54n9G19-Azz9f6mn7V1kAGvnJSOJjpxbTBeHgc'
product_v2:
  - id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2:
  - id: a0b5a505-2fd7-4c3d-b61c-b557fb6f0558
  - id: d1956731-2adb-4bb7-8301-2b239254ac72
subfeature_v2:
  - id: e69d5a42-0217-4ca5-9396-a9a826a170da
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 564171851fdccee43afd233da143d66182464889
workflow-type: tm+mt
source-wordcount: 2249
ht-degree: 100%

---


# Configuration cliente {#customer-configuration}

Le tableau de bord de la configuration cliente est un outil puissant qui fournit des informations sur la visibilité de votre marque dans les LLM. En configurant correctement des catégories, des rubriques et des prompts, vous pouvez vous assurer que votre marque est bien positionnée pour apparaître dans les réponses générées par les LLM. Cette configuration garantit que la plateforme adapte les informations à votre contexte commercial, ce qui permet une visibilité, un trafic et une analyse des opportunités précis.

Le tableau de bord de configuration cliente (illustré ci-dessous) s’applique lorsque votre organisation utilise toujours cette navigation.

![Tableau de bord de la configuration cliente](/help/dashboards/assets/customer-config.png)

Pour configurer la manière dont LLM Optimizer surveille et analyse la présence de votre marque sur différents marchés et paysages concurrentiels, vous avez accès aux onglets suivants :

* [Prompts](#prompts-brand)
* [Catégories](#categories)
* [Autres marques](#other-brands)
* [Alias de marque](#brand-aliases)
* [Configuration du CDN](#agentic-cdn)
* [Google Search Console](#google-console)

Si vous utilisez l’[expérience orientée marque](/help/overview/quick-start.md#brand-centric-experience), accédez à **Gestion des marques** pour configurer les marques et les alias de marque, puis définissez les concurrents par rapport auxquels effectuer un suivi. **Gestion des marques** est également utilisé pour configurer des intégrations telles que Google Search Console, Adobe Analytics et le transfert du journal CDN, liées aux URL associées aux marques. Pour cela, cliquez sur les onglets correspondants : GSC, CDN, etc.

![Gestion des marques : navigation dans l’application (expérience orientée marque)](/help/assets/brand-centric-experience/llmo-app-shell.png)

![Gestion des marques : vue d’ensemble de la configuration (expérience orientée marque)](/help/assets/brand-centric-experience/brands-management-configuration.png)

>[!IMPORTANT]
>
> Pour plus d’informations sur la configuration des catégories, rubriques et prompts, reportez-vous à la page [Bonnes pratiques pour la configuration des catégories, rubriques, prompts](/help/overview/best-practices-topics-prompts.md).

## Prompts {#prompts-brand}

L’onglet **Prompts** permet de vérifier, gérer et personnaliser les prompts. Vous pouvez charger un fichier CSV [Analyse de présence de la marque](/help/dashboards/brand-presence.md) et la liste sera remplie avec les prompts et les rubriques de cette analyse ou [télécharger une bibliothèque de prompts](/help/overview/best-practices-topics-prompts.md) créée par Adobe. Vous pouvez également supprimer, modifier et ajouter des rubriques et leurs prompts associés selon vos besoins.

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

Pour les clientes et clients qui utilisent l’[expérience orientée marque](/help/overview/quick-start.md#brand-centric-experience), pour ajouter des rubriques et des prompts, accédez à **Gestion des prompts**.

![Gestion des prompts (expérience orientée marque)](/help/assets/brand-centric-experience/prompts-management.png)

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

Pour supprimer un alias de marque, cliquez sur l’icône de **suppression** dans la liste des alias.

## Configuration du CDN {#cdn-configuration}

Dans cet onglet, vous pouvez configurer vos flux CDN pour permettre à Adobe LLM Optimizer d’analyser vos données CDN. Ces données seront utilisées pour alimenter les tableaux de bord (comme le trafic généré par l’IA agentique), fournissant des informations sur les modèles de trafic, les mesures de performances et les opportunités d’optimisation. Pour intégrer votre fournisseur de CDN, cliquez sur **Intégrer le CDN**.

![Configuration cliente du CDN](/help/overview/assets/cc-cdn.png)

Dans la fenêtre **Intégrer le fournisseur du CDN** :

1. Sélectionnez votre fournisseur de CDN.
2. Cliquez sur **Intégration** pour activer le transfert des journaux.

Si vous sélectionnez **Autre**, vous devrez contacter llmo-now@adobe.com pour obtenir de l’aide.

## Google Search Console {#google-console}

Adobe LLM Optimizer vous permet d’intégrer votre compte Google Search Console pour importer des requêtes de recherche réelles directement dans l’interface. En affichant les requêtes réelles de la Google Search Console, vous pouvez créer des jeux de prompts basés sur le comportement réel de la recherche et les modèles de découverte à haute intention. Cela vous permet de hiérarchiser les prompts en fonction de la demande éprouvée et d’aligner les efforts d’optimisation LLM sur la manière dont les recherches sont effectuées. De plus, vous conservez le contrôle total, car les requêtes ne sont jamais ajoutées automatiquement et doivent être explicitement sélectionnées avant de devenir des prompts actifs.

### Fonctionnement {#how-it-works}

La principale chose à retenir à propos de l’intégration entre LLM Optimizer et la Google Search Console est la suivante : au lieu de deviner manuellement ce que la clientèle pourrait demander à un assistant d’IA, nous regardons ce qu’elle **recherche déjà** et transformons ces requêtes réelles en prompts conversationnels naturels. Ce processus de transfert des requêtes de recherche vers les prompts d’IA est illustré dans le diagramme ci-dessous.

![Flux de processus](/help/dashboards/assets/diagram-flow.png)

En général, le processus comporte cinq étapes :

#### Étape 1 — Collecter vos données de recherche réelles {#gsc-one}

Le processus commence par les mots-clés que votre audience utilise réellement lorsqu’elle trouve votre site web via Google. Ce jeu de données brut (souvent des milliers de requêtes uniques) est la base de tout ce qui suit.

#### Étape 2 — Analyser la signification et filtrer pour la sécurité {#gsc-two}

Chaque requête est analysée pour sa signification sémantique (ce sur quoi la personne interroge réellement) et filtrée à l’aide d’un filtre de sécurité qui supprime le contenu inapproprié ou hors marque. Ainsi, seuls les mots-clés propres et pertinents sont conservés.

#### Étape 3 — Regrouper en catégories et rubriques {#gsc-three}

Les requêtes associées sont automatiquement regroupées en **catégories** (thèmes commerciaux généraux) et **rubriques** (sous-rubriques ciblées dans chaque catégorie). Le système donne la priorité aux catégories déjà configurées dans votre configuration de LLM Optimizer. De plus, il peut également faire émerger de nouvelles catégories révélées par vos données de recherche, mais non encore surveillées. Le diagramme suivant donne un exemple de catégories et de thèmes pour une marque de meubles :

![Marque de meubles](/help/dashboards/assets/diagram-example.png)

#### Étape 4 — Générer des prompts basés sur de vrais mots-clés {#gsc-four}

Pour chaque rubrique, le système génère des prompts imitant la façon dont les gens parlent aux assistants IA. Chaque prompt est directement influencé par les mots clés de recherche réels de votre Google Search Console, transformant ainsi l’intention de recherche en questions conversationnelles naturelles.

Cette approche (fondée sur des mots-clés) signifie que :

* Les questions posées reflètent une demande réelle, et non des questions hypothétiques.
* Le langage utilisé reflète la façon dont votre clientèle s’exprime réellement.
* La couverture englobe toute la gamme des recherches effectuées par les internautes sur votre site.

La génération des prompts tient également compte de votre profil de marque — y compris vos produits, vos concurrents, votre positionnement dans l’industrie et votre public cible — afin de garantir des prompts contextuellement précis.

#### Étape 5 — Assurance qualité et livraison {#gsc-five}

Avant la livraison, chaque message fait l’objet de plusieurs contrôles de qualité automatisés :

* Déduplication : les prompts quasi identiques sont supprimés.
* Équilibrage des ratios de marques : assure un mélange réaliste (~75 % sans marque, ~25 % de marque).
* Qualité du langage : élimine les formulations robotiques pour que les messages sonnent naturels.
* Contrôles de cohérence : valide les dates, supprime les phrases superflues, garantit une longueur concise.

De plus, chaque prompt est étiqueté selon sa catégorie, sa rubrique, son type d’intention et sa classification (avec ou sans marque), pour que LLM Optimizer puisse commencer la surveillance.

#### Anatomie des prompts {#prompt-anatomy}

Une fois le processus ci-dessus terminé, chaque prompt transmis à LLM Optimizer possède les attributs suivants :

| Champ | Description |
|---------|----------|
| Texte | Le prompt est similaire à la manière dont une personne le saisirait dans un assistant IA. |
| Catégorie | Le thème commercial général associé à ce prompt. |
| Rubrique | Le sous-thème spécifique au sein de la catégorie. |
| Zone géographique | Le marché cible (par exemple, les États-Unis, le Royaume-Uni, etc.). |
| Intention | L’état d’esprit de la personne : informationnel, comparatif, transactionnel, instructionnel, de planification ou de délégation. |
| Type | Le type peut être de marque (mentionne la marque/les produits) ou sans marque (question générique du secteur). |

### Utilisation {#how-to-use}

Suivez les étapes présentées ci-dessous pour intégrer et utiliser les requêtes de la Google Search Console à LLM Optimizer.

#### Connecter la Google Search Console {#connect-console}

Avant d’utiliser cette fonctionnalité, vous devez intégrer votre compte Google Search Console à l’optimiseur LLM.

1. Ouvrez le tableau de bord de **Configuration cliente** (navigation classique) ou **Gestion des marques** (expérience orientée marque), puis accédez à l’intégration de la Google Search Console (balise GSC dans l’expérience orientée marque).
1. Accédez à l’onglet Google Search Console et cliquez sur **Connecter le compte**.
   ![Google Search Console](/help/dashboards/assets/google-console.png)
1. Connectez-vous avec un compte Google ayant accès à la propriété Search Console souhaitée.
   ![Compte Google](/help/dashboards/assets/google-account.png)
1. Sélectionnez la propriété à connecter.
   ![Propriété de la console](/help/dashboards/assets/console-property.png)
1. Une fois la connexion établie, LLM Optimizer commence à récupérer les requêtes de recherche pertinentes.
   ![Récupération des données d’utilisation](/help/dashboards/assets/console-complete.png)

#### Requêtes d’avis et de recherche {#search-query}

Après avoir intégré le compte de la Google Search Console à LLM Optimizer, vous pouvez consulter la liste des rubriques et des prompts provenant de la console de recherche et ajouter les prompts de la liste.

1. Dans l’onglet Google Search Console, passez en revue la liste des rubriques et des prompts provenant de la Search Console.
   ![Liste des prompts](/help/dashboards/assets/prompts-list.png)
1. Cliquez sur la catégorie de rubrique/prompt de votre choix pour développer la liste.
1. Utilisez le bouton **Ajouter** pour ajouter des prompts à la liste. Vous pouvez également ajouter des prompts et des catégories en bloc à l’aide de **Ajouter tout**.
   ![Ajouter des prompts](/help/dashboards/assets/add-prompts.png)
1. Une fois la sélection effectuée, cliquez sur **Enregistrer** dans le message de notification.

#### Afficher les requêtes ajoutées à la liste des prompts {#prompts-list}

Une fois une requête ajoutée, elle apparaît dans l’onglet [Prompts](#prompts-brand) du tableau de bord Configuration cliente (navigation classique) ou dans **Gestion des prompts** (expérience orientée marque). Les prompts provenant de la Google Search Console sont marqués d’une icône dans la colonne **Origine**. L’icône distingue entre les prompts basés sur le comportement réel de la recherche de ceux ajoutés manuellement ou par d’autres sources.

### Questions fréquentes {#gsc-faq}

Q : À quelle fréquence les prompts sont-elles mises à jour dans le tableau de bord de la Google Search Console ?

Les prompts provenant de la Google Search Console sont généralement actualisés une fois par mois. Chaque actualisation extrait les dernières données de requête de recherche de votre Google Search Console, réexécute le pipeline de génération et met à jour votre ensemble de prompts. Cela garantit que vos prompts restent alignés sur les tendances de recherche actuelles et les changements saisonniers du comportement des utilisateurs et utilisatrices.

Q : Combien de prompts sont généralement sourcés depuis la Google Search Console ?

Le nombre dépend de la taille de votre déploiement et du nombre de catégories suivies. Par exemple :

| Catégories | Total des rubriques | Prompts diffusés |
|---------|----------|----------|
| 1-2 | 3-8 | ~65-180 |
| 4-5 | 12-20 | ~270-450 |
| 10 | 30-40 | ~675-900 |

Notre objectif est de fournir des ensembles de prompts qui répondent aux objectifs de qualité communiqués lors de l’évaluation et de l’intégration : au moins 20 prompts par rubrique, avec 3 à 4 rubriques par catégorie, et un équilibre sain entre marques/sans marques.

Q : Dans combien de temps les prompts provenant de la Google Search Console apparaîtront-ils après ma connexion à la Google Search Console ?

Les prompts sont généralement disponibles **en quelques heures** une fois la connexion à la Google Search Console établie. Le pipeline extrait automatiquement vos données de recherche, les traite par le biais des étapes de génération et d’assurance qualité et diffuse le prompt final défini sur LLM Optimizer.

Q : Qui peut se connecter à la Google Search Console ?

Toute personne disposant des droits **Propriétaire** ou **Autorisation complète** sur la propriété de la Google Search Console peut autoriser la connexion. Il s’agit des niveaux d’autorisation qui accordent l’accès en lecture aux données de requête. Si vous ne connaissez pas votre niveau d’autorisation, vous pouvez le vérifier sous **Paramètres >Utilisateurs, utilisatrices** et autorisations dans votre Google Search Console.

Q : Puis-je marquer des prompts comme ignorés ou ignorer certains prompts afin qu’ils n’apparaissent plus dans la liste des prompts de Google Search Console ?

Oui, vous pouvez supprimer tout prompt que vous ne souhaitez pas surveiller. Les prompts supprimés sont supprimés de votre liste de prompts active et n’apparaîtront pas dans les futurs rapports. Si un prompt supprimé est régénéré lors d’une actualisation mensuelle ultérieure, vous pouvez le supprimer à nouveau.

Q : Une fois que j’ajoute des prompts de la Google Search Console à ma liste de prompts, combien de temps vais-je voir les données de présence de la marque pour ces prompts ?

Les données de présence de la marque des nouveaux prompts ajoutés apparaîtront lors de la prochaine actualisation planifiée des données, qui s’exécute généralement au début de chaque semaine. Selon le moment où vous ajoutez les prompts, les résultats s’affichent sous quelques jours.
