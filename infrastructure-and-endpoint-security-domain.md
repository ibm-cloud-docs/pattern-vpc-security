---

copyright:
  years: 2024
lastupdated: "2024-08-08"

subcollection: pattern-vpc-security

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Infrastructure and endpoint security
{: #IES-domain}

## Core network protection and network segmentation capability
{: #core-network-protection}

{{site.data.keyword.Bluemix_notm}} provides several standard network isolation capabilities to help customer separate and secure traffic and compute workloads. These isolation techniques ensure that any attacks are contained in a network area and to limit the blast radius. For more information, see the following links:

 - [Security in Your VPC](/docs/vpc?topic=vpc-security-in-your-vpc)
 - [About Networking](/docs/vpc?topic=vpc-about-networking-for-vpc)

### Segmentation methods
{: #segmentation-methods}

 - Virtual Private Cloud: VPCs can separate various environments, for example, one VPC for production, one VPC for development and test, one for management, and so on.  There are use cases where there might be one general use VPC that is separate from another VPC in an account like if a customer has two different workload environments. For more information, see [Virtual Private Cloud](https://www.ibm.com/cloud/vpc).
 - Access Control Lists (ACLs): Separate ingress and egress traffic within Virtual Private Cloud (VPC) subnets. For more information, see [Access Control Lists (ACLs)](/docs/vpc?topic=vpc-using-acls)
 - Security groups: Segregates traffic in and out of virtual server network interfaces. This can be considered host firewalling. For more information, see [Security Groups](/docs/security-groups?topic=security-groups-about-ibm-security-groups).
 - Transit gateway: {{site.data.keyword.Bluemix_notm}}’s Transit Gateway can interconnect {{site.data.keyword.Bluemix_notm}} classic, IBM PowerVS, and Virtual Private Cloud (VPC) infrastructures, keeping traffic securely within the {{site.data.keyword.Bluemix_notm}} network. Transit Gateway can be deployed for VPCs in the same region (local routing) and VPCs in different regions (global routing) VPCs to your {{site.data.keywordBluemix_notm}} classic infrastructure VPCs to PowerVS environments. Transit gateways are not always thought as a specific security capability, but transit gateways can provide a form of network segmentation that is known as Pretext Filtering, similar to basic standard firewalls. For more information, see [Filtering routes using Transit Gateway pretext filtering](/docs/dl?topic=dl-prefix-filtering).
 - NexGen firewalls: Firewalls at the Internet can separate public access from internal private compute beyond L3/L4 filtering. It can be considered a key “demilitarized” zone segmentation.

### Options
{: #segmentation-options}

 - Virtual Private Cloud (VPC): There are no options to VPC segmentation, but a customer might elect, for example, to use only one VPC and place all resources in that VPC. This might be used in noncritical environments where there is only one function, for example, a test environment and there is no public access and cost is a factor.
 - Access Control Lists (ACLs): There are no options for using ACLs in VPC environments.
 - Security Groups: There are no alternatives in a VPC environment
 - NexGen firewall: Customers can elect, based on a risk profile and the workload types, to place NexGen firewalls in a separate DMZ (DMZ) edge VPC.
 - Transit gateway: There are no options for using Transit Gateway when you want to interconnect VPCs or connect to other environment, for example, PowerVS. The use of pretext filtering is an option in many situations.

### Best Practices:
{: #segmentation-best-practices}

 - In public environments, always have an Internet edge VPC where a firewall can be placed and act as a DMZ segmentation.
 - Separate environments such as production, development, and test from each other using VPC segmentation.
 - Always apply a “deny all” approach to ACLs and Security Groups and only open ports, protocols, and IP addresses as needed.
 - Conduct periodic reviews of all ACL and Security Group rules. Understand traffic flows between servers to understand what segmentation is needed.

### Solutioning guidance:
{: #segmentation-guidance}

 - [Getting started with Virtual Private Cloud (VPC)](/docs/vpc?topic=vpc-getting-started)
 - [Adding and deleting pretext filters](/docs/transit-gateway?topic=transit-gateway-adding-prefix-filters&interface=ui)

## Edge protection and firewalling capability
{: #core-network-protection-firewall}

Segmentation techniques can be considered firewalling methods. {{site.data.keyword.Bluemix_notm}} has native firewalling in several areas to control IP addresses, ports and protocols and associated ingress and egress traffic. Most notable are ACLs that are firewalls that are applied to created cloud subnets. Security Groups are firewalls that are applied to virtual server instance (VSI) network interfaces. Security Groups work at Level 3 and Level 4 controlling allowed IP addresses, ports, and protocols.

 - [Access Control Lists](/docs/vpc?topic=vpc-using-acls) controls ingress and egress IP addresses, ports and protocol in subnets
 - [Security Groups](/docs/security-groups?topic=security-groups-about-ibm-security-groups): Controls ingress and egress IP addresses, ports, and protocols on virtual server instances network interfaces. This can be considered host firewalling.
 - NexGen firewalls: {{site.data.keyword.Bluemix_notm}} has two firewalls within its catalog, Juniper and Fortinet that can be deployed on VSIs at the edge, and these can fully control Level 3 & 4 traffic, but these are capable of much more filtering like controlling URLs, files, DNS queries and layer 7 web application firewalling. In addition to the firewalls in the {{site.data.keyword.Bluemix_notm}} catalog, customers can bring their own firewall and host it on a VSI.
 - {{site.data.keyword.cis_full_notm}}: {{site.data.keyword.cis_short_notm}} setup has a traditional layer 3/4 firewall, in addition to its WAF capability and other security features. This would be applicable in situation where the customer has dispersed users and where a content delivery network (CDN) solution might be used.
 - [Context Restrictions](/docs/account?topic=account-context-restrictions-whatis): Firewalls in essence that front-end services to control ingresses from certain allowed IP addresses. An example of this is blocking access from Russia on a Saturday night.

### Options
{: #firewalling-options}

 - VPCs, Access Control Lists (ACLs), security groups: There are no mandatory options for all VPC environments. For more information, see [exploring firewalls](/docs/fortigate-10g?topic=fortigate-10g-exploring-firewalls).
 - NexGen Firewalls: Required when there are public connections to the Internet and {{site.data.keyword.cis_full_notm}} will not be used. Required when there are public connections to the Internet and where advanced firewalls features are needed, for example, SD-WAN, file inspections, and so on. Optional in private connections to on-premises, but is still recommended. Optional when {{site.data.keyword.cis_short_notm}} will be used.
 - {{site.data.keyword.cis_full_notm}}: Required where there are other needs such as content delivery networking (CDN), for example, edge content caching, URI controls, distributed TLS terminations, global load balancing, DDoS, and so on. For more information, see [{{site.data.keyword.cis_short_notm}}](/docs/cis?topic=cis-getting-started).

### Best practices
{: #core-network-protection-best-practices}

 - Knowing and documenting all traffic flows, and segment accordingly.
 - Firewalls should be first setup with a “deny all” configurations and IPs. Port and protocols are only opened when necessary.
 - Periodic firewall rules reviews
 - Review the {{site.data.keyword.cis_full_notm}} [best practices](/docs/cis?topic=cis-best-practices-for-cis-setup).

### Solutioning guidance
{: #core-network-protection-guidance}

 - [Monitoring {{site.data.keyword.cis_short_notm}} for optimal security](/docs/cis?topic=cis-manage-your-ibm-cis-for-optimal-security)
 - [Security groups guidelines](/docs/security-groups?topic=security-groups-security-groups-guidelines)
 - [Creating a Network Access Control List (ACL)](/docs/vpc?topic=vpc-acl-create-ui&interface=ui)
 - [Getting started with FortiGate Security Appliance 10 Gbps](/docs/fortigate-10g?topic=fortigate-10g-getting-started)
 - [Getting started with {{site.data.keyword.Bluemix_notm}} Juniper vSRX](/docs/vsrx?topic=vsrx-getting-started)
 - [Monitoring {{site.data.keyword.cis_short_notm}} setup}} for optimal security](/docs/cis?topic=cis-manage-your-ibm-cis-for-optimal-security)
 - [Security groups guidelines](/docs/security-groups?topic=security-groups-security-groups-guidelines)
 - [Creating a Network Access Control List (ACL)](/docs/vpc?topic=vpc-acl-create-ui&interface=ui)
 - [Getting started with FortiGate Security Appliance 10 Gbps](/docs/fortigate-10g?topic=fortigate-10g-getting-started)
 - [Getting started with {{site.data.keyword.Bluemix_notm}} Juniper vSRX](/docs/vsrx?topic=vsrx-getting-started).

## Endpoint detection and endpoint protection capability
{: #EDR-EPP}

Endpoint detection and endpoint protection security are a detection and protect mechanism that works at the operating system and application levels. This can loosely be thought of as anti-virus on a server, but today’s endpoint detection and endpoint protection security solutions provide so much more like hardening, software patching, compliance monitoring, and threat hunting.  Within {{site.data.keyword.Bluemix_notm}}’s Security and Compliance Center (SCC) solution is a component known as IBM Cloud Workload Protection. This might be likened to endpoint detection and endpoint protection security. This provides a broad range of security capabilities to include:

-   A unified and centralized framework to manage the security and compliance of applications, workloads, and infrastructure.
-   Host and image scanning, auditing, and runtime vulnerability management capabilities.
-   Posture management for a distributed environment.
-   Runtime detection and data enrichment.


Within the context of this particular section, only runtime vulnerability and detection are discussed. IBM Cloud Workload Protection also has compliance components, and these are discussed in the governance, risk, and compliance section.

For more information, see [Key features of {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.compliance_long}} Workload Protection](/docs/workload-protection?topic=workload-protection-key-features). This capability can also fall into a security mechanism that is known as vulnerability management.

In addition, see [What is endpoint security](https://www.ibm.com/topics/endpoint-security) and [What is endpoint detection and response.](https://www.ibm.com/topics/edr). 

### Options
{: #endpoint-security-options}

 - {{site.data.keyword.Bluemix_notm}} Workload Protection: Fully integrated into {{site.data.keyword.Bluemix_notm}} with automation aspects and ties in with {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.compliance_long}}.
 - 3rd Party endpoint protection and detection: Stand-alone solutions without {{site.data.keyword.Bluemix_notm}} integration, but that might be applicable if a customer is using an endpoint security solution on-premises or in a multi-cloud situation. IBM Security, now known as Cybersecurity Services, has a endpoint detection and endpoint protection solution known as [Reaqtq](https://mediacenter.ibm.com/media/IBM+Security+ReaQta+Explained/1_l31z0vax){: external}. IBM Cybersecurity Services also sells, consults on, implements, and manages various 3rd-party endpoint detection and endpoint protection market solutions.
 - No workload protection or endpoint security: This option depends upon the customer risk profile and what type of workloads are being used. This might be applicable in a private environment with no Internet access or low risk situations with dev and test environments, and perhaps where cost is a factor.

### Best practices
{: #endpoint-security-best-practices}

 - Cloud Workload Protection is always recommended in public environments.
 - Any cloud workload protection should be accompanied with people and processes to use the service or tool to find threats and vulnerability holistically. A set and forget approach should never be used.

### Solutioning guidance
{: #endpoint-security-solution}

 - [Getting started with {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.compliance_long}} Workload Protection](/docs/workload-protection?topic=workload-protection-getting-started)
 - In addition, review the respective 3rd party endpoint detection and endpoint protection solution documentation that's applicable to your use case.

## Virtual Private Endpoints (VPEs)
{: #VPE}

{{site.data.keyword.Bluemix_notm}} has Virtual Private Endpoints (VPE) that allow secure access to various cloud services without traversing the Internet. VPEs have firewalls in the form of access control lists and security groups previously discussed.  {{site.data.keyword.Bluemix_notm}} Virtual Private Endpoints (VPE) for VPC enables you to connect to supported {{site.data.keyword.Bluemix_notm}} services from your VPC network by using the IP addresses of your choosing, which is allocated from a subnet within your VPC. VPE is an evolution of the private connectivity to {{site.data.keyword.Bluemix_notm}} services. VPEs are virtual IP interfaces that are bound to an endpoint gateway created on a per service, or service instance, basis depending on the service operation model. The endpoint gateway is a virtualized function that scales horizontally, is redundant and highly available, and spans all availability zones of your VPC. Endpoint gateways enable communications from virtual server instances within your VPC and {{site.data.keyword.Bluemix_notm}} service on the private backbone. VPE for VPC gives you the experience of controlling all the private addressing within your cloud.

### Options
{: #VPE-options}

 - VPE use: This option is always recommended due to its inherent security and private traffic transit.
 - Cloud Service Access Through the Internet: This is never recommended, but a possible transit if cloud service access is needed in some way across the Internet.

### Best practices
{: #VPE-best-practices}

 - Virtual Private Endpoints (VPEs) should always be used when there is a need to access cloud services as opposed to any access over the Internet
 - VPEs have security features that should be considered during the implementation process. One is that VPEs have Access Control Lists (ACLs) that can control all traffic in and out of the VPE
 - Additionally, vPE security groups can be applied to control inbound application traffic.

### Solutioning guidance
{: #VPE-guidance}

 - [Privately connecting to {{site.data.keyword.Bluemix_notm}} services](/docs/overview?topic=overview-endpoints-support)
 - [About virtual private endpoint gateways](/docs/vpc?topic=vpc-about-vpe)
 - [Configuring ACLs and security groups for use with endpoint gateways](/docs/vpc?topic=vpc-configure-acls-sgs-endpoint-gateways&interface=ui)
