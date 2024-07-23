---

copyright:
  years: 2024
lastupdated: "2024-07-23"

subcollection: pattern-vpc-security

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Infrastructure and Endpoint Security Domain
{: #IES domain}

## Infrastructure and Endpoint Security Domain
{: #IES}

## Core Network Protection / Network Segmentation Capability
{: #core-network-protection}

{{site.data.keyword.Bluemix_notm}} provides several standard network isolation capabilities to help customer segregate and secure traffic and compute workloads.  Please see the methods below. These isolation techniques ensure that any attacks are contained in a network area and to limit the “blast radius."  Please see the following links for more information on network segmentation:

 - [Security in Your VPC](/docs/vpc?topic=vpc-security-in-your-vpc),
 - [About Networking](/docs/vpc?topic=vpc-about-networking-for-vpc), and
 - [Security in your VPC](/docs/vpc?topic=vpc-security-in-your-vpc)

### Segmentation Methods:
{: #segmentation-methods}

 - **Virtual Private Cloud** - VPCs Can segregate various environments, e.g., one VPC for production, one VPC for Dev/Test, one for management, etc.  And of course, there are use cases where there may be one general use VPC that is completely separate from another VPC in an account, i.e., a customer have two different workload environments. [Virtual Private Cloud](https://www.ibm.com/cloud/vpc),
 - **Access Control Lists (ACLs)** - Segregate ingress and egress traffic within Virtual Private Cloud (VPC) subnets. [Access Control Lists (ACLs)](/docs/vpc?topic=vpc-using-acls#:~:text=You%20can%20use%20an%20access,to%20and%20from%20the%20instances.),
 - **Security Groups** - Segregates traffic in and out of virtual server network interfaces, This could be considered host firewalling. [Security Groups](/docs/security-groups?topic=security-groups-about-ibm-security-groups)
 - **Transit Gateway** - {{site.data.keyword.Bluemix_notm}}’s Transit Gateway can interconnect {{site.data.keyword.Bluemix_notm}} classic, IBM PowerVS and Virtual Private Cloud (VPC) infrastructures, keeping traffic securely within the {{site.data.keyword.Bluemix_notm}} network.  Transit Gateway can be deployed for: VPCs in the same region (local routing) and VPCs in different regions (global routing) VPCs to your {{site.data.keyword.Bluemix_notm}} classic infrastructure VPCs to PowerVS environments.  Now transit gateways are not always thought as a specific security capability, but Transit Gateways can provide a form of network segmentation known as Pretext Filtering, similar to basic standard firewalls.  More information here can be found at: [Filtering Routes using Transit Gateway pretext filtering](/docs/dl?topic=dl-prefix-filtering)
 - **NexGen Firewalls** - Firewalls at the Internet can segregate public access from internal private compute beyond L3/L4 filtering. It can be considered a key “demilitarized” zone segmentation.

### Options:
{: #segmentation-options}

 - **VPC** - There are no options to VPC segmentation, but customer could elect, for example, to only use one VPC and place all resources in that VPC.  This could be used in non-critical environments where there is only one function, e.g., test and there is no public access and cost is a factor,
 - **Access Control Lists** - There are no options for using ACLs in VPC environments,
 - **Security Groups** - There are no alternatives in a VPC environment,
 - **NexGen Firewall** - Customers can elect, based upon a risk profile and the workload types, to place NexGen firewalls in a separate Dimilaritized Zone (DMZ) edge VPC.
 - **Transit Gateway** - There are no options for using Transit Gateway when you want to interconnect VPCs or connect to other environment, e.g., PowerVS.  But the use of pretext filtering is options in many situations.

### Best Practices:
{: #segmentation-best-practices}

 - In public environments, always have an Internet edge VPC where a firewall can be placed and act as a Demilitarized Zone segmentation,
 - Separate production, dev, test, etc. from each other using VPC segmentation,
 - Always apply a “deny all” approach to ACLs and Security Groups and only open ports, protocols and IP addresses as needed, and
 - Conduct periodic reviews of all ACL and Security Group rules. Understand traffic flows between servers so as to understand what segmentation is needed.

### Solutioning Guidance:
{: #segmentation-guidance}

 - [Getting started with Virtual Private Cloud (VPC)](/docs/vpc?topic=vpc-getting-started)
 - [Adding and deleting pretext filters](/docs/transit-gateway?topic=transit-gateway-adding-prefix-filters&interface=ui)

## Edge Protection / Firewalling Capability
{: #core-network-protection-firewall}

Segregation techniques were discussed in the previous section and in some way, these can be considered firewalling methods as well.  {{site.data.keyword.Bluemix_notm}} has native firewalling in several areas to control IP addresses, ports and protocols and associated ingress and egress traffic.  Most notable are ACLs that are firewalls that are applied to created cloud subnets.  Security Group are firewalls that are applied virtual server instance (VSI) network interfaces.  Security Groups work at the Level 3/ Level 4 level controlling allowed IP addresses, ports, and protocols.

 - [Access Control Lists](/docs/vpc?topic=vpc-using-acls#:~:text=You%20can%20use%20an%20access,to%20and%20from%20the%20instances.) Controls ingress and egress IP addresses, ports and protocol in subnets,
 - [Security Groups](/docs/security-groups?topic=security-groups-about-ibm-security-groups) - Controls ingress and egress IP addresses, ports and protocols on virtual server instances network interfaces. This can be considered host firewalling,
 - **NexGen Firewalls** - {{site.data.keyword.Bluemix_notm}} has two firewalls within its catalog, Juniper and Fortinet, that can be deployed on VSIs at the edge, and these can fully control Level 3 & 4 traffic, but these are capable of much more filtering like controlling URLs, files, DNS queries and layer 7 web application firewalling. In addition to the firewalls in the {{site.data.keyword.Bluemix_notm}} catalog, customers can bring their own firewall and host it on a VSI,
 - **{{site.data.keyword.cis_full_notm}}** - {{site.data.keyword.cis_short_notm}} setup has a traditional layer 3/4 firewall, in addition to its WAF capability and other security features. This would be applicable in situation where the customer has dispersed users and where a content delivery network (CDN) solution may be used, and
 - [Context Restrictions](/docs/account?topic=account-context-restrictions-whatis)                                            Firewalls in essence that front end services to control ingresses from certain allowed IP addresses. E.g., blocking accesses from Russia on a Saturday night.

### Options:
{: #firewalling-options}

 - **VPCs, Access Control Lists (ACLs), Security Groups** - No options – mandatory for all VPC environments. Please see: [exploring firewalls](/docs/fortigate-10g?topic=fortigate-10g-exploring-firewalls)

 - **NexGen Firewalls** - Required when there are public connections to the Internet and {{site.data.keyword.cis_full_notm}} will not be used. Required when there are public connections to the Internet and where advanced firewalls features are needed, e.g., SD-WAN, file inspections, etc. Optional in private connections to on-prem, but still recommended. Optional when {{site.data.keyword.cis_short_notm}} will be used.

 - **{{site.data.keyword.cis_full_notm}}** - [{{site.data.keyword.cis_short_notm}}](/docs/cis?topic=cis-getting-started).  Required where there are other needs such as content delivery networking (CDN), e.g., edge content caching, URI controls, distributed TLS terminations, global load balancing, DDoS, etc.

### Best Practices
{: #core-network-protection-best-practices}

 - Knowing and documenting all traffic flows, and segment accordingly,
 - Firewalls should be first setup with a “deny all” configurations and IPs, port and protocols are only opened when necessary,
 - Periodic firewall rules reviews, and
 - {{site.data.keyword.cis_full_notm}}[best practices](/docs/cis?topic=cis-best-practices-for-cis-setup)

### Solutoning Guidance
{: #core-network-protection-guidance}

 - [Monitoring {{site.data.keyword.cis_short_notm}} setup}} for optimal security](/docs/cis?topic=cis-manage-your-ibm-cis-for-optimal-security),
 - [Security Groups guidelines](/docs/security-groups?topic=security-groups-security-groups-guidelines),
 - [Creating a Network Access Control List (ACL)](/docs/vpc?topic=vpc-acl-create-ui&interface=ui),
 - [Getting started with FortiGate Security Appliance 10 Gbps](/docs/fortigate-10g?topic=fortigate-10g-getting-started), and
 - [Getting started with {{site.data.keyword.Bluemix_notm}} Juniper vSRX](/docs/vsrx?topic=vsrx-getting-started)

## Endpoint Detection / Endpoint Protection (EDR/EPP) Capability
{: #EDR-EPP}

EDR/EPP security is a detection and protect mechanism that works at the operating system and application levels. This can loosely thought of anti-virus on a server, but today’s EDR/EPP solutions provide so much more like hardening, software patching, compliance monitoring, threat hunting, etc.  Now within {{site.data.keyword.Bluemix_notm}}’s Security and Compliance Center solution is a component known as Cloud Workload Protection. This could be likened to Endpoint Protection / Detection (EPP/EDR) security.  This provides a broad range of security capabilities to include:

-   A unified and centralized framework to manage the security and compliance of applications, workloads, and infrastructure,
-   Host and image scanning, auditing, and runtime vulnerability management capabilities,
-   Posture management for a distributed environment, and
-   Runtime detection and data enrichment

Now within the context of this particular section, only runtime vulnerability and detection will be discussed. Cloud Workload Protection also has compliance components, and these are discussed in the Governance, Risk and Compliance section.

Please see the following link for information: [Key features of {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.compliance_long}} Workload Protection](/docs/workload-protection?topic=workload-protection-key-features). This capability can also fall into a security mechanism known as Vulnerability Management. Information on this follows in the Vulnerability Management section.

Also see this link which has broad information on endpoint security: [What is endpoint security](https://www.ibm.com/topics/endpoint-security) and [What is endpoint detection and response.](https://www.ibm.com/topics/edr)

### Options
{: #endpoint-security-options}

 - **{{site.data.keyword.Bluemix_notm}} Workload Protection** - Fully integrated into {{site.data.keyword.Bluemix_notm}} with automation aspects and ties in with {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.compliance_long}},
 - **3rd Party Endpoint Protection and Detection (EPP/EDR)** - Stand-alone solutions without {{site.data.keyword.Bluemix_notm}} integration, but that may be applicable if a customer is using an endpoint security solution on-prem or in a multi-cloud situation. IBM Security, now known as Cybersecurity Services (CSS), has a EPP/EDR solution known as [Reaqtq](https://mediacenter.ibm.com/media/IBM+Security+ReaQta+Explained/1_l31z0vax).  IBM Cybersecurity Services also sells, consults on, implements and manages various 3rd party EPP/EDR market solutions.
 - **No Workload Protection Endpoint Security** - This option depends upon the customer risk profile and what type of workloads are being used.  This could be applicable in a private environment with no Internet access or low risk situations with dev and test environments, and perhaps where cost is a factor.

### Best Practices
{: #endpoint-security-best-practices}

 - Cloud Workload Protection (CWP) is always recommended in public environments, and
 - Any cloud workload protection should be accompanied with people and processes to use the service or tool to find threats and vulnerability wholistically. A “set and forget” approach should never be used.

### Solutioning Guidance
{: #endpoint-security-solution}

 - [Getting started with {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.compliance_long}} Workload Protection](/docs/workload-protection?topic=workload-protection-getting-started)
 - See respective 3rd party EPP/EDR solution documenation.

## Virtual Private Endpoints
{: #VPE}

{{site.data.keyword.Bluemix_notm}} has Virtual Private Endpoints that allow secure access to a variety of cloud services without traversing the Internet. Note that VPEs have firewalls in the form of access control lists and security groups previously discussed.  {{site.data.keyword.Bluemix_notm}}® Virtual Private Endpoints (VPE) for VPC enables you to connect to supported {{site.data.keyword.Bluemix_notm}} services from your VPC network by using the IP addresses of your choosing, allocated from a subnet within your VPC.  VPE is an evolution of the private connectivity to {{site.data.keyword.Bluemix_notm}} services. VPEs are virtual IP interfaces that are bound to an endpoint gateway created on a per service, or service instance, basis (depending on the service operation model).  The endpoint gateway is a virtualized function that scales horizontally, is redundant and highly available, and spans all availability zones of your VPC. Endpoint gateways enable communications from virtual server instances within your VPC and {{site.data.keyword.Bluemix_notm}}® service on the private backbone.  VPE for VPC gives you the experience of controlling all the private addressing within your cloud. Please see the following links for more information:

### Options
{: #VPE-options}

 - **VPE use** - always recommended due to its inherent security and private traffic transit, and
 - **Cloud Service Access Through the Internet** - Never recommended, but a possible transit if cloud service access is needed in some way across the Internet.

### Best Practices
{: #VPE-best-practices}

 - Virtual Private Endpoints should always be used when there is a need to access cloud services as opposed to any access over the Internet,
 - VPEs have security features that should be considered during the implementation process. One is that VPEs have Access Control Lists (ACLs) that can control all traffic in and out of the VPE, and
 - Another is that VPE Security Groups can additionally be applied to control inbound application traffic.

### Solutioning Guidance
{: #VPE-guidance}

 - [Privately connecting to {{site.data.keyword.Bluemix_notm}} services](/docs/overview?topic=overview-endpoints-support),
 - [About virtual private endpoint gateways](/docs/vpc?topic=vpc-about-vpe), and
 - [Configuring ACLs and security groups for use with endpoint gateways](/docs/vpc?topic=vpc-configure-acls-sgs-endpoint-gateways&interface=ui).




