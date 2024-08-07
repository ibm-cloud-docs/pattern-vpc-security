---

copyright:
  years: 2024
lastupdated: "2024-08-07"

subcollection: pattern-vpc-security

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Data security
{: #data-security}

Data security is the process of protecting digital information throughout its life cycle from unauthorized access, corruption, theft, or destruction. The following sections discusses {{site.data.keyword.Bluemix_notm}}'s capabilities in this domain.

## Data-at-rest encryption
{: #data-at-rest-encryption}

{{site.data.keyword.Bluemix_notm}} provides native, integrated data-at-rest encryption for VPC volumes and snapshots and file storage/VPC shares automatically. {{site.data.keyword.Bluemix_notm}} also provides data-at-rest encryption for its object storage by default. All the encryption used adheres to the AES-256 standard. Customers can use IBM-managed encryption (default) or customer-managed keys.

### Options
{: #data-at-rest-encryption-options}

The following options are available for data-at-rest encryption:

 - {{site.data.keyword.Bluemix_notm}} default encryption: This is automatic if another key management scheme isn't selected. IBM keys are used
 - {{site.data.keyword.Bluemix_notm}} encryption with customer keys: The customer selects an {{site.data.keyword.Bluemix_notm}} native key management system (KMS). {{site.data.keyword.Bluemix_notm}} has two KMSs: {{site.data.keyword.keymanagementservicelong_notm}} and {{site.data.keyword.hsplatform}}
 - External encryption solution: A customer might be using their own data encryption solution on-premises and want to extend this to the cloud. Or, a customer might want centralized data control across multiple clouds. {{site.data.keyword.IBM_notm}} IBM Cybersecurity Services has an applicable solution known as [Guardium](https://www.ibm.com/guardium){: external}.

### Best practices
{: #data-at-rest-encryption-best-practices}

 - Data encryption should always be used as can be expected
 - Cloud native encryption with a designated cloud native KMS provides the best lifecycle automation and orchestration
 - Encrypting data with customer managed keys is recommended to meet regulatory compliance for additional security and customer control.

### Solutioning guidance
{: #data-at-rest-encryption-guidance}

 - [Securing Your Data in VPC](/docs/vpc?topic=vpc-mng-data&interface=ui)
 - [About data encryption for VPC](/docs/vpc?topic=vpc-vpc-encryption-about)
 - [Encrypting Your Data](/docs/cloud-object-storage?topic=cloud-object-storage-encryption).
 - [Encrypting Your Data](/docs/cloud-object-storage?topic=cloud-object-storage-encryption)

## Key management and lifecycle management
{: #key-management}

Key management allows cloud customers the ability to create, store, manage and rotate keys with automation to support storage encryption. {{site.data.keyword.Bluemix_notm}} has two native, integrated key management services, {{site.data.keyword.keymanagementservicelong_notm}} and Hyper Protect Crypto Services. For more information see:
 - [{{site.data.keyword.keymanagementservicefull}}](/docs/key-protect?topic=key-protect-about)
 - [Getting started with Hyper Protect Crypto Services](/docs/hs-crypto?topic=hs-crypto-get-started)
 - [Introducing Unified Key Orchestrator](/docs/hs-crypto?topic=hs-crypto-introduce-uko)

![A screenshot of a computer description automatically generated](images/keyprotectframework.svg){: caption="Figure 1. Key Management Capabilities" caption-side="bottom"}

### Options
{: #key-management-options}

The following options are available for key management:

 - {{site.data.keyword.keymanagementservicelong_notm}} - Applicable in situations where key storage security requirements are not highly critical and where a multi-tenant solution is sufficient. This capability is commonly referred to as Bring Your Own Key (BYOK) and it is certified to meet the Federal Information Processing Standard (FIPS)-140-2 level 3, hardware security module (HSM) requirements

 - Hyper Protect Crypto Service (HPCS): {{site.data.keyword.hsplatform}} provides key management services with the highest level of security and control offered by any cloud provider in the industry. It uses a dedicated (single-tenant) FIPS 140-2 Level 4 certified Hardware Security Module and supports customer-managed master keys, giving the customer exclusive control of the entire key hierarchy. {{site.data.keyword.hsplatform}} is specifically recommended for financial service environment

 - {{site.data.keyword.Bluemix_notm}} native {{site.data.keyword.hsplatform}} with Unified Key Orchestrator - This particular variant of the {{site.data.keyword.hsplatform}} key management solution noted directly above add the ability to manage key across various clouds in addition to {{site.data.keyword.Bluemix_notm}}

 - Customer or 3rd party key management solution: This might be applicable when a customer is using an external or 3rd party solution in a hybrid or multi-cloud environment.

### Best practices
{: #key-management-best-practices}

 - Cloud native key management offers the most secure, integrated and automated key lifecycle management.
 - User access to keys should be tightly controlled and monitored as can be expected.
 - Processes should be established on how keys should be used and managed. Proper rotation of keys should be established.
 - Regular inspection of activity logs surrounding key management should occur.

### Solutioning guidance
{: #key-management-guidance}

 - [Provisioning {{site.data.keyword.keymanagementservicelong_notm}}](/docs/key-protect?topic=key-protect-provision)
 - [Getting Started with {{site.data.keyword.Bluemix_notm}} Hyper Protect Crypto Service](/docs/hs-crypto?topic=hs-crypto-get-started).

## Data-in-transit encryption
{: #Data-in-Transit-Encryption}

Data-in-transit encryption can occur in multiple areas within the {{site.data.keyword.Bluemix_notm}}. There can be external applications using HTTPS/SSL that would terminate to servers within a VPC or load balancers and NexGen firewalls in front of the servers in VPCs. There is also default data-in-transit encryption when there are accesses and traffic transits to Object, Block and File Storage and cloud services.

### Options
{: #data-in-transit-encryption-options}

The following options are possibilities for data-in-transit encryption:

 - Data-in-Transit encryption to {{site.data.keyword.Bluemix_notm}} storage - No options. This is a default function
 - Application Level Data-in-Transition Encryption*- Applicable mostly in public access situations but of course this can be applied in private access situations. Transit Level Security (TLS) 1.2 should be used at a minimum
 - Application-level data-in-transit encryption termination - TLS termination at a NexGen firewall TLS termination at an edge load balancer TLS termination with {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.cis_short_notm}}

### Best practices
{: #data-in-transit-encryption-best-practices}

Application-level data-in-transition encryption should always be applied in public access situations. Application-level data-in-transit encryption should always be terminated at the edge at a firewall or a load balancer. When the traffic is decrypted at the edge, it can be inspected for threats, and so on. Application-level encryption termination should not occur on servers that are in the interior of a network.

### Solutioning guidance
{: #data-in-transit-encryption-best-guidance}

 - [Encryption in transit - Securing mount connections between file share and virtual server instance](/docs/vpc?topic=vpc-file-storage-vpc-eit)
 - [Encryption in transit - Securing mount connections between file share and virtual server instance](/docs/vpc?topic=vpc-file-storage-vpc-eit)
 - [SSL offload with {{site.data.keyword.Bluemix_notm}} Load Balancer](/docs/loadbalancer-service?topic=loadbalancer-service-ssl-offload-with-ibm-cloud-load-balancer)
 - [Managing origin certificates](/docs/cis?topic=cis-cis-origin-certificates)
 - [Setting Transport Layer Security (TLS) options](/docs/cis?topic=cis-cis-tls-options)
 - [Getting started with {{site.data.keyword.secrets-manager_full_notm}}](/docs/secrets-manager?topic=secrets-manager-getting-started&interface=ui)  ({{site.data.keyword.secrets-manager_full_notm}} will be discussed further in the document, but it can store certificates that can be used in data-in-transit encryption.) Also see the following immediate section relating to certificates.

## Certificate lifecycle management
{: #certificate-management}

Certificates can be used in several areas within {{site.data.keyword.Bluemix_notm}} to provide data-in-transit TLS encryption in such areas as load balancers, API gateways, and so on. {{site.data.keyword.Bluemix_notm}} has certificate management capabilities which allow customers to provision, manage, and deploy public and private SSL/TLS certificates for use with {{site.data.keyword.Bluemix_notm}} services and applications. For more information see: [Getting started with {{site.data.keyword.secrets-manager_full_notm}}](/docs/secrets-manager?topic=secrets-manager-getting-started)

### Options:
{: #certificate-management-options}

The following options are available for certificate management:

 - {{site.data.keyword.secrets-manager_full_notm}} - Highly recommended when {{site.data.keyword.Bluemix_notm}} is primarily used
 - No Certificate Management - Perhaps applicable in private environments with Dev/QA workloads and or where there is a minimal number of certificates to managed
 - Customer-Owned or 3rd Party Certificate Management Solutions.

### Best practices
{: #certificate-management-best-practices}

 - Regular rotations of certificates
 - Notification of expiring certificates
 - Certificate storage in a hardware security module
 - Maintain certificate inventory
 - Document certificate management procedures.

### Certificate management solutioning guidance
{: #certificate-management-guidance}

 - [Importing SSL/TLS certificates](/docs/secrets-manager?topic=secrets-manager-certificates&interface=ui)
 - [Ordering SSL/TLS public certificates](/docs/secrets-manager?topic=secrets-manager-public-certificates&interface=ui)
 - [Creating SSL/TLS private certificates](/docs/secrets-manager?topic=secrets-manager-private-certificates&interface=ui)

## Data lifecycle management and governance
{: #data-lifecycle-management}

{{site.data.keyword.Bluemix_notm}} provides a range of data security measures as discussed, but customers may want full data lifecycle management and security across data in hybrid or multi-cloud environments. These capabilities may include data discovery, data classification, data tagging, data integrity checks and loss prevention among others. There are several 3rd party solutions in the market in this full data lifecycle management realm. One such solution from IBM Cyber Security Services is known [Guardium](https://www.ibm.com/guardium){: external}.

## Data Loss Prevention (DLP) and data access, integrity and monitoring
{: #DLP}

{{site.data.keyword.Bluemix_notm}} has a number of ways to control data access such as identity and access management (IAM) and permissions on object storage and so on. And there is {{site.data.keyword.cloudaccesstraillong_notm}} which logs all user and API access to data. But there are no specific ways to specifically monitor and control data loss and data integrity. This is typically the realm of 3rd party data control solutions.For more information on this security function see:

For more information, see [What Is Data Loss Prevention (DLP)](https://www.ibm.com/topics/data-loss-prevention){: external}.
