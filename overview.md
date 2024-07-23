---

copyright:
  years: 2024
lastupdated: "2024-07-23"

subcollection: pattern-vpc-security

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Infrastructure as a Service (IaaS) Security in VPC Environments
{: #IaaS-security-whitepaper}


## Introduction
{: #introduction}

This paper provides an overview of {{site.data.keyword.cloud_notm}}’s security capabilities and then proceeds to discuss options, best practices and solutioning guidance associated with those capabilities.  But note this paper only discusses Virtual Private Cloud (VPC) Infrastructure as a Services (IaaS) security capabilities.  Security in other areas such as VMWare and OpenShift will be handled in different papers.

This document is geared towards cloud consultants, architects, engineers, etc. and it assumes that the reader has a level of cloud proficiency and general knowledge of security concepts.  This paper is not meant to be a cloud or security tutorial, nor is it meant to be technically comprehensive with the particular security solutions noted.

Note that most of the links in this paper refer to information in [{{site.data.keyword.Bluemix_notm}} Docs](/docs), which can provide deeper information on the various security services. Another reference source is the security section within the [{{site.data.keyword.Bluemix_notm}} Architecture Center.](https://mediacenter.ibm.com/channel/IBM+Cloud+Architecture+Center/182050661)

This paper primarily discusses security capabilities or solutions within {{site.data.keyword.Bluemix_notm}}. But other options, e.g., 3rd party solutions, may be discussed that could be applicable hybrid or multi-cloud situations.  Some of the options may also include those from IBM Cyber Security Services (CSS). These are first presented in the following IBM Cybersecurity Security Services (CSS) Capabilities.

## General Security Best Practices and Solutioning Guidance
{: #general-security-best-practices}

There are many different security best practices for cloud deployments, but one that is most prominent and important today is the overarching approach of zero trust.  Zero trust has a number of key principles that should be considered in any security design. These principles include:

-   Never trust, always verify,
-   Enforce least privilege access,
-   Enable strong authentication, and periodic / recurring authentication as possible,
-   Assume breaches everywhere and protect and detect accordingly,
-   Segment functions and related network areas to create security perimeters to limit blast radiuses of attacks,
-   Discover all possible resources, functions, components and data used in an environment and ensure total visibility – **you cannot secure what you cannot see**, and
-   Use continuous security monitoring.

Please refer to the following National Institute of Standards and Technology paper for more information on Zero Trust: <https://csrc.nist.gov/pubs/sp/800/207/final>{: external}.  And there is many other web sources on zero trust principles and applications. This paper will show how various {{site.data.keyword.Bluemix_notm}} security elements can be deployed following a Zero Trust approach.

## Security Solutions Framework
{: #Security-Solutions-Framework}

IBM uses a broad standard framework in all its security endeavors, e.g., design, consulting, implementation, etc. and this is shown below for reference. Now some, but not all of these are necessarily applicable for {{site.data.keyword.Bluemix_notm}} in Virtual Private Cloud environments from a technical capability perspective. This paper therefore will only cover the capabilities highlighted in blue. And note that some of these capability categories can be broken down further and these are discussed in detail starting in following sections.

![illustrates the security framework for IaaS Security Whitepaper](images/securityframework.svg){: caption="Figure 1. IBM Security Framework" caption-side-"bottom"}

## IBM Cybersecurity Security Services (CSS) Capabilities – Options in Certain Situations
{: #CSS-capabilities}

IBM Cybersecurity Services is a specific business unit within IBM that focuses specifically on security. They have a broad range of security solutions and associated consulting and managed services. The table below provides an overview of their solutions, and these can be considered additional options in {{site.data.keyword.Bluemix_notm}} that may be applicable in certain scenarios, e.g., hybrid or mult-cloud situations. Note: their separate consulting and managed service are not covered here. As {{site.data.keyword.Bluemix_notm}} security domains are discussed in the following sections, options in the domains will be presented and some of those could be IBM CSS solutions.

 - **Infrastructure & Endpoint Security** - Various 3rd Party Firewalls, e.g., Palo Alto, Cisco, etc.
 - **QRadar Security Event & Information Management (SIEM), Network Detection and Response (NDR)**(https://www.ibm.com/docs/en/qsip/7.5?)topic=qradar-network-detection-responseVarious 3rd party
 - **Endpoint Protection / Detection & Response (EPP/EDR) solutions** [Qradar / ReaqTa](https://www.ibm.com/products/qradar-edr){: external} endpoint detection and response  unified endpoint management
 - **Unified Endpoint Management** - [MaaS360](https://www.ibm.com/products/maas360/unified-endpoint-management){: external}
 - **Data Security** - [Guardium](https://www.ibm.com/guardium){: external} data security suite, e.g., data classification, data loss prevention, etc. [CloudPak for Data](/docs/en/cloud-paks/cp-data/4.8.x?topic=overview){: external} [Guardium key lifecycle manager](https://www.ibm.com/products/ibm-security-key-lifecycle-manager){: external}
 - **Privilege Access Management** - **Verify** security access manager [Verify}](https://www.ibm.com/verify?utm_content=SRCWW&p1=Search&p4=43700074603995210&p5=e&p9=58700008209808680&gbraid=0AAAAAD-_QsSZDEGKcMolwjQsuv8eqwjLo&gclid=Cj0KCQjwv7O0BhDwARIsAC0sjWOaQuEP0I2kLEyJl9wJ5UCNnM7uk8aP8K7aGQsntGk-6rP4o2ixZJ8aAnBzEALw_wcB&gclsrc=aw.ds)
 - **Container Security** - 3rd Parties – Palo Alto Prisma Cloud & Illumio
