# AZURE A LEARNING GUIDE


**What is Azure?**


Microsoft Azure is an ever-expanding set of cloud services to help your organization meet your business challenges. It’s the freedom to build, manage, and deploy applications on a massive, global network using your favorite tools and frameworks.
Azure is Microsoft's cloud solution. A cloud is essentially a collection of host data centers that you don't have to directly manage. You can request services from that cloud Cost, Global scale, performance, security, speed, productivity, Reliability.

Microsoft Azure is a cloud computing platform that offers services and products to help users build, run, and manage applications: 


**Services and products**
Azure offers over 200 products and services, including analytics, storage, networking, and virtual computing. 


**Solutions**
Azure offers solutions for various industries, such as retail and manufacturing. 


**Benefits**
Azure offers benefits such as enhanced security, compliance, backup and recovery capabilities, and simplified management. 

**Flexibility**
Azure offers flexibility to choose preferred technology, tools, and languages. 


**Access**
Azure offers access to industry-leading AI services, cloud infrastructure, and an intelligent data platform. 

**Access and management**
Azure provides an online portal that allows users to access and manage cloud services and resources. 


**Capabilities**
Azure provides capabilities that are usually not included within other cloud platforms, including software as a service (SaaS), platform as a service (PaaS), and infrastructure as a service (IaaS)

===========================================================================================

## Azure is Responsible for:


In an Azure cloud environment, the responsibilities are divided between Microsoft (Azure) and the customer, following a shared responsibility model. Based on your statement, Azure is responsible for the following aspects:


**1. Availability of the Platform (Datacenter, Connectivity, Server, Power, Cooling):**


Azure is responsible for ensuring that the underlying infrastructure, including the physical data centers, power supply, network connectivity, servers, and cooling systems, are available and maintained. This includes ensuring the physical hardware and its supporting systems (such as power and cooling) are operational and resilient.


**2.	Data Availability:**


Azure is responsible for the availability of services and platforms, ensuring the infrastructure is designed for high availability, redundancy, and disaster recovery. However, customers must implement their own strategies for data availability, such as backups, replication, and failover.


**3.	Maintenance of the Platform (Datacenter, Connectivity, Server, Storage):**


Azure is responsible for the regular maintenance of the underlying platform, which includes updating and patching hardware, software, and infrastructure. This also includes maintaining servers, storage, network, and ensuring that the physical environment remains up-to-date and operational.


**4.	Physical Security:**


Azure ensures the physical security of data centres, including access control, surveillance, and protection from physical threats. This involves securing the hardware, buildings, and network connections from unauthorized physical access and ensuring that the environment is resilient to physical attacks or failures.


**5.	Availability of the Service (VM, Storage, Network):**


Azure ensures the availability of the services it provides, such as virtual machines (VMs), storage, and networking. This means managing the infrastructure to ensure it is available for the customer, including handling the orchestration, scaling, and maintenance of these services.



**Shared Responsibility Model:**


*Customer's Responsibility:*
The customer is responsible for things like configuring services correctly, managing the applications they deploy, maintaining data security, and setting up proper access controls.


*Azure's Responsibility:* 
Azure handles the infrastructure level, ensuring the platform and its services (network, compute, storage, etc.) are operational and secure.

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image1.png)



===========================================================================================
# Governance


* Governance in Azure is one aspect of Azure Management
* Azure governance is a framework that helps organizations manage and control their Azure resources, policies, and access.
*Governance provides mechanisms and processes to maintain control over your applications and resources in Azure. 
* It involves planning your initiatives and setting strategic priorities. Governance in Azure is primarily implemented with two services. 
* Azure Policy allows you to create, assign, and manage policy definitions to enforce rules for your resources. This feature keeps those resources in compliance with your corporate standards. 
* Azure Cost Management allows you to track cloud usage and expenditures for your Azure resources and other cloud providers.

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image2.png)


===========================================================================================
# Azure Subscription?

An Azure subscription is a logical container that groups resources together for billing and management in Microsoft Azure and is linked to an Azure account.

An Azure Subscription is a key component in Microsoft Azure's cloud service platform. It is a logical container that is used to manage resources and services in the Azure cloud. Here is a more detailed breakdown based on the points you have mentioned:


**Logical Unit of Azure Services:**

An Azure subscription acts as a container that holds various Azure resources such as virtual machines (VMs), databases, networking resources, and storage accounts. Each subscription is linked to an Azure account, and the resources within that subscription are governed and managed by that account.


**Billing:** 

Azure services are billed on a per-subscription basis. This means that all resources deployed under a specific subscription are grouped together for billing purposes. The subscription defines the scope of the costs, and the billing can be tracked based on usage under that subscription.


**Access to Azure Services:** 

An Azure subscription gives users access to Azure’s cloud services and the management portal (Azure Portal). This portal allows users to manage and deploy various services, monitor usage, and control resource allocation.


**Container for Services:** 

An Azure subscription is often described as a billing container for the services that are deployed within it. This includes IaaS (Infrastructure as a Service), PaaS (Platform as a Service), SaaS (Software as a Service) offerings, and other cloud-based resources such as virtual machines, web applications, and storage accounts.


**Relationship with Azure Active Directory (Azure AD):** 

Azure subscriptions have a trusted relationship with Azure Active Directory (Azure AD). Azure AD is a cloud-based identity and access management service, which provides authentication and authorization for users, services, and devices. Users can sign in to the Azure Portal using their Azure AD credentials, and their roles within the subscription are defined by Azure AD.


**Role-based Access Control (RBAC):** 

Within an Azure subscription, Azure AD is used to manage user roles and access permissions through Role-Based Access Control (RBAC). This allows administrators to control who can access the resources within the subscription and what actions they can perform.


**Resource Organization:** 
Azure subscriptions can be organized into resource groups, and each resource group can contain a set of resources that share the same lifecycle. Administrators can create multiple subscriptions for different purposes (e.g., development, testing, production) to separate concerns or manage budgets and access levels effectively.




**1. Azure Enterprise Agreement (EA)**

An Azure Enterprise Agreement is a licensing model that allows large organizations to purchase and manage Azure services at scale. It provides benefits such as:
* Centralized Billing: All subscriptions under the Enterprise Agreement are billed together, offering centralized management of costs.
* Cost Management and Reporting: Administrators can track and report on usage and spending across all subscriptions linked to the enterprise.
* Discounted Pricing: Organizations that commit to a certain volume of Azure usage can benefit from discounted pricing.



**2. Azure Subscription Types**

Azure supports various types of subscriptions, each serving a different purpose depending on the size, requirements, and billing preferences of the organization:
* Pay-As-You-Go Subscription: Ideal for smaller businesses or testing environments where users pay only for the resources they use.
* Enterprise Agreement (EA) Subscription: Designed for large organizations that need more advanced billing and management features.
* Microsoft Customer Agreement: For customers who want a flexible purchasing model without the need for an Enterprise Agreement.
* Cloud Solution Provider (CSP) Subscription: Typically used by Microsoft partners to resell Azure services to customers.


**3. Management Groups**

To organize and manage multiple subscriptions, Azure offers Management Groups. These are containers that allow you to group multiple subscriptions under a common hierarchy. This helps you apply governance and policies at a higher level rather than at the subscription level.
* Hierarchical Structure: You can organize subscriptions into multiple management groups to create a structure based on business units, regions, or any other criteria that suit your organization’s needs.
* Policy Enforcement: Management groups help enforce governance policies, security controls, and compliance requirements across all subscriptions within the group.


**4. Billing and Cost Management**

Managing costs is one of the most critical aspects of Azure Enterprise and Subscription Management. Azure provides several tools to help monitor and control costs:
* Cost Management + Billing: This tool helps you track and manage Azure costs. It provides a detailed breakdown of usage, charges, and forecasted costs, and helps with budgeting and cost optimization.
* Budgets and Alerts: Azure allows you to set budgets for each subscription or resource group and configure alerts that notify you when you approach or exceed the defined budget.
* Azure Reservations: For long-term usage of resources like virtual machines and SQL databases, you can reserve capacity and receive discounted pricing.


**5. Azure Active Directory (Azure AD) Integration**

AD plays a central role in Enterprise and Subscription Management by controlling access to resources across multiple subscriptions. Azure AD provides:
* Single Sign-On (SSO): Users can sign in to all Azure services using their Azure AD credentials.
* User and Group Management: Administrators can manage users and groups in Azure AD, assigning roles and permissions across multiple subscriptions using RBAC.
* External Identities: Organizations can also configure access for external users (partners, vendors) via Azure AD B2B (Business-to-Business) collaboration.


===========================================================================================

# What is an Azure account?
In Microsoft Azure, an Azure account is the basic identity used to access and manage Azure services. The roles of Account Administrator, Service Administrator, and Co-Administrator pertain to different levels of management and permissions within an Azure subscription. Here is an overview of each:


**Azure Account**
An Azure account refers to the credentials used to access Microsoft Azure services. This account is typically tied to an email address, and it allows the user to create and manage Azure resources, such as virtual machines, databases, and storage. An Azure account can belong to an individual or an organization. It may also be associated with a Microsoft account or work or school account depending on the setup.


**Account Administrator**

The Account Administrator is the highest-level role associated with an Azure subscription. The key responsibilities of an Account Administrator include:

* **Subscription Ownership:** The Account Administrator has full access to manage the subscription, including the ability to assign roles and manage billing.

* **Management of Services:** While this role can manage Azure resources, its primary function is to manage the overall subscription settings and billing.

* **Account Control** The Account Administrator can add and remove other users and assign them roles, including the Service Administrator and Co-Administrator roles.
  
**Note: There is only one Account Administrator per Azure subscription.**


**Service Administrator**

The Service Administrator is a role with specific permissions within the Azure subscription. This role is usually tied to the management of Azure services but has some limitations compared to the Account Administrator.
Key responsibilities:

* **Manage Services and Resources:** 

The Service Administrator can manage resources and services (e.g., creating virtual machines, setting up networking, etc.).

* **Role Restrictions:** 

This role does not have full control over the subscription settings (like billing or transferring the subscription) and cannot manage other administrators (e.g., adding users or changing their roles).

* **Management of Azure Subscriptions:** 

In most cases, this role is associated with managing the actual Azure services and resources but with fewer permissions than the Account Administrator.
An Azure subscription can have only one Service Administrator, and typically, this role is set to the first person who creates the subscription.


**Co-Administrator**

The Co-Administrator is a role that provides the ability to manage resources and services, similar to the Service Administrator, but with additional flexibility. Co-Administrators can perform most administrative tasks except for billing and subscription management.
Key responsibilities:

* **Manage Resources:** Co-Administrators have full access to Azure resources, like creating and configuring virtual machines, managing storage, etc.

* **User Management:** A Co-Administrator can add or remove users and assign roles (except for changing the Account Administrator role).

* **Similar to Service Administrator:**

 In terms of permissions for managing Azure services, Co-Administrators and Service Administrators have similar access.
A subscription can have multiple Co-Administrators, and they can manage resources without being restricted by the billing functions of the Account Administrator.



===========================================================================================

# Azure Resource Group

An Azure resource group is a logical container that organizes related resources for an Azure solution:

**Purpose**

Resource groups allow you to manage resources as a single entity, based on security and lifecycle. For example, you can create, update, or delete resources as a group if they share a similar lifecycle

**Resources**

Resource groups can include VMs, storage accounts, virtual networks, web apps, databases, and database servers

* Associating resource groups and their resources with an Azure subscription 
* Using tags for metadata, documentation, automation, cost, and billing 
* Creating and managing roles and assigning them permissions at the resource group or subscription level

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image3.png)



===========================================================================================
# Role Base Access Control

RBAC provides fine-grained access management to your resources in Azure 
Role-based access control (RBAC) in Azure is a system that manages access to Azure resources by granting users only the access they need to perform their jobs. RBAC is built on Azure Resource Manager and helps to:

**Improve security**

By limiting access to only what users need, RBAC reduces the risk of unauthorized access, data breaches, and insider threats.

**Segregate duties**

RBAC allows you to assign different levels of access to different users based on their roles and responsibilities

**How Azure RBAC works**

The way you control access to resources using Azure RBAC is to assign Azure roles. This is a key concept to understand – it's how permissions are enforced. A role assignment consists of three elements: security principal, role definition, and scope.



**Security principal**
A security principal is an object that represents a user, group, service principal, or managed identity that is requesting access to Azure resources. You can assign a role to any of these security principals.


Role-based access control can be used to assign permissions to:

 
![alt text](https://github.com/acmarpu/images/Azure/blob/main/image4.png)




**Scope**
Scope is the set of resources that the access applies to. When you assign a role, you can further limit the actions allowed by defining a scope

What level these permissions will apply 

The scope of role assignment can be: 
- Subscription
- Resource group
- Single resource
- Management group level

 ![alt text](https://github.com/acmarpu/images/Azure/blob/main/image5.png)



**Here are some examples of what you can do with RBAC:**
* Allow one user to manage virtual machines in a subscription and another user to manage virtual networks
* Allow a DBA group to manage SQL databases in a subscription
* Allow a user to manage all resources in a resource group, such as virtual machines, websites, and subnets
* Allow an application to access all resources in a resource group

**Owner** has full access to all resources including the right to delegate access to other users.

**Contributor** has full access to all resources but cannot delegate control to other users.

**Resource Policy Contributor** can create and manage policies in the directory on the resources.

**Reader** can view existing Azure resources

* Provide exact permission to user or group
* Grant access by assigning the appropriate RBAC role
* Can use built-in role or create custom role 
* We ca grant to access at subscription level 
* We can give the access at resource group
* We can grant the access for specific site 


===========================================================================================

# View Activity logs for RBAC changes 

The Azure Activity log provides visibility into subscription-level events that have occurred in Azure
You can determine what operations were taken on the resources in your subscription 


The Activity log has eight categories

**Administrative:** this contains all the records for create, update, delete, and action operations performed. Here we will see events related to RBAC

**Service Health:** This contains any health-related events that affect Azure.

**Resource health:** This contains that record of any resource health events that have occurred to your deployed resources in Azure 

**Alert:** This contains all the alerts that have been activated 

**Auto scale:** This includes all the record of events related to Auto scale.

**Recommendation:** this contains recommendation events from azure advisor 

**Security:** This contains the record of any alerts generated by Azure security center

**Policy:** This contains records of all effect action operations performed by Azure policy 

===========================================================================================

# What is a management group? 

An Azure Management Group is a container used to organize and manage multiple Azure subscriptions. It allows you to apply governance, policies, and access controls at a higher level than individual subscriptions, providing a way to manage multiple subscriptions efficiently.

Key features of Azure Management Groups:

**Hierarchical Structure:**

Azure Management Groups enable you to create a hierarchy of management groups, allowing you to structure your Azure environment in a way that reflects your organization’s needs. You can have management groups within management groups, creating a tree-like structure.

**Inheritance of Policies:** 

Policies, role-based access control (RBAC), and other governance settings can be applied at the management group level. These settings are inherited by all subscriptions under that management group, ensuring consistency and compliance across multiple subscriptions.

**Simplified Management:**

 By using management groups, you can streamline administrative tasks. For example, rather than applying settings to each subscription individually, you can apply them once at the management group level and have them cascade to the subscriptions.

**Access Control:**

You can apply Azure RBAC to manage who has access to the management group, ensuring that the right individuals or groups have the necessary permissions across multiple subscriptions.

**Scalability:**
 Azure Management Groups are scalable, allowing organizations to manage tens, hundreds, or even thousands of subscriptions in a structured and efficient way

 ![alt text](https://github.com/acmarpu/images/Azure/blob/main/image6.png)



===========================================================================================


# Azure AD / Microsoft Entra ID
# **Azure Active Directory is now Microsoft Entra ID**

Active Directory (AD) and Azure Active Directory (AAD) are both identity management solutions from Microsoft, but they serve different purposes.

**Windows Active Directory** is a directory service developed by Microsoft for Windows domain networks. It is included in most Windows Server operating systems as a set of processes and services. Initially, Active Directory was used only for centralized domain management. 

**Microsoft Entra ID** is an Identity and Access Management system. It is used to grant access to your employees to specific products and services in your network. For example: Salesforce.com, twitter etc. Azure AD has some in-built support for applications in its gallery which can be added directly. 

**Identity:** Something that can be authenticated before permitting access to the desired resources. 

**Account:** they the data associated with the identities that defines your permission 

**Azure Tenant:** 
* An Azure Tenant is an instance of Azure Active Directory (Azure AD) that is used to manage identities, access, and resources in Microsoft Azure. It acts as a dedicated, isolated environment for an organization and is tied to a specific domain
* The Azure Tenant is logically isolated from other tenants, meaning it cannot share user identities or resources with other tenants unless specific configurations (like Azure AD B2B or Azure AD B2C) are used.
* A single Azure Tenant can contain multiple subscriptions

**Custom domain:** 
An Azure Custom Domain refers to the ability to configure and associate your own domain name (such as example.com) with Azure services, instead of using the default domain names provided by Azure (e.g., yourtenant.onmicrosoft.com). This is particularly useful for organizations that want to use their own branding or have a consistent domain for resources like applications, websites, or email systems.

**Azure Active Directory (Azure AD) Custom Domain:**
By default, when you create a new Azure AD tenant, it is assigned a default domain name like yourtenant.onmicrosoft.com. However, for branding and identity consistency, you can add your own custom domain (e.g., example.com) to Azure AD.

**Azure DNS:**
Azure DNS enables you to manage your domain’s DNS records. You can configure DNS zones in Azure to manage the mappings of your custom domain to various Azure resources (like virtual machines, app services, etc.).


**AD features:** 
Active Directory (AD) features are essential for managing users, devices, and resources within an organization. Below is an explanation of the AD features you mentioned:

**1)	Application management** 
Active Directory enables centralized management of applications across an organization. It allows administrators to assign, configure, and manage access to applications based on user roles and policies. This integration simplifies application deployment and access control

**2)	B2B (Business-to-Business), B2C (Business-to-Consumer) Management**

*B2B:* Active Directory supports external partner and supplier access to corporate resources through Azure AD B2B. This allows businesses to securely share applications and resources with external partners while maintaining control over access.

*B2C:* Azure AD B2C allows organizations to create customer-facing applications with secure authentication. It supports social logins (like Facebook, Google) and custom identity providers, allowing businesses to manage customer identity securely.

**3)	Conditional access** 
Conditional Access in Azure AD allows organizations to enforce access policies based on conditions such as user location, device state, and user role. It helps ensure that only authorized users, on secure devices, can access sensitive resources. It can block or restrict access based on risk levels or user behavior.

**4)	Device management** 
Azure AD provides device management features, allowing organizations to register and manage devices that access corporate resources. Integration with Microsoft Intune provides advanced capabilities for configuring, monitoring, and securing devices, including mobile devices, laptops, and desktops.

**5)	Identity management** 
Identity management in Active Directory involves managing user identities and their associated permissions. AD allows administrators to create, update, and delete user accounts, as well as manage their access to applications, devices, and other resources. It is also responsible for managing authentication and authorization across services.

**6)	Domain services** 
Active Directory Domain Services (AD DS) is the core feature of AD that allows administrators to create and manage domains, users, computers, and organizational units (OUs). It enables centralized authentication and authorization for networked resources and is essential for maintaining a secure IT infrastructure.

**7)	Privileged identity management** 
Privileged Identity Management is a security feature that helps organizations manage, control, and monitor access to critical resources and administrative privileges. PIM allows for just-in-time (JIT) elevation of privileges, ensuring that users only have administrative rights when necessary and that all elevated access is logged and audited.

* Provide just-in-time privileged access to Azure AD and Azure resources 
* Assign time-bound access to resources using start and end dates 
* Require approval to activate privileged roles 
* Enforce multi-factor authentication to activate any role 
* Use justification to understand why users activate 
* Get notifications when privileged roles are activated 
* Conduct access reviews to ensure users still need roles 
* Download audit history for internal or external audit 
* Prevents removal of the last active Global Administrator role assignment 


**8)	Reporting and monitoring**
Active Directory provides reporting and monitoring tools that allow administrators to track user activity, access logs, security events, and system performance.

**9)	End-user self-service**
End-user self-service features enable users to manage their own accounts, reset passwords, and update profile information without requiring IT assistance. This reduces the workload on administrators and enhances user productivity.


===========================================================================================

# MFA (Multi-Factor Authentication) on Azure 

Multi-Factor Authentication (MFA) on Azure is a key security feature that helps protect your organization’s data and resources by requiring multiple forms of authentication. 

*Multi-Factor Authentication (MFA)* requires users to verify their identity through at least two different factors from the following categories:

*   Something you know: This is typically a password or PIN.
*	Something you have: This could be a mobile device, smartcard, or security token.
*	Something you are: This refers to biometrics, such as fingerprint or facial recognition.


Azure Multi-Factor Authentication adds an important layer of security, requiring users to authenticate via two or more methods.


**Preferred Authentication Methods:**

*Phone call:* The system calls the user’s phone and asks them to confirm their identity by pressing a number.

*Text message (SMS):* A one-time passcode (OTP) is sent via SMS to the user's phone.

*Mobile app notification:* The user receives a push notification in the Microsoft Authenticator app, which they approve to authenticate.

*Authenticator app verification code:* A time-sensitive passcode generated by the Authenticator app for the user to enter.


**Microsoft Intune Overview**

Microsoft Intune is a cloud-based enterprise mobility management (EMM) solution that helps organizations securely manage the mobile devices, applications, and data used by employees. Intune plays a vital role in securing and managing the increasingly diverse set of devices (e.g., smartphones, tablets, laptops) that employees use to access corporate resources, including email, files, and applications.


**Azure AD Connect**

It is used to integrate the on-premise directories (Active Directories) with Azure Active Directory which provides a common identity for accessing both cloud and on-premise resources. 

There are various features of Azure AD Connect: 
* Password Hash Synchronization: Sign-in method that synchronizes a hashed user on-premised AD password with Azure AD. 
* Pass-through authentication: Sign-in method that provides access to users to use the same password on-premise and on the cloud. 
* Synchronization: Responsible for creating users, groups, and other objects and also validate if the identity information of your on-premise users and groups matches with the cloud. 
* Health Monitoring: A central place to view the activity and also provide monitoring. 


===========================================================================================

# Managed Identity:
* Managed Identity is a feature in Azure that provides an identity for applications, services, or resources that run within the Azure environment. 
* This identity is managed by Azure Active Directory (Azure AD), simplifying the management of credentials used by services and applications to authenticate to other Azure resources securely. 
* Managed identities are designed to eliminate the need for developers to handle credentials manually, reducing the complexity and enhancing security.
*Use cases:* Managed identities are typically used when you have a resource (such as an Azure Virtual Machine or Azure Function) that needs to authenticate and access other Azure resources securely. Instead of managing credentials (e.g., usernames and passwords) manually, you can use a managed identity.

*How it works:* 

When you enable a managed identity for an Azure resource, Azure creates a service principal in the Azure AD tenant that represents that resource. This service principal is used to authenticate the resource with Azure AD, and it has specific permissions associated with it.

 
*There are two types of managed identities:* 

**System-assigned** Some Azure services allow you to enable a managed identity directly on a service instance. When you enable a system-assigned managed identity an identity is created in Azure AD that is tied to the lifecycle of that service instance. So, when the resource is deleted, Azure automatically deletes the identity for you. By design, only that Azure resource can use this identity to request tokens from Azure AD. 

**User-assigned** You may also create a managed identity as a standalone Azure resource. You can create a user-assigned managed identity and assign it to one or more instances of an Azure service. In the case of user-assigned managed identities, the identity is managed separately from the resources that use it. 



**Service Principal in Azure**

A service principal in Azure is a security identity that is created to allow an application, service, or automation tool to access resources within a specific Azure Active Directory (Azure AD) tenant. It serves to authenticate and authorize services or applications to interact with Azure resources and other Microsoft services in a controlled and secure manner.
Key Features of Service Principals:

**Identity for Applications/Services:**

* A service principal acts as an identity for non-human entities such as applications, automated processes, and scripts. This identity is used to authenticate and authorize these services to interact with Azure resources securely.
* Unlike user identities, a service principal is designed for service-to-service authentication, enabling applications or services to authenticate without relying on human intervention or user credentials.
Used Across Microsoft Services:
* While service principals are commonly used within Azure to access Azure resources, they are not limited to Azure. Service principals can be used to authenticate and interact with other Microsoft services, such as Microsoft Graph, Office 365, and Power BI.
* Service principals can also be used in integrations or automation tools (e.g., CI/CD pipelines) to interact programmatically with services.


**Used Across Microsoft Services:**

* While service principals are commonly used within Azure to access Azure resources, they are not limited to Azure. Service principals can be used to authenticate and interact with other Microsoft services, such as Microsoft Graph, Office 365, and Power BI.
* Service principals can also be used in integrations or automation tools (e.g., CI/CD pipelines) to interact programmatically with services.


