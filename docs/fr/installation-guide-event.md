# COVID-19 Guide d'installation des paquets Evénements v0.3.2

<ul style="text-align: right">
  <li style="list-style: none">Dernière mise à jour 27/03/2020</li>
  <li style="list-style: none">Version du paquet 0.3.2</li>
  <li style="list-style: none">Compatibilité de la version DHIS2 2.33.2</li>
  <li style="list-style: none">Démo: <a href="https://covid.dhis2.org/">https://covid.dhis2.org/</a></li>
</ul>

## Aperçu

Le paquet d'événements COVID-19 a été développé en utilisant le DHIS2.33.2. L'objectif est de prendre en charge certaines des dernières fonctionnalités de DHIS2. Pour pouvoir utiliser le paquet, il est recommandé de l'installer dans une instance de DHIS2 utilisant DHIS2 2.33.2 ou supérieur. Si vous souhaitez l'installer sur une nouvelle instance, veuillez consulter le [guide d'installation de DHIS2] (https://docs.dhis2.org/master/en/dhis2_system_administration_guide/installation.html).


## Installation

L'installation du module se fait en plusieurs étapes :

1. [Préparer](#preparing-the-metadata-file) le fichier de métadonnées avec les métadonnées de DHIS2.
2. [Importer](#importing-metadata) le fichier de métadonnées DHIS2.
3. [Configurer](#configuration-additionnelle) les métadonnées importées.
4. [Adapter](#adapting-the-event-program) le programme après son importation

Il est recommandé de lire d'abord chaque section avant de commencer le processus d'installation et de configuration dans le DHIS2. Les sections non applicables ont été identifiées, selon que vous importiez dans une nouvelle instance de DHIS2 ou dans une instance de DHIS2 ayant déjà des métadonnées. La procédure décrite dans le présent document doit être testée dans un environnement de test et de simulation avant d'être répétée ou transférée dans une instance de production du système de DHIS2.

## Conditions requises

Pour installer le module, il faut nécessairement un compte d'utilisateur administrateur sur DHIS2. La procédure décrite dans le présent document doit être testée dans un environnement de test et de simulation avant d'être exécutée sur une instance de production du DHIS2.

Il convient de veiller à ce que le serveur lui-même et l'application DHIS2 soient bien sécurisés, afin de limiter l'accès aux données collectées. Les détails relatifs à la sécurisation d'un système DHIS2 ne sont pas abordés dans le présent document, et nous renvoyons donc à la [documentation DHIS2] (http://dhis2.org/documentation).

## Préparation du fichier de métadonnées

**N.B.** : Si vous installez le paquet sur une nouvelle instance de DHIS2, vous pouvez alors ignorer la section "Préparation du fichier de métadonnées" et passer immédiatement à la section "[Importer un fichier de métadonnées dans DHIS2](#importing-metadata)".

Bien que ce ne soit pas toujours nécessaire, il peut souvent être avantageux d'apporter certaines modifications au fichier de métadonnées avant son importation dans DHIS2.

### Dimension de données par défaut

Dans les premières versions du DHIS2, l'UID de la dimension des données par défaut était généré automatiquement. Ainsi, alors que toutes les instances du DHIS2 ont une option de catégorie par défaut, une catégorie d'élément de données, une combinaison de catégories et une combinaison d'options de catégories, les UID de ces valeurs par défaut peuvent être différents. Les versions ultérieures du DHIS2 ont des UID codés en dur pour la dimension par défaut, et ces UID sont utilisés dans les paquets de configuration.

Pour éviter les conflits lors de l'importation des métadonnées, il est conseillé de rechercher et de remplacer l'ensemble du fichier .json pour toutes les occurrences de ces objets par défaut, en remplaçant les UID du fichier .json par les UID de la base de données dans laquelle le fichier sera importé. Le tableau 1 indique les UID qui doivent être remplacés, ainsi que les point d'extrémité de l'API pour l'identification des UID existants.


<table style="margin-bottom:1em">
  <tr>
   <td>Objet
   </td>
   <td>UID
   </td>
   <td>Point d'extrémité de l'AP
   </td>
  </tr>
  <tr>
   <td>Catégorie
   </td>
   <td>GLevLNI9wkl
   </td>
   <td>../api/categories.json?filter=name:eq:default
   </td>
  </tr>
  <tr>
   <td>Option de catégorie
   </td>
   <td>xYerKDKCefk
   </td>
   <td>../api/categoryOptions.json?filter=name:eq:default
   </td>
  </tr>
  <tr>
   <td>Combinaison de catégories
   </td>
   <td>bjDvmb4bfuf
   </td>
   <td>../api/categoryCombos.json?filter=name:eq:default
   </td>
  </tr>
  <tr>
   <td>Combinaison d'options de catégories
   </td>
   <td>HllvX50cXC0
   </td>
   <td>../api/categoryOptionCombos.json?filter=name:eq:default
   </td>
  </tr>
</table>


Par exemple, si vous importez un progiciel de configuration dans [https://play.dhis2.org/demo](https://play.dhis2.org/demo), l'UID de la combinaison d'options de catégorie par défaut peut être identifié via [https://play.dhis2.org/demo/api/categoryOptionCombos.json?filter=name:eq:default](https://play.dhis2.org/demo/api/categoryOptionCombos.json?filter=name:eq:default) comme `bRowv6yZOF2`.

Vous pourriez alors rechercher et remplacer toutes les occurrences de `HllvX50cXC0` par `bRowv6yZOF2` dans le fichier .json, puisque c'est l'ID par défaut du système dans lequel vous importez. ***Notez que cette opération de recherche et de remplacement doit être effectuée avec un éditeur de texte brut***, et non avec un logiciel de traitement de textes comme Microsoft Word.

### Types d'indicateurs

Le type d'indicateur est un autre type d'objet pouvant créer un conflit d'importation puisque certains noms sont utilisés dans différentes bases de données de DHIS2 ("Pourcentage", par exemple). Étant donné que les types d'indicateurs sont définis simplement par leur facteur et par le fait qu'il s'agisse ou non de simples nombres sans dénominateur, ils sont sans aucune ambiguïté et peuvent être remplacés par une recherche et un remplacement des UID. Cela permet d'éviter d'éventuels conflits d'importation et de ne pas créer de types d'indicateurs dupliqués. Le tableau 2 montre les UID qui pourraient être remplacés, ainsi que les points d'extrémité de l'API pour identifier les UID existants

<table style="margin-bottom:1em">
  <tr>
   <td>Objet
   </td>
   <td>UID
   </td>
   <td>Point d'extrémité de l'AP
   </td>
  </tr>
  <tr>
   <td>Pourcentage
   </td>
   <td>DadSzqgyAex
   </td>
   <td>../api/indicatorTypes.json?filter=number:eq:false&filter=factor:eq:100
   </td>
  </tr>
</table>

## Importation de métadonnées

Le fichier de métadonnées .json est importé via l'application [Importer/Exporter](https://docs.dhis2.org/master/en/user/html/import_export.html) de DHIS2. Il est conseillé d'utiliser la fonction "test" pour identifier les problèmes avant d'effectuer une importation réelle des métadonnées. Si le "test" signale des problèmes ou des conflits, voir la section [importer des conflits] (#manipulation-importation-de-conflits) ci-dessous.

Si l'importation "d'essai"/"de validation fonctionne sans erreur, essayez d'importer les métadonnées. Si l'importation réussit sans aucune erreur, vous pouvez alors passer à la [configuration](#configuration-additionnelle) du module. Dans certains cas, les conflits ou les problèmes d'importation ne sont pas affichés pendant le "test", mais apparaissent lorsque l'on tente l'importation proprement dite. Dans ce cas, le résumé de l'importation énumère les erreurs à résoudre.

### Gestion des conflits d'importation

**N.B.** : Si vous importez dans une nouvelle instance DHIS2, vous n'aurez pas à vous soucier des conflits d'importation, car il n'y a rien dans la base de données que vous importez qui puisse entrer en conflit avec celle-ci. Suivez les instructions pour importer les métadonnées, puis passez à la section "[Configuration supplémentaire](#configuration-supplémentaire)".

Plusieurs de conflits peuvent survenir, mais le plus courant est le fait qu'il y ait des objets de métadonnées dans le paquet de configuration avec un nom, un nom abrégé et/ou un code qui existe déjà dans la base de données cible. Il existe plusieurs solutions alternatives à ces problèmes, avec de différents avantages et inconvénients. La solution la plus appropriée dépendra, par exemple, du type d'objet pour lequel un conflit survient.

#### Option 1

Renommez l'objet de votre base de données de DHIS2 pour lequel il y a un conflit. L'avantage de cette approche est que vous n'avez pas besoin de modifier le fichier .json, puisque les modifications sont effectuées par l'interface utilisateur de DHIS2. Cette méthode est probablement moins sujette aux erreurs. Cela signifie également que le progiciel de configuration est laissé tel quel, ce qui peut être un avantage, par exemple, lorsque du matériel de formation et de la documentation basés sur le progiciel de configuration seront utilisés.

#### Option 2

Renommez l'objet pour lequel il y a un conflit dans le fichier .json. L'avantage de cette approche est que les métadonnées DHIS2 existantes sont laissées telles quelles. Cela peut être un facteur lorsqu'il y a du matériel de formation ou de la documentation, comme les procédure normale d'exploitation des dictionnaires de données liés à l'objet en question, et cela n'implique aucun risque de confusion pour les utilisateurs lors de la modification des métadonnées qui leur sont familières.

Notez que pour les deux options 1 et 2, la modification peut être aussi simple que l'ajout d'un petit pré/post-fixe au nom, pour minimiser le risque de confusion.

#### Option 3

Une troisième approche, plus complexe, consiste à modifier le fichier .json pour réutiliser les métadonnées existantes. Par exemple, dans les cas où un ensemble d'options existe déjà pour un certain concept (par exemple "sexe"), cet ensemble d'options pourrait être supprimé du fichier .json et toutes les références à son UID remplacées par l'ensemble d'options correspondant existant déjà dans la base de données. Le grand avantage de cette méthode (qui n'est pas limitée aux seuls cas où il y a un conflit d'importation direct) est d'éviter de créer des métadonnées dupliquées dans la base de données. Il y a des aspects essentiels à prendre en compte lors de ce type de modification :

*   il nécessite une connaissance approfondie de la structure détaillée des métadonnées du DHIS2
*   Cette approche ne fonctionne pas pour tous les types d'objets. En particulier, certains types d'objets ont des dépendances compliquées à résoudre de cette manière, par exemple en ce qui concerne les désagrégations.
*   Il sera compliqué d'éffectuer des mises à jour du paquet de configuration dans le futur.

## Configuration supplémentaire

Une fois que toutes les métadonnées sont importées avec succès, des étapes doivent être mises en oeuvre avant que le module ne soit fonctionnel.

### Partage

Tout d'abord, vous devrez utiliser la fonctionnalité *Partage* de DHIS2 pour configurer quels utilisateurs (groupes d'utilisateurs) doivent voir les métadonnées et les données associées au programme ainsi que qui peut enregistrer/saisir des données dans le programme. Par défaut, le partage a été configuré pour ce qui suit :

* Programme
* Étape du programme

Il y a trois groupes d'utilisateurs qui sont fournis avec le paquet :

* COVID19 Accès
* COVID19 Administrateur
* COVID 19 Saisie de données

Les éléments suivants sont attribués par défaut à ces groupes d'utilisateurs

<table style="margin-bottom:1em">
  <tr>
   <td rowspan="2" ><strong>Objet</strong>
   </td>
   <td colspan="3" ><strong>Groupe d'utilisateurs</strong>
   </td>
  </tr>
  <tr>
   <td><em>COVID19 Accès</em>
   </td>
   <td><em>COVID19 Administrateur</em>
   </td>
   <td><em>COVID19 Saisie de données</em>
   </td>
  </tr>
  <tr>
   <td><em>Programme</em>
   </td>
   <td>Métadonnées : peut visualiser
<p>
Données : visualiser
   </td>
   <td>Métadonnées : peut modifier et visualiser
<p>
Données : peut visualiser
   </td>
   <td>Métadonnées : peut visualiser
<p>
Données : peut saisir et visualiser
   </td>
  </tr>
  <tr>
   <td><em>Etape du programme</em>
   </td>
   <td>Métadonnées : peut visualiser
<p>
Données : peut visualiser
   </td>
   <td>Métadonnées : peut modifier et visualiser
<p>
Données : peut visualiser
   </td>
   <td>Métadonnées : peut visualiser
<p>
Données : peut saisir et visualiser
   </td>
  </tr>
</table>

Vous voudrez bien affecter vos utilisateurs au groupe d'utilisateurs approprié en fonction de leur rôle dans le système. Vous pouvez également activer le partage pour d'autres objets du paquet en fonction de votre configuration. Reportez-vous à la [Documentation DHIS2] (https://docs.dhis2.org/master/en/dhis2_user_manual_en/about-sharing-of-objects.html) pour plus d'informations sur la configuration du partage.

### Rôles des utilisateurs

Les utilisateurs auront besoin de rôles d'utilisateur pour pouvoir utiliser les différentes applications du DHIS2. Les rôles minimums suivants sont recommandés pour les utilisateurs finaux :

1. Analyse des données Tracker : Il peut visualiser des analyses d'événements et accéder à des tableaux de bord, des rapports d'événements, un visualiseur d'événements, un visualiseur de données, des tableaux croisés dynamiques, des rapports et des cartes.
2. Saisie de données de suivi : possibilité d'ajouter des valeurs de données, de mettre à jour les entités suivies, de rechercher des entités suivies dans les unités d'organisation et d'accéder à l'application Saisie Tracker

Reportez-vous à la [Documentation DHIS2] (http://dhis2.org/documentation) pour plus d'informations sur la configuration des rôles des utilisateurs.

### Unités d'organisation

Vous devez assigner le programme à des unités d'organisation au sein de votre propre hiérarchie afin de pouvoir le visualiser dans Saisie Tracker.

### Métadonnées dupliquées

**N.B.** : Cette section ne s'applique que si vous importez dans une base de données DHIS2 ayant déjà des méta-données. Si vous travaillez avec une nouvelle instance de DHIS2, veuillez ignorer cette section et aller à [Adapter le programme tracker] (#adapter-le-programme-d'événements)".

Même lorsque les métadonnées sont importées avec succès sans aucun conflit d'importation, il peut y avoir des doublons dans les métadonnées - éléments de données, attributs d'entités suivies ou ensembles d'options qui existent déjà. Comme indiqué dans la section ci-dessus sur la résolution des conflits, il est important de garder à l'esprit que les décisions relatives à la modification des métadonnées dans le DHIS2 doivent également tenir compte d'autres documents et ressources associés de différentes manières aux métadonnées existantes et aux métadonnées importées par le biais du progiciel de configuration. La résolution des doublons ne consiste donc pas seulement à "nettoyer la base de données", mais aussi à s'assurer que cela est fait sans, par exemple, casser le potentiel d'intégration avec d'autres systèmes, la possibilité d'utiliser du matériel de formation, la rupture des SOP, etc. Cela dépend beaucoup du contexte.

Il est important de garder à l'esprit que le DHIS2 dispose d'outils pouvant dissimuler certaines des complexités des duplications potentielles dans les métadonnées. Par exemple, lorsqu'il existe des ensembles d'options en double, ils peuvent être masqués pour des groupes d'utilisateurs par le biais de [Partage](https://docs.dhis2.org/master/en/user/html/sharing.html).


## Adapter le programme d'événements

Une fois le programme importé, il est possible que vous souhaitiez y apporter certaines modifications. Voici quelques exemples d'adaptations locales que vous *pourrez* effectuer :

* Ajout de variables supplémentaires au formulaire.
* Adapter les noms des éléments de données/options en fonction des usages au niveau national.
* Ajouter des traductions aux variables et/ou au formulaire de saisie des données.
* Modifier les indicateurs du programme en fonction des définitions de cas locales

Toutefois, il est fortement recommandé de faire preuve d'une grande prudence si vous décidez de modifier ou de supprimer l'un des formulaires/métadonnées inclus. Il y a donc un risque que des modifications brisent des fonctionnalités, par exemple les règles du programme et les indicateurs du programme.
