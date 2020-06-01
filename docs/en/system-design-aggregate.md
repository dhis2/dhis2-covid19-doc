<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 0; WARNINGs: 1; ALERTS: 6.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p><a href="#gdcalert1">alert1</a>
<a href="#gdcalert2">alert2</a>
<a href="#gdcalert3">alert3</a>
<a href="#gdcalert4">alert4</a>
<a href="#gdcalert5">alert5</a>
<a href="#gdcalert6">alert6</a>

<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>



# **COVID-19 Surveillance - Aggregate System Design Guide**

<p style="text-align: right">
Last updated 27/03/2020</p>


<p style="text-align: right">
Package Version 0.3.2</p>


<p style="text-align: right">
DHIS2 Version compatibility 2.30 - 2.33</p>


<p style="text-align: right">
Demo: <a href="https://covid.dhis2.org/">https://covid.dhis2.org/</a></p>



# Purpose 

The COVID-19 Surveillance Aggregate System Design document provides an overview of the design principles and guidance used to develop the digital data package for aggregate COVID-19 surveillance. This document is intended for use by DHIS2 implementers at country and regional level to be able to support implementation and localisation of the package. The COVID-19 metadata package can be adapted to local needs and national guidelines. In particular, local work flows and national guidelines should be considered in the localization and adoption of the programs included in this package.

# Background

**This aggregate design has been updated to reflect new aggregate reporting requirements from the [WHO interim surveillance guidelines updated March 20, 2020](https://apps.who.int/iris/bitstream/handle/10665/331506/WHO-2019-nCoV-SurveillanceGuidance-2020.6-eng.pdf).** The COVID-19 digital data package was developed in response to an expressed need from countries to rapidly adapt a solution for managing COVID-19 data. UiO has developed COVID-19 surveillance packages for three types of data models (tracker, event-based aggregate) to enable countries to select the model that is most appropriate for their context given the burden of disease and available resources. These models and their relative benefits/limitations are summarized below:

| Type of Surveillance Package| Case-based Surveillance (Tracker)| Case surveillance line-listing (Event)| Case surveillance (Aggregate)|
|---|---|---|---|
|***Description***| Enrolls a case and tracks over time through laboratory confirmation & case outcome| Captures critical case details in line-listing format| Enables daily or weekly reporting of key aggregate data points|
|***Pros***| Highly granular data and multiple time dimensions for analysis, can support decentralized workflow, all events linked to the case| More granular than aggregate and can capture key time dimensions (i.e. report date vs onset of symptoms); reduced burden of data entry compared to tracker and little complexity| Low complexity, easy to implement, most manageable when cases numbers are high|
|***Cons***| Burden of data entry may be overwhelming when number of cases reach threshold; complexity of implementation| Does not support case-follow up or other decentralized workflows| Less granularity for detailed analysis (i.e. analysis only based on case reporting date, limited disaggregation)|

**This document covers only the design of the aggregate package**; separate system design documents are available for DHIS2 Tracker and Line-listing (event-based) packages. As cases increase rapidly, some countries may struggle with case-based reporting as the burden becomes too high. The aggregate package is designed to meet the most critical reporting requirements and analytical capacities for surveillance and response.

The objectives of COVID-19 surveillance are:

1. to monitor trends of the disease where human to human transmission occurs;
2. rapidly detect new cases in countries where the virus is not circulating;
3. provide epidemiological information to conduct risk assessments at the national, regional and global level; and
4. provide epidemiological information to guide preparedness and response measures.

The system design builds upon existing disease surveillance principles and information system requirements that have been developed collaboratively between the WHO and UiO since 2017. The COVID-19 package was developed with the intent to align to [WHO technical guidance on nCoV-19 surveillance and case definitions](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions), last updated March 20, 2020. Note that this design may not necessarily reflect the latest available interim global guidance developed by WHO as updates may be released rapidly. National guidelines and policies may vary and it is recommended to adapt this package to local context.

# System Design Summary

In the development of this configuration package, an effort has been made to follow UiO’s [general design principles](https://who.dhis2.org/documentation/general_design_principles.html) and a common [naming convention](https://who.dhis2.org/documentation/naming_convention.html).

The aggregate COVID-19 surveillance package includes

1. Daily aggregate data set and data elements for key COVID-19 surveillance reporting
2. Weekly dataset for reporting sub-national classification of transmission
3. Core indicators 
4. Dashboard 

The dataset captures a minimum number of data points that meet the current WHO daily and weekly reporting requirements; and generate a core set of indicators and dashboards for national and sub-national decision-makers to rapidly analyze and respond to disease trends. 


<table>
  <tr>
   <td><strong>Name</strong>
   </td>
   <td><strong>Periodicity</strong>
   </td>
   <td><strong>Purpose</strong>
   </td>
  </tr>
  <tr>
   <td>COVID-19 Surveillance Report
   </td>
   <td>Daily 
   </td>
   <td>Reporting of key COVID-19 surveillance data including cases, tests and deaths. 
   </td>
  </tr>
  <tr>
   <td>COVID-19 Weekly Provincial (or sub-national) Report
   </td>
   <td>Weekly
   </td>
   <td>Reporting of transmission classification by sub-national level (no cases, sporadic cases, clusters of cases, community transmission)
   </td>
  </tr>
</table>


It is recommended that the daily dataset is assigned to Organisation Units at the lowest level of the health system feasible for reporting data, such as health facility. The weekly dataset should be assigned at least to Subnational/Admin Level 1 (i.e. province, region, state), but may be assigned lower levels (i.e. district) as determined by the country. 

Digital data packages are optimized for Android data collection with the DHIS2 Capture App, free to download on the [GooglePlay store](https://play.google.com/store/apps/details?id=com.dhis2&hl=en). 


## Intended users



*   Health facility users: capture and report key data on COVID-19 cases and deaths presenting at the health facility
*   Surveillance officers: surveillance officers at national and sub-national level may be responsible for supporting data entry and analysis. The weekly transmission classification report is based on an assessment of the type of transmission occurring at sub-national levels. 
*   National and local health authorities: monitor and analyse disease surveillance data through dashboards and analytics tools to conduct risk assessments and plan response measures; generate reports for regional and global reporting


# Datasets

This dataset is intended to capture daily data needed for rapid response to disease transmission. If the burden of reporting becomes too great or when it is no longer considered an emergency situation in country, the data set may be changed to weekly according to MOH policies. 


### Daily Surveillance Data Elements 

The following lists the data elements and disaggregation (category combinations) included in the data set:


<table>
  <tr>
   <td><strong>Data Elements</strong>
   </td>
   <td><strong>Category Combinations</strong>
   </td>
  </tr>
  <tr>
   <td>Number of new probable cases
   </td>
   <td>Gender (M/F) and Age (0-1, 2-4, 5-14, 15-49, 50-64, 65-79, 80+ years)
   </td>
  </tr>
  <tr>
   <td>Number of new confirmed cases
   </td>
   <td>Gender (M/F) and Age (0-1, 2-4, 5-14, 15-49, 50-64, 65-79, 80+ years)
   </td>
  </tr>
  <tr>
   <td>Number of recovered cases
   </td>
   <td>Gender (M/F) and Age (0-1, 2-4, 5-14, 15-49, 50-64, 65-79, 80+ years)
   </td>
  </tr>
  <tr>
   <td>Number of new deaths
   </td>
   <td>Gender (M/F) and Age (0-1, 2-4, 5-14, 15-49, 50-64, 65-79, 80+ years)
   </td>
  </tr>
  <tr>
   <td>Number of cases tested
   </td>
   <td>None
   </td>
  </tr>
  <tr>
   <td>Number of new cases hospitalised
   </td>
   <td>None
   </td>
  </tr>
  <tr>
   <td>Number of new cases by treatment type
   </td>
   <td>Treatment type: Mechanical ventilation/ECMO/Admitted into ICU
   </td>
  </tr>
  <tr>
   <td>Probable cases by transmission classification
   </td>
   <td>Transmission classification: Imported/Known cluster/Community Transmission/Unknown
   </td>
  </tr>
  <tr>
   <td>Confirmed cases by transmission classification
   </td>
   <td>Transmission classification: Imported/Known cluster/Community Transmission/Unknown
   </td>
  </tr>
</table>

### Daily Surveillance Data Entry Form

**Section 1: New cases, recoveries and deaths**

Data should be entered for new cases reported during the reporting period. Confirmed cases refer to laboratory confirmed cases per WHO guidance; probable cases are defined by WHO as cases where laboratory test result is inconclusive; however countries may apply their own case definitions. The total column is automatically summed during data entry.

## 

![alt_text](resources/images/image1.png "image_tooltip")

**Section 2: Cases tested and hospitalized **

This section captures the number of cases that received a laboratory test or were admitted into the hospital.

<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/19-Aggregate1.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/19-Aggregate1.png "image_tooltip")

**Section 3: Cases treated by treatment type**

While many cases are not treated in the hospital, WHO recommends to capture data for patients -- usually those with severe symptoms --  who are treated with mechanical ventilation, Extracorporeal membrane oxygenation (ECMO), or admitted into intensive care unit (ICU). 

<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/19-Aggregate2.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/19-Aggregate2.png "image_tooltip")

**Section 4: Transmission classification**

This section summarizes cases by suspected type of transmission. 

<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/19-Aggregate3.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/19-Aggregate3.png "image_tooltip")

### Weekly Transmission Classification Data Elements 

<table>
  <tr>
   <td><strong>Data Elements</strong>
   </td>
   <td><strong>Data type</strong>
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Transmission pattern (No cases)
   </td>
   <td>Yes only
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Transmission pattern (Sporadic cases)
   </td>
   <td>Yes only
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Transmission pattern (Cluster cases)
   </td>
   <td>Yes only
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Transmission pattern (Community cases)
   </td>
   <td>Yes only
   </td>
  </tr>
</table>


WHO guidelines classify transmission as follows:


### 

<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/19-Aggregate4.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/19-Aggregate4.png "image_tooltip")



### Weekly Transmission Classification Data Entry Form



<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/19-Aggregate5.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/19-Aggregate5.png "image_tooltip")



### Customizing Data Entry Forms

The dataset in this package does not contain a custom form. To improve the usability of the form for data entry, implementers may design a custom form to meet their needs by following the DHIS2 User manual: [https://docs.dhis2.org/2.33/en/user/html/dhis2_user_manual_en_full.html#manage_customform](https://docs.dhis2.org/2.33/en/user/html/dhis2_user_manual_en_full.html#manage_customform)


# Data Validation 

The following data validation rules have been configured. These validation rules do not run in the data entry form itself as it is anticipated that the urgent reporting of data where events occur in different time frames (e.g. one week can see only 3 new cases but 5 deaths).


<table>
  <tr>
   <td><strong>Name</strong>
   </td>
   <td><strong>Operator</strong>
   </td>
   <td><strong>Instruction</strong>
   </td>
   <td><strong>Left side description</strong>
   </td>
   <td><strong>Right side description</strong>
   </td>
  </tr>
  <tr>
   <td>COVID-19 - New Cases tested &lt;= All New Cases
   </td>
   <td>less_than_or_equal_to
   </td>
   <td>New cases tested should be less than or equal to All new cases reported
   </td>
   <td>New Cases tested
   </td>
   <td>All New Cases
   </td>
  </tr>
  <tr>
   <td>COVID-19 - New Cases hospitalised &lt;= All New Cases
   </td>
   <td>less_than_or_equal_to
   </td>
   <td>New Cases hospitalised should be less than or equal to All new cases reported
   </td>
   <td>New Cases hospitalised
   </td>
   <td>All New Cases
   </td>
  </tr>
  <tr>
   <td>COVID-19 - New cases treated &lt;= All New Cases
   </td>
   <td>less_than_or_equal_to
   </td>
   <td>New Cases hospitalised should be less than or equal to All new cases reported
   </td>
   <td>New cases treated
   </td>
   <td>All New Cases
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Probable cases by transmission classification &lt;= New probable cases (sex/age)
   </td>
   <td>less_than_or_equal_to
   </td>
   <td>Probable cases by transmission classification should be less than or equal to New probable cases (sex/age)
   </td>
   <td>Probable cases by transmission classification
   </td>
   <td>New probable cases (sex/age)
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Confirmed cases by transmission classification &lt;= New confirmed cases (sex/age)
   </td>
   <td>less_than_or_equal_to
   </td>
   <td>Confirmed cases by transmission classification should be less than or equal to New confirmed cases (sex/age)
   </td>
   <td>Confirmed cases by transmission classification
   </td>
   <td>New confirmed cases (sex/age)
   </td>
  </tr>
</table>



# User Groups

The following user groups are included in the metadata package:



1. COVID19 admin -- intended for system admins to have metadata edit rights
2. COVID19 data capture -- intended for data entry staff to have access to capture data
3. COVID19 access -- intended for users such as analytics users who should be able to view the data, but not edit metadata. 

Please refer to the installation guidance for more information. 


# Indicators

From the data captured, we can calculate at least the following indicators -- many of which are recommended by the WHO for [daily and weekly reporting](https://apps.who.int/iris/bitstream/handle/10665/331506/WHO-2019-nCoV-SurveillanceGuidance-2020.6-eng.pdf)-- and present them in a dashboard. All COVID-19 program indicators are assigned to the Indicator Group ‘COVID-19’.


<table>
  <tr>
   <td><strong>Indicator Name</strong>
   </td>
   <td><strong>Indicator description</strong>
   </td>
  </tr>
  <tr>
   <td>COVID-19 case fatality rate
   </td>
   <td>Numerator: COVID-19 deaths
<p>
Denominator: Confirmed+probable cases
   </td>
  </tr>
  <tr>
   <td>COVID-19 Recovered cases
   </td>
   <td>Number of cases reported recovered
   </td>
  </tr>
  <tr>
   <td>COVID-19 Active cases
   </td>
   <td>(Confirmed + probable cases) minus (deaths + recoveries). <em>Note this indicator only estimates active cases as time frames can be altered by the reporting period and analytics period. </em>
   </td>
  </tr>
  <tr>
   <td>COVID-19 Closed cases
   </td>
   <td>Number of deaths + recoveries. <em>Note this indicator only estimates active cases as time frames can be altered by the reporting period and analytics period. </em>
   </td>
  </tr>
  <tr>
   <td>COVID-19 Cases treated by mechanical ventilation or ECMO or ICU
   </td>
   <td>Number of suspected cases that received mechanical ventilation, ECMO or admitted into intensive care unit
   </td>
  </tr>
  <tr>
   <td>COVID-19 Deaths
   </td>
   <td>COVID-19 deaths reported
   </td>
  </tr>
  <tr>
   <td>COVID-19 Hospitalised Cases
   </td>
   <td>Number of cases that were admitted into hospital
   </td>
  </tr>
  <tr>
   <td>COVID-19 Laboratory confirmed cases
   </td>
   <td>Reported laboratory confirmed cases
   </td>
  </tr>
  <tr>
   <td>COVID-19 Suspected cases
   </td>
   <td>Suspected cases not laboratory confirmed (according to WHO or country case definitions)
   </td>
  </tr>
  <tr>
   <td>COVID-19 Proportion of males among confirmed cases (%)	
   </td>
   <td>Numerator: confirmed cases that are male
<p>
Denominator: confirmed cases where sex is known
   </td>
  </tr>
  <tr>
   <td>COVID-19 Proportion of males among deaths (%)	
   </td>
   <td>Numerator: confirmed case deaths that are male
<p>
Denominator: total confirmed case deaths where sex is known
   </td>
  </tr>
  <tr>
   <td>COVID-19 Laboratory tested cases
   </td>
   <td>Number of suspected cases that received a laboratory test (regardless of test result)
   </td>
  </tr>
  <tr>
   <td>COVID-19 Imported Cases
   </td>
   <td>Probable and confirmed cases by transmission type: Imported.
<p>
Cases where a likely source of infection is recorded as another country or imported from another country. [Some countries may additionally define cases as imported from <em>within</em> the country]
   </td>
  </tr>
  <tr>
   <td>COVID-19 Cases infected by local transmission
   </td>
   <td>Probable and confirmed cases by transmission type: Known cluster + community transmission
<p>
Cases where infection is suspected to have occurred locally, not in another country. [Some countries may additionally define local cases according to sub-national geography and may include or alter this indicator]
   </td>
  </tr>
  <tr>
   <td>COVID-19 Cases infected by community transmission
   </td>
   <td>Probable and confirmed cases by transmission type: community transmission.
<p>
Cases where infection is suspected to have occurred through community spread
   </td>
  </tr>
  <tr>
   <td>COVID-19 Cases linked to known cluster
   </td>
   <td>Probable and confirmed cases by transmission type: Known cluster.
<p>
Cases where infection is suspected to have occurred by linkage to a known cluster of cases
   </td>
  </tr>
  <tr>
   <td>COVID-19 Cases exposure unknown
   </td>
   <td>Probable and confirmed cases by transmission type: Unknown
<p>
Cases where source of infection or exposure is unknown
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Provinces/regions with Transmission pattern (No cases)
   </td>
   <td>Territories/areas with no cases
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Provinces/regions with Transmission pattern (Sporadic cases)
   </td>
   <td>Territories/areas with one or more cases, imported or locally detected
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Provinces/regions with Transmission pattern (Cluster cases)
   </td>
   <td>Territories/areas experiencing cases, clustered in time, geographic location and/or by common exposures
   </td>
  </tr>
  <tr>
   <td>COVID-19 - Provinces/regions with Transmission pattern (Community cases)
   </td>
   <td>Area/territories experiencing larger outbreaks of local transmission defined through an assessment of factors including, but not limited to:
<p>
- Large numbers of cases not linkable to transmission chains
<p>
- Large numbers of cases from sentinel lab surveillance
<p>
- Multiple unrelated clusters in several areas of the country/territory/area
   </td>
  </tr>
</table>



# References



*   Installation guidance: [https://www.dhis2.org/covid-19](https://www.dhis2.org/covid-19)
*   WHO Interim guidelines on nCoV-19 surveillance & case definitions (last updated March 20, 2020)

    [https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions)

*   WHO COVID-19 surveillance data dictionary (v6)	[https://www.who.int/docs/default-source/coronaviruse/data-dictionary-covid-crf-v6.xlsx?sfvrsn=a7d4ef98_2](https://www.who.int/docs/default-source/coronaviruse/data-dictionary-covid-crf-v6.xlsx?sfvrsn=a7d4ef98_2)
*   WHO Laboratory testing for 2019 novel coronavirus (2019-nCoV) in suspected human cases (last updated 2 March 2020) [https://www.who.int/publications-detail/laboratory-testing-for-2019-novel-coronavirus-in-suspected-human-cases-20200117](https://www.who.int/publications-detail/laboratory-testing-for-2019-novel-coronavirus-in-suspected-human-cases-20200117)
*   WHO Coronavirus situation reports

    [https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/situation-reports)