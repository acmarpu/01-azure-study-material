# Azure Compute

# Availability set
* An availability set is a logical grouping of VMs that allows Azure to understand how your application is built to provide redundancy and availability. 
* It is recommended that two or more VMs are created within an availability set to provide for a highly available application and to meet the 99.95% Azure SLA. 
* When a single VM is used with Azure Premium Storage, the Azure SLA applies for unplanned maintenance events. 
* Consist of Fault domain and update domain
* Consist of VM which are running the same application 
* Distribute the VMs which are in availability set to different fault domains and updates domains 

* **Fault domain:** Set of physical servers connected to same power source and network source
![alt text](https://github.com/acmarpu/images/blob/main/image7.png)
* **Update domain:** set of physical servers running win2012 Hyper-V where MS will do patch management or firmware upgradations at once 
![alt text](https://github.com/acmarpu/images/Azure/blob/main/image8.png)

===========================================================================================

# Availability Zone
* an Availability Zone (AZ) is a physically separate data center within an Azure region, designed to provide high availability and resiliency for applications and services. Each Availability Zone is equipped with its own independent power supply, network infrastructure, and cooling systems, ensuring that they can continue to function even if one zone experiences a failure (e.g., power outage, hardware failure).

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image9.png)
===========================================================================================

# Auto scaling(VMSS)
Auto scaling is the process of dynamically allocating resources to match performance requirements. 
As the volume of work grows, an application may need additional resources to maintain the desired performance levels and satisfy service-level agreements (SLAs). As demand slackens and the additional resources are no longer needed, they can be de-allocated to minimize costs. 

* **Limitations**

* SKUs are not mutable. You may not change the SKU of an existing resource.
A Load Balancer rule cannot span two virtual networks. Frontends and their related backend instances must be located in the same virtual network.

Load Balancer frontends are not accessible across global virtual network peering

* **a) Vertical scaling,** also called scaling up and down, means changing the capacity of a resource. For example, you could move an application to a larger VM size. Vertical scaling often requires making the system temporarily unavailable while it is being redeployed. Therefore, it's less common to automate vertical scaling.

* **b) Horizontal scaling,** also called scaling out and in, means adding or removing instances of a resource. The application continues running without interruption as new resources are provisioned. When the provisioning process is complete, the solution is deployed on these additional resources. If demand drops, the additional resources can be shut down cleanly and deallocated.

===========================================================================================



# Virtual Applications

* Azure network virtual appliance is used in the Azure application to enhance high availability. It is used as an advanced level of control over traffic flows, such as when building a demilitarized zone (DMZ) in the cloud.
Many virtual appliances are available in the azure marketplace

**license can be based on**
*   Bring your own license*
*   Hourly billing*

* Essentially a VM pre-configured software and configuration to perform a certain set of functionalities
Common examples include firewall and load balancer

===========================================================================================

# Network Security Appliances

Network security appliances are integral to maintaining the safety, confidentiality, and availability of your IT infrastructure. These appliances, which include both Microsoft and third-party products, offer comprehensive security and protection for various aspects of your network. Here’s an overview of the key features and offerings:

* **Featuring:**
* security and protection
* Infrastructure security 
* Web application 
**Third-party security appliances available through the marketplace** 
* Barracuda
* Palo alto 
* Sophos
* And more
**Pricing will vary** 
* Most have try before you buy
* cale as needed 
**Creates a VM**
* Sizing options availability will vary


===========================================================================================

# Azure Networking

Azure Networking is a set of cloud-based services and technologies offered by Microsoft Azure that enables you to connect, secure, and manage resources in a networked environment. Azure Networking helps businesses build scalable, high-performance, and secure networking solutions in the cloud. It provides a suite of tools for virtual networking, load balancing, DNS, security, and hybrid connectivity, allowing seamless communication and integration between different resources and environments (cloud, on-premises, or hybrid).

**Use Cases for Azure Networking:**

* **Hybrid Cloud Networking:** Connect on-premises datacentres to Azure using VPN, ExpressRoute, and VNet Peering.
* **High-Availability Applications:** Use Azure Load Balancer, Application Gateway, and Traffic Manager to ensure high availability and optimal performance.
* **Secure Network Architecture:** Build isolated environments using Network Security Groups (NSGs), Azure Firewall, and Private Link.
* **Global Applications:** Use Azure CDN, Traffic Manager, and Application Gateway to deliver content and services globally.


**Ingress Egress**
* Data in bound to Azure 
* There is no charge for ingress 

**Egress**
* Data outbound from Azure, there are charge for egress (unless using an unmetered express route connection) from azure datacenter.

**IPV4 and IPV6**

* IPv4 is the most used IP protocol. In Azure, virtual networks support IPv4 by default for VM communication.
* IPv6 support is gradually expanding. Azure now allows the configuration of IPv6 on virtual networks and enables dual-stack (IPv4 and IPv6) configurations for communication.
* TCP, UDP, and ICMP
* TCP (Transmission Control Protocol): Ensures reliable communication by establishing a connection before data is transmitted. It is widely used for applications requiring guaranteed data delivery (e.g., HTTP, FTP, SSH).
* UDP (User Datagram Protocol): A connectionless protocol used where speed is more critical than reliability (e.g., video streaming, VoIP).
* ICMP (Internet Control Message Protocol): Primarily used for diagnostic purposes, such as pinging hosts to check network availability or error messages like "Destination Unreachable".


**Private IP vs. Public IP:**

* Private IP addresses are used within a Virtual Network (VNet) and cannot be used directly for internet-facing services.
* Public IP addresses are internet-routable and are required to offer services to the internet.
Azure Public IP Address:
* Public IPs in Azure can be either static or dynamic.
* These IP addresses are tied to the region in which they are created and cannot be moved between regions.
* Azure Public IP Addresses are managed as Azure resources.
* DNS Name: Each public IP can be assigned a DNS name in the format:
<name>.<region>.cloudapp.azure.com

**Impact of VM Operations:**

* **Stop:** When a VM is stopped, the public IP is released, and the NAT (Network Address Translation) is deleted. The temporary disk is permanently deleted.

* **Start:** When the VM is started again, Azure will assign a Dynamic IP address. A temporary disk will be attached again.

* **Reboot:** The VM's guest OS will restart, but the VM will stay on the same physical host and retain the same public IP and temporary disk.

* **Delete:** Deleting the VM will permanently delete the VM, its disks, and associated public/private IP addresses, including the temporary disk.


**Dynamic vs. Static Public IP:**

*Dynamic IP:*

* Assigned when the service (like a VM) is started.
* Released when the VM is stopped or deleted.
* Generally used for cases where a stable IP is not essential.

*Static IP:*

* Assigned at the time of creation and remains even if the VM is powered off.
* Useful for services where you need to ensure the IP address remains constant (e.g., DNS records, SSL certificates, firewall rules).
* Allows the IP address to be moved across different regions or resources.


**CIDR**
* Class less Inter – Domain Routing 
* When configuring a VNet and its subnets, you use CIDR notation to specify IP ranges. For example, 10.0.0.0/16 defines an address range with 65,536 available IP addresses.
* Subnets can be smaller ranges, such as 10.0.1.0/24, allowing up to 256 IP addresses in that subnet.
* CIDR notation is a compact representation of an IP address and its associated routing prefix.
* The notation is constructed from an IP address, a slash (“/”) character and a decimal number. The number is the count of leading 1 bit in the routing mask traditionally called the network mask 

**Network Interface Card (NIC)**
* NIC is a critical component in virtual machine (VM) networking in Azure, as it enables communication between the VM and other resources within a network, both inside and outside the Azure environment. Here are the key points about NICs in Azure: 

**Azure DNS**
* Azure DNS is a scalable, reliable, and secure Domain Name System (DNS) hosting service provided by Microsoft Azure. 
* It allows organizations to manage their DNS records and domains with the same tools, APIs, and credentials that they use for other Azure services.
* Azure DNS benefits from Microsoft’s global infrastructure, which ensures high availability, redundancy, and fast name resolution
* Azure DNS supports the following common DNS record types:

* **A:** Maps a domain to an IPv4 address.*
* **AAAA:** Maps a domain to an IPv6 address.*
* **CNAME:** Alias for a domain name (e.g., www pointing to example.com).*
* **MX:** Mail Exchange records for routing email.*
* **NS:** Nameserver records that specify authoritative DNS servers.*
* **PTR:** Pointer records used for reverse DNS lookups.*
* **SOA:** Start of Authority record indicating authoritative DNS servers for the domain.*
* **SRV:** Service records for identifying services (e.g., for SIP or LDAP).*
* **TXT:** Text records for adding arbitrary information (often for domain validation).*


**Private DNS Zones:**
* Azure DNS also supports Private DNS Zones, which are designed for private IP address management within a virtual network (VNet). These zones allow for DNS resolution to occur within an Azure Virtual Network (VNet) without exposing those records to the internet.

* **Registration VNet:** A private zone can have one registration VNet, where records are published. The registration VNet is responsible for creating and updating DNS records in the private zone.
* **Resolution VNets:** Private zones can have up to 10 resolution VNets. These VNets resolve DNS records from the private zone, meaning resources in these VNets can access the private DNS records.

* Azure DNS can be part of a hybrid cloud solution where on-premises networks and Azure VNets work together. Azure DNS allows you to set up DNS resolution rules that ensure services across hybrid environments can communicate effectively.
* For enterprises already using Azure Active Directory, Azure Networking, and other Azure services, Azure DNS offers a seamless experience to manage everything in one place, providing unified management and billing.
=========================================================================================

# **Azure Virtual Network (VNet)**

An Azure Virtual Network (VNet) is a representation of your own network in the cloud. It is a logical isolation of the Azure cloud dedicated to your subscription.

**1.VNet as a Representation of Your Network in the Cloud**
* Azure Virtual Network (VNet) allows you to create an isolated, private network within the Azure cloud. It is the foundational network service for managing and connecting resources, such as Virtual Machines (VMs), Databases, and other services, within Azure
* A VNet is analogous to a traditional on-premises network but fully managed by Azure. It allows you to securely extend your on-premises network into the cloud and manage traffic between your cloud resources.

**2.Fundamental Building Block for Private Networks**
* A VNet serves as the central platform for deploying Infrastructure as a Service (IaaS) component like VMs and Platform as a Service (PaaS) components like web apps, databases, and other Azure services. Without VNets, you would not have a private network on which to connect these resources.

**3.Region and Subscription-Based**
* A VNet is specific to an Azure region and belongs to a single Azure subscription. Each subscription can contain multiple VNets, but each VNet can only exist in one region. This is important for planning both regional availability and network latency.

 
**4.IP Addressing**
* When you create a VNet, you define a CIDR block (Classless Inter-Domain Routing) to allocate a range of private IP addresses for your network. This address space is used to assign IPs to your virtual machines, load balancers, and other resources in the VNet.
* Azure supports up to 4096 IP addresses in a single VNet, though smaller subnets can be created within this range for better resource management.
* It’s essential to plan the IP address space carefully to avoid conflicts with other VNets, on-premises networks, or other Azure services.

=========================================================================================
# 5.Subnet

* A subnet is a range of IP addresses within a VNet. You can divide a VNet into multiple subnets based on your design and network architecture.
* Subnets help segregate different types of resources for organization, security, and traffic management purposes.
* Resources deployed in different subnets within a VNet can communicate with each other automatically, without requiring any additional configuration, unless network security controls (such as Network Security Groups - NSGs) or custom routing (using route tables) are applied.

**Subnet Communication**
* VMs (and other resources) deployed in the same subnet or across different subnets in the same VNet can communicate without any extra configuration.
* For example, if you have a VNet with multiple subnets (e.g., "web", "application", and "database"), the VMs in each subnet can directly communicate, assuming there are no restrictions (such as NSG rules) in place.

**Subnet Configuration: Route Tables and NSGs**
* You can associate Route Tables and Network Security Groups (NSGs) with individual subnets:
* **Route Tables:** These define how traffic is directed within the VNet or between VNets and external resources.
* **NSGs:**  You can apply NSGs to subnets (or individual network interfaces) to control inbound and outbound traffic based on rules.

**IP Addressing within Subnets**
* When defining a subnet within a VNet, certain IP addresses are reserved for Azure’s internal use and cannot be assigned to VMs or other resources:

**For every subnet in Azure, the following IP addresses are reserved**
* **Network address (x.x.x.0):** Identifies the subnet itself.

* **Default gateway (x.x.x.1):** This IP address is reserved for Azure’s default gateway to route traffic within the VNet and to external networks.

* **Reserved for Azure DNS (x.x.x.2, x.x.x.3):** These IP addresses are reserved for Azure's internal DNS services, which allow the resources in the VNet to resolve domain names.

* **Last IP address: (x.x.x.255)** is reserved as the broadcast address. It is used to send broadcast messages to all devices in the subnet (although, in Azure, broadcast traffic is typically restricted).

* *Reserved IPs: 5 IPs (network address, default gateway, 2 Azure DNS addresses, and broadcast address).*
* *Usable IPs: 256 - 5 = 251 usable IP addresses.*

**5.	Non-Overlapping IP Address Ranges**
* When creating a VNet, the CIDR blocks you choose should not overlap with other VNets or your on-premises network. This is crucial for routing traffic correctly between networks.
* If there is an overlap, communication between the VNets or the VNet and on-premises networks will not work correctly, and you will encounter routing issues.

**6.	Traffic Control**
* You can control how traffic flows between different subnets, VNets, and on-premises networks through route tables and custom network security policies.


**Benefits of Using Azure VNets:**
* **Isolation.** Vnets are completely isolated from one another. That allow you to create disjoint network from development, testing, production that use the same CIDR address book 
* **Access to the Public internet** All IaaS and PaaS role instances in a Vnet can access the public internet by default. You can control access by using by network security group (NSG)
* **Access to VMs with the Vnet.** PaaS role instance and IaaS VMs can be launched in the same virtual network and they can connect each other using private IP address if they are in different subnets without need to configure a getaway or use public IP address 
* **Name resolution** Azure provide the internal name resolution for IaaS VMs and PaaS role instance deployed in your Vnet you can also deploy your own DNS servers and configure the Vnet use them.
* **Security** traffic entering and existing the virtual machines and PaaS role instance in a Vnet can be controlling use Network Security Group
* **Connectivity** Vnets can be connected to each other, and even to your on-premises datacentre by using Site-to-Site VPN connection or Express route connection.  

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image10.png)

===========================================================================================

# Virtual Network Peering (VNet Peering)
* Definition: VNet Peering allows connectivity between two virtual networks (VNets) in the same Azure region or across different regions. This enables resources in each VNet to communicate with each other using private IP addresses, as though they were part of the same network.

**Key Points:**
* **No Gateways Required:** Peering establishes direct connectivity using the Azure backbone network, without needing a VPN gateway or public internet.

* **Low Cost:** The ingress and egress traffic between peered VNets incurs nominal costs, typically based on data transfer between regions.

**Global VNet Peering**
* This is an extension of VNet Peering, where you connect VNets across different Azure regions.

* **Global Connectivity:** It enables network traffic between VNets in different geographic regions without needing to route traffic over the public internet.

* **Regions:** The peering link between VNets can span multiple Azure regions, enabling geographically dispersed resources to communicate securely.

* **Cost:** Data transfer charges for Global VNet Peering are typically higher than those for peering within the same region.

**VNet Peering Across Different Subscriptions**
* **Support for Different Subscriptions:** Azure allows VNet Peering even if the VNets are in different Azure subscriptions, as long as the user has the appropriate permissions for both subscriptions.

* **Use Case:** This can be particularly useful in multi-tenant scenarios or where different departments or teams have separate Azure subscriptions but need to establish network communication.

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image11.png)

**Routing between Azure and on-premises**
* Must use unique IP address ranges: It is essential that the IP address ranges for on-premises networks and Azure Virtual Networks (VNets) are unique.

**Types of peering**
* **Site-to-Site VPN** (Private Peering) This is a private peering method where a VPN connection is used to securely link an on-premises network to an Azure VNet. Site-to-Site VPNs are common for hybrid environments where on-premises data centers need to connect to Azure networks securely.
* This method is also supported with ExpressRoute.

* **ExpressRoute Peering ExpressRoute** provides a private, dedicated connection between an on-premises network and Azure, bypassing the public internet. This method is used for high-performance and low-latency network requirements.

**Azure VPN Gateway**
* The Azure VPN Gateway is used to send encrypted traffic between an Azure VNet and an on-premises network over the internet. It can also be used for inter-VNet communication within Azure.

Can also be used between azure virtual networks 

* Encrypted traffic across the azure platform 

Connects with azure validated devices 

**Types of VPN Gateway**
* IPSEC is computationally expensive which limits bandwidth 
**Four SKUs of gateway**
* **Basic:**
* Maximum throughput: 100 Mbps.
* Supports up to 10 tunnels.
* **VpnGw1:**
* Maximum throughput: 500 Mbps.
* Supports up to 10 tunnels.
* **VpnGw2:**
* Maximum throughput: 1 Gbps.
* Supports up to 30 tunnels.
* **VpnGw3:**
* Maximum throughput: 1.25 Gbps.
* Supports up to 30 tunnels.

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image12.png)

===========================================================================================

# Point-to -Site VPN
* A Point-to-Site (P2S) VPN allows individual computers (or devices) to connect securely to a Azure Virtual Network (VNet) over the public internet. This is particularly useful when remote users or small offices need to connect to Azure without requiring a full-site connection, which is provided by Site-to-Site VPNs.
* Point-to-Site VPNs in Azure typically use SSTP as the protocol for secure communication. SSTP is a SSL-based VPN that uses HTTPS over TCP port 443, which makes it easier to bypass firewalls and proxies, as it can work over standard web traffic ports.
* Point-to-Site VPN utilizes certificate-based authentication to ensure secure connections.
* The process involves two main types of certificates:
* **Root certificate:** This is the certificate that is uploaded to Azure to authenticate the incoming connections.
* **Client certificates:** These are installed on the computers or devices that will use the Point-to-Site VPN to connect to Azure. The client certificates prove the identity of the device when attempting to establish a secure connection.

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image13.png)
===========================================================================================

# Site -to -Site VPN

* A Site-to-Site (S2S) VPN is a method for securely connecting an on-premises network to an Azure Virtual Network (VNet) over the internet. It is commonly used to extend an on-premises data center or network into Azure, enabling hybrid cloud architectures that allow secure communication between on-premises resources and Azure-hosted services.
* Site-to-Site VPNs provide connectivity not only between on-premises networks and Azure VNets but also allow connecting multiple VNets within Azure. This means you can link Azure VNets that might be in different regions or subscriptions.
* The connection between the on-premises network and Azure is established over the public internet. The traffic is encrypted using IPsec/IKE protocols, ensuring secure transmission of data between the on-premises site and Azure.
* The VPN allows bi-directional communication, meaning that traffic can flow in both directions: from Azure to the on-premises network and from on-premises to Azure. This is essential for seamless hybrid cloud architectures where both sides need to communicate with each other.
* Network Security Groups (NSGs) should not be applied to the VPN Gateway subnet. This is because the VPN Gateway needs to handle traffic in and out of the Azure VNet without being filtered by security rules. Placing an NSG on the gateway subnet could block or interfere with VPN traffic, causing connection issues.
* During the configuration of the VPN Gateway, a shared key (pre-shared key or PSK) is used to authenticate the connection between Azure and the on-premises VPN device. Both sides must use the same shared key for the connection to be established successfully.

**Site – to- Site VPN Challenges**

* One of the most common issues when setting up a Site-to-Site VPN is IP address overlap between the on-premises network and the Azure VNet.
* It uses the internet
* Bandwidth and Latency Limitations IPsec VPNs are computationally expensive, which can limit the available bandwidth for traffic passing through the VPN tunnel.
* When setting up a Site-to-Site VPN in Azure, the VPN Gateway needs to be deployed in its own gateway subnet. Misconfiguring this subnet can lead to connectivity issues.
* Authentication and Key Management Issues Challenge: Site-to-Site VPNs use shared pre-shared keys (PSK) or certificates for authentication between Azure and on-premises devices


![alt text](https://github.com/acmarpu/images/Azure/blob/main/image14.png)

===========================================================================================

# Azure ExpressRoute
Azure ExpressRoute is a service that enables private, high-speed, and secure connections between Microsoft datacenters and your on-premises infrastructure, or data centers in colocation facilities. Unlike traditional internet-based connections, ExpressRoute connections do not traverse the public internet, providing advantages in terms of security, reliability, speed, and latency.

**Key Features of Azure ExpressRoute**
* **Private Connection:** Traffic flows through private connections, ensuring security and reliability, with up to 10 Gbps speeds.
* **Redundancy:** The service offers a redundant connection to ensure continuous availability.
* **Predictable Performance:** Unlike public internet connections, ExpressRoute provides predictable throughput and performance.
* **High Throughput:** ExpressRoute can handle high throughput traffic, ensuring that large-scale enterprise workloads can be supported.
* **Service Level Agreement (SLA):** It comes with an SLA that guarantees availability, reliability, and performance.
* **Low Latency:** Reduced latency compared to traditional public internet connections.

**Gateway SKUs and Bandwidth**

ExpressRoute offers different SKUs based on bandwidth requirements:

Basic (500 Mbps): Deprecated.

Standard (1000 Mbps).

High Performance (2000 Mbps).

Ultra Performance (9000 Mbps).

**Route Filters**
* **Service Control:** Route filters help control the specific Azure services advertised through the ExpressRoute connection, such as Exchange or other regional services.
* **Regional Control** You can also control the availability of Azure services on a regional basis using route filters and BGP community values.

* **Connecting Multiple Azure VNets**

* **Standard ExpressRoute:** Supports connecting multiple virtual networks (VNets) within the same geopolitical region (e.g., any US region).
* **ExpressRoute Premium:** Extends connectivity capabilities to allow connections across different global regions.

* **Peering Considerations:** Communications occur through peering points, which may add latency compared to using other network peering options, so it's important to plan network architecture carefully.


![alt text](https://github.com/acmarpu/images/Azure/blob/main/image15.png)

===========================================================================================
# Hub-Spoke Network Topology in Azure
The Hub-Spoke topology in Azure is a popular architecture pattern used to efficiently organize and manage virtual networks (VNets) while ensuring proper isolation, security, and cost-effectiveness. In this architecture, the hub VNet acts as a central point of connectivity, typically connecting on-premises resources to the Azure cloud, while the spokes are individual VNets used to host workloads and applications that may or may not need direct communication with each other.

**Hub VNet:**
*	The hub is a central VNet in Azure that typically connects to your on-premises datacenter through ExpressRoute or VPN gateways.
*	Shared services like DNS, network virtual appliances (NVAs), firewalls, NTP, and Active Directory Domain Services (AD DS) are often deployed in the hub.

**Spoke VNets:**
*	The spokes are individual VNets connected to the hub and are typically used to isolate workloads for different environments or applications.
*	Spokes can be organized around different purposes, such as development, testing, production, or different business units, maintaining network isolation between them.
*	They do not communicate directly with each other but can communicate with the hub for accessing shared services like DNS or NTP.

**Cost Efficiency:**
* Centralizing shared services in the hub VNet reduces the need for redundant infrastructure in each spoke, which helps to lower costs. For example, centralized services like firewalls, DNS servers, and NTP servers can be shared by multiple workloads in the spokes. 

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image16.png)

===========================================================================================

# Azure Private Link
Azure Private Link is a service that enables secure, private connectivity to Azure services, resources, or your own services from within an Azure Virtual Network (VNet). It allows you to access services in Azure over a private IP address rather than the public internet, providing enhanced security and data privacy.

**What is Azure Private Link Service?**

The Azure Private Link Service refers to your own service (hosted behind an Azure Standard Load Balancer) that is made accessible to consumers via Private Link. This enables customers to access your service securely from their own VNets, over a private connection, without going over the public internet.

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image17.png)


===========================================================================================

# Private Endpoint
A Private Endpoint is a crucial component of Azure's Private Link service. It is a network interface that uses a private IP address from your Azure Virtual Network (VNet) to connect securely and privately to a service powered by Azure Private Link. By enabling a Private Endpoint, you bring Azure services (or your own services hosted on Azure) into your VNet, ensuring that traffic between your VNet and the service remains entirely private and does not traverse the public internet.
The service could be an Azure service such as:

* **Services Accessible via Private Endpoint**
Azure Private Link allows you to access many Azure services securely through Private Endpoints. These services can be Azure-managed services or even custom services you deploy in your own Azure environment. Some of the services commonly accessed through Private Endpoints include:
* **Azure Storage:** Secure access to Blob Storage, File Shares, and other storage services via a private IP.
* **Azure Cosmos DB:** Private access to Azure Cosmos DB resources, ensuring data is securely accessed without traversing the public internet.
* **Azure SQL Database:** Secure, private access to Azure SQL Database instances, allowing traffic between your VNet and the SQL Database without exposing it to the public internet.
* **Azure Key Vault:** Secure access to Azure Key Vault secrets and keys through a private endpoint, ensuring data protection and secure management of credentials.
* **Azure Kubernetes Service (AKS):** Private access to services running in Azure Kubernetes Service (AKS), enabling secure communication between your VNet and the AKS resources.
* **Other Azure Services:** Many other Azure services, such as Azure Synapse Analytics, Azure Database for MySQL/PostgreSQL, and Azure App Service, can also be accessed privately via Private Endpoints

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image18.png)

===========================================================================================

# Service Endpoints
Azure Service Endpoints provide a way for private IP addresses in your Azure Virtual Network (VNet) to reach the endpoints of specific Azure services, such as Azure Storage, Azure SQL Database, and other PaaS services, without requiring a public IP address. By using Service Endpoints, traffic between your VNet and the Azure service stays within the Azure backbone network rather than going over the public internet. However, unlike Azure Private Link and Private Endpoints, Service Endpoints do not provide access to services through a private IP directly. They enable secure communication to the service via its public endpoint, but still use the private IP within your VNet for communication.

* **How Azure Service Endpoints Work**
* **Public Service Access with Private IP:** Service Endpoints allow you to securely extend your VNet to specific Azure services. When you enable Service Endpoints for a service like Azure Storage or Azure SQL Database, your VNet’s private IP address is used to access the service’s public endpoint. The traffic still flows through the Azure backbone network.

**Service-specific:** Service Endpoints are available for certain Azure services, including Azure Storage, Azure SQL Database, Azure Cosmos DB, Azure Key Vault, and more. You need to explicitly enable Service Endpoints for each service on the VNet subnet.

* **No Need for Public IP:** With Service Endpoints, your VNet can access these services without exposing your VNet to the public internet via a public IP address.

**Service Endpoints:**
* Access Azure services via public endpoints but over a private connection from within your VNet.
* No private IP address for the service—communication happens through the public endpoint of the Azure service.
* Use cases: Typically for services like Azure Storage or Azure SQL Database when private, secure communication is required but a direct private IP connection is not needed.

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image19.png)

**Private Link / Private Endpoints:**
* Provides private IP access to Azure services, ensuring the entire communication path between your VNet and the service remains private, within the Azure backbone network.
* Offers more granular control by assigning a private IP to the service and allowing it to be exposed to customers via private endpoints.
* Use cases: Recommended for scenarios requiring strong data security, compliance, and private network connections, like accessing sensitive services or exposing your own services securely.




===========================================================================================

# Azure Load Balancer

* Azure Load Balancer is a cloud-based service that distributes incoming traffic across a pool of virtual machines (VMs) to ensure high availability and resilience for applications. If a VM fails, the load balancer stops routing traffic to it, directing it to healthy VMs instead.

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image20.png)

**Resilience and High Availability:**

* Distributes traffic across multiple VMs to ensure continuous availability.
* Prevents traffic from being routed to failed VMs, ensuring application stability

**OSI Model Layer**
* Azure Load Balancer operates at Layer 4 (Transport Layer) of the OSI model, which handles traffic distribution based on TCP and UDP protocols.

**Single Point of Contact:**
* It acts as the single point of contact for clients, managing traffic between the client and backend services

**Scalability and Performance:**
* Scales to handle millions of flows, providing low latency and high throughput for both inbound and outbound traffic.
* Suitable for scaling applications and ensuring high service availability.
* With Azure Load Balancer, you can scale your applications and create high availability for your services. Load Balancer supports inbound and outbound scenarios, provides low latency and high throughput, and scales up to millions of flows for all TCP and UDP applications.

**Application Load Distribution:**
* Azure Load Balancer can be used to distribute traffic between virtual machines (VMs) or cloud services in a virtual network

**Load Balancing Rules:**
* Load-balancing rules define how traffic should be distributed to backend pool instances.
* Traffic distribution is done via a hash-based algorithm, which balances incoming flows across backend resources.
* If a backend endpoint fails, the load balancer relies on health probes to detect failures and ensure traffic is directed only to healthy VMs.

**Port Forwarding with Azure Load Balancer**
*	Azure Load Balancer allows you to configure Port Forwarding through the use of Inbound NAT rules. This feature enables traffic to be forwarded from a specific port on a frontend IP address to a specific port on a backend instance, which is typically a virtual machine (VM) inside a virtual network.

*Inbound NAT Rule:*
* When you create an inbound NAT rule, you're essentially mapping a port on the frontend IP to a port on the backend instance (a specific VM). This allows external traffic to reach the VM even if it's behind the Load Balancer.

*Traffic Flow:*
* A client sends traffic to a specified port on the frontend IP of the Azure Load Balancer.
* The Inbound NAT rule maps that specific port on the frontend IP to a port on a backend instance (VM).
* The traffic is then forwarded to the appropriate backend VM on the specified port.

*Hash-based Distribution:*
*	Azure Load Balancer uses the same hash-based algorithm for inbound NAT rules as it does for regular load balancing. This ensures that traffic is consistently routed to the same backend instance based on the frontend IP and port.

**Automatic reconfiguration**
* **Seamless Scaling:** When you scale your instances up or down (e.g., adding or removing VMs), Azure Load Balancer automatically adjusts its configuration without needing manual intervention.
* **No Additional Operations:** Once a VM is added or removed from the backend pool, the Load Balancer instantly reconfigures itself to account for these changes. This means you don’t need to perform additional operations on the Load Balancer resource itself to accommodate these changes.

**Health probes**
* Monitoring Backend Health: Azure Load Balancer uses health probes to monitor the health of backend instances (VMs).
* Health Check Process: If a probe fails (i.e., the backend instance is unhealthy), the Load Balancer stops sending new connections to that instance. However, existing connections are not immediately impacted and will continue until:
* The application terminates the connection.
* An idle timeout occurs.
* The VM is shut down.
* This ensures that only healthy backend instances receive new traffic, while existing sessions are not disrupted unexpectedly.

**Source IP Affinity mode (also known as Session Affinity or Client IP Affinity)**
* **Purpose:** This mode ensures that traffic from the same client IP address is consistently directed to the same backend server (VM) throughout the duration of the session.
* **How it Works:** It uses a hash-based mechanism involving a 2-tuple (source IP and destination IP) or a 3-tuple (source IP, destination IP, and protocol type) to map incoming traffic to the available backend servers.
* **Use Case:** For applications that require session persistence, such as web applications where user sessions must remain on the same backend server.
* **Benefit** It provides session persistence, ensuring that all requests from the same client during a session go to the same backend VM.

**External Load Balancer (Internet-Facing Load Balancer)**
* An External Load Balancer is used to provide high availability for IaaS VMs (Infrastructure as a Service) and PaaS role instances (Platform as a Service) that need to be accessed from the public internet. T
* his type of Load Balancer balances incoming traffic from the internet to the virtual machines (VMs) hosted in Azure.

**Frontend IP Address:**
* The frontend IP address of an external load balancer has a public IP, which means it is exposed to the public internet. Clients from outside Azure can access this frontend IP to reach the services hosted behind the Load Balancer.

* **Internal Load Balancer**
* An Internal Load Balancer (ILB) is used to provide high availability for IaaS VMs and PaaS role instances that are accessed internally within Azure Virtual Networks (VNets) or from connected networks, but not from the public internet.
* The internal load balancer balances traffic between VMs within the same virtual network or between networks that are connected to the VNet (via VNet peering, VPN Gateway, etc.).

* **Frontend IP Address:**
* The frontend IP address of an internal load balancer has a private IP, which means it is only accessible from within the VNet or connected networks

* Key Differences Between Basic and Standard SKUs:

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image21.png)

===========================================================================================

# Azure Application Gateway
* Azure Application Gateway is a web traffic load balancer that enables you to manage and optimize the distribution of traffic to your web applications. It operates at OSI Layer 7 (the Application Layer), which is more advanced than traditional load balancers that work at Layer 4 (Transport Layer). This allows Azure Application Gateway to provide more granular traffic management based on application-specific criteria like URLs, headers, and even cookies.

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image22.png)

**Features** 
* Autoscaling
* SSL termination 
* Connection draining 
* Web application firewall
* URL-based routing
* ETC.
 
**Web Traffic Load Balancer (Layer 7):**
* Unlike traditional load balancers that route traffic based on IP addresses and ports (Layer 4), Azure Application Gateway routes traffic based on application-specific attributes such as URLs, host headers, and other HTTP request properties.
* For example, requests with the path /images can be directed to a pool of servers optimized for serving images, while requests with the path /video can be routed to a separate pool optimized for video content.

**URL-based Routing:**
* URL-based routing is one of the most powerful features of Application Gateway. It allows you to route incoming traffic based on the URL path. This makes it easy to direct different types of traffic to specific backend pools (sets of servers).
* Example:
- Requests to example.com/images go to a backend pool optimized for serving images.
- Requests to example.com/videos go to a backend pool optimized for video delivery.

**Autoscaling:**
* Autoscaling automatically adjusts the capacity of the Application Gateway based on the incoming traffic volume. This ensures that the gateway can handle varying traffic loads without manual intervention.

**SSL Termination:**
* SSL termination is the process of decrypting SSL/TLS traffic at the Application Gateway, offloading the computational burden from backend servers.

**Connection Draining:**
* Connection draining ensures that the backend pool can gracefully handle ongoing requests when a server is taken out of service (e.g., during scaling operations, updates, or maintenance).

**Web Application Firewall (WAF):**
* Azure Application Gateway includes a Web Application Firewall (WAF) that helps protect your web applications from common web vulnerabilities and attacks, such as SQL injection and cross-site scripting (XSS).
* WAF uses predefined rules to filter and monitor HTTP traffic for malicious content, enhancing the security of the applications behind the gateway.

**Static VIP:**
* Static VIP ensures that the Virtual IP (VIP) associated with the Application Gateway remains static, meaning it doesn’t change even after a restart. This is particularly important for DNS resolution and application stability, as it avoids the need for reconfiguring IP addresses or DNS records.
* Static VIP provides a consistent and reliable endpoint for users accessing your application, improving resilience and simplifying network management.

===========================================================================================
# Azure Traffic Manager

Azure Traffic Manager is a DNS-based global traffic load balancer that optimizes the distribution of traffic across services hosted in various Azure regions or external endpoints. It enables businesses to build high-availability, low-latency applications by intelligently routing requests based on specific policies.

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image23.png)

* **DNS-based Traffic Load Balancer:**
* Azure Traffic Manager uses DNS to route client requests to the most suitable service endpoint. When a client makes a request, Traffic Manager returns the DNS address of the optimal endpoint based on:

- Traffic-routing method
- Health of the endpoints

* **Global Traffic Distribution:**
* Traffic Manager enables global traffic distribution to services hosted across various Azure regions, ensuring optimized performance and high availability for users regardless of their geographic location.
Endpoint Types:
An endpoint in Traffic Manager is any internet-facing service. These endpoints can be:

* **Azure Endpoints:** 
* Services hosted within Azure.
* These are Azure-hosted services, such as virtual machines, web apps, or cloud services.
* DNS Resolution: Traffic Manager resolves DNS queries to the appropriate Azure-based endpoint.

**External Endpoints:** 
* Services hosted outside of Azure, such as on-premises or with other hosting providers (via IPv4/IPv6 addresses).
* These endpoints point to services hosted outside of Azure, either on-premises or with other cloud providers.
* Pv4/IPv6 Addresses: External endpoints use public IP addresses (IPv4 or IPv6) to point to services not hosted on Azure.

**Nested Endpoints:** 
* Combines multiple Traffic Manager profiles to create more flexible routing schemes, particularly for complex deployments.
* Nested endpoints allow you to combine multiple Traffic Manager profiles into a more complex, flexible traffic-routing scheme.
* This is particularly useful for large-scale deployments where you need to support sophisticated routing logic and failover models.

**Traffic Routing Methods:**
* **Performance Routing:** Routes client requests to the endpoint with the lowest latency, i.e., the closest endpoint in terms of performance.
* **Priority Routing:** Directs all traffic to a primary endpoint (with the highest priority) and uses other endpoints as backup if the primary endpoint fails.
* **Weighted Round-Robin Routing:** Distributes traffic across endpoints based on assigned weights. Endpoints with higher weights receive a greater share of the traffic.

===========================================================================================
# Azure Front Door 
Azure Front Door is a global, scalable entry-point service designed to optimize the performance, security, and reliability of web applications and content. By leveraging the Microsoft global edge network, it enhances the delivery of applications to a global audience, providing robust solutions for both consumer and enterprise needs. Here is a summary of why you should consider using Azure Front Door, its key features, and how it fits into broader network security infrastructure:

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image24.png)

* **Why Use Azure Front Door?**
* **Global Performance and Scalability:** It ensures low-latency and fast delivery of both dynamic and static content to users around the world by utilizing the Microsoft global edge network.
* **High Availability and Reliability:** With features like global traffic routing and quick failover, Azure Front Door ensures that applications are always accessible with minimal downtime, even in the event of a service disruption.
* **Simplified Infrastructure:** Front Door enables organizations to manage multiple web applications under a single service, making it easier to scale and maintain applications without the complexity of multiple point solutions.

**Key Features of Azure Front Door:**
* **Accelerated Application Performance:** It uses a split TCP-based anycast protocol to improve response times and reduce latency, enhancing the user experience globally.
* **Intelligent Health Probe Monitoring:** Automatically monitors the health of backend resources, ensuring traffic is routed to healthy instances.
* **URL Path-based Routing:** You can define routing rules based on the URL path, which helps in directing traffic to specific backend resources or applications.
* **Multi-Site Hosting:** Front Door supports hosting multiple websites, enabling efficient infrastructure management for complex application needs.
* **Cookie-based Session Affinity:** Ensures that user sessions are consistently routed to the same backend server for a smoother experience.
* **SSL Offloading and Certificate Management:** Reduces the load on backend servers by handling SSL termination at the edge, improving both performance and security.
* **Custom Domains and HTTPS Redirect:** Offers custom domain support and the ability to automatically redirect HTTP traffic to HTTPS, ensuring secure communications.
* **Web Application Firewall (WAF):** Integrated security measures to protect against common web vulnerabilities and attacks. IPv6 and HTTP/2 Support: Ensures modern, scalable network protocols are supported for better performance and reach.


===========================================================================================

# CDN (Azure Content Delivery Network): 
*	It is used for the delivery of the contents stored in the storage account. 
*	We can use a content delivery network to reduce the latency of the delivery. 
*	We will create a CDN endpoint near to the users to reduce the latency.

*	**Azure Content Delivery Network (CDN)** is a distributed network of servers that accelerates the delivery of content, such as web pages, images, videos, and other static or dynamic content, to users across the globe. The main purpose of Azure CDN is to reduce latency, improve user experience, and ensure high availability by serving content from servers that are geographically closer to the end user.
*	**Reduced Latency:**
Azure CDN caches content at edge locations around the world. When a user requests content, the request is routed to the nearest CDN server, reducing the time it takes to fetch the content.
*	**Improved Performance:**
By serving content from the edge server closest to the user, Azure CDN reduces the load on the origin server, which results in improved overall application performance
*	**Global Reach:**
Azure CDN provides a global network of edge locations to ensure that users from any region can access content with minimal latency. By creating a CDN endpoint near to the users, content delivery is accelerated regardless of the user's location.
*	**Scalability:**
Azure CDN automatically scales to meet the demands of users. As traffic increases, the CDN adjusts its resources to handle the increased load without requiring manual intervention.
*	**Cost Savings:**
By caching content at edge locations, Azure CDN reduces the number of requests made to the origin server, which can lower the load on the server and reduce the associated data transfer costs.
*	**Security:**
Azure CDN can work with HTTPS to encrypt content during transit, providing secure delivery of content. It also offers protection against DDoS (Distributed Denial-of-Service) attacks by mitigating traffic spikes and redirecting requests to healthy servers.
*	**Media and Video Streaming:**
For websites or applications delivering videos or high-resolution images, Azure CDN helps provide fast loading times and high-quality streaming experiences, regardless of the user's geographic location.


*	**Azure CDN Pricing**

Azure CDN pricing is based on:

* **Data Transfer:** Charges for data transferred from the CDN to the users.
* **Requests:** Charges for the number of requests made to the CDN (e.g., GET, POST, etc.).
* **Geographical Location:** Pricing may vary depending on the region from which the content is served and the network's edge locations.
* **Caching Options:** Some CDN services offer custom caching rules and the option to control how long content is cached at the edge location.

*	**CDN Types in Azure**

Azure provides three types of CDN offerings:

**Standard Microsoft CDN:**

A Microsoft-backed CDN service that uses the global edge network of Microsoft’s data centers.
**Standard Akamai CDN:**

A CDN service backed by Akamai, one of the largest and most established CDN providers globally. It is ideal for users looking for more advanced features and global coverage.
**Standard Verizon CDN:**

A CDN service backed by Verizon's edge network, offering optimized performance and reliability across their network.

===========================================================================================
# Monitoring and Maintain Azure Resources

# Azure Monitor 
*	A single source for the monitoring of Azure resource
*	Provide insight into log metric alerts 
*	Can create action groups which can be utilized as part of alerts to perform multiple actions centrally defined 

# Azure Network Watcher**

*	An instance is deployed to a region for services in that region
*	Large number of capabilities
*	Topology viewer 
*	Packet capture (Via an agent installed into VM)
*	IP flow verify and next hop determination 
*	Connection monitor and troubleshoot 
*	Security group viewer 
*	NSG flow logging 
*	Virtual network gateway and virtual network connection troubleshooting 
*	Network use against subscription limits 
*	Enable or disable log for resource for virtual network

# Azure Monitoring 
Azure Monitor is a comprehensive service offered by Microsoft that helps organizations collect, analyze, and act on telemetry data from both cloud and on-premises environments. It is an essential tool for ensuring the health, performance, and security of resources within your Azure environment. Azure Monitor provides valuable insights into your system, helping you identify issues quickly and improve system performance through data-driven decisions.

- Metrics 
- Logs 
- Health 
- Service events

===========================================================================================
# Log Analytics 
*	Log Analytics is a powerful feature of Azure Monitor that provides centralized log collection, searching, and analysis across your Azure environment. It allows you to aggregate, analyze, and visualize logs from various Azure resources and on-premises systems, helping you gain deeper insights into the health, performance, and security of your infrastructure and applications.

*	Log Analytics is built on the Azure Monitor Log Analytics Workspace, a central repository for collecting, storing, and querying log data. It uses Kusto Query Language (KQL) for querying logs, offering powerful capabilities for filtering, analyzing, and visualizing the data.

*	Data in Log Analytics is stored in a Log Analytics Workspace, where you can configure retention policies to specify how long data is kept.


# Azure Diagnostics 
Azure Diagnostics is a feature that enables you to collect detailed diagnostic data from your applications and virtual machines (VMs) running in Azure. It helps you capture critical metrics, logs, performance counters, and diagnostic information, which are essential for debugging, troubleshooting, performance measurement, resource usage monitoring, traffic analysis, and capacity planning. By leveraging Azure Diagnostics, developers and operations teams can ensure the health and performance of their applications and infrastructure within Azure.

Azure Diagnostics is typically used with Azure Virtual Machines (VMs), Web Apps, and other Azure resources to monitor the internal workings of applications and the operating system.

**Collection of Diagnostic Data:**
*	The collected data is stored in Azure Storage (typically Blob Storage) or streamed to Azure Monitor for further analysis and action.
*	Azure Diagnostics enables the collection of several types of diagnostic data, including:
*	**Application logs:** Logs generated by the application running in Azure, such as error messages, warnings, or custom logs.
*	**System logs:** Logs from the underlying operating system, including system errors, service status, and hardware health data.
*	**Performance counters:** Metrics about the system's CPU, memory usage, disk I/O, network usage, etc., that provide insights into how the application or VM is performing.
*	**Network traffic data:** Detailed information about the network traffic, including inbound and outbound data, can help in troubleshooting network-related issues.
*	**Event logs:** Operating system event logs, such as Windows Event logs, can provide useful information about system failures or performance bottlenecks.
*	**Azure Diagnostics** helps you identify and troubleshoot issues by collecting logs and metrics that are critical for diagnosing problems in applications or system-level services.

===========================================================================================

# Azure Application Insights 
Azure Application Insights is an Application Performance Management (APM) service that is part of Azure Monitor. It is designed for developers and DevOps professionals to help monitor the performance, availability, and usage of applications in real-time. By integrating with your application, Application Insights automatically detects performance anomalies, provides powerful analytics tools, and helps you diagnose issues, providing a comprehensive overview of your app's health and user interactions.

**Application Insights** continuously monitors your live applications, automatically detecting anomalies in performance such as slow response times, server-side errors, or failed requests. It provides real-time alerts so that you can address performance issues immediately.

**Telemetry Collection:**
Application Insights collects telemetry data from your application to give a full view of its performance and user behavior. This data includes:
*	**Request Data:** Information about HTTP requests, including response times and status codes.
*	**Dependency Data:** Information about external calls your application makes (e.g., databases, REST APIs, or third-party services).
*	**Exception Data:** Errors and exceptions generated by your application, helping you trace the root cause of issues.
*	**Custom Events:** Custom telemetry that you can define to track business logic, user interactions, or other application-specific metrics.
*	**Performance Counters:** CPU usage, memory consumption, and other system-level metrics for your application.

===========================================================================================



# Network Security Groups (NSG)

![alt text](https://github.com/acmarpu/images/Azure/blob/main/image25.png)

* NSGs are composed of a set of security rules.
* Each rule defines whether inbound (incoming) or outbound traffic is allowed or denied.
* NSGs play a key role in managing the security and traffic flow between VMs and subnets in cloud environments like Azure, acting as virtual firewalls.

**Traffic Inspection:**
* NSGs inspect incoming and outgoing traffic at the **network level.**
* They work like a virtual firewall to control the flow of traffic between virtual machines (VMs) and subnet

**Rules & Priorities:**
* NSG rules can either **allow or deny** traffic based on the defined criteria.
* Priority determines rule evaluation order: **lower numerical values have higher priority**. For instance, a rule with priority 100 is evaluated before a rule with priority 200.
* The last rule (with the lowest priority) is the default deny rule, which blocks any traffic not explicitly allowed by earlier rules.
* For example, if there's a rule allowing traffic from a specific source IP address on a certain port (with a high priority), and another rule denying all traffic on the same port (with a lower priority), the traffic would be allowed because the first rule takes precedence due to the higher priority number.

**Association:**
* A single NSG can be associated with multiple network interfaces (NICs) or subnets.
* However, each NIC or subnet can only be associated with one NSG at a time.

**The rules are based on the 5-tuple, which includes:**

* **Protocol:** Specifies the protocol (TCP, UDP, or wildcard "*").
* **Source IP address range:** The range of IP addresses from which traffic originates.
* **Source port range:** The range of ports from which traffic originates.
* **Destination IP address range:** The range of IP addresses where traffic is going.
* **Destination port range:** The range of destination ports.


![alt text](https://github.com/acmarpu/images/Azure/blob/main/image8.png)


===========================================================================================

# **Azure Firewall**

* Azure Firewall is a managed, cloud-based network security service that protects your Azure Virtual Network resources. 
* It is a fully stateful firewall as a service with built-in high availability and unrestricted cloud scalability.

**Fully Managed, Cloud-Based Solution:**
* Azure Firewall is a fully stateful firewall service, meaning it maintains the state of active connections and is able to track traffic flows.
* It is entirely managed and runs as a cloud service, meaning Microsoft handles its maintenance, updates, and scaling.

**Comparison with Network Security Groups (NSGs):**
* NSGs (Network Security Groups) provide basic traffic filtering based on IP ranges and protocols and are implemented using the Virtual Filtering Platform (VFP).
* Unlike NSGs, Azure Firewall is a more comprehensive solution with advanced features like stateful inspection, centralized management, and integration with other Azure services. NSGs are typically used in conjunction with Azure Firewall to further refine traffic control within subnets.


===========================================================================================

# Application Security Groups (ASGs):
Application Security Groups helps to manage the security of the Azure Virtual Machines by grouping them according the applications that runs on them. It is a feature that allows the application-centric use of Network Security Groups.

**Application-Centric Security:**
* ASGs allow you to group VMs based on the applications they run, rather than managing security rules based on IP addresses. This approach simplifies security management, particularly in dynamic environments where VMs are frequently added or removed.
* By grouping VMs based on their roles (e.g., web servers, database servers), security rules can be applied according to the application instead of managing complex IP-based access control lists (ACLs).

===========================================================================================

# Azure DDOs standard protection
* A malicious attempt to disrupt normal traffic by flooding a website with large amount of fake traffic.
* **Azure DDoS (Distributed Denial of Service) Standard Protection** is designed to protect internet-facing services and applications hosted on Azure from large-scale, malicious traffic floods. It is a comprehensive solution that builds on the basic DDoS protection provided by Azure and offers advanced features for better protection and management.
* Distributed denial of service (DDos) is a major threat to internet facing services 
* Azure provides a basic large-scale DDos protection for all services but its tolerance is not configurable nor can it be monitored.
* Azure DDos standard protection is enabled at a virtual network level based on user-defined policies that is applied to all public IPs associated with resource in the virtual network.
* Real-time monitoring and telemetry available
* Services basic and standard 
* Instant on protection 
* Traffic monitoring
* Adaptive tuning
* Attack analytics, metrics, and alerting  

===========================================================================================
