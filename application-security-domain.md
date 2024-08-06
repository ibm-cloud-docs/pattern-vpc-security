---

copyright:
  years: 2024
lastupdated: "2024-08-06"

subcollection: pattern-vpc-security

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Application Security
{: #Appsec}

## Web Application Firewalling (WAF)
{: #WAF}

Web Application Firewalls (WAF) help protect web applications by performing edge filtering and monitoring HTTP traffic between a web application and the Internet. WAF is an OSI protocol Layer-7 defense in the OSI model, and it is not designed to defend against all types of attacks. {{site.data.keyword.Bluemix_notm}} has two ways to provide web application firewalling at the Internet edge. One that is typically used in a Content Delivery Network (CDN) and which is named {{site.data.keyword.cis_short_notm}}. The other WAF option is using NexGen firewalls that can be placed on the “edge” or in front of Transit VPCs. You can find information on your NexGen firewalls WAF capabilities in their respective product documentation.

### Options
{: #WAF-options}

- {{site.data.keyword.cis_full_notm}}: Using Cloud Internet Service WAFs may be more applicable in situations where you need a broad range of capabilities that are commonly found in Content Delivery Networks such as global load balancing, DNS features, URL control and so on
- NexGen Firewall: Applicable where a NexGen firewall is already at the Internet edge and there are no additional needs that can be found in content delivery networks. NexGen firewalls are typically deployed in “edge” or transit VPCs to provide more advanced firewall functions like Intrusion Detection / Intrusion Protect (IDS/IPS) among other capabilities
- {{site.data.keyword.cis_full_notm}}: Using Cloud Internet Service (CIS) WAFs may be more applicable in situations where you need a broad range of capabilities that are commonly found in Content Delivery Networks such as global load balancing, DNS features, URL control
- NexGen Firewall: Applicable where a NexGen firewall is already at the Internet edge and there are no additional needs that can be found in content delivery networks. NexGen firewalls are typically deployed in “edge” or transit VPCs to provide more advanced firewall functions like Intrusion Detection / Intrusion Protect (IDS/IPS) among other capabilities
- No WAF: Customer might elect to forgo the use of a WAF in private environments where there might be a private connection to on-premises infrastructure. A customer might have their own WAF in a Demilitarized Zone (DMZ) on-premises.

### Best practices
{: #WAF-best-Practices}

Review the following best practices for Web Application Firewalls:

 - WAF should always be used in public access environments. There are many options and configurations with WAF that relate to HTTP/HTTPS, domains, and detection policies. Customers should thoroughly review these items and adapt to their own specific security needs and associated security policies
 - As with other security protection and detections capabilities, logs should be stored and inspected regularly for signs of anomalies
 - As with other security protection and detections capabilities, logs should be stored and inspected regularly for signs of anomalies
 - WAF logs should generally be correlated with other logs, perhaps through a Security Event and Information Management (SIEM) platform, if available.

### Solutioning guidance:
 {: #WAF-best-guidance}

 - [Best practices for {{site.data.keyword.cis_short_notm}}](/docs/cis?topic=cis-best-practices-for-cis-setup)
 - [Bring Your Own (BYO) firewalls in {{site.data.keyword.Bluemix_notm}}.](/docs/gateway-appliance?topic=gateway-appliance-order-byoa)
 - [Deploying Fortigate firewall on IBM VPC Cloud.](/docs/fortigate-10g?topic=fortigate-10g-getting-started)
 - [Deploying Fortigate firewall on IBM VPC Cloud.](/docs/fortigate-10g?topic=fortigate-10g-getting-started).

## Distributed Denial of Service (DDoS)
{: #DDoS}

A distributed denial of service (DDoS) attack is a malicious attempt to disrupt normal traffic of a server, service, or network by overwhelming the target or its surrounding infrastructure with a flood of internet traffic. These attacks can occur at the application layer and the network layer. {{site.data.keyword.Bluemix_notm}} has two ways of providing DDoS protection for designs that have public internet access. One is using {{site.data.keyword.cis_short_notm}}, and the other is using NexGen firewalls, that can be deployed on Virtual Server Instances at the Internet edge. Review the following links for more information:
- [Dealing with Distributed Denial of Service attacks](/docs/cis?topic=cis-distributed-denial-of-service-ddos-attack-concepts)
- [About {{site.data.keyword.Bluemix_notm}} Internet Services](/docs/cis?topic=cis-about-ibm-cloud-internet-services-cis)
- Information on NexGen firewalls DDoS capabilities can be found in their respective product documentation.

### Options:
 {: #ddos-options}

- {{site.data.keyword.cis_short_notm}}: Applicable in public internet access environments, particularly in production environments and where dispersed users are accessing apps in a content delivery manner
- NexGen Firewall: More applicable where an edge firewall is already being used to and users are not dispersed, and cost is a factor.
- {{site.data.keyword.cis_short_notm}}: Applicable in public internet access environments, particularly in production environments and where dispersed users are accessing apps in a content delivery manner
- NexGen Firewall: More applicable where an edge firewall is already being used to and users are not dispersed, and cost is a factor.
- No DDoS: Not required in private only networks.

### Best practices:
 {: #ddos-best-practice}

 - [Best practices for {{site.data.keyword.cis_short_notm}} setup}} setup](/docs/cis?topic=cis-best-practices-for-cis-setup)
 - [Best practices for {site.data.keyword.cis_short_notm} setup](/docs/cis?topic=cis-best-practices-for-cis-setup)
 - Create a DDoS attack threat model that is a structured approach to identifying and analyzing potential risks to your online service or website from a DDoS attack
 - Implement rate limiting by controlling the amount of traffic that is sent to a network or server
 - Ensure log monitoring and analysis of web traffic to look for anomalies such as unusual high traffic volume or server errors.

### Solutioning guidance:
{: #ddos-guidance}

 - [FAQs for {{site.data.keyword.Bluemix_notm}} Internet Services](/docs/cis?topic=cis-faq)
 - [Managing your {{site.data.keyword.cis_short_notm}} setup deployment](/docs/cis?topic=cis-manage-your-cis-deployment).
