<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 1; WARNINGs: 2; ALERTS: 11.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p><a href="#gdcalert1">alert1</a>
<a href="#gdcalert2">alert2</a>
<a href="#gdcalert3">alert3</a>
<a href="#gdcalert4">alert4</a>
<a href="#gdcalert5">alert5</a>
<a href="#gdcalert6">alert6</a>
<a href="#gdcalert7">alert7</a>
<a href="#gdcalert8">alert8</a>
<a href="#gdcalert9">alert9</a>
<a href="#gdcalert10">alert10</a>
<a href="#gdcalert11">alert11</a>

<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>



# **COVID-19 Conception d'un système de surveillance basée sur des cas et de Recherche des contacts v0.3.3**

<ul style="text-align: right">
  <li style="list-style: none">Dernière mise à jour 27/03/2020</li>
  <listyle="list-style: none">Version du paquet 0.3.3</li>
  <li style="list-style: none">Compatibilité de la version DHIS2 2.33.2 et plus</li>
  <li style="list-style: none""> Démo: <a href="https://covid.dhis2.org/">https://covid.dhis2.org/</a></li>
</ul>

## Objectif

Le document "Conception du système de surveillance du COVID-19" donne un aperçu du design conceptuel utilisé dans la configuration d'un ensemble de données numériques du COVID-19 dans le DHIS2. Le paquet COVID-19 a été développé en réponse à un besoin exprimé par les pays d'adapter rapidement une solution de gestion des données du COVID-19. Ce document est destiné aux responsables de la mise en œuvre du DHIS2 au niveau national et régional pour soutenir la mise en œuvre et la localisation du progiciel. Le progiciel de métadonnées de COVID-19 peut être adapté aux besoins locaux et aux directives nationales. Les flux de travail locaux et les lignes directrices nationales doivent être en particulier pris en compte lors de la localisation et de l'adoption des programmes inclus dans ce progiciel.


## Contexte

**Ce modèle a été mis à jour pour tenir compte des nouvelles exigences en matière de déclaration globale figurant dans les [directives de surveillance provisoires de l'OMS mises à jour le 20 mars 2020] (https://apps.who.int/iris/bitstream/handle/10665/331506/WHO-2019-nCoV-SurveillanceGuidance-2020.6-eng.pdf)**. L'ensemble de données numériques du COVID-19 a été développé en réponse à un besoin exprimé par les pays d'adapter rapidement une solution de gestion des données du COVID-19. L'UiO a développé le progiciel de surveillance du COVID-19 pour trois types de modèles de données (tracker, agrégat basé sur les événements) afin de permettre aux pays de sélectionner le modèle le plus approprié à leur contexte compte tenu de la charge de morbidité et des ressources disponibles. Ces modèles et leurs avantages/limites relatifs sont résumés ci-dessous :


<table>
  <tr>
   <td><strong>Type of Surveillance Package</strong>
   </td>
   <td><strong>Case-based Surveillance (Tracker)</strong>
   </td>
   <td><strong>Surveillance (Event)</strong>
   </td>
   <td><strong>Surveillance (Aggregate)</strong>
   </td>
  </tr>
  <tr>
   <td><strong><em>Description</em></strong>
   </td>
   <td>Enrolls a case and tracks over time through laboratory confirmation & case outcome
   </td>
   <td>Captures critical case details in line-listing format
   </td>
   <td>Enables daily or weekly reporting of key aggregate data points
   </td>
  </tr>
  <tr>
   <td><strong><em>Pros</em></strong>
   </td>
   <td>Highly granular data and multiple time dimensions for analysis, can support decentralized workflow, all events linked to the case
   </td>
   <td>More granular than aggregate and can capture key time dimensions (i.e. report date vs onset of symptoms); reduced burden of data entry compared to tracker and little complexity
   </td>
   <td>Low complexity, easy to implement, most manageable when cases numbers are high
   </td>
  </tr>
  <tr>
   <td><strong><em>Cons</em></strong>
   </td>
   <td>Burden of data entry may be overwhelming when number of cases reach threshold; complexity of implementation
   </td>
   <td>Does not support case-follow up or other decentralized workflows
   </td>
   <td>Less granularity for detailed analysis (i.e. analysis only based on case reporting date, limited disaggregation)
   </td>
  </tr>
</table>


**Ce document ne couvre que la conception de l'ensemble du programme de suivi de la surveillance** ; des documents de conception de système distincts sont disponibles pour les ensembles d'événements et d'agrégats de DHIS2.

L'OMS "exhorte tous les pays à se préparer à l'arrivée éventuelle de COVID-19 en préparant des systèmes d'intervention d'urgence, en augmentant la capacité à détecter et à soigner les patients, en veillant à ce que les hôpitaux disposent de l'espace, du matériel et du personnel nécessaires et en mettant au point des interventions médicales visant à sauver des vies".

Les objectifs du progiciel de surveillance du COVID-19 sont les suivants :

1. surveiller les tendances de la maladie là où il y a transmission interhumaine ;
2. détecter rapidement les nouveaux cas dans les pays où il n'y a pas de circulation du virus ;
3. fournir des informations épidémiologiques pour effectuer des évaluations des risques aux niveaux national, régional et mondial ; et
4. fournir des informations épidémiologiques pour orienter les mesures de préparation et d'intervention.

La conception du système s'appuie sur les principes existants de surveillance des maladies sur la base de cas et les exigences du système d'information élaborés conjointement par l'OMS et l'UiO depuis 2017. Le progiciel de surveillance de COVID-19 a été développé dans l'intention de s'aligner sur les [directives techniques de l'OMS en matière de surveillance du nCoV-19 et les définitions de cas] (https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions), mises à jour le 20 mars 2020. Il convient de noter que cette conception ne reflète pas nécessairement les dernières directives mondiales provisoires disponibles élaborées par l'OMS, étant donné que les mises à jour peuvent être publiées rapidement. Les directives et les politiques nationales peuvent varier et il est donc recommandé d'adapter ce progiciel au contexte local.

## Résumé de la conception du système

Les métadonnées de suivi de la surveillance basée sur les cas du système DHIS2 étaient basées sur le **[modèle de rapport de cas du COVID-19 de l'OMS](https://www.who.int/docs/default-source/coronaviruse/2020-02-27-data-dictionary-en.xlsx)** et la cartographie des dictionnaires de données peut être consultée à l'adresse [DHIS2 CBS tracker metadata WHO line-list data dictionary](https://drive.google.com/open?id=1vigXHkP7L2hJ2lrZpdf9u4csQtppMH16).

Lors du développement de ce paquet de configuration, nous avons essayé de respecter les [principes généraux de conception] (https://who.dhis2.org/documentation/general_design_principles.html) et une [convention d'appellation] commune (https://who.dhis2.org/documentation/naming_convention.html) de UiO.

Le paquet de données numériques du COVID-19 prend en charge les flux de travail de surveillance et l'analyse automatisée des éléments clés de la surveillance de routine et active. Ce paquet comprend un système de suivi de la surveillance des cas ainsi qu'un système d'enregistrement et de suivi des contacts, installés ensemble dans le même progiciel de métadonnées. Les programmes de suivi sont optimisés pour être installés avec d'autres progiciels de surveillance de COVID-19, notamment le programme de suivi du contrôle aux points d'entrée et l'ensemble de données de surveillance quotidiennes agrégées.

1. **[COVID-19 Case-based surveillance tracker](https://docs.google.com/document/d/1-trbdYVS_9eUusicFdBzANuinlujMdJlNqb4zg0IKAI/edit#heading=h.q0mt1wyorc6m)**: enrolls & tracks suspected cases; captures symptoms, demographics, risk factors & exposures; creates lab requests; links confirmed cases with contacts; and monitors patient outcomes. This package can be installed as a standalone COVID-19 package or can be integrated into a country’s existing integrated disease surveillance & response tracker. Metadata for the case-based surveillance tracker is aligned with the WHO [COVID-19 surveillance data dictionary ](https://www.who.int/docs/default-source/coronaviruse/data-dictionary-covid-crf-v6.xlsx?sfvrsn=a7d4ef98_2)

        _n.b. The COVID-19 case-based tracker can be implemented either as a ‘standalone’ program for COVID-19 specific disease surveillance as described here; or, COVID-19 concepts can be integrated into an existing case-based surveillance tracker program if one already exists in-country. Please refer to installation and implementation guidance for more details._

2. ** [Cas d'utilisation 2 : Enregistrement et suivi des contacts](#heading=h.62o76lajzaos)** : permet de renforcer la détection active des cas par des activités de recherche des contacts, telles que l'identification et la recherche des contacts d'un cas suspecté ou confirmé de COVID-19.

Les paquets de données numériques sont optimisés pour la collecte de données Android grâce à l'application DHIS2 Capture, téléchargeable gratuitement sur le [Google Play store] (https://play.google.com/store/apps/details?id=com.dhis2&hl=en).

## Cas d'utilisation 1 : COVID-19 : Suivi de la surveillance basée sur les cas

Le système de suivi de la surveillance basée sur les cas du COVID-19 peut être adapté et utilisé par les pays pour compléter les programmes nationaux de surveillance des maladies existants. Le programme de surveillance basée sur les cas est conçu pour :

1. Enregistrer les cas suspects* de COVID-19 (_qui se présentent généralement dans un établissement de santé, mais qui peuvent être enregistrés dans d'autres endroits_)
2. Saisir les informations clés sur le cas suspect, y compris les données démographiques et les expositions, telles que les symptômes, les contacts avec un cas précédemment confirmé et les antécédents de voyage
3. Générer des demandes d'analyse de laboratoire
4. Enregistrer le diagnostic du laboratoire
5. Enregistrer les contacts d'un cas confirmé** ou probable*** pour suivi
6. Record case outcome
7. Faciliter la notification des cas et le signalement des cas au niveau national/régional/global
8. Générer des tableaux de bord et des outils d'analyse pour suivre les tendances des maladies et planifier les interventions

La conception du programme de suivi basé sur les cas suppose que [les définitions de cas de l'OMS] (https://apps.who.int/iris/bitstream/handle/10665/331506/WHO-2019-nCoV-SurveillanceGuidance-2020.6-eng.pdf) sont appliquées dans le cas d'utilisation ; son utilisation peut être adaptée aux définitions de cas locales selon les besoins. Les définitions de cas de l'OMS ont été mises à jour le 20 mars 2020 et sont indiquées ci-dessous.

    _*Cas suspect : A) un patient atteint d'une maladie respiratoire aiguë (fièvre et au moins un signe/symptôme de maladie respiratoire (par exemple toux, essoufflement), ET sans autre étiologie expliquant pleinement la présentation clinique ET des antécédents de voyage ou de résidence dans un pays, une zone ou un territoire déclarant une transmission locale de la COVID-19 au cours des 14 jours précédant l'apparition des symptômes ; **OU,**B) Un patient atteint d'une maladie respiratoire aiguë ET ayant été en contact avec un cas confirmé ou probable de COVID-19 (voir définition de contact) au cours des 14 jours précédant l'apparition des symptômes ; **OU,** C) Un patient atteint d'une infection respiratoire aiguë sévère (fièvre et au moins un signe/symptôme de maladie respiratoire (e. g., toux, essoufflement) ET nécessitant une hospitalisation ET sans autre étiologie expliquant pleinement la présentation clinique._

    _**Cas probable : A) un cas suspect pour lequel le test COVID-19 n'est pas concluant (le résultat du test rapporté par le laboratoire n'est pas concluant) **OU,** B) un cas suspect pour lequel le test n'a pu être effectué pour une raison quelconque._

    _***Cas confirmée : Une personne dont le laboratoire confirme l'infection par COVID-19, quels que soient les signes et symptômes cliniques._

## Utilisateurs cibles

* Health facility users: capture and record details about a suspected case, including clinical symptoms & exposures; track lab results; record case outcome
* Utilisateurs de laboratoire : reçoivent les demandes d'analyses de laboratoire et enregistrent résultat d'analyses de laboratoire pour un cas suspect particulier
* Autorités sanitaires nationales et locales : suivi et analyse des données de surveillance des maladies au moyen de tableaux de bord et d'outils d'analyse permettant de réaliser des évaluations des risques et de planifier les interventions ; production de rapports en vue des rapports régionaux et global


## Flux de travail : Suivi de la surveillance basée sur les cas du COVID-19


## Structure : Programme de suivi de la surveillance des cas du COVID-19



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  alerte gd2md-html : dessins en ligne non pris en charge directement par les documents. Vous pouvez copier le dessin en ligne dans un dessin autonome et l'exporter par référence. Voir <a href="https://github.com/evbacher/gd2md-html/wiki/Google-Drawings-by-reference">Google Drawings par référence</a> pour plus de détails. L'URL de l'image ci-dessous est un espace réservé. </span><br>(<a href="#">Retourner en haut</a>)(<a href="#gdcalert3">Alerte suivante</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![drawing](https://docs.google.com/drawings/d/12345/export/png)

### Program Description: COVID-19 Case Testing, Diagnosis & Outcome

<table>
  <tr>
   <td>Stage
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td><strong>Enrollment details</strong>
<p>
<strong>Attributes</strong>
   </td>
   <td>The Tracked Entity is the case, which is represented by a Tracked Entity Type of ‘person.’
<p>
Enrollment date = Date of registration of the case.
<p>
Related programs = COVID-19 Contact registration & follow-up
<p>
Attributes include basic personal information and unique case identifiers
<ul>

<li>System Generated Case ID

<li>Local Case ID

<li>Age

<li>First Name

<li>Surname

<li>Sex

<li>Case phone number

<li>First Name (parent or carer)

<li>Surname (parent or carer)

<li>Home Address

<li>Workplace/school physical address

<li>Country of Residence

<li>Facility contact number
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Stage 1: \
 \
Clinical Examination and Exposures</strong>
   </td>
   <td>This stage records a suspected case’s clinical symptoms and exposures including:
<ul>

<li>Symptoms

<li>Pregnancy and underlying conditions

<li>Hospitalisation and Isolation

<li>Exposures in 14 days prior to symptoms

<li>Travel history

<li>Contact with confirmed case

<p>
After examination, you can record if the case has been hospitalised or isolated, and information surrounding this.
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Stage 2: \
 \
Lab Request</strong>
<p>
<strong>[repeatable]</strong>
   </td>
   <td>The lab request records the reason for testing and other information that a lab needs to process a sample and test it for COVID19. The information provided here can help lab personnel prioritize lab tests when resources are limited. The person entering this data could be the same person who registered the suspected case and recorded the patient’s clinical exam and exposures; or may be other personnel charged with making lab requests.
<p>

   </td>
  </tr>
  <tr>
   <td><strong>Stage 3: \
 \
Lab Results</strong>
<p>
<strong>[repeatable]</strong>
   </td>
   <td>The Lab Results stage records  the type and results from laboratory testing. It can be done directly at the lab or as secondary data entry. This stage is repeatable as samples for a given case may be tested multiple times (i.e. in the case of an inconclusive laboratory results, a new lab test can be conducted and results recorded).
   </td>
  </tr>
  <tr>
   <td><strong>Stage 4:</strong>
<p>
<strong>Health Outcome</strong>
   </td>
   <td>The health outcome records the final outcome of the case: (recovered, not recovered, dead or unknown) including date of discharge or death as applicable.
   </td>
  </tr>
</table>

### Enrôlement 

![alt_text](images/Copy-of0.png "image_tooltip")

#### Étape 1 du programme - Examen clinique et diagnostic

##### Section 1 - Signes et symptômes cliniques

En sélectionnant "oui" à l'élément de données "Signes ou symptômes ?", vous découvrirez les autres options.

![alt_text](images/Copy-of1.png "image_tooltip")

##### Section 2 - Détails sur la grossesse

Cette section est masqée si le sexe sélectionné est "Femme".

##### Section 3 - Conditions sous-jacentes/comorbidité

Cette section est masquée sauf si "Toute condition sous-jacente" est marqué "Oui". \

##### Section 4 - Hospitalisation

Cette section est cachée, sauf si "Hospitalisé" est marqué "Oui".

##### Section 5 - Risque d'exposition

This section is used to record exposures (fields are hidden by program rules if the case is not a health care worker; if the case has not had contact with a confirmed case in 14 days). A suspected case’s exposure to a *previously confirmed _case is distinct from prospective contact tracing in Program Stage 5.*

##### Section 6 - Antécédents de voyage

#### Étape 2 du programme : Demande d'analyses de laboratoire

![alt_text](images/Copy-of2.png "image_tooltip")

### Étape 3 : Résultats d'analyses de laboratoire

![alt_text](images/Copy-of3.png "image_tooltip")

### Étape 4 : Résultats médicaux

![alt_text](images/Copy-of4.png "image_tooltip")

## Règles du programme : Suivi de la surveillance des cas de COVID19

Les règles du programme suivantes ont été configurées. Si un pays dispose d'un programme de surveillance basé sur les cas et souhaite incorporer des éléments du système de suivi des cas du COVID-19 dans son programme existant, une attention particulière doit alors être accordée à la configuration des règles du programme.

<table>
  <tr>
   <td>Program Rule Name
   </td>
   <td>Program Rule Description
   </td>
  </tr>
  <tr>
   <td>Calculate and assign patient age in years
   </td>
   <td>Calculate and assign patient age in years based on DOB
   </td>
  </tr>
  <tr>
   <td>Display patient age in years + days
   </td>
   <td>Display patient age in years + days
   </td>
  </tr>
  <tr>
   <td>Hide health care worker details if not a health worker
   </td>
   <td>Hide health care worker details if not a health worker
   </td>
  </tr>
  <tr>
   <td>Hide health outcome explanation if health outcome is not other
   </td>
   <td>Hide health outcome explanation if health outcome is not other
   </td>
  </tr>
  <tr>
   <td>Hide hospitalisation details if hospitalisation is no or unknown
   </td>
   <td>Hide hospitalisation details if hospitalisation is no or unknown
   </td>
  </tr>
  <tr>
   <td>Hide isolation date if case is not in isolation
   </td>
   <td>Hide isolation date if case is not in isolation
   </td>
  </tr>
  <tr>
   <td>Hide pregnancy details for a female if not pregnant
   </td>
   <td>Hide pregnancy details for a female if not pregnant
   </td>
  </tr>
  <tr>
   <td>Hide pregnancy details section if sex is male
   </td>
   <td>Hide pregnancy details section if sex is male
   </td>
  </tr>
  <tr>
   <td>Hide reason for testing explanation if an option is selected
   </td>
   <td>Hide reason for testing explanation if an option is selected
   </td>
  </tr>
  <tr>
   <td>Hide travel history details if no travel 14 days prior to symptom onset
   </td>
   <td>Hide travel history details if no travel 14 days prior to symptom onset
   </td>
  </tr>
  <tr>
   <td>Hide underlying conditions if case does not have any
   </td>
   <td>Hide underlying conditions if case does not have any
   </td>
  </tr>
  <tr>
   <td>Show warning if the event date is after the enrollment date
   </td>
   <td>Show warning on completion of an event if the event date is before the enrollment date
   </td>
  </tr>
</table>


Vous pouvez en savoir plus sur les règles du programme ici :

[https://docs.dhis2.org/master/en/user/html/configure_program_rule.html](https://docs.dhis2.org/master/en/user/html/configure_program_rule.html)

## Indicateurs de programme

À partir des données saisies dans le Programme de surveillance des cas de COVID-19, nous pouvons calculer au moins les indicateurs suivants, y compris ceux recommandés par l'OMS pour la déclaration globale quotidienne et hebdomadaire, et les présenter dans un tableau de bord :

<table>
  <tr>
   <td>COVID-19 - Cases treated with mechanical ventilation or ECMO or admitted in intensive care unit (ICU)
   </td>
   <td>Cases treated with mechanical ventilation or ECMO or admitted in intensive care unit (ICU)
   </td>
  </tr>
  <tr>
   <td>COVID-19 Contacts
   </td>
   <td>Counts the number of relationships (‘has been in contact with’) created that are linked to the case TEI
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Deaths (all suspected cases)
   </td>
   <td>COVID-19 related deaths (deaths recorded among all suspected cases)
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Deaths (confirmed cases)
   </td>
   <td>COVID-19 related deaths (deaths recorded among confirmed cases)
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Deaths (probable cases)
   </td>
   <td>COVID-19 related deaths (deaths recorded among all probable cases)
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Confirmed Hospitalised Cases
   </td>
   <td>Number of confirmed cases that were admitted into hospital
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Imported Cases
   </td>
   <td>Cases where likely source of infection is recorded as another country or imported from another country.
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Laboratory confirmed cases
   </td>
   <td>Suspected cases that were confirmed through laboratory testing (multiple lab tests may be conducted; this indicator assumes that the last test result is "Positive"); displayed by report date
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Laboratory confirmed cases - by onset of symptoms
   </td>
   <td>Suspected cases that were confirmed through laboratory testing (multiple lab tests may be conducted; this indicator assumes that the last test result is "Positive"); displayed by date of onset of symptoms
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Laboratory tested cases
   </td>
   <td>Number of suspected cases that received a laboratory test (includes inconclusive lab testing results)
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Local transmission cases
   </td>
   <td>Number of suspected cases where transmission is local (no travel in last 14 days)
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Probable cases
   </td>
   <td>Suspected cases with inconclusive laboratory results or not tested for any reason, by reported date
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Probable cases - by onset of symptoms
   </td>
   <td>Suspected cases with inconclusive laboratory results or not tested for any reason, by date of onset of symptoms
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Recovered confirmed cases
   </td>
   <td>Number of laboratory confirmed cases with outcome recovered
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Suspected cases
   </td>
   <td>Total number of cases suspected with COVID-19, by report date
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Suspected cases - by onset of symptoms
   </td>
   <td>Total number of cases suspected with COVID-19, by date of onset of symptoms
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Suspected cases without a positive test result
   </td>
   <td>Total number of suspected cases without a positive lab result
   </td>
  </tr>
  <tr>
   <td>COVID-19 Total number of laboratory tests conducted
   </td>
   <td>Total number of lab tests conducted (count of tests, not cases)
   </td>
  </tr>
  <tr>
   <td>COVID-19 Total number of positive tests
   </td>
   <td>Total number of lab tests returned with positive results (count of tests, not cases)
   </td>
  </tr>
  <tr>
   <td>COVID-19 Deaths by sex and age group
   </td>
   <td>Male, 0-4, 5-14, 15-24, 25-34, 35-44, 45-54, 55-64, 65-74, 75-84, 85+
<p>
Female, 0-4, 5-14, 15-24, 25-34, 35-44, 45-54, 55-64, 65-74, 75-84, 85+
   </td>
  </tr>
  <tr>
   <td>COVID-19 Confirmed cases by sex and age group
   </td>
   <td>Male, 0-4, 5-14, 15-24, 25-34, 35-44, 45-54, 55-64, 65-74, 75-84, 85+
<p>
Female, 0-4, 5-14, 15-24, 25-34, 35-44, 45-54, 55-64, 65-74, 75-84, 85+
   </td>
  </tr>
  <tr>
   <td>COVID-19 Suspected cases by sex and age group
   </td>
   <td>Male, 0-4, 5-14, 15-24, 25-34, 35-44, 45-54, 55-64, 65-74, 75-84, 85+
<p>
Female, 0-4, 5-14, 15-24, 25-34, 35-44, 45-54, 55-64, 65-74, 75-84, 85+
   </td>
  </tr>
</table>

# Cas d'utilisation 2 : COVID-19 Enregistrement et suivi des contacts

This program can be used in addition to the case-based surveillance tracker to facilitate the registration and follow-up of contacts of a confirmed case. In this scenario, it is assumed that if any contacts of a confirmed case meet criteria for suspected case and are referred for testing, the case will be enrolled into the COVID-19 Case Surveillance tracker program.

The Contact registration & follow-up program registers each contact of a case (as described in COVID-19 Case Surveillance Use Case) as a new Tracked Entity Instance (person) and links them to the case in the COVID-19 Case Surveillance Program via a ‘relationship.’ It has a simple repeatable follow-up stage where symptoms and any follow-up undertaken can be registered.

## Flux de travail : Enregistrement des contacts et suivi

![alt_text](images/Copy-of5.png "image_tooltip")

## Description du programme : Enregistrement des contacts et suivi

<table>
  <tr>
   <td>Stage
   </td>
   <td>Description
   </td>
  </tr>
  <tr>
   <td><strong>Enrollment details</strong>
<p>
<strong>Attributes</strong>
   </td>
   <td>The Tracked Entity is represented by a Tracked Entity Type of ‘person.’
<p>
Related programs: COVID-19 Case based surveillance
<p>
Attributes include basic personal information and unique case identifiers
<ul>

<li>System Generated Case ID

<li>Local Case ID

<li>First Name

<li>Surname

<li>Date of birth

<li>Age

<li>Sex

<li>Phone number (local)

<li>Home Address

<li>Country of Residence
</li>
</ul>
   </td>
  </tr>
  <tr>
   <td><strong>Stage 1: \
Follow-Up</strong>
<p>
<strong>[non-repeatable]</strong>
   </td>
   <td>This stage is meant to record information related to contact tracing follow up, given that a contact has already been identified. It is divided into two sections:
<ol>

<li>Relation with case

<li>Exposure Assessment
</li>
</ol>
   </td>
  </tr>
  <tr>
   <td><strong>Stage 2: </strong>
<p>
<strong>Symptoms</strong>
<p>
<strong>[repeatable]</strong>
   </td>
   <td>This stage is intended to record symptoms of the case. Follow-up to check on the symptoms of a contact can be repeated until the follow-up period is complete (for example, after 14 days or according to national guidelines). When follow-up period is complete, the enrollment can be ‘completed.’
<ol>

<li>Symptoms
</li>
</ol>
   </td>
  </tr>
</table>

Les contacts sont ajoutés au cas index en utilisant le menu des relations du programme de surveillance des cas :

![alt_text](images/Copy-of6.png "image_tooltip")

Once you select “Add” from the relationships box, you are able to select the relationship and program and either select an existing person or enroll a new contact using the enrollment stage that appears. This will enroll the contact into the contact registration and follow-up program. \
Contacts that are added will then be listed on the case’s tracker dashboard in the relationship widget

You may also enroll them separately into the program. Once enrolled, you will be able to find them for the follow-up as required.

Enrôlement 

# Étape 1 du programme : Suivi 



<p id="gdcalert10" ><span style="color: red; font-weight: bold">>>>>>  alerte gd2md-html : lien vers l'image en ligne ici (les images/Copy-of8.png). Stockez l'image sur votre serveur d'images et ajustez le chemin d'accès/nom de fichier si nécessaire. </span><br>(<a href="#">Retourner en haut</a>)(<a href="#gdcalert11">Alerte suivante</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of7.png "image_tooltip")


Étape 2 du programme : Symptômes



<p id="gdcalert11" ><span style="color: red; font-weight: bold">>>>>>  alerte gd2md-html : lien vers l'image en ligne ici (les images/Copy-of8.png). Stockez l'image sur votre serveur d'images et ajustez le chemin d'accès/nom de fichier si nécessaire. </span><br>(<a href="#">Retourner en haut</a>)(<a href="#gdcalert12">Alerte suivante</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of8.png "image_tooltip")



## Indicateurs de programme : Enregistrement des contacts


<table>
  <tr>
   <td><strong>Program Indicator Name</strong>
   </td>
   <td><strong>Description</strong>
   </td>
  </tr>
  <tr>
   <td>COVID-19 travelers screened
   </td>
   <td>Total number of travelers screened and enrolled in screening program from POE
   </td>
  </tr>
  <tr>
   <td>COVID-19 travelers cleared at POE
   </td>
   <td>Number of travelers cleared after POE screening (no follow-up required)
   </td>
  </tr>
  <tr>
   <td>COVID-19 travelers with symptoms at POE
   </td>
   <td>Number of travelers presenting with symptoms during POE screening
   </td>
  </tr>
  <tr>
   <td>COVID-19 travelers cleared after 14 days monitoring
   </td>
   <td>Number of travelers that are cleared after 14 day follow up (no onset of symptoms during 14 day period)
   </td>
  </tr>
  <tr>
   <td>COVID-19 travelers referred to health facility
   </td>
   <td>Number of travelers that were referred to a health facility at any time during 14 day followup
   </td>
  </tr>
  <tr>
   <td>COVID-19 travelers enrolled for 14 day follow-up
   </td>
   <td>Number of travelers that did not present with symptoms at POE screening and were not cleared at POE screening
   </td>
  </tr>
  <tr>
   <td>COVID-19 currently under follow-up
   </td>
   <td>Number of travelers that have not been cleared or referred to a health facility
   </td>
  </tr>
  <tr>
   <td>COVID-19 travelers developed symptoms during follow-up
   </td>
   <td>Number of travelers that developed symptoms during follow-up (exclude travelers presenting with symptoms during POE screening)
   </td>
  </tr>
</table>



# Références



*   Conseils pour l'installation : [https://www.dhis2.org/covid-19](https://www.dhis2.org/covid-19)
*   Guide technique de l'OMS sur la surveillance et les définitions de cas de COVID-19 (dernière mise à jour le 20 mars 2020)

    [https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions)

*   Dictionnaire de données de l'OMS pour le formulaire de déclaration de cas de COVID-19

    [https://www.who.int/docs/default-source/coronaviruse/2020-02-27-data-dictionary-en.xlsx](https://www.who.int/docs/default-source/coronaviruse/2020-02-27-data-dictionary-en.xlsx)

*   WHO Laboratory testing for 2019 novel coronavirus (2019-nCoV) in suspected human cases (last updated 2 March 2020) [https://www.who.int/publications-detail/laboratory-testing-for-2019-novel-coronavirus-in-suspected-human-cases-20200117](https://www.who.int/publications-detail/laboratory-testing-for-2019-novel-coronavirus-in-suspected-human-cases-20200117)
*   WHO Considerations in the investigation of cases and clusters of COVID-19 (last updated 13 March 2020) [https://www.who.int/internal-publications-detail/considerations-in-the-investigation-of-cases-and-clusters-of-covid-19](https://www.who.int/internal-publications-detail/considerations-in-the-investigation-of-cases-and-clusters-of-covid-19)
*   Rapports de l'OMS sur la situation du coronavirus

    [https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports)
