# Package de données numériques de surveillance du COVID-19 

DHIS2 a publié un package de données numériques pour accélérer la détection de cas, l'analyse de situation, la surveillance active et la riposte au COVID-19. Ce package s'inspire de la conception pionnière du Tracker DHIS2 par le ministère de la santé du Sri Lanka pour la détection des cas de COVID-19 et s'appuie sur des années de collaboration avec l'Organisation mondiale de la santé (OMS) pour développer des normes en matière de système d'information pour la surveillance des maladies basée sur l'identification des cas. Le package de données numériques de COVID-19 comprend des métadonnées standard alignées sur les [orientations techniques de l'OMS en matière de surveillance du COVID-19 et les définitions de cas](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions) et des conseils de mise en œuvre pour permettre un déploiement rapide dans les pays.

DHIS2 est actuellement utilisé pour la surveillance du COVID-19 dans plusieurs pays à travers le monde. Consultez la carte ci-dessous pour voir où les packages COVID-19 de DHIS2 sont testés et déployés.


## À quoi peuvent servir les packages DHIS2 de données numériques de surveillance du COVID-19 ?

Les packages prennent en charge les flux de surveillance et l'analyse automatisée pour les éléments clés de la surveillance de routine et active :

*   **Surveillance basée sur les cas de COVID-19 [tracker]** : enregistre et suit les cas suspects ; collecte les symptômes, les données démographiques, les facteurs de risque et les expositions ; crée des demandes de tests de laboratoire ; relie les cas confirmés aux contacts ; et surveille les résultats des patients. Ce module peut être installé en tant que module COVID-19 autonome ou peut être intégré dans le système de surveillance et de suivi de la riposte aux maladies d'un pays.
*   **Programme d'enregistrement et de suivi des contacts [tracker]** : renforce la détection active des cas par des activités de recherche des contacts, telles que l'identification et le suivi des contacts d'un cas COVID-19 suspecté ou confirmé.
*   **Programme de contrôle et de suivi aux points d'entrée [tracker]** : enregistre aux points d'entrée les voyageurs qui ont visité des endroits à haut risque afin de les surveiller et les suivre pendant 14 jours.
*   **Programme d'événements de surveillance COVID-19 [événement]** : une liste simplifiée qui permet de saisir un sous-ensemble de données critiques minimales pour faciliter une analyse et une riposte rapides ; particulièrement utile lorsque la charge de travail ou la charge de déclaration dépasse la capacité pour la mise en place de la surveillance basée sur l'identification des cas.
*   **Surveillance agrégée du COVID-19 [aggregate]** : un ensemble de données de déclaration agrégées qui permet de saisir le nombre minimum de données nécessaires pour une déclaration quotidienne ou hebdomadaire

Tous les packages de données numériques sont optimisés pour la collecte de données sur Android grâce à l'application DHIS2 Capture, qui peut être téléchargée gratuitement sur [Google Play store](https://play.google.com/store/apps/details?id=com.dhis2&hl=en).

Travaillez-vous dans un pays intéressé par la mise en place du tracker COVID-19 de DHIS2 ? Veuillez nous contacter à l'adresse suivante : [post@dhis2.org](mailto:post@dhis2.org).


## Découvrez la démo de la surveillance COVID-19 de DHIS2

Explorez le DHIS2 Tracker pour la surveillance du COVID-19 par vous-même en utilisant notre base de données de démonstration en ligne (connexion requise) : **[démo interactive de la surveillance du COVID-19 dans DHIS2](https://covid.dhis2.org/demo)**.

## Télécharger le package de surveillance COVID-19 de DHIS2

Les versions ci-après du package de surveillance COVID-19 de DHIS2 sont disponibles en téléchargement et pour installation. Le package de configuration COVID-19 est constitué de métadonnées DHIS2 qui permettent une configuration standard de DHIS2 selon [les dernières recommandations de l'OMS disponibles](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions).

Voir les [notes de version du package v 0.3](release-notes-v03.md) pour un résumé des mises à jour et des nouveaux élements.

Veuillez consulter les documents suivants avant de vous lancer :

*   Le **document de conception du système** fournit des détails sur le cas d'utilisation et la configuration du package.
*   Le **guide d'installation** fournit des conseils sur la préparation, l'importation et l'adaptation du package.

Sont également disponibles les ressources en ligne suivantes :

*   Le **[guide de mise en œuvre du Tracker (en anglais)](https://docs.dhis2.org/master/en/dhis2_tracker_implementation_guide/target-audience.html)** fournit des conseils généraux sur la planification d'une instance du Tracker DHIS2.
*   Le document **["FAQ"](https://community.dhis2.org/t/frequently-asked-questions-faq/38690)** fournit des réponses aux questions les plus fréquentes sur le package.
*   Le **[canal de discussion et d'assistance dédié au COVID-19](https://community.dhis2.org/c/implementation/covid-19/41)** sur la communauté de pratique de DHIS2 est un forum où vous pouvez poser des questions (en français), obtenir de l'aide pour votre mise en œuvre et consulter les questions (majoritairement en anglais) qui ont été soulevées et résolues par d'autres membres de la communauté.

<table style="margin-bottom:1em;">
  <tr>
   <td>
<strong>Version de DHIS2</strong>
   </td>
   <td><strong>Version du package</strong>
   </td>
   <td><strong>Type de package</strong>
   </td>
   <td><strong>Documentation</strong>
   </td>
   <td><strong>Métadonnées</strong>
   </td>
   <td><strong>Dernière mise à jour</strong>
   </td>
  </tr>
  <tr>
   <td>2.33
   </td>
   <td>V 0.3.3
   </td>
   <td>Surveillance basée sur les cas de COVID-19
<p>
Programme d'enregistrement et de suivi des contacts
   </td>
   <td><a href="https://docs.google.com/document/d/12-pex7VOMoRAnsiIcTLq0mTD6UTSfVBZWIX0vufIt6I/edit?usp=sharing">Document de conception du système</a>
<p>
<a href="installation-guide-tracker">Guide d'installation</a>
   </td>
   <td><a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19/COVID19_TRACKER_V1_DHIS2.33/metadata.json">Fichier des métadonnées</a>
   </td>
   <td>27 mars 2020
   </td>
  </tr>
  <tr>
   <td>2.33
   </td>
   <td>V 0.3.2
   </td>
   <td>Programme d'événements de surveillance COVID-19 
   </td>
   <td><a href="https://docs.google.com/document/d/1_OxdOmlPouNmoXD6FUEFZAgaPQARKUdrq0h0Gco4ARw/edit">Document de conception du système</a>
<p>
<a href="installation-guide-event">Guide d'installation</a>
   </td>
   <td> <a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_EVENT/COVID19_EVENT_TRACKER_V1_DHIS2.33/metadata.json">Fichier des métadonnées</a>
   </td>
   <td>27 March 2020
   </td>
  </tr>
  <tr>
   <td>2.30
<p>
2.31
<p>
2.32
<p>
2.33
   </td>
   <td>V 0.3.2
   </td>
   <td>Surveillance agrégée du COVID-19
   </td>
   <td><a href="https://docs.google.com/document/d/1My2jVCAwPVA3j9m21xp0UCti--N8am9BXsYEjI7qn3I/edit#">Document de conception du système</a>
<p>
<a href="installation-guide-aggregate">Guide d'installation</a>
   </td>
   <td><a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.30/metadata.json">Fichier des métadonnées pour 2.30</a>
<p>
<a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.31/metadata.json">Fichier des métadonnées pour 2.31</a>
<p>
<a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.32/metadata.json">Fichier des métadonnées pour 2.32</a>
<p>
<a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.33/metadata.json">Fichier des métadonnées pour 2.33</a>
   </td>
   <td>27 March 2020
   </td>
  </tr>
  <tr>
   <td>2.33
   </td>
   <td>V 0.3.1
   </td>
   <td>Programme de contrôle et de suivi aux points d'entrée
   </td>
   <td> <a href="https://drive.google.com/open?id=1PJ4iRJGmUBv6jF7hcACxt-dhd5JRpeBt0mKxgPBsmvc">Document de conception du système</a>
<p>
<a href="installation-guide-tracker">Guide d'installation</a>
   </td>
   <td><a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_POE/COVID19_POE_TRACKER_V1_DHIS2.33/metadata.json">Fichier des métadonnées</a>
   </td>
   <td>27 March 2020
   </td>
  </tr>
</table>
