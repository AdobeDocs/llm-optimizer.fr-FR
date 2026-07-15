---
title: Configuration cliente
description: Utilisez la configuration cliente pour définir comment votre marque sera surveillée et analysée sur la plateforme LLM Optimizer.
feature: Customer Configuration
autotag-review: '2026-07-15T17:48:20.742Z'
TQID: 'https://experienceleague.adobe.com/BvaFF-pMzojy1TNZvCQQRbcT5c5AQ75OqjclmDi14Z0'
product_v2: id: d830747e-f8f3-4fce-8eff-d53b333b1639
feature_v2: id: c898dfb2-0885-42fb-b2af-b2d756752646id: d1956731-2adb-4bb7-8301-2b239254ac72id: e1b649f0-0a61-46e4-9082-64d5cb2576c6
subfeature_v2: id: e69d5a42-0217-4ca5-9396-a9a826a170da
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: e1e0219c-f879-479f-8427-888ed2a6e9c2id: eddd9b14-83bd-4ff4-9072-54a4a484abb7id: fc314d1d-7cb9-4a38-8dbd-8f9b6478f40d
source-git-commit: 2705cf26faea9c09817bbdcec4b4c531552df7ba
workflow-type: tm+mt
source-wordcount: 3935
ht-degree: 57%

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
* [Suggestions rapides basées sur les tentatives de citation et le Trafic de recommandation](#prompt-suggestions)

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

## Suggestions rapides basées sur les tentatives de citation et le Trafic de recommandation {#prompt-suggestions}

Au lieu de deviner les invites importantes, **Suggestions d’invite** commencez par savoir à quoi les agents et les utilisateurs de l’IA accèdent déjà ou auxquels il est fait référence sur votre site.

Adobe LLM Optimizer analyse les données de votre réseau CDN pour identifier les pages auxquelles les agents de l’IA accèdent déjà de manière cohérente (tentatives de citation) et les utilisateurs qui y font référence (trafic de recommandation LLM). Ensuite, il génère automatiquement des suggestions rapides en fonction des lacunes de votre couverture rapide actuelle. Au lieu de deviner les URL à prioriser et les invites à créer, le workflow commence par de vrais signaux de trafic : les pages que les agents atteignent déjà et la définition du type d&#39;utilisateur qui invite ces pages doit répondre.

Lorsqu’une page est déjà accessible de manière cohérente par les agents d’IA, la question n’est pas de savoir comment les agents doivent la connaître, mais à quelles questions le contenu de la page peut répondre. Sans invites configurées pour ces pages, vous n&#39;avez aucune visibilité sur la façon dont votre marque apparaît dans les réponses d&#39;IA sur les sujets qui comptent le plus. L’invite de suggestions du trafic d’agents comble cet écart afin que vous puissiez commencer à effectuer le suivi et à améliorer la visibilité des marques des pages sur lesquelles les agents sont déjà les plus actifs.

>[!NOTE]
>
> Dans l’[expérience centrée sur la marque](/help/overview/quick-start.md#brand-centric-experience), des suggestions d’invites sont affichées dans la section **Gestion des invites**.

### Fonctionnement {#prompt-suggestions-how-it-works}

Le workflow d’invite de suggestions s’exécute en quatre étapes, transformant les signaux de trafic CDN en suggestions d’invite prêtes à être configurées. Chaque étape s’appuie sur la précédente : en commençant par les pages où l’activité de l’agent d’IA est déjà éprouvée, en comprenant de quoi il s’agit, en vérifiant ce qui est déjà couvert et en générant des invites spécifiques, ancrées et prêtes à être publiées.

![Suggestions d’invite du workflow de trafic d’agent](/help/dashboards/assets/prompt-suggestions-workflow.png)

#### Étape 1 — Identification des pages à signal élevé à partir du trafic agentic {#prompt-suggestions-step-1}

Le pipeline commence par identifier les pages de votre site sur lesquelles les systèmes d’IA interagissent déjà activement, à l’aide de deux signaux provenant de vos données CDN : la fréquence à laquelle les systèmes d’IA accèdent à vos pages en tant que source tout en répondant à des questions réelles des utilisateurs et utilisatrices, et le fait de savoir si ces pages orientent déjà des utilisateurs et utilisatrices réels vers votre site à partir de réponses générées par l’IA.

* **Tentatives de citation** — comment les systèmes d’IA ont accédé à une page en tant que source potentielle tout en répondant aux questions des utilisateurs. Le pipeline recherche les pages qui affichent une activité de tentative de citation cohérente semaine après semaine, ce qui donne une vue d’ensemble plus globale de l’intérêt que la situation à un seul moment.
* trafic de recommandation LLM **: instances dans lesquelles un utilisateur a cliqué à partir d’une réponse générée par l’IA pour accéder à l’URL.** Le pipeline se concentre sur les données de référence les plus récentes et donne la priorité aux pages avec le plus grand volume de visites pilotées par l’IA, en s’assurant que les suggestions sont fondées sur les modèles de recommandation actuels et éprouvés de l’IA.

| Signal | Signification |
|--------|---------------|
| Tentatives de citation uniquement | Les agents accèdent constamment à cette page en tant que source potentielle |
| TRAFIC DE RECOMMANDATION LLM uniquement | Les agents envoient activement des utilisateurs à cette page |
| Les deux | Les agents y accèdent et les utilisateurs cliquent dessus : la cible la plus fiable |

Une page peut être qualifiée par l’un ou l’autre des signaux, ou les deux. Les pages affichant les deux signaux représentent les cibles avec le degré de confiance le plus élevé pour la génération rapide.

#### Etape 2 — Analyser le contenu et l&#39;intention de la page {#prompt-suggestions-step-2}

Pour chaque page de qualification, le pipeline lit le contenu de la page et :

* **Résume** le tout sous la forme d’une description concise et fondée sur des faits, qui devient la base de tout ce qui suit.
* **Classe** type de page : produit, ressource, support ou hub.
* Indique l’**intention principale du parcours** — le type de question à laquelle la page est la mieux placée pour répondre, par exemple de type informatif, didactique, comparatif ou transactionnel.

Les deux classifications fonctionnent ensemble. Par exemple, les invites générées à partir d&#39;une page d&#39;assistance, telles qu&#39;un guide de configuration ou un tutoriel, sont plus susceptibles d&#39;être pertinentes pour un utilisateur existant que pour une nouvelle audience.

#### Étape 3 — Vérifier la couverture d&#39;invite existante {#prompt-suggestions-step-3}

Avant de générer de nouveaux éléments, le pipeline vérifie que chaque page de qualification est déjà couverte par des invites configurées dans votre compte LLM Optimizer, qui s’exécutent en deux étapes :

1. Analyse de similarité sémantique qui identifie rapidement les invites candidates de votre bibliothèque d&#39;invites existantes potentiellement liées à la page.
2. Une révision optimisée par LLM qui évalue dans quelle mesure chaque invite candidate correspond au contenu de la page, non seulement s’il est lié au sujet, mais s’il couvre le sujet de la page.

Une page est considérée comme couverte si au moins une invite existante atteint ce seuil. Les pages sans correspondance adéquate sont identifiées comme des lacunes et passent à l’étape 4.

#### Étape 4 : générer, vérifier la qualité et classer les invites par URL {#prompt-suggestions-step-4}

![Génération d’invites et contrôle qualité](/help/dashboards/assets/prompt-suggestions-generation.png)

Pour chaque page d’espace, le pipeline génère des invites à son naturel basées sur le contenu de la page. Il commence par identifier les personnes pertinentes, c’est-à-dire quelqu’un qui poserait de manière réaliste les questions auxquelles cette page répond et construirait un scénario réaliste autour de cette personne avant de générer des invites de candidat.

Chaque invite fait l’objet d’un examen de qualité automatisé dans trois dimensions :

* S’il est **spécifique** à cette page plutôt qu’à une question générique qui peut s’appliquer à n’importe quelle page de la catégorie.
* Si elle est **ancrée** dans le contenu réel de la page.
* Si cela ressemble à quelque chose qu’un **utilisateur réel** saisirait dans un outil d’IA tel que ChatGPT.

Les invites qui ne réussissent pas cette révision sont réécrites avec des commentaires spécifiques et réexaminées. S&#39;ils ne sont toujours pas adoptés, ils sont abandonnés.

La dernière étape consiste en une vérification de la diversité. Les invites à travers les URL trop similaires les unes aux autres sont supprimées de la liste finale. Chaque invite est balisée avec votre rubrique et votre catégorie préconfigurées et inclut un champ de raisonnement qui explique pourquoi l’URL source a été ciblée en fonction de sa tentative de citation et de ses signaux de trafic de recommandation. Un classement de priorité est également attribué aux invites afin que vous sachiez sur quelles suggestions agir en premier. Une priorité plus élevée signifie un signal d&#39;IA combiné plus fort provenant de l&#39;URL source. Les invites sont alors prêtes à être consultées sous l&#39;onglet **Suggestions d&#39;invite** dans le tableau de bord de la configuration du client.

### Utilisation {#prompt-suggestions-how-to-use}

1. Ouvrez le tableau de bord **Configuration du client** et accédez à l’onglet **Demander des suggestions**.
1. Utilisez le filtre **** pour sélectionner **Tentative de citation** afin d&#39;afficher les suggestions générées à partir du trafic d&#39;agent.
1. Examinez les colonnes **Raisonnement** et **Priorité** pour évaluer chaque suggestion.
1. Sélectionnez les invites à ajouter et cliquez sur **Ajouter une sélection** pour les ajouter à vos invites configurées.

![Onglet Suggestions d’invite avec filtre source Tentative de citation](/help/dashboards/assets/prompt-suggestions-citation-attempt.png)

![Ajouter les suggestions d&#39;invite sélectionnées](/help/dashboards/assets/prompt-suggestions-add-selection.png)

### Questions fréquentes {#prompt-suggestions-faq}

Q : Mon organisation a-t-elle besoin d’une configuration supplémentaire pour utiliser cette fonctionnalité ?

Cette fonctionnalité repose sur les données du journal du réseau CDN. Si vous avez déjà activé le [transfert de journal CDN](#cdn-configuration), aucune configuration supplémentaire n’est nécessaire. Sans les journaux CDN, les données de tentative de citation ou de trafic de recommandation ne seront pas disponibles pour analyse.

Q : Pourquoi une URL spécifique ne s’affiche-t-elle pas dans les suggestions ?

Il y a quelques raisons courantes. La page peut ne pas encore avoir d’activité de récupération d’IA cohérente ou de trafic de recommandation significatif ; sans l’un de ces signaux, elle n’entre pas dans le pipeline. Elle peut déjà être couverte par une invite configurée existante, car le pipeline ne génère que des suggestions pour de véritables écarts. Ou le type de page peut ne pas être éligible pour la génération d’invites.

Q : Les suggestions peuvent-elles changer au fil du temps ?

Oui. Le pipeline s’exécute régulièrement à mesure que de nouvelles données CDN sont disponibles. À mesure que le comportement des utilisateurs et des agents évolue (quelles pages sont consultées, à quelle fréquence et lesquelles génèrent du trafic de recommandation), les suggestions reflètent ces modifications. Les pages qui n’étaient pas très performantes auparavant peuvent être incluses dans les prochaines exécutions. Les lacunes existantes qui ont été corrigées ne généreront plus de nouvelles suggestions.

Q : Pourquoi est-ce que je vois des URL auxquelles je ne m’attendais pas dans les suggestions ?

Les URL affichées sont entièrement basées sur le comportement agent observé (des pages auxquelles les systèmes d’IA ont systématiquement accédé ou auxquelles ils ont référencé des utilisateurs et utilisatrices, quelle que soit la place qu’elles occupent dans votre stratégie de contenu). Dans certains cas, il peut s’agir de pages que vous n’avez jamais considérées comme importantes, mais que l’IA a consultées à plusieurs reprises. Si une URL apparaît dans les suggestions, c’est parce que les données la prennent en charge. Vous êtes toujours libre d’ignorer les suggestions qui ne correspondent pas à votre stratégie, mais les données sous-jacentes à chaque suggestion sont basées sur une véritable activité d’IA.

Q : Que signifie le champ de raisonnement ?

Chaque invite comprend une explication de la raison pour laquelle son URL source a été répertoriée comme suggestion. Pour les pages qualifiées par des tentatives de citation, cela indique comment la page se classe parmi toutes les pages accessibles en fonction des tentatives hebdomadaires. Pour les pages qualifiées par trafic de recommandation, il en va de même pour les pages vues de référence. Les pages contenant les deux signaux affichent les deux. Cela vous permet de comprendre la priorité et de choisir les suggestions à publier en premier.

Pour une page contenant les deux signaux, le raisonnement peut ressembler à ceci : *Généré pour [URL de la page] — se classe dans le top 3 % par tentative de citation hebdomadaire médiane et dans le top 1 % par trafic de recommandation LLM.*

Q : Comment la priorité est-elle déterminée ?

La priorité est basée sur un score combiné de deux signaux : comment une page se classe parmi toutes les pages par tentatives de citation et comment elle se classe parmi toutes les pages par pages vues de référence LLM. Les deux sont exprimées en centiles et additionnées, de sorte que les pages qui obtiennent de bons scores sur les deux signaux se hissent naturellement en haut. Une page à laquelle l’IA accède de manière cohérente et vers laquelle elle envoie activement des utilisateurs sera toujours mieux classée qu’une page ne comportant qu’un seul signal.

Q : Comment le pipeline décide-t-il quelles pages sont qualifiées en fonction des tentatives de citation ?

Le pipeline recherche les pages qui affichent une activité de récupération de l’IA cohérente au fil du temps. Pour être admissible, une page doit remplir deux conditions : elle doit montrer une activité significative dans au moins la moitié des semaines dans les données disponibles et son nombre médian d’accès authentiques au cours de ces semaines actives doit se classer dans les 25 % supérieurs sur toutes les pages. Les deux conditions doivent tenir — la fréquence seule ne suffit pas et le volume des accès seul ne suffit pas non plus.

Q : Comment le pipeline décide-t-il quelles pages sont qualifiées en fonction du trafic de recommandation ?

Une page se qualifie si elle apparaît dans les 10 % supérieurs de toutes les pages par nombre total de visites de référence LLM au cours des trois derniers mois. Cela permet de s’assurer que les suggestions sont fondées sur des pages qui génèrent déjà des clics publicitaires réels et mesurables à partir des réponses de l’IA, en fonction du comportement récent.

Q : Des suggestions rapides sont-elles disponibles dans d&#39;autres langues que l&#39;anglais ?

Pas encore. Le pipeline génère actuellement des invites en anglais uniquement. La prise en charge multilingue sera ajoutée dans une version ultérieure.
