# COVID-19 Guide d'installation du paquet d'agrégats

<ul style="text-align: right">
  <li style="list-style: none">Dernière mise à jour 27/03/2020</li>
  <li style="list-style: none">Version du paquet 0.3.2</li>
  <li style="list-style: none">Compatibilité de la version DHIS2 2.30 - 2.33</li>
  <li style="list-style: none">Démo: <a href="https://covid.dhis2.org/">https://covid.dhis2.org/</a></li>
</ul>

## Aperçu

Ce document est destiné à guider les administrateurs dans le processus d'installation du progiciel de configuration standard COVID-19 pour le DHIS2 pour la déclaration agrégée. Il est donc nécessaire d'avoir une bonne compréhension de DHIS2.

Les progiciels de configuration pour DHIS2 consistent en un fichier de métadonnées au format [JSON](https://en.wikipedia.org/wiki/JSON) qui peut être importé dans une instance de DHIS2, ainsi que la documentation d'accompagnement. Le progiciel fournit un contenu prédéfini et standard selon les recommandations de l'OMS. Ce document traite des progiciels complets comprenant des configurations de collecte de données (ensembles de données, éléments de données, règles de validation) ainsi que des analyses et des tableaux de bord (graphiques, cartes et tableaux croisés dynamiques favoris). Il est destiné à être utilisé lorsqu'aucune collecte de données n'est configurée dans DHIS2, ou en cas de remplacement ou de révision du contenu existant pour l'aligner sur les recommandations de l'OMS.

Les paquets de configuration se composent de 4 éléments principaux :

* des ensembles de données avec des éléments de données ;
* un ensemble d'indicateurs ;
* les résultats analytiques (tableau croisé dynamique, visualiseur de données et favoris SIG) ; et
* un ensemble de tableaux de bord.

Ces composantes sont toutes liées, c'est-à-dire que les indicateurs sont basés sur les éléments de données inclus, les résultats analytiques sont basés sur les indicateurs inclus, et les tableaux de bord sont constitués des résultats analytiques inclus.

## Installation

L'installation du module se fait en deux étapes :

1. [Préparer](#preparing-the-metadata-file) le fichier de métadonnées avec les métadonnées de DHIS2.
2. [Importer](#importing-metadata-file) le fichier de métadonnées dans DHIS2.
3. [Configurer](#configuration-additionnelle) les métadonnées importées.
4. [Effectuer](#exemples-d'autres-modifications) des modifications spécifiques au paquet.

Cette section traite des deux premières étapes de la préparation et de l'importation du fichier de métadonnées dans DHIS2, tandis que la procédure de configuration est abordée dans la section suivante. Il est recommandé de lire les deux sections avant de commencer le processus d'installation et de configuration dans DHIS2. Outre les étapes générales décrites ici, certains des paquets de configuration comportent des annexes au guide d'installation, qui décrivent des points particuliers. Ces annexes sont énumérées dans la section appropriée [ici] (https://who.dhis2.org/documentation#configuration-packages).

La procédure décrite dans ce document doit être testée dans un environnement de test et de simulation avant d'être répétée ou transférée à une instance de production du DHIS2.

Paquets à configuration multiple

Certains progiciels de configuration ont des métadonnées qui se chevauchent, par exemple les indicateurs. Cela signifie que dans certaines situations, les modifications apportées aux métadonnées des progiciels de configuration importés précédemment peuvent être écrasées lors de l'importation d'un progiciel différent. Cette situation peut être évitée en important des métadonnées "nouvelles seulement" plutôt que "nouvelles et mises à jour", mais notez que dans les deux cas, des modifications manuelles seront nécessaires. Vous devez au moins vous assurer que les métadonnées utilisées par plusieurs programmes sont [partagées] (https://who.dhis2.org/documentation/access-and-sharing) avec les groupes d'utilisateurs appropriés pour les deux programmes.

## Conditions requises

Pour installer le paquet de configuration, un compte d'utilisateur administrateur dans le DHIS2 est nécessaire, avec les autorisations permettant d'ajouter/de modifier les objets de métadonnées (publiques), y compris (mais sans s'y limiter) :

*   les éléments de données (y compris les catégories)
*   Ensembles de données
*   Indicateurs
*   Types d'indicateurs
*   Tableaux de bord
*   visualiseur de données, tableau croisé dynamique et favoris du SIG

La liste complète des objets inclus dans le module (pour lesquels l'administrateur a besoin d'autorisation avant de les gérer) peut être trouvée dans le Document de référence des métadonnées pour le paquet de configuration spécifique.

Dans les cas où des modifications du fichier de métadonnées .json du paquet de configuration sont nécessaires [(voir ci-dessous)](https://who.dhis2.org/documentation/installation_guide_complete.html#preparing-the_metadata-file), un [éditeur de texte](https://en.wikipedia.org/wiki/Text_editor) est alors nécessaire - ces modifications ne doivent pas être effectuées avec un logiciel de traitement de textes tel que Microsoft Word.

Le paquet de configuration peut être installé dans le DHIS2 par l'intermédiaire de l'application DHIS2 Health, ou manuellement par le biais d'un fichier .json contenant les métadonnées du DHIS2 en utilisant l'application [Importer/Exporter](https://docs.dhis2.org/2.27/en/user/html/ch19.html) du DHIS2. La procédure décrite dans le reste de cette section s'applique au processus d'importation manuelle des métadonnées.

La section [Configuration] (https://who.dhis2.org/documentation/installation_guide_complete.html#configuration) s'applique aux deux méthodes.

## Préparation du fichier de métadonnées

**N.B.** : Si vous installez le paquet sur une nouvelle instance de DHIS2, vous pouvez alors ignorer la section "Préparation du fichier de métadonnées" et passer immédiatement à la section "[Importer un fichier de métadonnées dans DHIS2](#importing-a-metadata-file-into-dhis2)".

Bien que ce ne soit pas toujours nécessaire, il peut souvent être avantageux d'apporter certaines modifications au fichier de métadonnées avant son importation dans DHIS2.

## Dimension de données par défaut

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

Par exemple, si vous importez un progiciel de configuration dans [https://play.dhis2.org/demo](https://play.dhis2.org/demo), l'UID de la combinaison d'options de catégorie par défaut peut être identifié via [https://play.dhis2.org/demo/api/categoryOptionCombos.json?filter=name:eq:default](https://play.dhis2.org/demo/api/categoryOptionCombos.json?filter=name:eq:default) comme `bRowv6yZOF2`. Vous pourriez alors rechercher et remplacer toutes les occurrences de `HllvX50cXC0` par `bRowv6yZOF2` dans le fichier .json. Notez que cette opération de recherche et de remplacement doit être effectuée avec un éditeur de texte simple, et non avec un logiciel de traitement de textes comme Microsoft Word.

## Types d'indicateurs

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
   <td>Numérateur uniquement (nombre)
   </td>
   <td>kHy61PbChXr
   </td>
   <td>../api/indicatorTypes.json?filter=number:eq:true&filter=factor:eq:1
   </td>
  </tr>
  <tr>
   <td>Pourcentage
   </td>
   <td>hmSnCXmLYwt
   </td>
   <td>../api/indicatorTypes.json?filter=number:eq:false&filter=factor:eq:100
   </td>
  </tr>
</table>

**N.B. 1** : en remplaçant les UID comme décrit et en important le fichier .json, le nom (y compris les traductions éventuelles) des types d'indicateurs en question sera mis à jour pour correspondre à ceux inclus dans les paquets de configuration.

**Note 2** : Une autre approche pour réutiliser les types d'indicateurs existants consiste à importer ceux inclus dans le paquet de configuration, et à supprimer ceux qui se chevauchent. Pour ce faire, il faudrait que tous les indicateurs utilisant ces types d'indicateurs existants soient mis à jour avec les types d'indicateurs nouvellement importés, avant que les types d'indicateurs puissent être supprimés.

## Importation de métadonnées dans DHIS2

Le fichier de métadonnées .json est importé via l'application [Importer/Exporter](https://docs.dhis2.org/2.28/en/user/html/import_export.html) de DHIS2. Il est conseillé d'utiliser la fonction "test" pour identifier les problèmes avant d'essayer d'importer les métadonnées. Si la fonction "test" signale des problèmes ou des conflits, consultez la section [importer des conflits] (https://who.dhis2.org/documentation/installation_guide_complete.html#handling-import-conflicts) ci-dessous.

Si l'importation "d'essai"/"de validation fonctionne sans erreur, essayez d'importer les métadonnées. Si l'importation réussit sans aucune erreur, vous pouvez alors passer à la [configuration](https://who.dhis2.org/documentation/installation_guide_complete.html#configuration) du module. Dans certains cas, les conflits ou les problèmes d'importation ne sont pas affichés pendant le "test", mais apparaissent lorsque l'on tente l'importation proprement dite. Dans ce cas, le résumé de l'importation énumère les erreurs à résoudre.

### Gestion des conflits d'importation

**N.B.** : Si vous importez dans une nouvelle instance DHIS2, vous n'aurez pas à vous soucier des conflits d'importation, car il n'y a rien dans la base de données que vous importez qui puisse entrer en conflit avec celle-ci. Suivez les instructions pour importer les métadonnées, puis passez à la section "[Configuration supplémentaire](#configuration-supplémentaire)".

Plusieurs de conflits peuvent survenir, mais le plus courant est le fait qu'il y ait des objets de métadonnées dans le paquet de configuration avec un nom, un nom abrégé et/ou un code qui existe déjà dans la base de données cible. Il existe plusieurs solutions alternatives à ces problèmes, avec de différents avantages et inconvénients. La solution la plus appropriée dépendra, par exemple, du type d'objet pour lequel un conflit survient.

#### Option 1

Renommez l'objet de votre base de données de DHIS2 pour lequel il y a un conflit. L'avantage de cette approche est que vous n'avez pas besoin de modifier le fichier .json, puisque les modifications sont effectuées par l'interface utilisateur de DHIS2. Cette méthode est probablement moins sujette aux erreurs. Cela signifie également que le progiciel de configuration est laissé tel quel, ce qui peut être un avantage, par exemple, lorsque du matériel de formation et de la documentation basés sur le progiciel de configuration seront utilisés.

#### Option 2

Renommez l'objet pour lequel il y a un conflit dans le fichier .json. L'avantage de cette approche est que les métadonnées DHIS2 existantes sont laissées telles quelles. Cela peut être un facteur lorsqu'il y a du matériel de formation ou de la documentation, comme les procédure normale d'exploitation des dictionnaires de données liés à l'objet en question, et cela n'implique aucun risque de confusion pour les utilisateurs lors de la modification des métadonnées qui leur sont familières. Au même moment, la modification de l'objet du fichier .json signifie que l'utilisation de la documentation et du matériel de formation associés pourrait devenir plus compliquée.

Notez que pour les deux options 1 et 2, la modification peut être aussi simple que l'ajout d'un petit pré/post-fixe au nom, pour minimiser le risque de confusion.

#### Option 3

Une troisième approche, plus complexe, consiste à modifier le fichier .json pour réutiliser les métadonnées existantes. Par exemple, dans les cas où un indicateur existe déjà pour un certain concept (par exemple "Couverture de CPN 1"), cet indicateur pourrait être supprimé du fichier .json et toutes les références à son UID remplacées par l'indicateur correspondant existant déjà dans la base de données. Le grand avantage de cette méthode (qui n'est pas limitée aux seuls cas où il y a un conflit d'importation direct) est d'éviter de créer des métadonnées en double dans la base de données. Cependant, elle n'est généralement pas recommandée pour plusieurs raisons :

* il nécessite une connaissance approfondie de la structure détaillée des métadonnées du DHIS2
* Cette approche ne fonctionne pas pour tous les types d'objets. En particulier, certains types d'objets ont des dépendances compliquées à résoudre de cette manière, par exemple en ce qui concerne les désagrégations.
* comme pour l'option 2, cela signifie que le résultat de l'installation n'est pas entièrement conforme à la configuration standard, et que le matériel de formation et la documentation élaborés pour cette configuration pourraient ne pas être utilisables sans modifications.
* Il sera compliqué d'éffectuer des mises à jour du paquet de configuration dans le futur.

## Configuration supplémentaire

Une fois que toutes les métadonnées ont été importées avec succès, le module devrait être utilisable avec seulement quelques ajustements mineurs supplémentaires. En outre, en fonction de l'instance DHIS2 dans laquelle le module a été importé, une configuration et des modifications supplémentaires peuvent être nécessaires ou avantageuses. Cette section passera d'abord en revue les étapes de configuration nécessaires, puis mentionnera certains des autres types de modifications ou de configuration qui pourraient être utiles.

## Configuration requise

Avant que les paquets de configuration puissent être utilisés pour la collecte de données, deux étapes sont nécessaires.

* Affecter le ou les ensemble(s) de données aux unités d'organisation appropriées
* Partager le ou les ensemble(s) de données avec les groupes d'utilisateurs appropriés
* Ajoutez votre/vos utilisateur(s) aux groupes d'utilisateurs appropriés

Les ensembles de données doivent être attribués aux unités d'organisation (établissements) qui sont censées faire rapport sur cet ensemble de données particulier.

Les ensembles de données et les options de catégories doivent également être partagés avec le ou les groupe(s) d'utilisateurs concernés du personnel chargé de la saisie des données pour ces ensembles de données.

### Partage

Tout d'abord, vous devrez utiliser la fonctionnalité *Partage* de DHIS2 pour configurer quels utilisateurs (groupes d'utilisateurs) doivent voir les métadonnées et les données associées au programme ainsi que qui peut enregistrer/saisir des données dans le programme. La fonctionnalité Partage doit être configurée pour ce qui suit :

* Éléments de données/Groupes d'éléments de données
* Indicateurs/Groupes d'indicateurs
* Ensembles de données
* Tableaux de bord

Il y a trois groupes d'utilisateurs qui sont fournis avec le paquet :

* COVID19 Accès
* COVID19 Administrateur
* COVID 19 Saisie de données

Nous recommandons l'accès suivant

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
   <td><em>Eléments de données/Groupe d'éléments de données</em>
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
Données : peut visualiser
   </td>
  </tr>
  <tr>
   <td><em>Indicateurs/Groupe d'indicateurs</em>
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
Données : peut visualiser
   </td>
  </tr>
  <tr>
   <td><em>Ensembles de données</em>
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
  <tr>
   <td><em>Tableaux de bord</em>
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
Données : peut visualiser
   </td>
  </tr>
</table>

### Métadonnées dupliquées

Même lorsque les métadonnées sont importées avec succès sans aucun conflit d'importation, il peut y avoir des doublons dans les métadonnées - éléments de données, attributs d'entités suivies ou ensembles d'options qui existent déjà. Comme indiqué dans la section ci-dessus sur la résolution des conflits, il est important de garder à l'esprit que les décisions relatives à la modification des métadonnées dans le DHIS2 doivent également tenir compte d'autres documents et ressources associés de différentes manières aux métadonnées existantes et aux métadonnées importées par le biais du progiciel de configuration. La résolution des doublons ne consiste donc pas seulement à "nettoyer la base de données", mais aussi à s'assurer que cela est fait sans, par exemple, casser le potentiel d'intégration avec d'autres systèmes, la possibilité d'utiliser du matériel de formation, la rupture des SOP, etc. Cela dépend beaucoup du contexte.

Une chose importante à garder à l'esprit est que le DHIS2 dispose d'outils pouvant dissimuler certaines des complexités des duplications potentielles dans les métadonnées. Par exemple, lorsqu'il existe des catégories d'éléments de données double, ces doublons peuvent être masqués aux utilisateurs finaux grâce à des ensembles de groupes d'options de catégories, ou certains objets de métadonnées peuvent être masqués pour des groupes d'utilisateurs à travers l'option de partage.

Il est recommandé de ne pas supprimer ou remplacer les indicateurs inclus dans les progiciels de configuration même si le même indicateur existe déjà, afin de pouvoir conserver les résultats analytiques (qui, eux, reposent exclusivement sur des indicateurs). Cela permettra de réutiliser le matériel de formation basé sur les progiciels de configuration.

## Exemples d'autres modifications

Outre la configuration requise, il existe plusieurs autres modifications et configurations qui peuvent s'avérer utiles, en fonction de la situation spécifique. Il ne sera pas possible de fournir des orientations et des recommandations couvrant tous les différents scénarios, mais nous présentons ici une brève discussion de certains problèmes courants.

### Les traductions

Des traductions supplémentaires pourraient être ajoutées, si d'autres langues que celles incluses sont nécessaires.

### Ajout de variables supplémentaires

Les progiciels de configuration comprennent les principaux éléments de données et indicateurs recommandés. Toutefois, il peut être nécessaire dans certains cas d'ajouter des variables supplémentaires pour répondre aux besoins d'information spécifiques à chaque pays. Ces variables pourraient être ajoutées aux ensembles de données inclus.

### Mise à jour de la présentation des formulaires de déclaration

Pour faciliter le travail du personnel chargé de la saisie des données dans DHIS2, il est parfois souhaitable d'ajouter un formulaire de saisie personnalisé qui correspond au format des formulaires papier utilisés au premier niveau.

## Maintenance

Aucune maintenance particulière n'est requise pour les paquets de configuration, puiqu'ils sont constitués d'objets de métadonnées DHIS2 standard. Toutefois, avant de passer aux nouvelles versions de DHIS2, il est important de tester toutes les fonctionnalités du système en général sur un serveur de test et de simulation avant la mise à niveau des instances de production du système.
