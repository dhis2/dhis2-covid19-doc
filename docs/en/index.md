# COVID-19 Surveillance Digital Data Package

DHIS2 has released a digital data package to accelerate case detection, situation reporting, active surveillance and response for COVID-19. The package is inspired by the Ministry of Health Sri Lanka’s pioneering design of DHIS2 tracker for COVID-19 case detection and draws on years of collaboration with the World Health Organisation (WHO) to develop information system standards for case-based disease surveillance. The COVID-19 digital data package includes standard metadata aligned with the WHO’s [technical guidance on COVID-19 surveillance and case definitions](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions) and implementation guidance to enable rapid deployment in countries.

DHIS2 is currently being used for COVID-19 Surveillance in countries around the world. Explore the map below to see where the DHIS2 COVID-19 Packages are being tested and deployed..


## What can the DHIS2 COVID-19 Surveillance Package be used for?

The package supports surveillance workflows and automated analysis for key components of routine and active surveillance:

*   **COVID-19 Case-based surveillance [tracker]**: enrols & tracks suspected cases; captures symptoms, demographics, risk factors & exposures; creates lab requests; links confirmed cases with contacts; and monitors patient outcomes. This package can be installed as a standalone COVID-19 package or can be integrated into a country’s existing integrated disease surveillance & response tracker.
*   **Contact registration & follow-up program [tracker]**: strengthens active case detection through contact tracing activities, such as identification and follow-up of contacts of a suspected or confirmed COVID-19 case.
*   **Ports of Entry screening & follow-up program [tracker]**: enrols travellers who have visited high-risk locations at Ports of Entry for 14-day monitoring and follow-up.
*   **COVID-19 Surveillance Event Program [event]**:a simplified line-list that captures a subset of minimum critical data points to facilitate rapid analysis & response, particularly useful when caseloads or burden of reporting exceeds capacity for case-based surveillance tracker
*   **COVID-19 Aggregate Surveillance [aggregate]**: an aggregate reporting dataset that captures minimum necessary data points for daily or weekly reporting

All digital data packages are optimized for Android data collection with the DHIS2 Capture App, which is free to download on the [Google Play store](https://play.google.com/store/apps/details?id=com.dhis2&hl=en).

Do you work in a country that is interested in installing the DHIS2 COVID-19 tracker? Please contact us at [post@dhis2.org](mailto:post@dhis2.org).


## Test Out the DHIS2 COVID-19 Surveillance Demo

Explore the DHIS2 COVID-19 Surveillance Tracker on your own using our online demo database (login required): **[DHIS2 COVID-19 Surveillance Interactive Demo](https://covid.dhis2.org/demo)**

## Download the DHIS2 COVID-19 Surveillance Package

The following versions of the DHIS2 COVID-19 Surveillance Package are available for download and installation. The COVID-19 configuration package consists of DHIS2 metadata that provides a standard configuration of DHIS2 according to [the latest WHO recommendations available](https://www.who.int/emergencies/diseases/novel-coronavirus-2019/technical-guidance/surveillance-and-case-definitions)

See [v 0.3 package release notes](release-notes-v03.md) for a summary of updates and new components.

Please consult the following package-specific documents before you begin:

*   The **System Design Document** provides details about the use case and configuration of the package.
*   The **Installation Guide** provides guidance on preparing, importing and adapting the package.

The following online resources are also available:

*   The **[Tracker Implementation Guide](https://docs.dhis2.org/master/en/dhis2_tracker_implementation_guide/target-audience.html)** provides general guidance on planning a DHIS2 Tracker instance.
*   The **[Frequently Asked Questions](https://community.dhis2.org/t/frequently-asked-questions-faq/38690)** document provides answers to common questions about the package.
*   The **[COVID-19 Discussion and Support Channel](https://community.dhis2.org/c/implementation/covid-19/41)** on the DHIS2 Community of Practice is a forum where you can ask questions, get support for your implementation, and review issues that have been raised and resolved by other community members.

<table style="margin-bottom:1em;">
  <tr>
   <td>
<strong>DHIS2 Version</strong>
   </td>
   <td><strong>Package Version</strong>
   </td>
   <td><strong>Package Type</strong>
   </td>
   <td><strong>Documentation</strong>
   </td>
   <td><strong>Metadata</strong>
   </td>
   <td><strong>Last Updated</strong>
   </td>
  </tr>
  <tr>
   <td>2.33
   </td>
   <td>V 0.3.3
   </td>
   <td>COVID-19 Case-based Surveillance Tracker
<p>
COVID-19 Contact Registration and Follow-up Tracker
   </td>
   <td><a href="https://docs.google.com/document/d/12-pex7VOMoRAnsiIcTLq0mTD6UTSfVBZWIX0vufIt6I/edit?usp=sharing">System Design file</a>
<p>
<a href="installation-guide-tracker">Installation Guide</a>
   </td>
   <td><a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19/COVID19_TRACKER_V1_DHIS2.33/metadata.json">Metadata file</a>
   </td>
   <td>27 March 2020
   </td>
  </tr>
  <tr>
   <td>2.33
   </td>
   <td>V 0.3.2
   </td>
   <td>COVID-19 Surveillance Event Program
   </td>
   <td><a href="https://docs.google.com/document/d/1_OxdOmlPouNmoXD6FUEFZAgaPQARKUdrq0h0Gco4ARw/edit">System Design File</a>
<p>
<a href="installation-guide-event">Installation Guide</a>
   </td>
   <td> <a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_EVENT/COVID19_EVENT_TRACKER_V1_DHIS2.33/metadata.json">Metadata file</a>
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
   <td>COVID-19 Aggregate Surveillance
   </td>
   <td><a href="https://docs.google.com/document/d/1My2jVCAwPVA3j9m21xp0UCti--N8am9BXsYEjI7qn3I/edit#">System Design File</a>
<p>
<a href="installation-guide-aggregate">Installation guide</a>
   </td>
   <td><a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.30/metadata.json">2.30 Metadata File</a>
<p>
<a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.31/metadata.json">2.31 Metadata File</a>
<p>
<a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.32/metadata.json">2.32 Metadata File</a>
<p>
<a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.33/metadata.json">2.33 Metadata File</a>
   </td>
   <td>27 March 2020
   </td>
  </tr>
  <tr>
   <td>2.33
   </td>
   <td>V 0.3.1
   </td>
   <td>Points of Entry Screening Tracker
   </td>
   <td> <a href="https://drive.google.com/open?id=1PJ4iRJGmUBv6jF7hcACxt-dhd5JRpeBt0mKxgPBsmvc">System design file</a>
<p>
<a href="installation-guide-tracker">Installation Guide</a>
   </td>
   <td><a href="https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_POE/COVID19_POE_TRACKER_V1_DHIS2.33/metadata.json">Metadata file</a>
   </td>
   <td>27 March 2020
   </td>
  </tr>
</table>
