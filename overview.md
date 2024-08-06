---

copyright:
  years: 2024
lastupdated: "2024-08-06"

subcollection: pattern-vpc-security

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Introduction
{: #introduction}

Cloud security is a set of security measures that protect cloud-based data, applications, and infrastructure. It's a type of cyber security that involves both cloud providers and their clients. Cloud security protects against internal and external threats to business security and ensures that legal requirements are met.  This document provides an overview of {{site.data.keyword.cloud_notm}}’s security capabilities and then proceeds to discuss options, best practices and solutioning guidance associated with those capabilities.  The scope includes Virtual Private Cloud (VPC) Infrastructure as a Services (IaaS) security capabilities.  Security in other landing zones such as VMWare and OpenShift will be handled in future documents.

This document discusses security capabilities or solutions within {{site.data.keyword.Bluemix_notm}}, but other options like 3rd party solutions might be discussed that might be applicable to hybrid or multi-cloud situations. Some of the options might also include those from IBM cybersecurity Services (CSS). These are presented in the IBM cybersecurity Security Services (CSS) Capabilities section.

Overview information on general cloud security concepts can be found at <https://www.ibm.com/topics/cloud-security#:~:text=These%20principles%20are%20built%20on,security%20posture%20management%20(CSPM)>{: external}. Another reference source is the security section within the [{{site.data.keyword.Bluemix_notm}} Architecture Center.](https://mediacenter.ibm.com/channel/IBM+Cloud+Architecture+Center/182050661)

This document is geared toward cloud consultants, architects, engineers, and it assumes that the reader has a level of cloud proficiency and general knowledge of security concepts. For more information about general security concepts, see [add link](). This is not meant to be a cloud or security tutorial, or technically comprehensive with the particular security solutions mentioned.

Most of the links that are contained in this document refer to information in [{{site.data.keyword.Bluemix_notm}} Docs](/docs), which can provide deeper information on the various security services. Another reference source is the security section within the [{{site.data.keyword.Bluemix_notm}} Architecture Center.](https://mediacenter.ibm.com/channel/IBM+Cloud+Architecture+Center/182050661)

## General security best practices and solutioning guidance
{: #general-security-best-practices}

There are many different security best practices for cloud deployments, but one that is most prominent and important today is the overarching approach of the zero trust model. Zero trust has some key principles that should be considered in any security design. These principles include:

- Never trust, always verify
- Enforce least privilege access
- Enable strong authentication, and periodic and recurring authentication as possible
- Assume breaches everywhere and protect and detect accordingly
- Segment functions and related network areas to create security perimeters to limit blast radiuses of attacks
- Discover all possible resources, functions, components, and data that is used in an environment and ensure total visibility – you cannot secure what you cannot see.
- Use continuous security monitoring.

This paper shows how various {{site.data.keyword.Bluemix_notm}} security elements can be deployed following a zero trust approach. For more information, see the [National Institute of Standards and Technology paper](https://csrc.nist.gov/pubs/sp/800/207/final){: external}. Additional sources on zero trust principles and applications are available.

## Security solutions framework
{: #Security-Solutions-Framework}

{{site.data.keyword.IBM_notm}} uses a broad standard framework in all its security endeavore. Thi includes design, consulting, and implementation described in the following sections for reference. Now some, but not all of these are necessarily applicable for {{site.data.keyword.Bluemix_notm}} in Virtual Private Cloud environments from a technical capability perspective. Some of these capability categories can be broken down further and these are discussed in detail starting in the following sections.

![illustrates the security framework for IaaS Security white paper](images/securityframework.svg){: caption="Figure 1. IBM Security Framework" caption-side-"bottom"}

## IBM cybersecurity Security Services (CSS) capabilities: Options in certain situations
{: #CSS-capabilities}

{{site.data.keyword.IBM_notm}} cybersecurity Services is a specific business unit within {{site.data.keyword.IBM_notm}} that focuses specifically on security. They have a broad range of security solutions and associated consulting and managed services. The following table provides an overview of their solutions, and these can be considered additional options in {{site.data.keyword.Bluemix_notm}} that may be applicable in certain scenarios like hybrid or Multicloud situations.

Their separate consulting and managed service are not covered in the table. As {{site.data.keyword.Bluemix_notm}} security domains are discussed in the following sections, options in the domains are presented and some of those might be {{site.data.keyword.IBM_notm}} CSS solutions.
{: note}

 - Infrastructure and endpoint security: Various 3rd Party Firewalls, for example, Palo Alto and Cisco.
 - [QRadar Security Event and Information Management (SIEM), Network Detection and Response (NDR)](https://www.ibm.com/docs/en/qsip/7.5?topic=qradar-network-detection-response) {: external} Various 3rd parties
 - Endpoint Protection and Detection & Response (EPP/EDR) solutions [Qradar / ReaqTa](https://www.ibm.com/products/qradar-edr){: external} endpoint detection and response unified endpoint management
 - Unified Endpoint Management: [MaaS360](https://www.ibm.com/products/maas360/unified-endpoint-management){: external}
 - Data Security: [Guardium](https://www.ibm.com/guardium){: external} data security suite, for example, data classification, data loss prevention, and so on, [Cloud Pak for Data](https://www.ibm.com/products/cloud-pak-for-data){: external} [Guardium key lifecycle manager](https://www.ibm.com/products/ibm-security-key-lifecycle-manager){: external}
 - Privilege Access Management: [Verify Security Access Manager](https://www.ibm.com/verify?utm_content=SRCWW&p1=Search&p4=43700074603995210&p5=e&p9=58700008209808680&gbraid=0AAAAAD-_QsSZDEGKcMolwjQsuv8eqwjLo&gclid=Cj0KCQjwv7O0BhDwARIsAC0sjWOaQuEP0I2kLEyJl9wJ5UCNnM7uk8aP8K7aGQsntGk-6rP4o2ixZJ8aAnBzEALw_wcB&gclsrc=aw.ds)
 - Container security - 3rd Parties: Palo Alto Prisma Cloud and Illumio
