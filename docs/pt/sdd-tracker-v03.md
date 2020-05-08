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



# **COVID-19 Case-based Surveillance & Contact Tracing Tracker System Design v0.3.3**

<ul style="text-align: right">
  <li style="list-style: none">Last updated 27/03/2020</li>
  <listyle="list-style: none">Package Version 0.3.3</li>
  <li style="list-style: none">DHIS2 Version compatibility 2.33.2 and above</li>
  <li style="list-style: none""> Demo: <a href="https://covid.dhis2.org/">https://covid.dhis2.org/</a></li>
</ul>

## Purpose

The COVID-19 Surveillance System Design document provides an overview of the conceptual design used to configure a COVID-19 digital data package in DHIS2. The COVID-19 package was developed in response to an expressed need from countries to rapidly adapt a solution for managing COVID-19 data. This document is intended for use by DHIS2 implementers at country and regional level to be able to support implementation and localisation of the package. The COVID-19 metadata package can be adapted to local needs and national guidelines. In particular, local work flows and national guidelines should be considered in the localization and adoption of the programs included in this package.


## Background

**This design has been updated to reflect new aggregate reporting requirements from the [WHO interim surveillance guidelines updated March 20, 2020](https://apps.who.int/iris/bitstream/handle/10665/331506/WHO-2019-nCoV-SurveillanceGuidance-2020.6-eng.pdf)**. The COVID-19 digital data package was developed in response to an expressed need from countries to rapidly adapt a solution for managing COVID-19 data. UiO has developed COVID-19 surveillance packages for three types of data models (tracker, event-based aggregate) to enable countries to select the model that is most appropriate for their context given the burden of disease and available resources. These models and their relative benefits/limitations are summarized below:


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


**This document covers only the design of the surveillance tracker program package**; separate system design documents are available for DHIS2 event and aggregate packages.

WHO is “urging all countries to prepare for the potential arrival of COVID-19 by readying emergency response systems; increasing capacity to detect and care for patients; ensuring hospitals have the space, supplies and necessary personnel; and developing life-saving medical interventions.”

The objectives of COVID-19 surveillance are:

1. to monitor trends of the disease where human to human transmission occurs;
2. rapidly detect new cases in countries where the virus is not circulating;
3. provide epidemiological information to conduct risk assessments at the national, regional and global level; and
4. provide epidemiological information to guide preparedness and response measures.

The system design builds upon existing case-based disease surveillance principles and information system requirements that have been developed collaboratively between the WHO and UiO since 2017. The COVID-19 surveillance package was developed with the intent to align to [WHO technical guidance on nCoV-19 surveillance and case definitions](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions), updated March 20, 2020.Note that this design may not necessarily reflect the latest available interim global guidance developed by WHO as updates may be released rapidly. National guidelines and policies may vary and it is recommended to adapt this package to local context.

## System Design Summary

The DHIS2 case-based surveillance tracker metadata was based on the **[WHO COVID-19 case reporting template](https://www.who.int/docs/default-source/coronaviruse/2020-02-27-data-dictionary-en.xlsx)** and the mapping of data dictionaries can be accessed at: [DHIS2 CBS tracker metadata WHO line-list data dictionary](https://drive.google.com/open?id=1vigXHkP7L2hJ2lrZpdf9u4csQtppMH16).

In the development of this configuration package, an effort has been made to follow UiO’s [general design principles](https://who.dhis2.org/documentation/general_design_principles.html) and a common [naming convention](https://who.dhis2.org/documentation/naming_convention.html).

The COVID-19 digital data package supports surveillance workflows and automated analysis for key components of routine and active surveillance. This package includes a Case Surveillance Tracker and a Contact registration & follow-up tracker, which are installed together in the same metadata package. The tracker programs are optimized to be installed with other COVID-19 surveillance packages, including the Points of Entry Screening Tracker and aggregate daily surveillance dataset.

1. **[COVID-19 Case-based surveillance tracker](https://docs.google.com/document/d/1-trbdYVS_9eUusicFdBzANuinlujMdJlNqb4zg0IKAI/edit#heading=h.q0mt1wyorc6m)**: enrolls & tracks suspected cases; captures symptoms, demographics, risk factors & exposures; creates lab requests; links confirmed cases with contacts; and monitors patient outcomes. This package can be installed as a standalone COVID-19 package or can be integrated into a country’s existing integrated disease surveillance & response tracker. Metadata for the case-based surveillance tracker is aligned with the WHO [COVID-19 surveillance data dictionary ](https://www.who.int/docs/default-source/coronaviruse/data-dictionary-covid-crf-v6.xlsx?sfvrsn=a7d4ef98_2)

        _n.b. The COVID-19 case-based tracker can be implemented either as a ‘standalone’ program for COVID-19 specific disease surveillance as described here; or, COVID-19 concepts can be integrated into an existing case-based surveillance tracker program if one already exists in-country. Please refer to installation and implementation guidance for more details._

2. **[Use Case 2: Contact registration & follow-up](#heading=h.62o76lajzaos)**: strengthens active case detection through contact tracing activities, such as identification and follow-up of contacts of a suspected or confirmed COVID-19 case.

Digital data packages are optimized for Android data collection with the DHIS2 Capture App, free to download on the [Google Play store](https://play.google.com/store/apps/details?id=com.dhis2&hl=en).

## Use Case 1: COVID-19 Case-based surveillance tracker

The COVID-19 case-based surveillance tracker can be adapted and used by countries to supplement existing national disease surveillance programs. The basic case surveillance program is designed to:

1. Enroll suspected* COVID-19 cases (_generally appearing at a health facility, but may be enrolled at other places_)
2. Capture key information about the suspected case including demographics and exposures, such as symptoms, contact with a previously confirmed case & travel history
3. Generate lab requests
4. Record laboratory diagnosis
5. Record contacts of a confirmed** or probable*** case for follow-up
6. Record case outcome
7. Facilitate case notification and national/regional/global case reporting
8. Generate dashboards and analytics tools for monitoring disease trends and planning response efforts

The design of the case-based tracker program assumes that [WHO case definitions](https://apps.who.int/iris/bitstream/handle/10665/331506/WHO-2019-nCoV-SurveillanceGuidance-2020.6-eng.pdf) are followed in the use case; its use can be adapted to local case definitions as needed. The WHO case definitions were updated on March 20, 2020 and noted below.

    _*Suspected case: A) a patient with acute respiratory illness (fever and at least one sign/symptom of respiratory disease (e.g., cough, shortness of breath), AND with no other aetiology that fully explains the clinical presentation AND a history of travel to or residence in a country/area or territory reporting local transmission of COVID-19 disease during the 14 days prior to symptom onset; **OR, **B) A patient with any acute respiratory illness AND having been in contact with a confirmed or probable COVID-19 case (see definition of contact) in the last 14 days prior to onset of symptoms; **OR,** C) A patient with severe acute respiratory infection (fever and at least one sign/symptom of respiratory disease (e.g., cough, shortness breath) AND requiring hospitalization AND with no other aetiology that fully explains the clinical presentation._

    _**Probable case: A) a suspect case for whom testing for COVID-19 is inconclusive (inconclusive being the result of the test reported by the laboratory) **OR,** B) a suspect case for whom testing could not be performed for any reason._

    _***Confirmed case: A person with laboratory confirmation of COVID-19 infection, irrespective of clinical signs and symptoms._

## Intended users

* Health facility users: capture and record details about a suspected case, including clinical symptoms & exposures; track lab results; record case outcome
* Laboratory users: receive lab requests and record laboratory results for a particular suspected case
* National and local health authorities: monitor and analyse disease surveillance data through dashboards and analytics tools to conduct risk assessments and plan response measures; generate reports for regional and global reporting


## Workflow: COVID-19 Case-based Surveillance Tracker


## Structure: COVID-19 Case Surveillance Tracker Program



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline drawings not supported directly from Docs. You may want to copy the inline drawing to a standalone drawing and export by reference. See <a href="https://github.com/evbacher/gd2md-html/wiki/Google-Drawings-by-reference">Google Drawings by reference</a> for details. The img URL below is a placeholder. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

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

### Enrollment

![alt_text](images/Copy-of0.png "image_tooltip")

#### Program Stage 1 -  Clinical Examination & Diagnosis

##### Section 1 - Clinical Signs and symptoms

Selecting “yes” to the Data Delement ‘Any signs or symptoms?’ reveals the rest of the options.

![alt_text](images/Copy-of1.png "image_tooltip")

##### Section 2 - Pregnancy Details

This section is hidden unless gender is selected as ‘Female.’

##### Section 3 - Underlying Conditions/Comorbidity

This section is hidden unless “Any underlying conditions” is marked as “Yes”. \

##### Section 4 - Hospitalisation

This section is hidden unless “Hospitalised” is marked as “Yes”.

##### Section 5  - Exposure Risk

This section is used to record exposures (fields are hidden by program rules if the case is not a health care worker; if the case has not had contact with a confirmed case in 14 days). A suspected case’s exposure to a *previously confirmed _case is distinct from prospective contact tracing in Program Stage 5.*

##### Section 6 - Travel History

#### Program Stage 2: Lab Request

![alt_text](images/Copy-of2.png "image_tooltip")

### Stage 3: Lab Results

![alt_text](images/Copy-of3.png "image_tooltip")

### Stage 4: Health Outcomes

![alt_text](images/Copy-of4.png "image_tooltip")

## Program Rules: COVID19 Case Surveillance Tracker

The following program rules have been configured. If a country has an existing case-based surveillance program and wishes to incorporate elements of the COVID-19 case-based tracker into their existing program, special attention must be paid to the configuration of program rules.

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


You can read more about program rules here:

[https://docs.dhis2.org/master/en/user/html/configure_program_rule.html](https://docs.dhis2.org/master/en/user/html/configure_program_rule.html)

## Program Indicators

From the data captured in the COVID-19 case surveillance program, we can calculate at least the following indicators including those recommended by the WHO for daily and weekly aggregate reporting and present them in a dashboard:

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

# Use Case 2: COVID-19 Contact registration & follow-up

This program can be used in addition to the case-based surveillance tracker to facilitate the registration and follow-up of contacts of a confirmed case. In this scenario, it is assumed that if any contacts of a confirmed case meet criteria for suspected case and are referred for testing, the case will be enrolled into the COVID-19 Case Surveillance tracker program.

The Contact registration & follow-up program registers each contact of a case (as described in COVID-19 Case Surveillance Use Case) as a new Tracked Entity Instance (person) and links them to the case in the COVID-19 Case Surveillance Program via a ‘relationship.’ It has a simple repeatable follow-up stage where symptoms and any follow-up undertaken can be registered.

## Workflow: Contact registration & follow-up

![alt_text](images/Copy-of5.png "image_tooltip")

## Program Description: Contact registration & follow-up

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

Contacts are added to the index case using the relationships menu in the case surveillance program:

![alt_text](images/Copy-of6.png "image_tooltip")

Once you select “Add” from the relationships box, you are able to select the relationship and program and either select an existing person or enroll a new contact using the enrollment stage that appears. This will enroll the contact into the contact registration and follow-up program. \
Contacts that are added will then be listed on the case’s tracker dashboard in the relationship widget

You may also enroll them separately into the program. Once enrolled, you will be able to find them for the follow-up as required.

Enrollment

# Program Stage 1 : Follow - Up



<p id="gdcalert10" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of7.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert11">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of7.png "image_tooltip")


Program Stage 2 : Symptoms



<p id="gdcalert11" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/Copy-of8.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert12">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/Copy-of8.png "image_tooltip")



## Program Indicators: Contact Registration


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



# References



*   Installation guidance: [https://www.dhis2.org/covid-19](https://www.dhis2.org/covid-19)
*   WHO Technical guidance on COVID-19 surveillance and case definitions (last updated 20 March 2020)

    [https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions)

*   WHO Data Dictionary for COVID-19 Case Reporting Form

    [https://www.who.int/docs/default-source/coronaviruse/2020-02-27-data-dictionary-en.xlsx](https://www.who.int/docs/default-source/coronaviruse/2020-02-27-data-dictionary-en.xlsx)

*   WHO Laboratory testing for 2019 novel coronavirus (2019-nCoV) in suspected human cases (last updated 2 March 2020) [https://www.who.int/publications-detail/laboratory-testing-for-2019-novel-coronavirus-in-suspected-human-cases-20200117](https://www.who.int/publications-detail/laboratory-testing-for-2019-novel-coronavirus-in-suspected-human-cases-20200117)
*   WHO Considerations in the investigation of cases and clusters of COVID-19 (last updated 13 March 2020) [https://www.who.int/internal-publications-detail/considerations-in-the-investigation-of-cases-and-clusters-of-covid-19](https://www.who.int/internal-publications-detail/considerations-in-the-investigation-of-cases-and-clusters-of-covid-19)
*   WHO Coronavirus situation reports

    [https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports)
