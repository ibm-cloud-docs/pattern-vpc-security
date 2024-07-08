---

copyright:
  years: 2024
lastupdated: "2024-07-08"

subcollection: pattern-vpc-security

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# overview
{: #overview}

# IaaS Security in VPC Environments
{: #IaaS-security-whitepaper}


## Introduction
{: #introduction}

This paper provides an overview of {{site.data.keyword.Bluemix_notm:}}’s security capabilities and then proceeds to discuss options, best practices and solutioning guidance associated with that capability.  But note this paper only discusses Virtual Private Cloud (VPC) Infrastructure as a Services (IaaS) security capabilities.  Security in other areas such as VMWare and OpenShift will be handled in different papers.

This document is geared towards cloud consultants, architects, engineers, etc. and it assumes that the reader has a level of cloud proficiency and general knowledge of security concepts.  This paper is not meant to be a cloud or security tutorial, nor is it meant to be technically comprehensive with the particular security solutions noted.

Note that most of the links in this paper refer to information in [{{site.data.keyword.Bluemix_notm:}} Docs](https://docs), which can provide deeper information on the various security services. Another reference source is the security section within the [{{site.data.keyword.Bluemix_notm:}} Architecture Center.](https://www.ibm.com/cloud/architecture/search/)

This paper primarily discusses security capabilities or solutions within {{site.data.keyword.Bluemix_notm:}}. But other options, e.g., 3rd party solutions, may be discussed that could be applicable hybrid or multi-cloud situations.  Some of the options may also include those from IBM Cyber Security Services (CSS). These are first presented in Section 4, IBM Cybersecurity Security Services (CSS) Capabilities.

## General Security Best Practices and Solutioning Guidance
{: #general-security-best-practices}

There are many different security best practices for cloud deployments, but one that is most prominent and important today is the overarching approach of zero trust.  Zero trust has a number of key principles that should be considered in any security design. These principles include:

-   Never trust, always verify.
-   Enforce least privilege access.
-   Enable strong authentication, and periodic / recurring authentication as possible.
-   Assume breaches everywhere and protect and detect accordingly.
-   Segment functions and related network areas to create security perimeters to limit blast radiuses of attacks.
-   Discover all possible resources, functions, components and data used in an environment and ensure total visibility – *you cannot secure what you cannot see*.
-   Use continuous security monitoring.

Please refer to the following National Institute of Standards and Technology paper for more information on Zero Trust: <https://csrc.nist.gov/pubs/sp/800/207/final>.  And there is many other web sources on zero trust principles and applications. This paper will show how various {{site.data.keyword.Bluemix_notm:}} security elements can be deployed following a Zero Trust approach.

## Security Solutions Framework
{: #Security-Solutions-Framework}

IBM uses a broad standard framework in all its security endeavors, e.g., design, consulting, implementation, etc. and this is shown below for reference. Now some, but not all of these are necessarily applicable for {{site.data.keyword.Bluemix_notm:}} in Virtual Private Cloud environments from a technical capability perspective. This paper therefore will only cover the capabilities highlighted in blue. And note that some of these capability categories can be broken down further and these are discussed in detail starting in Section 5.

![illustrates the security framework for IaaS Security Whitepaper](images/framework.svg){: caption="Figure 1. Security Framework" caption-side-"bottom"}

## IBM Cybersecurity Security Services (CSS) Capabilities – Options for Certain Situations.
{: #CSS-capabilities}

IBM Cybersecurity Services is a specific business unit within IBM that focuses specifically on security. They have a broad range of security solutions and associated consulting and managed services. The table below provides an overview of their solutions, and these can be considered additional options in {{site.data.keyword.Bluemix_notm:}} that may be applicable in certain scenarios, e.g., hybrid or mult-cloud situations. Note: their separate consulting and managed service are not covered here. As {{site.data.keyword.Bluemix_notm:}} security domains are discussed in the following sections, options in the domains will be presented and some of those could be IBM CSS solutions.

 - **Infrastructure & Endpoint Security** - Various 3rd Party Firewalls, e.g., Palo Alto, Cisco, etc.
 - **QRadar Security Event & Information Management (SIEM), Network Detection and Response (NDR)**(https://www.ibm.com/docs/en/qsip/7.5?)topic=qradar-network-detection-responseVarious 3rd party
 - **Endpoint Protection / Detection & Response (EPP/EDR) solution**s** [Qradar / ReaqTa](https://www.ibm.com/products/qradar-edr) endpoint detection and response  unified endpoint management
 - **Unified Endpoint Management** - [MaaS360](https://www.ibm.com/products/maas360/unified-endpoint-management)
 - **Data Security** - [Guardium](https://www.ibm.com/guardium) data security suite, e.g., data classification, data loss prevention, etc. [CloudPak for Data](https://www.ibm.com/docs/en/cloud-paks/cp-data/4.8.x?topic=overview) [Guardium key lifecycle manager](https://www.ibm.com/products/ibm-security-key-lifecycle-manager)
 - **Privilege Access Management** - Verify security access manager
 - **Container Security** - 3rd Parties – Palo Alto Prisma Cloud & Illumio

## Data Security
{: #data-security}

## Data-at-Rest Encryption
{: #data-at-rest-encryption}

{{site.data.keyword.Bluemix_notm:}} provides native, integrated data-at-rest encryption for VPC volumes and snapshots and file storage/VPC shares automatically.  {{site.data.keyword.Bluemix_notm:}} also provides data-at-rest encryption for its object storage by default. All the encryption used adheres to the AES-256 standard. Customers can use IBM-managed encryption (default) or customer-managed keys.

### Options:
{: #data-at-rest-encryption-options}

 - **{{site.data.keyword.Bluemix_notm:}} Default Encryption** - Automatic if no key management scheme is selected. IBM keys will be used,
 - **{{site.data.keyword.Bluemix_notm:}} Encryption with Customer Keys** - Customer selects an {{site.data.keyword.Bluemix_notm:}} native key management system (KMS). {{site.data.keyword.Bluemix_notm:}} has two KMSs – {{site.data.keyword.keymanagementservicelong_notm:}} and Hyper Protect Crypto Service (HPCS), and
 - **External Encryption Solution** - Customer may be using their own data encryption solution on-prem and want to extend this to the cloud. Or a customer may want centralized data control across multiple clouds. IBM Cyber Security Services (CSS) has an applicable solution known as Guardium. See Section 4.

### Best Practices:
{: #data-at-rest-encryption-best-practices}

 - Data encryption should always be used as can be expected,
 - Cloud native encryption with a designated cloud native KMS provides the best lifecycle automation and orchestration, and
 - Encrypting data with customer managed keys is recommended to meet regulatory compliance for additional security and customer control.

### Solutioning Guidance:
{: #data-at-rest-encryption-guidance}

 - [Securing Your Data in VPC](https://docs/vpc?topic=vpc-mng-data&interface=ui),
 - [About data encryption for VPC](https://docs/vpc?topic=vpc-vpc-encryption-about), and
 - [Encrypting Your Data](https://docs/cloud-object-storage?topic=cloud-object-storage-encryption)

## Key Management / Lifecycle Management
{: #key-management}

Key management allows cloud customers the ability to create, store, manage and rotate keys with automation to support storage encryption. {{site.data.keyword.Bluemix_notm:}} has two native, integrated key management services, {{site.data.keyword.keymanagementservicelong_notm:}} and Hyper Protect Crypto Services. Please see these links for more information:
 - <https://docs/key-protect?topic=key-protect-about>,
 - <https://docs/hs-crypto?topic=hs-crypto-get-started>, and
 - <https://docs/hs-crypto?topic=hs-crypto-introduce-uko>

![A screenshot of a computer description automatically generated](images/keyprotect.svg){: caption="Figure 2. Security Framework" caption-side="bottom"}

### Options:
{: #key-management-options}

 - **{{site.data.keyword.keymanagementservicelong_notm:}}** - Applicable in situations where key storage security requirements are not highly critical and where a multi-tenant solution is sufficient. This capability is commonly referred to as Bring Your Own Key (BYOK) and it is certified to meet the Federal Information Processing Standard (FIPS)-140-2 level 3, hardware security module (HSM) requirements.

 - **Hyper Protect Crypto Service** - HPCS provides Key Management Services with the highest level of security and control offered by any cloud provider in the industry. It uses a dedicated (single-tenant) FIPS 140-2 Level 4 certified Hardware Security Module and supports customer-managed master keys, giving the customer exclusive control of the entire key hierarchy. HPCS is specifically recommended for financial service

 - **{{site.data.keyword.Bluemix_notm:}} Native HPCS with Unified Key Orchestrator** - This particular variant of the HPCS key management solution noted directly above add the ability to manage key across various clouds in addition to {{site.data.keyword.Bluemix_notm:}}.

 - **Customer or 3rd Party Key Management Solution** - May be applicable when a customer is using an external or 3rd party solution in a hybrid or multi-cloud environment.

### Best Practices:
{: #key-management-best-practices}

 - Cloud native key management offers the most secure, integrated and automated key lifecycle management.
 - User access to keys should be tightly controlled and monitored as can be expected.
 - Processes should be established on how keys should be used and managed. Proper rotation of keys should be established.
 - Regular inspection of activity logs surrounding key management should occur.

### Solutioning Guidance
{: #key-management-guidance}

 - [Provisioning {{site.data.keyword.keymanagementservicelong_notm:}}](https://docs/key-protect?topic=key-protect-provision)
 - [Getting Started with {{site.data.keyword.Bluemix_notm:}} Hyper Protect Crypto Service](https://docs/hs-crypto?topic=hs-crypto-get-started)

## Data-in-Transit Encryption
{: #Data-in-Transit Encryption}

Data-in-Transit encryption can occur in multiple areas within the {{site.data.keyword.Bluemix_notm:}}. There can be external applications using HTTPS/SSL that would terminate to servers within a VPC or load balancers and NexGen firewalls in front of the servers in VPCs.  There is also default data-in-transit encryption when there are accesses/traffic transits to Object, Block and File Storage and cloud services.

### Options:
{: #data-in-transit-encryption-options}

 - **Data-in-Transit encryption to {{site.data.keyword.Bluemix_notm:}} storage** - No options. This is a default function,
 - **Application Level Data-in-Transition Encryption** - Applicable mostly in public access situations but of course this can be applied in private access situations. Transit Level Security (TLS) 1.2 should be used at a minimum and
 - **Application-level data-in-transit encryption termination** - TLS termination at a NexGen firewall TLS termination at an edge load balancer TLS termination with {{site.data.keyword.Bluemix_notm:}}, {{site.data.keyword.cis_short_notm:}} (CIS).

### Best Practices:
{: #data-in-transit-encryption-best-practices}

Application-level data-in-transition encryption should always be applied in public access situations.  Application-level data-in-transit encryption should always be terminated at the edge at a firewall or a load balancer.  When the traffic is decrypted at the edge, it can be inspected for threats, etc.  Application-level encryption termination should not occur on servers that are in the interior of a network.

### Solutioning Guidance
{: #data-in-transit-encryption-best-guidance}

 - [Encryption in transit - Securing mount connections between file share and virtual server instance](https://docs/vpc?topic=vpc-file-storage-vpc-eit),
 - [SSL offload with {{site.data.keyword.Bluemix_notm:}} Load Balancer](https://docs/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer),
 - [Managing origin certificates](https://docs/cis?topic=cis-cis-origin-certificates),
 - [Setting Transport Layer Security (TLS) options](https://docs/cis?topic=cis-cis-tls-options), and
 - [Getting started with {{site.data.keyword.secrets-manager_full_notm:}}](https://docs/secrets-manager?topic=secrets-manager-getting-started&interface=ui) ({{site.data.keyword.secrets-manager_full_notm:}} will be discussed further in the document, but it can store certificates that can be used in data-in-transit encryption.)Also see the following immediate section relating to certificates.

## Certificate Lifecycle Management
{: #certificate-management}

Certificates can be used in several areas within {{site.data.keyword.Bluemix_notm:}} to provide data-in-transit TLS encryption in such areas as load balancers, API gateways, etc.  {{site.data.keyword.Bluemix_notm:}} has certificate management capabilities which allow customers to provision, manage, and deploy public and private SSL/TLS certificates for use with {{site.data.keyword.Bluemix_notm:}} services and applications.  This For more information please follow this link: [Getting started with {{site.data.keyword.secrets-manager_full_notm:}}](https://docs/secrets-manager?topic=secrets-manager-getting-started)

### Options:
{: #certificate-management-options}

 - **{{site.data.keyword.Bluemix_notm:}} {{site.data.keyword.secrets-manager_full_notm:}}** - Highly recommended when {{site.data.keyword.Bluemix_notm:}} is primarily used.
 - **No Certificate Management** - Perhaps applicable in private environments with Dev/QA workloads and or where there is a minimal number of certificates to managed.
 - **Customer-Owned or 3rd Party Certificate Management Solu6tion**

### Best Practices
{: #certificate-management-best-practices}

 - Regular rotations of certificates.
 - Notification of expiring certificates.
 - Certificate storage in a hardware security module.
 - Maintain certificate inventory.
 - Document certificate management procedures.

### Certificate Management Solutioning Guidance
{: #certificate-management-guidance}

 - [Importing SSL/TLS certificates](https://docs/secrets-manager?topic=secrets-manager-certificates&interface=ui)
 - [Ordering SSL/TLS public certificates](https://docs/secrets-manager?topic=secrets-manager-public-certificates&interface=ui)
 - [Creating SSL/TLS private certificates](https://docs/secrets-manager?topic=secrets-manager-private-certificates&interface=ui)

### Data Lifecycle Management and Governance
{: #data-lifecycle-management}

{{site.data.keyword.Bluemix_notm:}} provides a range of data security measures as discussed, but customers may want full data lifecycle management and security across data in hybrid or multi-cloud environments. These capabilities may include data discovery, data classification, data tagging, data integrity checks and loss prevention among others. There are several 3rd party solutions in the market in this full data lifecycle management realm.  One such solution from IBM Cyber Security Services is known [Guardium](https://www.ibm.com/guardium){: external}, as noted in Section 4.

## Data Loss Prevention (DLP) and Data Access, Integrity and Monitoring
{: #DLP}

{{site.data.keyword.Bluemix_notm:}} has a number of ways to control data access such as identity and access management (IAM) and permissions on object storage and so on.  And there is {{site.data.keyword.cloudaccessfulltrail_notm:}} which logs all user and API access to data.  But there are no specific ways to specifically monitor and control data loss and data integrity.   This is typically the realm of 3rd party data control solutions.  Please see the following for more information on this security function:

- **What Is Data Loss Prevention (DLP)** - https://www.ibm.com/topics/data-loss-prevention

Also note that IBM Cybersecurity Services has a DLP solution known as Guardium:  https://www.ibm.com/guardium

## Identity and Access
{: #identity-and-access}

## Access and Role Access Management (IAM)
{: #IAM}

{{site.data.keyword.Bluemix_notm:}} has a full featured native IAM that can control all aspects of admin user actions and services within an account.  It enables you to securely authenticate users for platform services and control access to resources consistently across {{site.data.keyword.Bluemix_notm:}}.  Please see the following link for more information: [Access management in {{site.data.keyword.Bluemix_notm:}}](https://docs/account?topic=account-cloudaccess) and [How {{site.data.keyword.Bluemix_notm:}} IAM works.](/docs/account?topic=account-iamoverview&interface=ui) The table below highlights some of the major IAM functions available.

| IAM Capability                                                                                                 | Function / Feature                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Resource Groups](https://docs/account?topic=account-rgs&interface=ui)                               | A resource group is a way for you to organize your account resources in customizable groupings. Any account resource that is managed by using {{site.data.keyword.Bluemix_notm:}}® Identity and Access Management (IAM) access control belongs to a resource group within your account. You assign resources to a resource group when you create them from the catalog. Language here is straight from {{site.data.keyword.Bluemix_notm:}} docs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [Access Groups](https://docs/account?topic=account-groups&interface=ui)                              | An access group can be created to organize a set of users, service IDs, and trusted profiles into a single entity that makes it easy for you to assign access. You can assign a single policy to the group instead of assigning the same access multiple times for an individual user or service ID.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [Service IDs](https://docs/account?topic=account-serviceids&interface=ui)                            | A service ID identifies a service or application like how a user ID identifies a user. You can create a service ID and use it to enable an application outside of {{site.data.keyword.Bluemix_notm:}} access to your {{site.data.keyword.Bluemix_notm:}} services. You can assign specific access policies to the service ID that restrict permissions for using specific services, or even combine permissions for accessing different services.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| [Access Policies](https://docs/account?topic=account-iamusermanpol)                                  | A policy grants a subject one or multiple roles to a set of resources so that specific actions can be taken within the context of the specified target resources.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [Roles](https://docs/account?topic=account-userroles)                                                | Roles provide a certain level of access and there can be platform and service roles. Roles may have such roles as “Editor”, “Administrator”, etc. Further roles define a set of actions that can be performed on cloud resources. Platform roles control the ability to call platform APIs to do actions such as provisioning a service instance. Service roles are supported by some services and control the ability to call service APIs. {{site.data.keyword.Bluemix_notm:}} supports predefined roles such as "Administrator" and "Editor", that apply across multiple services. Services can also define custom roles that apply only to that service, and users can define their own custom roles that include only the specific actions they wish to grant access to. User-defined custom roles are useful for meeting least privilege requirements."                                                                                                                                                                                                                                                                                                      |
| [Context Restrictions](https://docs/account?topic=account-context-restrictions-whatis)               | Context-based restrictions give account owners and administrators the ability to define and enforce access restrictions for {{site.data.keyword.Bluemix_notm:}}® resources based on a rule's criteria. The criteria include the network location of access requests, the endpoint type from where the request is sent, and sometimes the API that the request tries to access. These restrictions work with traditional IAM policies, which are based on identity, to provide an extra layer of protection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [Multi-Factor Authentication](https://docs/account?topic=account-types&interface=ui)                 | Multifactor authentication (MFA) adds an extra layer of security to your account by requiring all or specific or designated users to authenticate by using another authentication factor beyond an ID and password. MFA is also commonly known as two-factor authentication (2FA).   When MFA is enabled, a user is prompted to provide a unique identifier (such as a username or email) and a one-time password (OTP) generated by an authenticator app or a hardware token. This type of MFA is much more secure than account-based MFA because it is not limited to classic infrastructure resources and applies to all resources within the account. It also reduces the risk of a breach because of a weak password or the use of the same password across multiple accounts.                                                                                                                                                                                                                                                                                                                                                      |
| [Trusted Profiles](https://docs/account?topic=account-trustedprofile-fedusers-tutorial&interface=ui) | By using trusted profiles, you can establish a flexible, secure way for federated users to access the {{site.data.keyword.Bluemix_notm:}}® resources they need to do their job. All federated users that share certain attribute that are defined in your corporate user directory are mapped to a common profile and can share access to {{site.data.keyword.Bluemix_notm:}} resources. This common identity makes it possible to give the members of your organization that share access requirements automatic access to resources one time, rather than having to add each user to an account and then grant them access directly or by using access groups. Trusted profiles can also be used to grant access to service IDs, compute resources, or services. Allowing a compute resource to assume a trusted profile allows you to assign access to applications running on that resource without the need for a long-term credential that then has to be managed and rotated. This greatly enhances the security of applications running in {{site.data.keyword.Bluemix_notm:}}. [Using a trusted profile to call IAM-enabled services](https://docs/vpc?topic=vpc-imd-trusted-profile-metadata) |
{: caption="Table 1: Classic data center security features"}

The diagram below provides insight on how IAM works in the {{site.data.keyword.Bluemix_notm:}}.

![illustrates the security framework for IaaS Security Whitepaper](images/iam.svg){: caption="Figure 3. Identity and Access Management" caption-side-"bottom"}


### Options
{: #IAM-Options}

 - Multi-Factor Authentication (MFA) and complex passwords - always recommended,
 - Assigning individual-based accesses and policies - Never recommended – users should be placed into access groups or in trusted profiles with specific policie, and
 - Single Sign On (SSO) Federation - Applicable where customers already have a single sign on infrastructure or perhaps where customers want to use their established Active Directory or LDAP, etc.

### Best Practices
 {: #IAM-best-practices}

 - [Best Practices for Organizing Resources and Assigning Access](https://docs/account?topic=account-account_setup)
 - Always apply a least privilege approach for all cloud accesses.
 - Never use a root account for any administration.  Always apply context restrictions for IAM access.
 - Never apply IAM capabilities to a single user.
 - Use Trusted Profiles or access groups and assign policies to the access group.
 - Always use multi-factor authentication and a complex password and rotation policy.
 - Develop thorough documentation that dictates how IAM will be used and managed in your {{site.data.keyword.Bluemix_notm:}} account(s).
 - Conduct regular, periodic reviews of your account IAM settings in relation to your IAM documentation and policies. Over time settings can drift or be inadvertently changes resulting in overly permissible states.
 - Conduct periodic reviews of IAM logs provided by [{{site.data.keyword.cloudaccessfulltrail_notm:}}](https://docs/activity-tracker?topic=activity-tracker-about) (following section) to look for access anomalies.

### Solultioning Guidance
 {: #IAM-guidance}

 - [Access management in {{site.data.keyword.Bluemix_notm:}}](https://docs/account?topic=account-cloudaccess),
 - [How {{site.data.keyword.Bluemix_notm:}} IAM works](https://docs/account?topic=account-iamoverview),
 - Customers are encouraged to read all the documentation in the Managing Your Account, Resources, Access section in {{site.data.keyword.Bluemix_notm:}} Docs for more insight on best IAM practices and solutioning guidance,
 - [Best Practices for Organizing Resources and Assigning Access](https://docs/account?topic=account-account_setup), and
 - Use trusted profiles to assign access to compute resources rather than embedding credentials in applications.

## IAM with Single Sign-On / Identity Provider Federation
{: #IAM-SSO}

{{site.data.keyword.Bluemix_notm:}} IAM allows federation so that you can integrate with your external identity provider (IdP) to securely authenticate external users to your {{site.data.keyword.Bluemix_notm:}}® account. By using your IdP, you can provide a way for users in your company to use single sign-on (SSO).  Please see the following link for general information: [Singe Sign On](https://docs/appid?topic=appid-cd-sso#:~:text=You%20can%20configure%20the%20SSO,before%20the%20SSO%20session%20expires.)

### Options
{: #SSO-options}

 - SSO - Applicable where federation with other identity providers or external directories is required, and
 - No SSO - Customers may forgo SSO if they have no federation with Identity Providers.

### Best Practices
{: #SSO-best-practices}

 - Use {{site.data.keyword.Bluemix_notm:}} Trusted Profiles in conjunction with any SSO solution,
 - Ensure multi-factor authentication with the SSO solution, and
 - Enforce granular role and permission management.

### Solutioning Guidance
{: #SSO-guidance}

 - [Which is the right federation option for you?](https://docs/account?topic=account-federation-option-for-you)
 - {{site.data.keyword.Bluemix_notm:}} SAML Federation Guide [Enabling authentication from an external identity provider.](https://docs/account?topic=account-idp-integration)
 - [Managing access for federated users by using trusted profiles](https://docs/account?topic=account-trustedprofile-fedusers-tutorial&interface=ui)

## Secrets Management
{: #secrets-management}

Cloud secrets management is a way to securely store and manage API keys, certificates, user ID and password credentials and other sensitive information with automation and integration.  {{site.data.keyword.Bluemix_notm:}}’s service here is known as {{site.data.keyword.secrets-manager_full_notm:}} and it has several key security features such as secrets lifecycle management, logging, default encryption, IAM integration, versioning, etc.  Please see the following link for more information: [Getting started with {{site.data.keyword.secrets-manager_full_notm:}}](https://docs/secrets-manager?topic=secrets-manager-getting-started)

### Options:
{: #secrets-management-options}

- **{{site.data.keyword.Bluemix_notm:}} {{site.data.keyword.secrets-manager_full_notm:}}** - Automated and native secrets management solution that is fully integrated with IBM,
- **No Secrets Management** - Never recommended again, but this may be applicable where you have a totally private environment that is used for non-critical dev and test and the like. Secrets here could possibly be embedded into applications here, if security requirements are low and cost is a factor, and
- **3rd Party Secrets Managment Solution** - This option may be applicable in multi-cloud situation but secrets management automation with {{site.data.keyword.Bluemix_notm:}} would be lost.

### Best Practices:
{: #secrets-management-best-practices}

 - {{site.data.keyword.Bluemix_notm:}} is focused on enterprise workloads and these workloads should always include secrets management,
 - Cloud native secrets management that provides full Lifecyle capabilities and full cloud integration,
 - Automated creation, rotation, revocation and expiration of static secrets, and
 - Never transmit secrets via plaintext; all should transit using TLS encryption.

### Solutioning Guidance:
{: #secrets-management-best-guidance}

 - [Managing IAM access for {{site.data.keyword.secrets-manager_full_notm:}}](https://docs/secrets-manager?topic=secrets-manager-iam&interface=ui),
 - [Using service endpoints to privately connect to {{site.data.keyword.secrets-manager_full_notm:}}](https://docs/secrets-manager?topic=secrets-manager-service-connection&interface=ui),
 - [Securing your data in {{site.data.keyword.secrets-manager_full_notm:}}](https://docs/secrets-manager?topic=secrets-manager-mng-data&interface=ui),
 - [Protecting {{site.data.keyword.secrets-manager_full_notm:}} resources with context-based restrictions](https://docs/secrets-manager?topic=secrets-manager-access-control-cbr&interface=ui)
 - {{site.data.keyword.secrets-manager_full_notm:}} instances are provisioned per region to spread out workloads and limit the blast radius in case of a regional outage. {{site.data.keyword.secrets-manager_full_notm:}} is a single-tenant service. CPU and memory limits are applied per {{site.data.keyword.secrets-manager_full_notm:}} instance.  Those limits restrict the API request rates based on the usage pattern.  As a rule of thumb, it is recommended to keep the rate below 20 req/s.  Additionally, limit the number of unique clients that make requests to a single {{site.data.keyword.secrets-manager_full_notm:}} instance, and
 - Another best practice is the use of one of {{site.data.keyword.Bluemix_notm:}}’s key management systems ({{site.data.keyword.keymanagementservicelong_notm:}} or Hyper Protect Crypto Services (HPCS)) to encrypt secrets. Guidance on how you should organize your secrets can be found here: [Organizing Your Secrets.](https://docs/secrets-manager?topic=secrets-manager-secret-groups&interface=ui)

Note that {{site.data.keyword.secrets-manager_full_notm:}} is a high available platform which has built-in resiliency and backups in each region. Customers have specific responsibilities around secrets management.  More details can be found here: [Security Design](https://docs/vpc-resiliency?topic=vpc-resiliency-security-design). Ensure high availability of secrets management platform. Provisions for high availability and encrypted backups should be used.

## Privilege Identity and Access Management
{: #PIM}

## Bastion Host and Privilege Identity and Access Management (PAM)
{: #bastion-host}

A bastion host is a server used to manage access to an internal or private network from an external network - sometimes called a jump box or jump server. Because bastion hosts often sit in the Internet edge, they typically run a minimum number of services to reduce their attack surface.  They are also commonly used to proxy and log communications, such as SSH sessions.  Privilege Access Management (PAM) software can be loaded on top of the bastion host to provide more security functionality, granular access control and logging beyond terminal SSH access.

### Options
{: #bastion-host-options}

 - **Virtual Server Instance for Bastion Host** - There are no options for an underlying platform for a Bastion Host. Bastion Hosts must be created on a virtual server instances (VSI) within the confines of a Virtual Private Cloud (VPC),
 - **Bastion Host, No Privilege Access Management (PAM) Software** - Not recommended in that highly granular access, approval workflows and detailed logging may be needed,
 - **Bastion with PAM software** - Various 3rd party solutions are in the marketplace, and this is always recommended. Note that IBM Cyber Security Services (CSS) does have a PAM solution here known as **Verify**. More information on **Verify** can be found here: IBM CSS [Verify](https://www.ibm.com/verify?utm_content=SRCWW&p1=Search&p4=43700074603995210&p5=e&gad_source=1&gclid=Cj0KCQjwwMqvBhCtARIsAIXsZpa48PUASWhrDD-SGr-h-wY_b1IyThYC4DzKpHucYM_JWNdkzpHcjoYaAkZ_EALw_wcB&gclsrc=aw.ds)

### Best Practices
{: #bastion-host-best-practices}

 - Bastion hosts should always be accompanied with PAM software.  A least privilege approach should always be applied to permissions on the Bastion Host and the PAM software,
 - Detailed logs should be enabled, and regular reviews of logs should be undertaken to look for anomalies, and
 - Logs from the Bastion Host and the PAM software should be correlated with other logs to get inferences of threats. Typically, this correlation comes in the form of a Security Event and Information Management (SIEM) Platform.

### Solutioning Guidance
{: #bastion-host-guidance}

 - Securely access remote instances with a bastion host. (https://docs/solution-tutorials?topic=solution-tutorials-vpc-secure-management-bastion-server)

## Application Security
{: #app-security}

### Web Application Firewalling (WAF)
{: #WAF}

A WAF helps protect web applications by filtering and monitoring HTTP traffic between a web application and the Internet. A WAF is an OSI protocol Layer-7 defense in the OSI model, and it is not designed to defend against all types of attacks. {{site.data.keyword.Bluemix_notm:}} has two ways to provide web application firewalling at the Internet edge. One that is typically used in a Content Delivery Network (CDN) and which is named {{site.data.keyword.cis_short_notm:}} (CIS). The other WAF option is using NexGen firewalls that can be placed on the “edge” or in front Transit VPCs. You can find information on your NexGen firewalls WAF capabilities in their respective product information.

### Options:
{: #WAF-options}

- **{{site.data.keyword.cis_short_notm:}} (CIS)** - Using Cloud Internet Service WAFs may be more applicable in situations where you need a broad range of capabilities that are commonly found in Content Delivery Networks such as global load balancing, DNS features, URL control, etc.
- **NexGen Firewall** - Applicable where a NexGen firewall is already at the Internet edge and there are no additional needs that can be found in content delivery networks. NexGen firewalls are typically deployed in “edge” or transit VPCs to provide more advanced firewall functions like Intrusion Detection / Intrusion Protect (IDS/IPS) among other capabilities.
- **No WAF** - Customer may elect to forgo the use of a WAF in private environments where there may be a private connection to on-prem infrastructure. But note that a customer could have their own WAF in a Demilitarized Zone (DMZ) on-prem

### Best Practices:
{: #WAF-best-practices}

 - WAF should always be used in public access environments. There are many options and configurations with WAF that relate to HTTP/HTTPS, domains, detection policies, etc.,
 - Customers thoroughly review these items and adapt to their own specific security needs and associated security policies,
 - As with other security protection and detections capabilities, logs should be stored and inspected regularly for signs of anomalies, and
 - WAF logs should generally be correlated with other logs, perhaps through a Security Event and Information Management (SIEM) platform, if available.

### Solutioning Guidance:
 {: #WAF-best-guidance}

 - {{site.data.keyword.cis_short_notm:}} (CIS) [Best practices for CIS setup](https://docs/cis?topic=cis-best-practices-for-cis-setup),
 - [Bring Your Own (BYO) firewalls in {{site.data.keyword.Bluemix_notm:}}.](https://cloud.ibm.com/catalog/content/ibm-fortigate-AP-HA-terraform-deploy-5dd3e4ba-c94b-43ab-b416-c1c313479cec-global?catalog_query=aHR0cHM6Ly9jbG91ZC5pYm0uY29tL2NhdGFsb2c%2FY2F0ZWdvcnk9c2VjdXJpdHk%3D), and
 - [Deploying Fortigate firewall on IBM VPC Cloud.](https://docs.fortinet.com/document/fortigate-public-cloud/7.4.0/ibm-cloud-administration-guide/944419/deploying-fortigate-vm-a-p-ha-on-ibm-vpc-cloud-byol)

## Distributed Denial of Service (DDoS)
{: #DDoS}

A distributed denial of service (DDoS) attack is a malicious attempt to disrupt normal traffic of a server, service, or network by overwhelming the target or its surrounding infrastructure with a flood of internet traffic.  These attacks can occur at the application layer and the network layer. {{site.data.keyword.Bluemix_notm:}} has two ways of providing DDoS protection for designs that have public internet access.  One is using {{site.data.keyword.cis_short_notm:}}, and the other is using NexGen firewalls, that can be deployed on Virtual Server Instances at the Internet edge.  Please see the following links for more information:
- [Dealing with Distributed Denial of Service attacks](https://docs/cis?topic=cis-distributed-denial-of-service-ddos-attack-concepts),
- [About {{site.data.keyword.Bluemix_notm:}} Internet Services](https://docs/cis?topic=cis-about-ibm-cloud-internet-services-cis), and
- Information on NexGen firewalls DDoS capabilities can be found in their respective product information.

### Options:
 {: #ddos-options}

 - **{{site.data.keyword.cis_short_notm:}}  (CIS)** - Applicable in public internet access environments, particularly in production environments and where dispersed users are accessing apps in a content delivery manner,
 - **NexGen Firewall** - Perhaps more applicable where an edge firewall is already being used and users are not dispersed, and cost is factor, and
 - **No DDoS** - Not required in private only networks.

### Best Practices:
 {: #ddos-best-practice}

 - [Best practices for CIS setup](https://docs/cis?topic=cis-best-practices-for-cis-setup),
 - Create a DDoS attack threat model that is a structured approach to identifying and analyzing potential risks to your online service or website from a DDoS attack,
 - Implement rate limiting by controlling the amount of traffic sent to a network or server, and
 - Ensure log monitoring and analysis of web traffic to look for anomalies such as unusual high traffic volume or server errors, etc.

### Solutioning Guidance:
{: #ddos-guidance}

 - [FAQs for {{site.data.keyword.Bluemix_notm:}} Internet Services](https://docs/cis?topic=cis-faq)
 - [Managing your CIS deployment](https://docs/cis?topic=cis-manage-your-cis-deployment)

## Infrastructure and Endpoint Security
{: #IES}

## Core Network Protection / Network Segmentation
{: #core-network-protection}

{{site.data.keyword.Bluemix_notm:}} provides several standard network isolation capabilities to help customer segregate and secure traffic and compute workloads.  Please see the methocs. These isolation techniques ensure that any attacks are contained in a network area and to limit the “blast radius”.  Please see the following links for more information on network segmentation:

 - [Security in Your VPC](https://docs/vpc?topic=vpc-security-in-your-vpc),
 - [About Networking](https://docs/vpc?topic=vpc-about-networking-for-vpc), and
 - [Security in your VPC](https://docs/vpc?topic=vpc-security-in-your-vpc)

### Segmentation Methods:
{: #segmentation-methods}

 - **Virtual Private Cloud** - VPCs Can segregate various environments, e.g., one VPC for production, one VPC for Dev/Test, one for management, etc.  And of course, there are use cases where there may be one general use VPC that is completely separate from another VPC in an account, i.e., a customer have two different workload environments. [Virtual Private Cloud](https://docs/vpc?topic=vpc-about-vpc),
 - **Access Control Lists (ACLs)** - Segregate ingress and egress traffic within Virtual Private Cloud (VPC) subnets. [Access Control Lists (ACLs)](https://docs/vpc?topic=vpc-using-acls#:~:text=You%20can%20use%20an%20access,to%20and%20from%20the%20instances.),
 - **Security Groups** - Segregates traffic in and out of virtual server network interfaces, This could be considered host firewalling. [Security Groups](https://docs/security-groups?topic=security-groups-about-ibm-security-groups)
 - **Transit Gateway** - {{site.data.keyword.Bluemix_notm:}}’s Transit Gateway can interconnect {{site.data.keyword.Bluemix_notm:}} classic, IBM PowerVS and Virtual Private Cloud (VPC) infrastructures, keeping traffic securely within the {{site.data.keyword.Bluemix_notm:}} network.  Transit Gateway can be deployed for: VPCs in the same region (local routing) and VPCs in different regions (global routing) VPCs to your {{site.data.keyword.Bluemix_notm:}} classic infrastructure VPCs to PowerVS environments.  Now transit gateways are not always thought as a specific security capability, but Transit Gateways can provide a form of network segmentation known as Pretext Filtering.  More information here can be found at: [Filtering Routes using Transit Gateway pretext filtering](https://docs/dl?topic=dl-prefix-filtering).
 - **NexGen Firewalls** - Firewalls at the Internet can segregate public access from internal private compute beyond L3/L4 filtering. It can be considered a key “demilitarized” zone segmentation.

### Options:
{: #segmentation-options}

 - **VPC** - There are no options to VPC segmentation, but customer could elect, for example, to only use one VPC and place all resources in that VPC.  This could be used in non-critical environments where there is only one function, e.g., test and there is no public access and cost is a factor,
 - **Access Control Lists** - There are no options for using ACLs in VPC environments,
 - **Security Groups** - There are no alternatives in a VPC environment,
 - **NexGen Firewall** - Customers can elect, based upon a risk profile and the workload types, to place NexGen firewalls in a separate Dimilaritized Zone (DMZ) VPC.
 - **Transit Gateway** - There are no options for using Transit Gateway when you want to interconnect VPCs or connect to other environment, e.g., PowerVS.  But the use of pretext filtering is options in many situations.


### Best Practices:
{: #segmentation-best-practices}

 - In public environments, always have an Internet edge VPC where a firewall can be placed and act as a Demilitarized Zone segmentation.
 - Separate production, dev, test, etc. from each other using VPC segmentation. Always apply a “deny all” approach to ACLs and Security Groups and only open ports, protocols and IP addresses as needed.
 - Conduct periodic reviews of all ACL and Security Group rules. Understand traffic flows between servers so as to understand what segmentation is needed.

### Solutioning Guidance:
{: #segmentation-guidance}

 - [Getting started with Virtual Private Cloud (VPC)](https://docs/vpc?topic=vpc-getting-started)
 - [Adding and deleting pretext filters](https://docs/transit-gateway?topic=transit-gateway-adding-prefix-filters&interface=ui)

## Edge Protection / Firewalling
{: #core-network-protection}

Segregation techniques were discussed in the previous section and in some way, these can be considered firewalling methods as well.  {{site.data.keyword.Bluemix_notm:}} has native firewalling in several areas to control IP addresses, ports and protocols and associated ingress and egress traffic.  Most notable are ACLs that are firewalls that are applied to created cloud subnets.  Security Group are firewalls that are applied virtual server instance (VSI) network interfaces.  Security Groups work at the L3/L4 level controlling allowed IP addresses, ports, and protocols.

 - [Access Control Lists](https://docs/vpc?topic=vpc-using-acls#:~:text=You%20can%20use%20an%20access,to%20and%20from%20the%20instances.) Controls ingress and egress IP addresses, ports and protocol in subnets,
 - [Security Groups](https://docs/security-groups?topic=security-groups-about-ibm-security-groups) - Controls ingress and egress IP addresses, ports and protocols on virtual server instances network interfaces. This can be considered host firewalling,
 - **NexGen Firewalls** - {{site.data.keyword.Bluemix_notm:}} has two firewalls within its catalog, Juniper and Fortinet, that can be deployed on VSIs at the edge, and these can fully control Level 3 & 4 traffic, but these are capable of much more filtering like controlling URLs, files, DNS queries and layer 7 web application firewalling. In addition to the firewalls in the {{site.data.keyword.Bluemix_notm:}} catalog, customers can bring their own firewall and host it on a VSI,
 - **{{site.data.keyword.cis_short_notm:}}** - CIS has a traditional layer 3/4 firewall, in addition to its WAF capability and other security features. This would be applicable in situation where the customer has dispersed users and where a content delivery network (CDN) solution may be used, and
 - [Context Restrictions](https://docs/account?topic=account-context-restrictions-whatis)                                            Firewalls in essence that front end services to control ingresses from certain allowed IP addresses. E.g., blocking accesses from Russia on a Saturday night.

### Options:
{: #firewalling-options}

 - **VPCs, Access Control Lists (ACLs), Security Groups** - No options – mandatory for all VPC environments. Please see: [(exploring firewalls)](https://docs/security-groups?topic=security-groups-exploring-firewalls)

 - **NexGen Firewalls** - Required when there are public connections to the Internet and {{site.data.keyword.cis_short_notm:}} (CIS) will not be used. Required when there are public connections to the Internet and where advanced firewalls features are needed, e.g., SD-WAN, file inspections, etc. Optional in private connections to on-prem, but still recommended. Optional when {{site.data.keyword.cis_short_notm:}} (CIS) will be used.
 - **{{site.data.keyword.cis_short_notm:}} (CIS)** - [{{site.data.keyword.cis_short_notm:}} (CIS)](https://docs/cis?topic=cis-getting-started).  Required where there are other needs such as content delivery networking (CDN), e.g., edge content caching, URI controls, distributed TLS terminations, global load balancing, DDoS, etc.

### Best Practices
{: #core-network-protection-best-practices}

 - Knowing and documenting all traffic flows, and segment accordingly,
 - Firewalls should be first setup with a “deny all” configurations and IPs, port and protocols are only opened when necessary,
 - Periodic firewall rules reviews, and
 - [CIS best practices](https://docs/cis?topic=cis-best-practices-for-cis-setup)

### Solutoning Guidance
{: #core-network-protection-guidance}

 - [Monitoring CIS for optimal security](https://docs/cis?topic=cis-manage-your-ibm-cis-for-optimal-security),
 - [Security Groups guidelines](https://docs/security-groups?topic=security-groups-security-groups-guidelines),
 - [Creating a Network Access Control List (ACL)](https://docs/vpc?topic=vpc-acl-create-ui&interface=ui),
 - [Getting started with FortiGate Security Appliance 10 Gbps](https://docs/fortigate-10g?topic=fortigate-10g-getting-started), and
 - [Getting started with {{site.data.keyword.Bluemix_notm:}} Juniper vSRX](https://docs/vsrx?topic=vsrx-getting-started)

## Endpoint Detection / Endpoint Protection (EDR/EPP)
{: #EDR-EPP}

EDR/EPP security is a detection and protect mechanism that works at the operating system and application levels. This can loosely thought of anti-virus on a server, but today’s EDR/EPP solutions provide so much more like hardening, software patching, compliance monitoring, threat hunting, etc.  Now within {{site.data.keyword.Bluemix_notm:}}’s Security and Compliance solution is a component known as Cloud Workload Protection. This could be likened to Endpoint Protection / Detection (EPP/EDR) security.  This provides a broad range of security capabilities to include:

-   A unified and centralized framework to manage the security and compliance of applications, workloads, and infrastructure,
-   Host and image scanning, auditing, and runtime vulnerability management capabilities,
-   Posture management for a distributed environment, and
-   Runtime detection and data enrichment

Now within the context of this particular section, only runtime vulnerability and detection will be discussed. Cloud Workload Protection also has compliance components, and these are discussed in the Governance, Risk and Compliance section.

Please see the following link for information: [Key features of {{site.data.keyword.Bluemix_notm:}} Security and Compliance Center Workload Protection](https://docs/workload-protection?topic=workload-protection-key-features). This capability can also fall into a security mechanism known as Vulnerability Management. Information on this follows in the Vulnerability Management section.

Also see this link which has broad information on endpoint security: [what is endpoint security](https://www.ibm.com/topics/endpoint-security) and [What is Endpoint detection and response.](https://www.ibm.com/topics/edr)

### Options
{: #endpoint-security-options}

 - **{{site.data.keyword.Bluemix_notm:}} Workload Protection** - Fully integrated into {{site.data.keyword.Bluemix_notm:}} with automation aspects and ties in with {{site.data.keyword.Bluemix_notm:}} Security and Compliance Center,
 - **3rd Party Endpoint Protection and Detection (EPP/EDR)** - Stand-alone solutions without {{site.data.keyword.Bluemix_notm:}} integration, but that may be applicable if a customer is using an endpoint security solution on-prem or in a multi-cloud situation. IBM Security, now known as Cybersecurity Services (CSS), has a EPP/EDR solution known as [Reaqtq](https://mediacenter.ibm.com/media/IBM+Security+ReaQta+Explained/1_l31z0vax).  IBM Cybersecurity Services also sells, consults on, implements and manages various 3rd party EPP/EDR market solutions.
 - **No Workload Protection Endpoint Security** - This option depends upon the customer risk profile and what type of workloads are being used.  This could be applicable in a private environment with no Internet access or low risk situations with dev and test environments.

### Best Practices
{: #endpoint-security-best-practices}

 - Cloud Workload Protection (CWP) is always recommended in public environments, and
 - Any cloud workload protection should be accompanied with people and processes to use the service or tool to find threats and vulnerability wholistically. A “set and forget” approach should never be used.

### Solutioning Guidance
{: #endpoint-security-best-practices}

[Getting started with {{site.data.keyword.Bluemix_notm:}} Security and Compliance Center Workload Protection](https://docs/workload-protection?topic=workload-protection-getting-started)

## Virtual Private Endpoints
{: #VPE}

{{site.data.keyword.Bluemix_notm:}} has Virtual Private Endpoints that allow secure access to a variety of cloud services without traversing the Internet. Note that VPEs have firewalls in the form of access control lists and security groups previously discussed.  {{site.data.keyword.Bluemix_notm:}}® Virtual Private Endpoints (VPE) for VPC enables you to connect to supported {{site.data.keyword.Bluemix_notm:}} services from your VPC network by using the IP addresses of your choosing, allocated from a subnet within your VPC.  VPE is an evolution of the private connectivity to {{site.data.keyword.Bluemix_notm:}} services. VPEs are virtual IP interfaces that are bound to an endpoint gateway created on a per service, or service instance, basis (depending on the service operation model).  The endpoint gateway is a virtualized function that scales horizontally, is redundant and highly available, and spans all availability zones of your VPC. Endpoint gateways enable communications from virtual server instances within your VPC and {{site.data.keyword.Bluemix_notm:}}® service on the private backbone.  VPE for VPC gives you the experience of controlling all the private addressing within your cloud. Please see the following links for more information:

### Options
{: #VPE-options}

 - **VPE use** - always recommended due to its inherent security and private traffic transit, and
 - **Cloud Service Access Through the Internet** - Never recommended, but a possible transit if cloud services access is needed in some way across the Internet.

### Best Practices
{: #VPE-best-practices}

 - Virtual Private Endpoints should always be used when there is a need to access cloud services as opposed to any access over the Internet,
 - VPEs have security features that should be considered during the implementation process. One is that VPEs have Access Control Lists (ACLs) that can control all traffic in and out of the VPE, and
 - Another is that Security Groups can additionally be applied to control inbound application traffic.

### Solutioning Guidance
{: #VPE-guidance}

 - [Privately connecting to {{site.data.keyword.Bluemix_notm:}} services](https://docs/overview?topic=overview-endpoints-support),
 - [About virtual private endpoint gateways](https://docs/vpc?topic=vpc-about-vpe), and
 - [Configuring ACLs and security groups for use with endpoint gateways](https://docs/vpc?topic=vpc-configure-acls-sgs-endpoint-gateways&interface=ui).

## Threat Detection and Threat Investigation and Response
{: #threat-detection&investigation}

### {{site.data.keyword.cloudaccessfulltrail_notm:}} – IAM Logging
{: #activity-tracker-IAM-logging}

{{site.data.keyword.Bluemix_notm:}}’s {{site.data.keyword.cloudaccessfulltrail_notm:}} logs and records all administrator and API actions within an {{site.data.keyword.Bluemix_notm:}} account.  This service can be used to investigate abnormal activities, for troubleshooting or forensics purposes and used for compliance audits.  This service provides such features as alerting, log storage encryption, compliance with the Cloud Auditing Data Federation (CADF) standard among others.  Logs from this service can also be forwarded externally to a Security Information Even Management (SIEM) for event correlation for threat detection.  More information on {{site.data.keyword.cloudaccessfulltrail_notm:}} can be found at the following link: [Learning about {{site.data.keyword.Bluemix_notm:}} {{site.data.keyword.cloudaccessfulltrail_notm:}} architecture and workload isolation](https://docs/activity-tracker?topic=activity-tracker-compute-isolation)

### Options
{: #activity-tracker-options}

There are no other {{site.data.keyword.Bluemix_notm:}} IAM logging options here – this is the default and built-in logging capability.

### Best Practices
{: #activity-best-practices}

 - Use of {{site.data.keyword.cloudaccessfulltrail_notm:}} auditing in regulated environment or compliance auditing is a must, and
 - Forwarding of {{site.data.keyword.cloudaccessfulltrail_notm:}} logs to a Security Event and Information Management (SIEM) platform, if a customer is using a SIEM.

### Solutioning Guidance
{: #activity-guidance}

 - [Getting started with {{site.data.keyword.Bluemix_notm:}} {{site.data.keyword.cloudaccessfulltrail_notm:}}](https://docs/activity-tracker?topic=activity-tracker-getting-started),
 - [About {{site.data.keyword.cloudaccessfulltrail_notm:}} in {{site.data.keyword.Bluemix_notm:}}](https://docs/activity-tracker?topic=activity-tracker-about), and
 - [Provisioning an instance](https://docs/activity-tracker?topic=activity-tracker-provision).

### Other Logging – That Can Be Forwarded to a SIEM
{: #other-logging}

Logging plays a key role in security in that captures events that may be anomalous and when are correlated and analyzed, can detect a threat and other problems.  Logging can also play a role in compliance auditing. Several {{site.data.keyword.Bluemix_notm:}} services create logs as noted in the below table:

| Logs                                                                                                                                | Function                                                                                                     |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| [VPC Flow Logs](https://docs/vpc?topic=vpc-flow-logs)                                                                     | Provides logs of all ingress and egress traffic within a VPC.                                                     |
| [{{site.data.keyword.cloudaccessfulltrail_notm:}}](https://docs/activity-tracker?topic=activity-tracker-getting-started)                                  | As noted above; Provides logs of all administrator actions and API activities within an IBM account.                              |
| NexGen Firewalls                                                                                                                    | Provides logs on a variety of functions / actions that occur within the firewalls, e.g., rule hits, alarms, etc. |
| [{{site.data.keyword.cis_short_notm:}} LogPush Service](https://docs/cis?topic=cis-logpush&interface=ui)                                | Captures {{site.data.keyword.cis_short_notm:}} firewall events.                                                                 |
| [Cloud Workload Protection Event Forwarding](https://docs/workload-protection?topic=workload-protection-event_forwarding) | Forwards various events from the Cloud Workload Protection solution.                                             |
{: caption="Table 1: Available Logging"}

## Other Logging Options
{: #logging-options}

 - **VPC Flow Logs** - There are no options if traffic capture in and out of a VPC is needed for security and troubleshooting purposes.
 - **{{site.data.keyword.cloudaccessfulltrail_notm:}}** - There are no options if logs are needed from IAM user and API actions for auditing, compliance or security reasons.
 - **NexGen Firewalls** - Customers can elect to capture and forward all kinds of logs.

### Best Practices
{: #otherlogging-best-practices}

 - Logging of IAM user and API actions should always be used, regardless of the security situation.  These can be used for troubleshooting purposes and mandatory in compliance situations.
 - Firewall logs should always be used for detection purposes, if deployed.

### Solutioning Guidance
{: #other-logging-guidance}

 - [Creating a flow log collector](https://docs/vpc?topic=vpc-ordering-flow-log-collector&interface=ui),
 - [Provisioning an instance](https://docs/workload-protection?topic=workload-protection-provision) (Workload Protection),
 - ({{site.data.keyword.cis_short_notm:}}) [Provisioning an instance](https://docs/workload-protection?),
 - [Creating a flow log collector](https://docs/vpc?topic=vpc-ordering-flow-log-collector&interface=ui), and
 - {{site.data.keyword.cloudaccessfulltrail_notm:}} [Using the Logpush service](https://docs/cis?topic=cis-logpush&interface=ui)


## Threat Detection
{: #threat-detection}

Threat detection in {{site.data.keyword.Bluemix_notm:}} can occur in various places. NexGen firewalls deployed at the edge can detect anomalous traffic through their Intrusion Detection / Intrusion Protection (IDS/IPS) and other capabilities. NexGen firewalls have other detection mechanisms as well to include file and URL blocking, etc.  {{site.data.keyword.Bluemix_notm:}} Internet Services, which also operates at the Internet Edge, can detects threats at the application layer through its WAF capability. {{site.data.keyword.Bluemix_notm:}} also has a workload protection, previous discussed which can detect runtime threats on workloads. Security and Compliance Center discussed, immediately below, can detect cloud configurations that are out of compliance and so on. These are summarized below:

| Area / Solution                                                                                                                                                                                                                           | Detections                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| NexGen Firewalls (see respective firewall documentation)                                                                                                                                                                                      | Anomalous traffic, blocked traffic, firewall rule hits, anomalous files, URLs, DNS queries, etc. |
| [{{site.data.keyword.cis_short_notm:}} (CIS)](https://docs/cis?topic=cis-about-ibm-cloud-internet-services-cis)                                                                                                                               | Layer 7/ WAF detections                                                                          |
| Cloud Workload Protection   [About Workload Protection](https://docs/workload-protection?topic=workload-protection-about).  [Key Features](https://docs/workload-protection?topic=workload-protection-key-features) | Runtime threat detections and vulnerability discovery around virtual server instances.           |
{: caption="Table 1: Threat Detection - Available Methods"}

### Options
{: #detection-options}

 - **NexGen Firewalls** - This detection option can be deployed in public access situations at the edge.  This option can also be deployed in private access situations where customers want an additional level of threat detection to whatever security maybe on-prem. Finally, this option can be deployed in conjunction with {{site.data.keyword.cis_short_notm:}} in certain situations.
 - **{{site.data.keyword.cis_short_notm:}} (CIS)** -      This detection option can be deployed in public access situations at the edge. But this option in public environments is typically used where broader Content Delivery Networking (CDN) capabilities are needed. Customers would not necessarily deploy this in private situations and where content delivery network capabilities are not needed.
 - **Cloud Workload Protection** - This detection option can be deployed where customers are using or will use {{site.data.keyword.Bluemix_notm:}} Security and Compliance Center This option may be needed where a customer just needs endpoint security, and particularly in public access environments.
 - **Security and Compliance Center** - This configuration status detection capability (different than threat detection) should be deployed in situations where compliance and auditing are critical. This can also be used in where customers want to keep track of security configurations.

### Best Practices**
{: #detection-best-practices}

Threat detection capabilities should always be deployed in public situations as can be imagined. Deployment in private situations dependent upon a customer risk profile. Threat detections capability should be accompanied with trained personnel and appropriate processes.  Threat detections need to be correlated in some way, perhaps through a Security Event and Information Management (SIEM) platform, to triangulate attacks and get a holistic view of threats.

### Solutioning Guidance
{: #detection-guidance}

- [Using the CIS Security Events capability](https://docs/cis?topic=cis-using-the-cis-security-events-capability).
- [Getting started with {{site.data.keyword.Bluemix_notm:}} Security and Compliance Center Workload Protection](https://docs/workload-protection?topic=workload-protection-getting-started).
- [Getting started with Security and Compliance Center](https://docs/security-compliance?topic=security-compliance-getting-started).
- Please refer to the selected firewall product documentation on threat detection and how to configure it.

## Response
{: #response}

Security responses functions typically fall into two categories: those that are automated by a security capability and those that are broader in nature that involve people, processes and technologies, e.g., incident response. For the first category, {{site.data.keyword.Bluemix_notm:}} has various security capabilities can take actions to stop or respond to a threat and these are outlined below. The broader incident response is discussed further down.

- **NexGen Firewalls** - Response - blocking traffic, files, URLs, DNS queries, etc. plus all kinds of response alerts and alarms.
- **[{{site.data.keyword.cis_short_notm:}} (CIS)](https://docs/cis?topic=cis-about-ibm-cloud-internet-services-cis)** - Response - blocking various HTTP/HTTS traffic and domains and then notifications based upon events.
- **Security and Compliance Center** - Response - blocking various HTTP/HTTS traffic and domains and then notifications based upon events.

### Options
{: #response-options}

 - **NexGen Firewalls** -Customers have the option to get a variety response alerts and alarms based upon a variety of detection items and other firewall criteria.
 - **{{site.data.keyword.cis_short_notm:}}** - Customers have the options of getting and selecting different notifications based upon security events.
 - **Security and Compliance Center** - Customers can choose a variety of alert notifications based upon several criteria. See the type of alerts in the solutioning guidance below.

### Best Practices
{: #response-best-practices}

- Procedures and processes to handle all the security notifications and alerts in a unified manner.
- Personnel established and trained to respond to security events.
- Having an established incident response plan.

### Solutioning Guidance
{: #response-best-guidance}

 -[Configuring alert policies](https://docs/cis?topic=cis-configuring-policies&interface=ui)
 (Cloud Internet Service)
 -[Enabling event notifications for Security and Compliance Center](https://docs/security-compliance?topic=security-compliance-event-notifications&interface=ui)

## Broader Incident Response
{: #broader-incident-response}

The above information discussed security response capabilities in {{site.data.keyword.Bluemix_notm:}}. But there are numerous broader solutions in the marketplace that handle security incident responses on a much larger scale to handle all aspects of risk exposure, people, process and technology when there is an event. IBM Cyber Security Services has a replete service in this area known as [IBM X-Force Incident Response Services.](https://www.ibm.com/services/incident-response)

## Vulnerability Management
{: #vulnerability-management}

Vulnerability testing can be quite broad but generally it involves tools that seek to uncover areas that can be exploited by attackers. For example, network vulnerability testing seeks to scan ports, protocols and IP addresses that are open for penetration, perhaps because of user misconfiguration. Often security configurations can “drift” over time because of some inadvertent user actions or changing needs. And there are other ways where vulnerabilities can develop, and which can be exposed. Below are some vulnerability testing/checking capabilities within {{site.data.keyword.Bluemix_notm:}} and some other solutions:


| Area / Solution                                                                                                                                                            | Vulnerability Checking / Testing                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Security and Compliance Center                                                                                                                                                 | Ability to scan resources for misconfigured settings per compliance requirements.                                                                                                                                                                                                                                                                                                                                                                                         |
| [Vulnerability Advisor](Vulnerability%20Advisor%20for%20IBM%20Cloud%20Container%20Registry%20%20IBM%20https:/cloud.ibm.com%20›%20container-registry%20›%20va-v4)               | Ability to scan container images. This vulnerability checking is really applicable where containers may be deployed on top of a Virtual Private Cloud (VPC) Virtual Service Instancea (VSIs).                                                                                                                                                                                                                                                                            |
| Software and Network Vulnerability (the reader may want to refer to this link: [Scanning software for vulnerabilities](https://docs/account?topic=account-scans)) | Various 3rd party market solutions are available, which can be deployed in {{site.data.keyword.Bluemix_notm:}} on Virtual Server Instances (VSIs) IBM Cybersecurity Services (CSS) can source a number of solutions here including its preferred partner [Tenable](https://www.tenable.com/products/vulnerability-management) IBM CSS also has vulnerability management services known as [X-Force Red vulnerability management service](https://www.ibm.com/services/vulnerability-management). |
{: caption="Table 1: Vulnerability Management - Methods"}

### Vulnerability Management - Options, Best Practices and Solutioning Guidance
{: #vulnerability-management-options}

### Options
{: #vulnerability-management-options}

 - **Security and Compliance Center** -  Customers have the option of choosing the resources and configurations they want to scan plus customer have the option picking a variety of compliance
 - **Vulnerability Advisor** - Customers can choose what images to scan and what exemptions there can be when a threat detection occurs.
 - **3rd Party** - Customers have the option of selecting and using a variety of vulnerability testing solutions and each of these have a myriad of configuration options.

### Best Practices
{: #vulnerability-management-best-practices}

 - Customers should establish a vulnerability testing plan and conduct regular vulnerability testing per the plan.
 - Processes, procedures and approval workflows for vulnerability remediations and similar should be well established.

### Solutioning Guidance
 {: #vulnerability-management-guidance}

- [Best practices for working with Security and Compliance Center](https://docs/security-compliance?topic=security-compliance-best-practices)
- [Configuring {{site.data.keyword.Bluemix_notm:}} Vulnerability Advisor scans](https://docs/devsecops?topic=devsecops-cd-devsecops-va-scans)

## Governance, Risk and Compliance
{: #risk-and-compliance}

## Configuration Governance and Compliance Monitoring
{: #configuration-governance-compliance-monitoring}

{{site.data.keyword.Bluemix_notm:}}’s configuration governance and compliance monitoring is handled through its Security and Compliance Center platform, which has been discussed in previous sections.

### Options
{: #config-governance}

- **Security and Compliance Center** - Customers have the option of choosing the resources and configurations they want to scan plus customers have the option picking a variety of compliance frameworks,
- **Palo Alto Prisma Cloud** - This solution from IBM Security provides configuration governance and compliance monitoring in multi-cloud situations,
- **No Configuration Governance or Compliance** -   Customers could elect to forgo security configuration governance in private environments with non-critical workloads. But vulnerabilities could appear where there is security configuration “drift” from personnel making inadvertent changes.  Customers could also forgo compliance monitoring where there are non-critical, non-regulated workloads.

### Best Practices
{: #config-best-practices}

- Understand the compliance framework applicable to your environment.
- Understand how needed compliance frameworks are translated into security configurations.
- Use automation such as Security and Compliance Center to automate security configurations and tracking thereof.
- Develop workflows and approval processes to control security configuration changes. Ensure change rights are strictly controlled through Identity and Access Management (IAM) permissions

### Solutioning Guidance
{: #config-best-practices}

[Best practices for working with Security and Compliance Center](https://docs/security-compliance?topic=security-compliance-best-practices)

### Audit and Regulatory
{: #auditing}

{{site.data.keyword.Bluemix_notm:}} has two main capabilities to aid in auditing: Security and Compliance Center and {{site.data.keyword.cloudaccessfulltrail_notm:}}, both of which were discussed earlier. Security and Compliance Center provides a wide range of compliance audit reports as to the overall state of a customer compliance as compared to various security frameworks, e.g., NIST 800-53, HIPPA, etc. {{site.data.keyword.cloudaccessfulltrail_notm:}} provides an auditing function in that it tracks all IAM and API activities, as previously discussed.  Auditors can use both of these audit functions.  See the following if there is a need to understand {{site.data.keyword.Bluemix_notm:}}'s infrastructure compliance monitoring:  https://docs/overview?topic=overview-compliance

## Options
{: #auditing-options}

 - **Security and Compliance Center** - Customers can use this tool for compliance audit reports and also configuration governance, as noted earlier.  If these functions are needed, Security and Compliance is highly reccommended due to its tight integration with {{site.data.keyword.Bluemix_notm:}}.
 - **Palo Alto Prisma Cloud** - This option may be applicable if there is need for multi-cloud compliance monitoring and configuration governance.  Or the customer may already be using this platform.  Using this solution just for {{site.data.keyword.Bluemix_notm:}} is not recommended due to possible costs and configuration complexities.
 - **No Compliance Monitoring** - Customers could possibly forgo compliance monitoring if the workloads are non-regulated and there are no audit reporting.

### Best Practices*
{: #auditing-best-practices}

- **Best practices for working with Security and Compliance Center** - [Best practices for working with Security and Compliance Center] (https://docs/security-compliance?topic=security-compliance-best-practices)

- **Understanding your responsibilities when using Security and Compliance Center** [Understanding your responsibilities when using Security and Compliance Center] https://docs/security-compliance?topic=security-compliance-responsibilities
