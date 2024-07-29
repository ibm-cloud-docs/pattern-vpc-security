---

copyright:
  years: 2024
lastupdated: "2024-07-29"

subcollection: pattern-vpc-security

keywords:

---

{{site.data.keyword.attribute-definition-list}}

## Identity and Access Security
{: #identity-and-access}

## Access and Role Access Management
{: #aram}

{{site.data.keyword.Bluemix_notm}} has a full featured native IAM that can control all aspects of admin user actions and services within an account.  It enables you to securely authenticate users for platform services and control access to resources consistently across {{site.data.keyword.Bluemix_notm}}.  Please see the following link for more information: [Access management in {{site.data.keyword.Bluemix_notm}}](/docs/account?topic=account-cloudaccess) and [How {{site.data.keyword.Bluemix_notm}} IAM works.](/docs/account?topic=account-iamoverview&interface=ui) The table below highlights some of the major IAM functions available.

| IAM Capability                                                                                                 | Function / Feature                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Resource Groups](/docs/account?topic=account-rgs&interface=ui)                               | A resource group is a way for you to organize your account resources in customizable groupings. Any account resource that is managed by using {{site.data.keyword.Bluemix_notm}}® Identity and Access Management (IAM) access control belongs to a resource group within your account. You assign resources to a resource group when you create them from the catalog.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| [Access Groups](/docs/account?topic=account-groups&interface=ui)                              | An access group can be created to organize a set of users, service IDs, and trusted profiles into a single entity that makes it easy for you to assign access. You can assign a single policy to the group instead of assigning the same access multiple times for an individual user or service ID.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [Service IDs](/docs/account?topic=account-serviceids&interface=ui)                            | A service ID identifies a service or application like how a user ID identifies a user. You can create a service ID and use it to enable an application outside of {{site.data.keyword.Bluemix_notm}} access to your {{site.data.keyword.Bluemix_notm}} services. You can assign specific access policies to the service ID that restrict permissions for using specific services, or even combine permissions for accessing different services.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| [Access Policies](/docs/account?topic=account-iamusermanpol)                                  | A policy grants a subject one or multiple roles to a set of resources so that specific actions can be taken within the context of the specified target resources.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [Roles](/docs/account?topic=account-userroles)                                                | Roles provide a certain level of access and there can be platform and service roles. Roles may have such roles as “Editor”, “Administrator”, etc. Further roles define a set of actions that can be performed on cloud resources. Platform roles control the ability to call platform APIs to do actions such as provisioning a service instance. Service roles are supported by some services and control the ability to call service APIs. {{site.data.keyword.Bluemix_notm}} supports predefined roles such as "Administrator" and "Editor", that apply across multiple services. Services can also define custom roles that apply only to that service, and users can define their own custom roles that include only the specific actions they wish to grant access to. User-defined custom roles are useful for meeting least privilege requirements."                                                                                                                                                                                                                                                                                                      |
| [Context Restrictions](/docs/account?topic=account-context-restrictions-whatis)               | Context-based restrictions give account owners and administrators the ability to define and enforce access restrictions for {{site.data.keyword.Bluemix_notm}}® resources based on a rule's criteria. The criteria include the network location of access requests, the endpoint type from where the request is sent, and sometimes the API that the request tries to access. These restrictions work with traditional IAM policies, which are based on identity, to provide an extra layer of protection.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [Multi-Factor Authentication](/docs/account?topic=account-types&interface=ui)                 | Multifactor authentication (MFA) adds an extra layer of security to your account by requiring all or specific or designated users to authenticate by using another authentication factor beyond an ID and password. MFA is also commonly known as two-factor authentication (2FA).   When MFA is enabled, a user is prompted to provide a unique identifier (such as a username or email) and a one-time password (OTP) generated by an authenticator app or a hardware token. This type of MFA is much more secure than account-based MFA because it is not limited to classic infrastructure resources and applies to all resources within the account. It also reduces the risk of a breach because of a weak password or the use of the same password across multiple accounts.                                                                                                                                                                                                                                                                                                                                                      |
| [Trusted Profiles](/docs/account?topic=account-trustedprofile-fedusers-tutorial&interface=ui) | By using trusted profiles, you can establish a flexible, secure way for federated users to access the {{site.data.keyword.Bluemix_notm}}® resources they need to do their job. All federated users that share certain attribute that are defined in your corporate user directory are mapped to a common profile and can share access to {{site.data.keyword.Bluemix_notm}} resources. This common identity makes it possible to give the members of your organization that share access requirements automatic access to resources one time, rather than having to add each user to an account and then grant them access directly or by using access groups. Trusted profiles can also be used to grant access to service IDs, compute resources, or services. Allowing a compute resource to assume a trusted profile allows you to assign access to applications running on that resource without the need for a long-term credential that then has to be managed and rotated. This greatly enhances the security of applications running in {{site.data.keyword.Bluemix_notm}}. [Using a trusted profile to call IAM-enabled services](/docs/vpc?topic=vpc-imd-trusted-profile-metadata) |
{: caption="Table 1: {{site.data.keyword.Bluemix_notm}} Identity and Access Management Capabilities"}

The diagram below provides insight on how IAM works in the {{site.data.keyword.Bluemix_notm}}.

![Illustrates the detailed framework for IAM](images/IAMframework.svg){: caption="Figure 3. Identity and access management" caption-side="bottom"}

### Options
{: #IAMOptions}

 - Multi-Factor Authentication (MFA) and complex passwords - always recommended,
 - Assigning individual-based accesses and policies - Never recommended – users should be placed into access groups or in trusted profiles with specific policie, and
 - Single Sign On (SSO) Federation - Applicable where customers already have a single sign on infrastructure or perhaps where customers want to use their established Active Directory or LDAP, etc.

### Best Practices
 {: #IAMbestpractices}

 - [Best Practices for Organizing Resources and Assigning Access](/docs/account?topic=account-account_setup),
 - Always apply a least privilege approach for all cloud accesses,
 - Never use a root account for any administration.  Always apply context restrictions for IAM access,
 - Never apply IAM capabilities to a single user.
 - Use Trusted Profiles or access groups and assign policies to the access group,
 - Always use multi-factor authentication and a complex password and rotation policy,
 - Develop thorough documentation that dictates how IAM will be used and managed in your {{site.data.keyword.Bluemix_notm}} account(s),
 - Conduct regular, periodic reviews of your account IAM settings in relation to your IAM documentation and policies. Over time settings can drift or be inadvertently changes resulting in overly permissible states, and
 - Conduct periodic reviews of IAM logs provided by [{{site.data.keyword.cloudaccesstraillong}}](/docs/activity-tracker?topic=activity-tracker-about) to look for access anomalies.  Discussed in a following section.

### Solutioning Guidance
 {: #IAMguidance}

 - [Access management in {{site.data.keyword.Bluemix_notm}}](/docs/account?topic=account-cloudaccess),
 - [How {{site.data.keyword.Bluemix_notm}} IAM works](/docs/account?topic=account-iamoverview),
 - Customers are encouraged to read all the documentation in the Managing Your Account, Resources, Access section in {{site.data.keyword.Bluemix_notm}} Docs for more insight on best IAM practices and solutioning guidance,
 - [Best Practices for Organizing Resources and Assigning Access](/docs/account?topic=account-account_setup), and
 - Use trusted profiles to assign access to compute resources rather than embedding credentials in applications.

## IAM with Single Sign-On / Identity Provider Federation
{: #IAMSSO}

{{site.data.keyword.Bluemix_notm}} IAM allows federation so that you can integrate with your external identity provider (IdP) to securely authenticate external users to your {{site.data.keyword.Bluemix_notm}}® account. By using your IdP, you can provide a way for users in your company to use single sign-on (SSO).  Please see the following link for general information: [Single Sign On](/docs/appid?topic=appid-cd-sso)

### Options
{: #SSO-options}

 - SSO - Applicable where federation with other identity providers or external directories is required, and
 - No SSO - Customers may forgo SSO if they have no federation with Identity Providers.

### Best Practices
{: #SSO-best-practices}

 - Use {{site.data.keyword.Bluemix_notm}} Trusted Profiles in conjunction with any SSO solution,
 - Ensure multi-factor authentication with the SSO solution, and
 - Enforce granular role and permission management.

### Solutioning Guidance
{: #SSO-guidance}

 - [Which is the right federation option for you?](/docs/account?topic=account-federation-option-for-you)
 - {{site.data.keyword.Bluemix_notm}} SAML Federation Guide [Enabling authentication from an external identity provider.](/docs/account?topic=account-idp-integration)
 - [Managing access for federated users by using trusted profiles](/docs/account?topic=account-trustedprofile-fedusers-tutorial&interface=ui)

## Secrets Management
{: #secrets-management}

Cloud secrets management is a way to securely store and manage API keys, certificates, user ID and password credentials and other sensitive information with automation and integration.  {{site.data.keyword.Bluemix_notm}}’s service here is known as {{site.data.keyword.secrets-manager_full_notm}} and it has several key security features such as secrets lifecycle management, logging, default encryption, IAM integration, versioning, etc.  Please see the following link for more information: [Getting started with {{site.data.keyword.secrets-manager_full_notm}}](/docs/secrets-manager?topic=secrets-manager-getting-started)

### Options:
{: #secrets-management-options}

- **{{site.data.keyword.Bluemix_notm}} {{site.data.keyword.secrets-manager_full_notm}}** - Automated and native secrets management solution that is fully integrated with IBM,
- **No Secrets Management** - Never recommended again, but this may be applicable where you have a totally private environment that is used for non-critical dev and test and the like. Secrets here could possibly be embedded into applications here, if security requirements are low and cost is a factor, and
- **3rd Party Secrets Managment Solution** - This option may be applicable in multi-cloud situation but secrets management automation with {{site.data.keyword.Bluemix_notm}} would be lost.

### Best Practices:
{: #secrets-management-best-practices}

 - {{site.data.keyword.Bluemix_notm}} is focused on enterprise workloads and these workloads should always include secrets management,
 - Cloud native secrets management that provides full Lifecyle capabilities and full cloud integration,
 - Automated creation, rotation, revocation and expiration of static secrets, and
 - Never transmit secrets via plaintext; all should transit using TLS encryption.

### Solutioning Guidance:
{: #secrets-management-best-guidance}

 - [Managing IAM access for {{site.data.keyword.secrets-manager_full_notm}}](/docs/secrets-manager?topic=secrets-manager-iam&interface=ui),
 - [Using service endpoints to privately connect to {{site.data.keyword.secrets-manager_full_notm}}](/docs/secrets-manager?topic=secrets-manager-service-connection&interface=ui),
 - [Securing your data in {{site.data.keyword.secrets-manager_full_notm}}](/docs/secrets-manager?topic=secrets-manager-mng-data&interface=ui), and
 - [Protecting {{site.data.keyword.secrets-manager_full_notm}} resources with context-based restrictions](/docs/secrets-manager?topic=secrets-manager-access-control-cbr&interface=ui)
 - {{site.data.keyword.secrets-manager_full_notm}} instances are provisioned per region to spread out workloads and limit the blast radius in case of a regional outage. {{site.data.keyword.secrets-manager_full_notm}} is a single-tenant service. CPU and memory limits are applied per {{site.data.keyword.secrets-manager_full_notm}} instance.  Those limits restrict the API request rates based on the usage pattern.  As a rule of thumb, it is recommended to keep the rate below 20 req/s.  Additionally, limit the number of unique clients that make requests to a single {{site.data.keyword.secrets-manager_full_notm}} instance, and
 - Another best practice is the use of one of {{site.data.keyword.Bluemix_notm}}’s key management systems {{site.data.keyword.keymanagementservicelong_notm}} or Hyper Protect Crypto Services {{site.data.keyword.hsplatform}} to encrypt secrets. Guidance on how you should organize your secrets can be found here: [Organizing Your Secrets.](/docs/secrets-manager?topic=secrets-manager-secret-groups&interface=ui)

Note that {{site.data.keyword.secrets-manager_full_notm}} is a high available platform which has built-in resiliency and backups in each region. Customers have specific responsibilities around secrets management.  More details can be found here: [Security Design](/docs/vpc-resiliency?topic=vpc-resiliency-security-design). Ensure high availability of secrets management platform. Provisions for high availability and encrypted backups should be used.

## Bastion Host and Privilege Identity and Access Management (PAM)
{: #bastion-host}

A bastion host is a server used to manage access to an internal or private network from an external network - sometimes called a jump box or jump server. Because bastion hosts often sit in the Internet edge, they typically run a minimum number of services to reduce their attack surface.  They are also commonly used to proxy and log communications, such as SSH sessions.  Privilege Access Management (PAM) software can be loaded on top of the bastion host to provide more security functionality, granular access control and logging beyond terminal SSH access.

### Options
{: #bastion-host-options}

 - **Virtual Server Instance for Bastion Host** - There are no options for an underlying platform for a Bastion Host. Bastion Hosts must be created on a virtual server instances (VSI) within the confines of a Virtual Private Cloud (VPC),
 - **Bastion Host, No Privilege Access Management (PAM) Software** - Not recommended in that highly granular access, approval workflows and detailed logging may be needed,
 - **Bastion with PAM software** - Various 3rd party solutions are in the marketplace, and this is always recommended. Note that IBM Cyber Security Services (CSS) does have a PAM solution here known as **Verify**. More information on **Verify** can be found here: IBM CSS [Verify](https://www.ibm.com/verify?utm_content=SRCWW&p1=Search&p4=43700074603995210&p5=e&gad_source=1&gclid=Cj0KCQjwwMqvBhCtARIsAIXsZpa48PUASWhrDD-SGr-h-wY_b1IyThYC4DzKpHucYM_JWNdkzpHcjoYaAkZ_EALw_wcB&gclsrc=aw.ds){: external}

### Best Practices
{: #bastion-host-best-practices}

 - Bastion hosts should always be accompanied with PAM software.  A least privilege approach should always be applied to permissions on the Bastion Host and the PAM software,
 - Detailed logs should be enabled, and regular reviews of logs should be undertaken to look for anomalies, and
 - Logs from the Bastion Host and the PAM software should be correlated with other logs to get inferences of threats. Typically, this correlation comes in the form of a Security Event and Information Management (SIEM) Platform.

### Solutioning Guidance
{: #bastion-host-guidance}

 - Securely access remote instances with a bastion host. [Access to bastion host](/docs/solution-tutorials?topic=solution-tutorials-vpc-secure-management-bastion-server)

## Identity Governance
{: #IAMgovernance}

 Identity governance is a policy or programmatic approach to identity management.  IBM Cloud IAM was previously discussed and all of the capabilities here support identity governance.  But surrounding or on top of these should governance processes and procedures and many of these could be manual processes through documentation or automation that would be out of scope for cloud, e.g., existing approval workflow systems, etc.



