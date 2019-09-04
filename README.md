# App for Vulnerabilities

## Deprecation Warning!!!
__This app has been deprecated. There will be no new development or bug fixes. It has been replaced by the [Aplura Vulnerabilities App for Splunk](https://splunkbase.splunk.com/app/4230/).__

## Overview
This app provides Splunk dashboards, forms, and reports which can be used to explore your vulnerability events, and make sense of what can often be a large volume of data.

To do this, the app relies on the Splunk Common Information Model (CIM) for vulnerability events. This means that the app can report on any vulnerability data, as long as it has been on-boarded properly, and is available through the `Vulnerabilities` data model.

## A note on Splunk Data Model Acceleration and Disk Space
This app requires data model acceleration, which will use additional disk space. If you are using the Splunk App for Enterprise Security, this is already enabled, and should have been factored into your retention policies. If not, you should review the documentation on data model acceleration, how it uses disk space, and how to plan for it. This documentation can be found here: <http://docs.splunk.com/Documentation/Splunk/latest/Knowledge/Acceleratedatamodels#Data_model_summary_size_on_disk>

## A note on the Splunk Common Information Model
As mentioned above, the app uses the CIM for vulnerability events. The CIM allows you to take events from a number of sources or products, and report on them in one cohesive manner, using a common set of names for fields and event types.

## Available Dashboards and Forms
These are the dashboards and forms currently present in the app:

### Vulnerabilities Overview
This dashboard serves as a jumping-off point for exploring your vulnerability data. It includes panels for vulnerabilities over time, severities, destinations, and signatures. Clicking on panels in this dashboard will drill down to the appropriate profile page for further exploration.

### Severity Profile
Form with reports and visualizations built around a set of severities (Critical, High, Medium, Low, Informational, Unknown, or all).

### Dest Profile
Form with reports and visualizations built around a destination (host or IP address, depending on how your CIM information for your vulnerability management events is mapped).

### Signature Profile
Form with reports and visualizations built around a signature, such as "Terminal Services Encryption Level is Medium or Low" or "Buffer overrun in NT kernel message handling". Note that this is different than a CVE number, this is the text description of the vulnerability.

### Vulnerability Search
Form with many input variables. This is a flexible form designed to help generate a knockout list for fixing a set, or particular type of vulnerability.

### Identifier Search
Form for searching based on an identifier for a vulnerability, such as CVE, Cert, MSFT, or other reference number.

## Prerequisites

### Splunk Versions
This app has been tested with Splunk versions 6.4.x. This app should be installed on the same search head on which the vulnerability data model has been accelerated.

### Splunk Common Information Model Add-on
This app depends on data models included in the Splunk Common Information Model Add-on, specifically the `Vulnerabilities` data model. Information on installing and using the Splunk Common Information Model Add-on can be found here: <http://docs.splunk.com/Documentation/CIM/latest/User/Install>. Information on configuring the acceleration on the data model can be found here: <http://docs.splunk.com/Documentation/Splunk/latest/Knowledge/Acceleratedatamodels#Enable_persistent_acceleration_for_a_data_model>.

The Splunk Common Information Model Add-on can be downloaded from here: <https://apps.splunk.com/app/1621/>

This app has been tested with versions 4.x of the CIM add-on.

### Data model Acceleration on the Vulnerabilities data model
In order to make the app respond and load quickly, accelerated data models are used to provide summary data. For this data to be available, the `Vulnerabilities` data model must be accelerated. Information on how to enable acceleration for the Vulnerabilities data model can be found here: <http://docs.splunk.com/Documentation/Splunk/latest/Knowledge/Managedatamodels#Enable_data_model_acceleration>

## Installation
This app should be installed on a search head where the Vulnerabilities data model has been accelerated. More information on installing or upgrading Splunk apps can be found here: <http://docs.splunk.com/Documentation/Splunk/latest/Admin/Wheretogetmoreapps>

__Note__: This app will require a restart of Splunk.

## Simple Installation Process
1. Make sure the field extractions and tags on your proxy events are correct.
2. Install the Splunk Common Information Model Add-on (skip if you are installing on an ES search head).
3. Install the App for Vulnerabilities. Restart Splunk.
4. Enable accelerations on the `Vulnerabilities` data model (skip if you are installing on an ES search head).
5. Wait for the accelerations to start. After the acceleration searches have run, you should start seeing the dashboards populate.

## Macros for Configuration
This app uses the following macros which can be used for customization:

### vuln\_show\_severity
This macro can be used to make the app use a less strict approach to the CIM. The CIM defines what valid values for `severity`. If your data does not follow this, you can use this for adding other definitions.

## About support for this app
Support for this app is provided on a best-effort basis. We have released this app for free, and want to help solve issues, and add features, but we also have day-jobs.

Need help? Use the Splunk community resources! I can be found on many of them:

* [Splunk Answers](https://answers.splunk.com/)
* [#splunk on Efnet IRC](https://wiki.splunk.com/Community:IRC)
* [Splunk Slack channel](http://splunk402.com/chat/)

The git repo for this app is located [here](https://github.com/automine/app_for_vulnerabilities).

## Changes

### v1.3
* Added deprecation warning and link to replacement.

### v1.2
* Certification revisions
* Removed local.meta
* Removed linkView tag from SimpleXML files

### v1.1
* corrected the README

### v1.0
Initial release

## References

### Splunk Common Information Model
* Splunk Common Information Model Add-on Docs: <http://docs.splunk.com/Documentation/CIM/latest/User/Overview>
* splunk common information model add-on vulnerabilities data model: <http://http://docs.splunk.com/documentation/cim/latest/user/Vulnerabilities>

### Downloads
* Splunk Common Information Model Add-on Download: <https://apps.splunk.com/app/1621/>

## Credits
This app was created by David Shpritz of Aplura, LLC. <http://www.aplura.com/consulting.html>

Thanks to other members of the Splunk Professional Services team, as well members of the #splunk IRC on efnet <http://wiki.splunk.com/Community:IRC>

Icon made by Freepik from http://www.flaticon.com is licensed under CC BY 3.0.
