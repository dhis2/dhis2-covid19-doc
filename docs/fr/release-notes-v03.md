# COVID-19 Notes de mise à jour du progiciel v0.3

## Aperçu

Nous avons procédé à plusieurs mises à jour du paquet existant pour l'aligner sur les nouvelles directives de surveillance COVID-19 [publiées par l'OMS le 20 mars 2020] (https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions) et avons introduit de nouveaux éléments dans le paquet de soutien. Pour toute question, veuillez consulter les notes ici et nous contacter sur le forum de discussion COVID-19 dans la [communauté de pratique] (https://community.dhis2.org/c/implementation/covid-19/).

**Tous les paquets de métadonnées et la documentation peuvent être téléchargés à partir de [dhis2.org.covid-19](https://www.dhis2.org/covid-19).**

Les paquets sont actuellement traduits en français, en espagnol, en portugais et en russe, et d'autres langues sont en préparation (Arabe, Lao, Birman). Nous pouvons prendre en charge la traduction des paquets de métadonnées sur notre plateforme de traduction mondiale et inviter la communauté à contribuer si votre pays est intéressé par la traduction du paquet dans une nouvelle langue. [Consultez l'annonce de notre Communauté de pratique ](https://community.dhis2.org/t/the-new-dhis2-translation-platform-is-now-available/37755) et commencez à contribuer en tant que traducteur ici [en rejoignant la plateforme de traduction DHIS2](https://docs.dhis2.org/master/en/implementer/html/user-interface-localization.html#translation-server). Veuillez nous contacter à l'adresse suivante : translate@dhis2.org.

La nouvelle version comprend :

1. COVID-19 Programme Tracker de surveillance basée sur les cas (v0.3.3)
2. COVID-19 Programme d'enregistrement et de suivi des contacts (v0.3.2)
3. COVID-19 Programme de surveillance des événements (v0.3.2)
4. COVID-19 Rapport de surveillance globale (v0.3.2)
5. **NOUVEAU** Programme Tracker de dépistage aux points d'entrée (v0.3.1)

## COVID-19 Programme de surveillance basé sur les cas (Tracker)

1. Codes de métadonnées mis à jour afin de s'accorder avec [dictionnaire des données de déclaration basée sur des cas de l'OMS] (https://www.who.int/docs/default-source/coronaviruse/2020-02-27-data-dictionary-en.xlsx)
2. Les indicateurs de programme ont été mis à jour pour refléter les nouvelles définitions de cas de l'OMS pour les cas probables (référence aux définitions de cas mises à jour dans les directives de surveillance provisoires mises à jour le 20 mars 2020 [Directives de surveillance provisoires de l'OMS mises à jour le 20 mars 2020](https://apps.who.int/iris/bitstream/handle/10665/331506/WHO-2019-nCoV-SurveillanceGuidance-2020.6-eng.pdf))
3. Les légendes d'âge ont été mises à jour pour répondre aux nouvelles directives de l'OMS relatives à la déclaration hebdomadaire
4. Type de relation ajouté au procigiel de métadonnées
5. Modifications mineures apportées aux métadonnées pour faciliter l'installation du paquet (c'est-à-dire que l'indicateur de type UID correspond au type d'indicateur inclus dans l'ensemble d'agrégation)

## COVID-19 Programme d'enregistrement et de suivi des contacts (Tracker)

1. Une nouvelle étape du programme a été ajoutée pour permettre un "suivi" reproductible d'un cas de contact. Elle a été ajoutée pour refléter les flux de travail mis en œuvre en Ouganda et au Togo, où les contacts peuvent être régulièrement suivis pendant 14 jours pour déterminer s'il existe des symptômes. Le ***programme*** est basé sur les directives de l'OMS que pouvez consulter [ici](https://www.who.int/internal-publications-detail/considerations-in-the-investigation-of-cases-and-clusters-of-covid-19), ainsi que sur les informations obtenues via le site web [OpenWHO](https://openwho.org/courses/introduction-to-ncov)
2. Les légendes d'âge ont été mises à jour pour répondre aux nouvelles directives de l'OMS relatives à la déclaration hebdomadaire
3. Type de relation ajouté au progiciel de métadonnées
4. Modifications mineures apportées aux métadonnées pour faciliter l'installation du paquet

### COVID-19 Programme de déclaration d'événements

1. Règles du programme mises à jour pour éviter les erreurs lors de la soumission du formulaire en affichage sous forme de ligne (voir [Jira issue 8519](https://jira.dhis2.org/browse/DHIS2-8519))
2. Mise à jour des indicateurs du programme pour refléter les nouvelles définitions de cas de l'OMS
3. Les légendes d'âge ont été mises à jour pour répondre aux nouvelles directives de l'OMS relatives à la déclaration hebdomadaire
4. Modifications mineures apportées aux métadonnées pour faciliter l'installation du paquet

### COVID-19 Rapport de surveillance globale

Les mises à jour suivantes ont été effectuées pour tenir compte des nouvelles orientations contenues dans les [lignes directrices de l'OMS mises à jour le 20 mars 2020] (https://apps.who.int/iris/bitstream/handle/10665/331506/WHO-2019-nCoV-SurveillanceGuidance-2020.6-eng.pdf), y compris la mise à jour des rapports globaux à l'OMS (hebdomadaires et quotidiens)

1. Les catégories d'âge sont mises à jour en fonction des nouvelles tranches d'âge
2. De nouveaux indicateurs ont été ajoutés en ce qui concerne la proportion d'hommes parmi les cas confirmés et la proportion d'hommes parmi les décès confirmés
3. Le nouvel ensemble de données hebdomadaires pour saisir la classification de la transmission au premier niveau infranational (c'est-à-dire provincial -- peut être attribué à n'importe quel niveau infranational selon le cas dans le pays) selon les directives actualisées de l'OMS en matière de déclaration hebdomadaire
4. Modifications mineures apportées aux métadonnées pour faciliter l'installation du paquet

### **NOUVEAU** Programme Tracker des points d'entrée

Le cas d'utilisation du Programme Tracker des points d'entrée a été conçu dans le but de soutenir l'enregistrement des voyageurs entrant dans un pays ayant des antécédents de voyage ou de résidence dans un pays/une région/un territoire qui signalent une transmission locale de COVID-19 et qui peuvent avoir besoin d'être suivis pour s'assurer qu'aucun symptôme ne se développe. Il est basé sur la conception mise en œuvre par HISP Sri Lanka pour soutenir le ministère de la Santé du Sri Lanka avec des changements mineurs visant à rendre le programme plus générique en vue d'une utilisation mondiale et pour s'aligner sur les autres programmes Tracker du paquet COVID-19. Le programme vient en appui aux interventions aux points d'entrée détaillées dans les [directives techniques de l'OMS pour la gestion des personnes malades aux points d'entrée] (https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/points-of-entry-and-mass-gatherings).

Pour en savoir plus sur le programme PDE, veuillez consulter le [document de conception du système] (https://docs.google.com/document/d/1PJ4iRJGmUBv6jF7hcACxt-dhd5JRpeBt0mKxgPBsmvc/edit#).
