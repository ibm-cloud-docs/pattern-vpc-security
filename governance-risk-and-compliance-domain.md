---

copyright:
  years: 2024
lastupdated: "2024-07-26"

subcollection: pattern-vpc-security

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Governance, Risk and Compliance
{: #governance-domain}

## Configuration Governance / Management
{: #configuration-governance-compliance-monitoring}

{{site.data.keyword.Bluemix_notm}}’s configuration governance is handled through its {{site.data.keyword.compliance_long}} platform, which has been discussed in previous sections.

### Options
{: #config-governance}

- **{{site.data.keyword.compliance_long}}** - Customers have the option of choosing the resources and configurations they want to scan for status and parameters,
- **Palo Alto Prisma Cloud** - This solution from IBM Cybersecurity Services provides configuration governance in multi-cloud situations,
- **Manual Configuration Management** - Customers could possible track configurations manually, say through spreadsheets and the like, but this method is tedious and prone to errors.  This could be a possibility with non-critical workloads in a private access situation and,
- **No Configuration Governance** -   Never recommended even in private situations and or non-critical.  Vulnerabilities could be opened up where there is security configuration “drift” from personnel making inadvertent changes.  And customers would be unable to locate possible problems without significant inspection.

### Best Practices
{: #config-best-practices-risk}

- Establish a configuration management policy and develop and design security configurstions well before any deployment,
- Understand the compliance framework applicable to your environment that could possibly drive configurations,
- Understand how needed compliance frameworks are translated into security configurations,
- Use automation such as {{site.data.keyword.compliance_long}} to automate security configurations and tracking thereof,
- Develop workflows and approval processes to control security configuration changes,
- Ensure change rights are strictly controlled through Identity and Access Management (IAM) permissions and any Privilege Access Management (PAM) granular permissions, and
- [Best practices for working with {{site.data.keyword.compliance_long}}]

### Solutioning Guidance
{: #config-best-practices}

[SCC guidance] (/docs/security-compliance?topic=security-compliance-assign-roles) and other drop downs in "how to - setting up the service" section.

## Audit and Regulatory and Compliance Monitoring
{: #auditing-risk-regulatory}

In some respects auditing and regulatory aspects and conmpliance monitoring are all related.{{site.data.keyword.Bluemix_notm}} has two main capabilities to aid in auditing: {{site.data.keyword.compliance_long}} and {{site.data.keyword.cloudaccesstraillong_notm}}, both of which were discussed earlier. {{site.data.keyword.compliance_long}} provides a wide range of compliance audit reports as to the overall state of a customer compliance as compared to various security frameworks, e.g., NIST 800-53, HIPPA, etc. {{site.data.keyword.cloudaccesstrailshort}} provides an auditing function in that it tracks all IAM and API activities, as previously discussed.  Auditors can use both of these audit functions.  See the following if there is a need to understand {{site.data.keyword.Bluemix_notm}}'s underlying infrastructure compliance monitoring (typically referred to "below the line monitoring):  [compliance monitoring](/docs/overview?topic=overview-compliance)

Note that regulated workloads have specific compliance framework adherence requirements and "regulatory" aspects are subsumed to a certain degree in compliance monitoring and auditing.

### Options
{: #auditing-options}

 - **{{site.data.keyword.compliance_long}}** - Customers can use this tool for compliance monitoring and audit reports.  This is highly reccommended due to its tight integration with {{site.data.keyword.Bluemix_notm}}.
 - **Palo Alto Prisma Cloud** - This option may be applicable if there is need for multi-cloud compliance monitoring.  Or the customer may already be using this platform.  Using this solution just for {{site.data.keyword.Bluemix_notm}} is not recommended due to possible costs and solution configuration complexities.
 - **No Compliance Monitoring** - Customers could possibly forgo compliance monitoring and auditing if the workloads are non-regulated and there are no audit reporting requirements.

### Best Practices
{: #auditing-best-practices}

- **Best practices for working with {{site.data.keyword.compliance_long}}** - [Best practices for working with SCC] (/docs/security-compliance?topic=security-compliance-best-practices)

### Solutioning Guidance
{: #auditing-best-guidance}

- [Provisioning an instance](/docs/activity-tracker?topic=activity-tracker-provision ) and related items on this page.

- [compliance best practices](/docs/security-compliance?topic=security-compliance-best-practices)



