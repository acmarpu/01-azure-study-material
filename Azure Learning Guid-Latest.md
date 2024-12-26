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

![alt text](images/image1.png)


# Governance


* Governance in Azure is one aspect of Azure Management
* Azure governance is a framework that helps organizations manage and control their Azure resources, policies, and access.
*Governance provides mechanisms and processes to maintain control over your applications and resources in Azure. 
* It involves planning your initiatives and setting strategic priorities. Governance in Azure is primarily implemented with two services. 
* Azure Policy allows you to create, assign, and manage policy definitions to enforce rules for your resources. This feature keeps those resources in compliance with your corporate standards. 
* Azure Cost Management allows you to track cloud usage and expenditures for your Azure resources and other cloud providers.
![alt text](images/image2.png)



# Azure Subscription?
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

A subscription is a logical unit of Azure services that is linked to an Azure account. 


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




