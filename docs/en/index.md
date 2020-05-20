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

| DHIS2 Version                | Package Version | Package Type                                                 | Documentation                                                | Metadata                                                     | Last Updated  |
| ---------------------------- | --------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------- |
| 2.33                         | V 0.3.3         | COVID-19 Case-based Surveillance Tracker<br>COVID-19 Contact Registration and Follow-up Tracker | [System Design file][st33]<br>[Installation Guide][it33]| [Metadata file][mt33] | 27 March 2020 |
| 2.33                         | V 0.3.2         | COVID-19 Surveillance Event Program                          | [System Design file][se33]<br>[Installation Guide][ie33]| [Metadata file][me33] | 27 March 2020 |
| 2.30<br>2.31<br>2.32<br>2.33 | V 0.3.2         | COVID-19 Aggregate Surveillance                              | [System Design File][sa33]<br>[Installation guide][ia33] | [2.30 Metadata File][ma30]<br>[2.31 Metadata File][ma31]<br>[2.32 Metadata File][ma32]<br>[2.33 Metadata File][ma33] | 27 March 2020 |
| 2.33                         | V 0.3.1         | Points of Entry Screening Tracker                            | [System design file][sp33]<br>[Installation Guide][ip33] | [Metadata file][mp33] | 27 March 2020 |


[st33]: <https://docs.google.com/document/d/12-pex7VOMoRAnsiIcTLq0mTD6UTSfVBZWIX0vufIt6I/edit> 
[it33]: <tracker-packages-installation-guide.html>
[mt33]: <https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19/COVID19_TRACKER_V1_DHIS2.33/metadata.json>

[se33]: <https://docs.google.com/document/d/1_OxdOmlPouNmoXD6FUEFZAgaPQARKUdrq0h0Gco4ARw/edit> 
[ie33]: <event-package-installation-guide-v032.html>
[me33]: <https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_EVENT/COVID19_EVENT_TRACKER_V1_DHIS2.33/metadata.json>

[sa33]: <https://docs.google.com/document/d/1My2jVCAwPVA3j9m21xp0UCti--N8am9BXsYEjI7qn3I/edit#>
[ia33]: <aggregate-package-installation-guide.html>
[ma30]: <https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.30/metadata.json>
[ma31]: <https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.31/metadata.json>
[ma32]: <https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.32/metadata.json>
[ma33]: <https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_AGG/COVID19_AGG_COMPLETE_V1_DHIS2.33/metadata.json>

[sp33]: <https://drive.google.com/open?id=1PJ4iRJGmUBv6jF7hcACxt-dhd5JRpeBt0mKxgPBsmvc>
[ip33]: <tracker-packages-installation-guide.html>
[mp33]: <https://raw.githubusercontent.com/dhis2/metadata-package-development/work-in-progress/metadata/COVID19_POE/COVID19_POE_TRACKER_V1_DHIS2.33/metadata.json>
