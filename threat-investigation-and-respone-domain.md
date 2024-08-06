---

copyright:
  years: 2024
lastupdated: "2024-08-06"

subcollection: pattern-vpc-security

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Threat Investigation and Response
{: #migration-design}

## Threat investigation
{: #other-logging-investigation}

Many security solutions have their own specific threat detection capabilities, e.g., NexGen firewalls.  Typically customers use a variety of logs and aggregate them and correlate them to provide a wholistic threat investigation picture.  The following discusses the possible logs that can be used for this purposes.

### {{site.data.keyword.cloudaccesstraillong}} – Identity and Access Management (IAM) logging
{: #activity-tracker-IAM-logging}

{{site.data.keyword.Bluemix_notm}}’s {{site.data.keyword.cloudaccesstraillong}} logs and records all administrator and API actions within an {{site.data.keyword.Bluemix_notm}} account.  This service can be used to investigate abnormal activities, for troubleshooting or forensics purposes and used for compliance audits.  This service provides such features as alerting, log storage encryption, compliance with the Cloud Auditing Data Federation (CADF) standard among others.  Logs from this service can also be forwarded externally to a Security Information Even Management (SIEM) for event correlation for threat detection.  More information on {{site.data.keyword.cloudaccesstraillong_notm}} can be found at the following link: [Learning about {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.cloudaccesstraillong}} architecture and workload isolation](/docs/activity-tracker?topic=activity-tracker-compute-isolation)

### Options
{: #activity-tracker-options}

There are no other {{site.data.keyword.Bluemix_notm}} IAM logging options, this is the default and built-in logging capability.

### Best practices
{: #activity-best-practices}

 - Use of {{site.data.keyword.cloudaccesstraillong}} auditing in regulated environment or compliance auditing is a must
 - Forwarding of {{site.data.keyword.cloudaccesstraillong_notm}} logs to a Security Event and Information Management (SIEM) platform, if a customer is using a SIEM
 - Use of {{site.data.keyword.cloudaccesstraillong}} auditing in regulated environment or compliance auditing is a must
 - Forwarding of {{site.data.keyword.cloudaccesstraillong_notm}} logs to a Security Event and Information Management (SIEM) platform, if a customer is using a SIEM
 - Regular reviews of user and API activity logs to determine any possible anomalies.

### Solutioning guidance
{: #activity-guidance}

 - [Getting started with {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.cloudaccesstraillong}}](/docs/activity-tracker?topic=activity-tracker-getting-started)
 - [About {{site.data.keyword.cloudaccesstraillong}} in {{site.data.keyword.Bluemix_notm}}](/docs/activity-tracker?topic=activity-tracker-about)
 - [Provisioning an instance](/docs/activity-tracker?topic=activity-tracker-provision)
 - [About {{site.data.keyword.cloudaccesstraillong}} in {{site.data.keyword.Bluemix_notm}}](/docs/activity-tracker?topic=activity-tracker-about)
 - [Provisioning an instance](/docs/activity-tracker?topic=activity-tracker-provision).

## Other logging for event correlation
{: #other-logging}

Logging plays a key role in security in that captures events that may be anomalous and when are correlated and analyzed, can detect a threat and other problems.  Logging can also play a role in compliance auditing. Several {{site.data.keyword.Bluemix_notm}} services create logs as noted in the below table:

| Logs                                                                                                                                | Function                                                                                                     |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| [VPC flow logs](/docs/vpc?topic=vpc-flow-logs)                                                                     | Provides logs of all ingress and egress traffic within a VPC.                                                     |
| [{{site.data.keyword.cloudaccesstraillong}}](/docs/activity-tracker?topic=activity-tracker-getting-started)                                  | As noted above this rovides logs of all administrator actions and API activities within an IBM account.                              |
| NexGen firewalls                                                                                                                    | Provides logs on a variety of functions / actions that occur within the firewalls, e.g., rule hits, alarms, and so on. Also note that most NexGen firewalls have their own portals where threats can be investigated|
| [{{site.data.keyword.cis_full_notm}} LogPush Service](/docs/cis?topic=cis-logpush&interface=ui)                                | Captures {{site.data.keyword.cis_short_notm}} firewall events.                                                                 |
| [Cloud workload protection Event Forwarding](/docs/workload-protection?topic=workload-protection-event_forwarding) | Forwards various events from the cloud workload protection solution.                                             |
{: caption="Table 1 : Available Logging"}

### Options
{: #logging-options}

 - VPC flow logs - There are no options if traffic capture in and out of a VPC is needed for security and troubleshooting purposes
 - {{site.data.keyword.cloudaccesstraillong}} - There are no options if logs are needed from IAM user and API actions for auditing, compliance or security reasons
 - NexGen firewalls - Customers can elect to capture and forward all kinds of logs.

### Best practices
{: #otherlogging-best-practices}

 - Logging of IAM user and API actions should always be used, regardless of the security situation.  These can be used for troubleshooting purposes and mandatory in compliance situations
 - Firewall logs should always be used for detection purposes, if deployed at the edge in a public access environment
 - Logging of IAM user and API actions should always be used, regardless of the security situation.  These can be used for troubleshooting purposes and mandatory in compliance situations
 - Firewall logs should always be used for detection purposes, if deployed at the edge in a public access environment
 - Use of VPC flow logs, Cloud Internet Services logs and Cloud Workload Protection logs is dependent upon the customer's use of a Security Information and Event Management (SIEM) platform and how many log feeds are sufficient and how much security inspection granularity.

### Solutioning guidance
{: #other-logging-guidance}

 - [Creating a flow log collector](/docs/vpc?topic=vpc-ordering-flow-log-collector&interface=ui)
 - [Provisioning an instance](/docs/workload-protection?topic=workload-protection-provision) (Workload Protection)
 - ({{site.data.keyword.cis_short_notm}}) [Cloud Internet Services provisioning an instance](/docs/workload-protection?)
 - [Creating a flow log collector](/docs/vpc?topic=vpc-ordering-flow-log-collector&interface=ui)
 - {{site.data.keyword.cloudaccesstraillong_notm}} [Using the Logpush service](/docs/cis?topic=cis-logpush&interface=ui).

## Threat detection
{: #threat-detection}

Threat detection in {{site.data.keyword.Bluemix_notm}} can occur in various places. NexGen firewalls deployed at the edge can detect anomalous traffic through their Intrusion Detection / Intrusion Protection (IDS/IPS) and other capabilities. NexGen firewalls have other detection mechanisms as well to include file and URL blocking, and so on.  {{site.data.keyword.Bluemix_notm}} Internet Services, which also operates at the Internet Edge, can detects threats at the application layer through its WAF capability. {{site.data.keyword.Bluemix_notm}} also has a workload protection, previous discussed which can detect runtime threats on workloads.  These are summarized below:

| Area / Solution                                                                                                                                                                                                                           | Detections                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| NexGen firewalls (see respective firewall documentation)                                                                                                                                                                                      | Anomalous traffic, blocked traffic, firewall rule hits, anomalous files, URLs, DNS queries, and so on. |
| [{{site.data.keyword.cis_short_notm}} (Cloud Internet Services)](/docs/cis?topic=cis-about-ibm-cloud-internet-services-cis)                                                                                                                               | Layer 7/ WAF detections                                                                          |
| Cloud workload protection   [About Workload Protection](/docs/workload-protection?topic=workload-protection-about) and [Key Features](/docs/workload-protection?topic=workload-protection-key-features) | Runtime threat detections and vulnerability discovery around virtual server instances.           |
{: caption="Table 2: Threat Detection - Available Methods"}

### Options
{: #detection-options}

 - NexGen Firewalls - This detection option can be deployed in public access situations at the edge.  This option can also be deployed in private access situations where customers want an additional level of threat detection to whatever security maybe on-prem. Finally, this option can be deployed in conjunction with {{site.data.keyword.cis_short_notm}} in certain situations
 - {{site.data.keyword.cis_full_notm}} -  This detection option can be deployed in public access situations at the edge. But this option in public environments is typically used where broader Content Delivery Networking (CDN) capabilities are needed. Customers would not necessarily deploy this in private situations and where content delivery network capabilities are not needed
 - Cloud Workload Protection - This detection option can be deployed where customers are using or will use {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.compliance_long}} This option may be needed where a customer just needs endpoint security, and particularly in public access environments.

### Best practices
{: #detection-best-practices}

- Threat detection capabilities should always be deployed in public situations as can be imagined
- Deployment in private situations dependent upon a customer risk profile
- Threat detections capability should be accompanied with trained personnel and appropriate processes
- Threat detections need to be correlated in some way, perhaps through a Security Event and Information Management (SIEM) platform, to triangulate attacks and get a holistic view of threats.

### Solutioning guidance
{: #detection-guidance}

- [Using the {{site.data.keyword.cis_short_notm}} setup Security Events capability](/docs/cis?topic=cis-using-the-cis-security-events-capability).
- [Getting started with {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.compliance_long}} Workload Protection](/docs/workload-protection?topic=workload-protection-getting-started)
- [Getting started with {{site.data.keyword.compliance_long}}]
- [Using the {{site.data.keyword.cis_short_notm}} setup Security Events capability](/docs/cis?topic=cis-using-the-cis-security-events-capability)
- [Getting started with {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.compliance_long}} Workload Protection](/docs/workload-protection?topic=workload-protection-getting-started)
- [Getting started with {{site.data.keyword.compliance_long](/docs/security-compliance?topic=security-compliance-getting-started)
- Please refer to the selected firewall product documentation on threat detection and how to configure it.

## Threat response
{: #response}

Security responses functions typically fall into two categories: those that are automated by a security capability and those that are broader in nature that involve people, processes and technologies, e.g., incident response. For the first category, {{site.data.keyword.Bluemix_notm}} has various security capabilities can take actions to stop or respond to a threat and these are outlined below. The broader incident response is discussed further down.

- NexGen Firewalls - Response - blocking traffic, files, URLs, DNS queries, and so on. plus all kinds of response alerts and alarms
- [{{site.data.keyword.cis_full_notm}}](/docs/cis?topic=cis-about-ibm-cloud-internet-services-cis) - Response - blocking various HTTP/HTTS traffic and domains and then notifications based upon events.

### Options
{: #response-options}

 - NexGen Firewalls -Customers have the option to get a variety response alerts and alarms based upon a variety of detection items and other firewall criteria
 - NexGen Firewalls -Customers have the option to get a variety response alerts and alarms based upon a variety of detection items and other firewall criteria
 - {{site.data.keyword.cis_short_notm}} - Customers have the options of getting and selecting different notifications based upon security events.

### Best practices
{: #response-best-practices}

- Procedures and processes to handle all the security notifications and alerts in a unified manner
- Personnel established and trained to respond to security events
- Having an established incident response plan
- Having an established incident response plan.

### Solutioning guidance
{: #response-best-guidance}

- [Configuring alert policies](/docs/cis?topic=cis-configuring-policies&interface=ui)
 (Cloud Internet Service)
- NexGen firewall response capability - please see the respective firewall documentation and how to set up possible responses.

## Broader incident response
{: #broader-incident-response}

The above information discussed security response capabilities in {{site.data.keyword.Bluemix_notm}}. But there are numerous broader solutions in the marketplace that handle security incident responses on a much larger scale to handle all aspects of risk exposure, people, process and technology when there is an event. IBM Cyber Security Services has a replete service in this area known as [IBM X-Force Incident Response Services](https://www.ibm.com/services/incident-response).  And there are other broader incident response solutions in the marketplace.

## Vulnerability management
{: #vulnerability-management}

Vulnerability testing and management can be quite broad but generally it involves tools that seek to uncover areas that can be exploited by attackers. For example, network vulnerability testing seeks to scan ports, protocols and IP addresses that are open for penetration, perhaps because of user misconfiguration. Often security configurations can “drift” over time because of some inadvertent user actions or changing needs. And there are other ways where vulnerabilities can develop, and which can be exposed. Below are some vulnerability testing/checking capabilities within {{site.data.keyword.Bluemix_notm}} and some other solutions:


| Area / Solution                                                                                                                                                            | Vulnerability checking / testing                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| {{site.data.keyword.compliance_long}}                                                                                                                                                 | Ability to scan resources for misconfigured settings per compliance requirements.                                                                                                                                                                                                                                                                                                                                                                                         |
| [Vulnerability Advisor](/docs/Registry?topic=Registry-va_index&interface=ui)               |Ability to scan container images. This vulnerability checking is really applicable where containers may be deployed on top of a Virtual Private Cloud (VPC) Virtual Service Instances (VSIs).                                                                                                                                                                                                                                                                            |
| Software and network vulnerability (the reader may want to refer to this link: [Scanning software for vulnerabilities](/docs/account?topic=account-scans)) | Various 3rd party market solutions are available, which can be deployed in {{site.data.keyword.Bluemix_notm}} on Virtual Server Instances (VSIs). IBM Cybersecurity Services (CSS) can source a number of solutions here including its preferred partner [Tenable](https://www.tenable.com/products/vulnerability-management). IBM CSS also has vulnerability management services known as [X-Force Red vulnerability management service](https://www.ibm.com/services/vulnerability-management). |
{: caption="Table 3: Vulnerability Management - Methods"}

### Options
{: #vulnerability-management-options}

 - {{site.data.keyword.compliance_long}} -  Customers have the option of choosing the resources and configurations they want to scan for vulnerabilities
 - Vulnerability Advisor - Customers can choose what images to scan and what exemptions there can be when a threat detection occurs
 - 3rd Party - Customers have the option of selecting and using a variety of vulnerability testing solutions and each of these have a myriad of configuration options.

### Best practices
{: #vulnerability-management-best-practices}

 - Customers should establish a vulnerability testing policy and plan and conduct regular vulnerability testing per the plan/policy
 - Processes, procedures and approval workflows for vulnerability remediations and similar should be well established.

### Solutioning guidance
 {: #vulnerability-management-guidance}

- [Best practices for working with {{site.data.keyword.compliance_long}}](/docs/security-compliance?topic=security-compliance-best-practices)
- [Configuring {{site.data.keyword.Bluemix_notm}} Vulnerability Advisor scans](/docs/devsecops?topic=devsecops-cd-devsecops-va-scans)
