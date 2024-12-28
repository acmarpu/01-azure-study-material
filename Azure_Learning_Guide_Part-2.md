# Azure Networking

Azure Networking is a set of cloud-based services and technologies offered by Microsoft Azure that enables you to connect, secure, and manage resources in a networked environment. Azure Networking helps businesses build scalable, high-performance, and secure networking solutions in the cloud. It provides a suite of tools for virtual networking, load balancing, DNS, security, and hybrid connectivity, allowing seamless communication and integration between different resources and environments (cloud, on-premises, or hybrid).

Use Cases for Azure Networking:
•	Hybrid Cloud Networking: Connect on-premises datacentres to Azure using VPN, ExpressRoute, and VNet Peering.
•	High-Availability Applications: Use Azure Load Balancer, Application Gateway, and Traffic Manager to ensure high availability and optimal performance.
•	Secure Network Architecture: Build isolated environments using Network Security Groups (NSGs), Azure Firewall, and Private Link.
•	Global Applications: Use Azure CDN, Traffic Manager, and Application Gateway to deliver content and services globally.


Ingress Egress
•	Data in bound to Azure 
•	There is no charge for ingress 

Egress
•	Data outbound from Azure, there are charge for egress (unless using an unmetered express route connection) from azure datacenter.

IPV4 and IPV6
•	IPv4 is the most used IP protocol. In Azure, virtual networks support IPv4 by default for VM communication.
•	IPv6 support is gradually expanding. Azure now allows the configuration of IPv6 on virtual networks and enables dual-stack (IPv4 and IPv6) configurations for communication.
•	TCP, UDP, and ICMP
•	TCP (Transmission Control Protocol): Ensures reliable communication by establishing a connection before data is transmitted. It is widely used for applications requiring guaranteed data delivery (e.g., HTTP, FTP, SSH).
•	UDP (User Datagram Protocol): A connectionless protocol used where speed is more critical than reliability (e.g., video streaming, VoIP).
•	ICMP (Internet Control Message Protocol): Primarily used for diagnostic purposes, such as pinging hosts to check network availability or error messages like "Destination Unreachable".

Private IP vs. Public IP:
•	Private IP addresses are used within a Virtual Network (VNet) and cannot be used directly for internet-facing services.
•	Public IP addresses are internet-routable and are required to offer services to the internet.
Azure Public IP Address:
•	Public IPs in Azure can be either static or dynamic.
•	These IP addresses are tied to the region in which they are created and cannot be moved between regions.
•	Azure Public IP Addresses are managed as Azure resources.
•	DNS Name: Each public IP can be assigned a DNS name in the format:
<name>.<region>.cloudapp.azure.com
Impact of VM Operations:
Stop: When a VM is stopped, the public IP is released, and the NAT (Network Address Translation) is deleted. The temporary disk is permanently deleted.
Start: When the VM is started again, Azure will assign a Dynamic IP address. A temporary disk will be attached again.
Reboot: The VM's guest OS will restart, but the VM will stay on the same physical host and retain the same public IP and temporary disk.
Delete: Deleting the VM will permanently delete the VM, its disks, and associated public/private IP addresses, including the temporary disk.
Dynamic vs. Static Public IP:
•	Dynamic IP:
•	Assigned when the service (like a VM) is started.
•	Released when the VM is stopped or deleted.
•	Generally used for cases where a stable IP is not essential.
•	Static IP:
•	Assigned at the time of creation and remains even if the VM is powered off.
•	Useful for services where you need to ensure the IP address remains constant (e.g., DNS records, SSL certificates, firewall rules).
•	Allows the IP address to be moved across different regions or resources.
CIDR
•	Class less Inter – Domain Routing 
•	When configuring a VNet and its subnets, you use CIDR notation to specify IP ranges. For example, 10.0.0.0/16 defines an address range with 65,536 available IP addresses.
•	Subnets can be smaller ranges, such as 10.0.1.0/24, allowing up to 256 IP addresses in that subnet.
•	CIDR notation is a compact representation of an IP address and its associated routing prefix.
•	The notation is constructed from an IP address, a slash (“/”) character and a decimal number. The number is the count of leading 1 bit in the routing mask traditionally called the network mask 
Network Interface Card (NIC) 
is a critical component in virtual machine (VM) networking in Azure, as it enables communication between the VM and other resources within a network, both inside and outside the Azure environment. Here are the key points about NICs in Azure: 

Azure DNS
•	Azure DNS is a scalable, reliable, and secure Domain Name System (DNS) hosting service provided by Microsoft Azure. 
•	It allows organizations to manage their DNS records and domains with the same tools, APIs, and credentials that they use for other Azure services.
•	Azure DNS benefits from Microsoft’s global infrastructure, which ensures high availability, redundancy, and fast name resolution
•	Azure DNS supports the following common DNS record types:
o	A: Maps a domain to an IPv4 address.
o	AAAA: Maps a domain to an IPv6 address.
o	CNAME: Alias for a domain name (e.g., www pointing to example.com).
o	MX: Mail Exchange records for routing email.
o	NS: Nameserver records that specify authoritative DNS servers.
o	PTR: Pointer records used for reverse DNS lookups.
o	SOA: Start of Authority record indicating authoritative DNS servers for the domain.
o	SRV: Service records for identifying services (e.g., for SIP or LDAP).
o	TXT: Text records for adding arbitrary information (often for domain validation).
•	Private DNS Zones:
•	Azure DNS also supports Private DNS Zones, which are designed for private IP address management within a virtual network (VNet). These zones allow for DNS resolution to occur within an Azure Virtual Network (VNet) without exposing those records to the internet.
•	Registration VNet: A private zone can have one registration VNet, where records are published. The registration VNet is responsible for creating and updating DNS records in the private zone.
•	Resolution VNets: Private zones can have up to 10 resolution VNets. These VNets resolve DNS records from the private zone, meaning resources in these VNets can access the private DNS records.
•	Azure DNS can be part of a hybrid cloud solution where on-premises networks and Azure VNets work together. Azure DNS allows you to set up DNS resolution rules that ensure services across hybrid environments can communicate effectively.
•	For enterprises already using Azure Active Directory, Azure Networking, and other Azure services, Azure DNS offers a seamless experience to manage everything in one place, providing unified management and billing.


Azure Virtual Network (VNet)

An Azure Virtual Network (VNet) is a representation of your own network in the cloud. It is a logical isolation of the Azure cloud dedicated to your subscription.

1.	VNet as a Representation of Your Network in the Cloud
•	Azure Virtual Network (VNet) allows you to create an isolated, private network within the Azure cloud. It is the foundational network service for managing and connecting resources, such as Virtual Machines (VMs), Databases, and other services, within Azure
•	A VNet is analogous to a traditional on-premises network but fully managed by Azure. It allows you to securely extend your on-premises network into the cloud and manage traffic between your cloud resources.

2.	Fundamental Building Block for Private Networks
•	A VNet serves as the central platform for deploying Infrastructure as a Service (IaaS) component like VMs and Platform as a Service (PaaS) components like web apps, databases, and other Azure services. Without VNets, you would not have a private network on which to connect these resources.

3.	Region and Subscription-Based
•	A VNet is specific to an Azure region and belongs to a single Azure subscription. Each subscription can contain multiple VNets, but each VNet can only exist in one region. This is important for planning both regional availability and network latency.

 
4.	IP Addressing
•	When you create a VNet, you define a CIDR block (Classless Inter-Domain Routing) to allocate a range of private IP addresses for your network. This address space is used to assign IPs to your virtual machines, load balancers, and other resources in the VNet.
o	Azure supports up to 4096 IP addresses in a single VNet, though smaller subnets can be created within this range for better resource management.
o	It’s essential to plan the IP address space carefully to avoid conflicts with other VNets, on-premises networks, or other Azure services.

Subnet
•	A subnet is a range of IP addresses within a VNet. You can divide a VNet into multiple subnets based on your design and network architecture.
•	Subnets help segregate different types of resources for organization, security, and traffic management purposes.
•	Resources deployed in different subnets within a VNet can communicate with each other automatically, without requiring any additional configuration, unless network security controls (such as Network Security Groups - NSGs) or custom routing (using route tables) are applied.

           Subnet Communication
•	VMs (and other resources) deployed in the same subnet or across different subnets in the same VNet can communicate without any extra configuration.
•	For example, if you have a VNet with multiple subnets (e.g., "web", "application", and "database"), the VMs in each subnet can directly communicate, assuming there are no restrictions (such as NSG rules) in place.

Subnet Configuration: Route Tables and NSGs
•	You can associate Route Tables and Network Security Groups (NSGs) with individual subnets:
Route Tables: These define how traffic is directed within the VNet or between VNets and external resources.
NSGs:  You can apply NSGs to subnets (or individual network interfaces) to control inbound and outbound traffic based on rules.





IP Addressing within Subnets
•	When defining a subnet within a VNet, certain IP addresses are reserved for Azure’s internal use and cannot be assigned to VMs or other resources:

First 3 IP addresses: These are reserved for network-related purposes, and they are:
	Network address (x.x.x.0): Identifies the subnet itself.
	Default gateway (x.x.x.1): This IP address is reserved for Azure’s default gateway to route traffic within the VNet and to external networks.
	Reserved for Azure DNS (x.x.x.2, x.x.x.3): These IP addresses are reserved for Azure's internal DNS services, which allow the resources in the VNet to resolve domain names.
	Last IP address: (x.x.x.255) is reserved as the broadcast address. It is used to send broadcast messages to all devices in the subnet (although, in Azure, broadcast traffic is typically restricted).

5.	Non-Overlapping IP Address Ranges
•	When creating a VNet, the CIDR blocks you choose should not overlap with other VNets or your on-premises network. This is crucial for routing traffic correctly between networks.
•	If there is an overlap, communication between the VNets or the VNet and on-premises networks will not work correctly, and you will encounter routing issues.

6.	Traffic Control
•	You can control how traffic flows between different subnets, VNets, and on-premises networks through route tables and custom network security policies.


Benefits of Using Azure VNets:
•	Isolation. Vnets are completely isolated from one another. That allow you to create disjoint network from development, testing, production that use the same CIDR address book 
•	Access to the Public internet All IaaS and PaaS role instances in a Vnet can access the public internet by default. You can control access by using by network security group (NSG)
•	Access to VMs with the Vnet. PaaS role instance and IaaS VMs can be launched in the same virtual network and they can connect each other using private IP address if they are in different subnets without need to configure a getaway or use public IP address 
•	Name resolution Azure provide the internal name resolution for IaaS VMs and PaaS role instance deployed in your Vnet you can also deploy your own DNS servers and configure the Vnet use them.
•	Security traffic entering and existing the virtual machines and PaaS role instance in a Vnet can be controlling use Network Security Group
•	Connectivity Vnets can be connected to each other, and even to your on-premises datacentre by using Site-to-Site VPN connection or Express route connection.  

Network Security Groups (NSG)
•	NSGs are composed of a set of security rules.
•	Each rule defines whether inbound (incoming) or outbound traffic is allowed or denied.
•	NSGs play a key role in managing the security and traffic flow between VMs and subnets in cloud environments like Azure, acting as virtual firewalls.

 


Traffic Inspection:
•	NSGs inspect incoming and outgoing traffic at the network level.
•	They work like a virtual firewall to control the flow of traffic between virtual machines (VMs) and subnet
Rules & Priorities:
•	NSG rules can either allow or deny traffic based on the defined criteria.
•	Priority determines rule evaluation order: lower numerical values have higher priority. For instance, a rule with priority 100 is evaluated before a rule with priority 200.
•	The last rule (with the lowest priority) is the default deny rule, which blocks any traffic not explicitly allowed by earlier rules.
•	For example, if there's a rule allowing traffic from a specific source IP address on a certain port (with a high priority), and another rule denying all traffic on the same port (with a lower priority), the traffic would be allowed because the first rule takes precedence due to the higher priority number.
Association:
•	A single NSG can be associated with multiple network interfaces (NICs) or subnets.
•	However, each NIC or subnet can only be associated with one NSG at a time.


Azure Firewall
•	Azure Firewall is a managed, cloud-based network security service that protects your Azure Virtual Network resources. 
•	It is a fully stateful firewall as a service with built-in high availability and unrestricted cloud scalability.
Fully Managed, Cloud-Based Solution:
•	Azure Firewall is a fully stateful firewall service, meaning it maintains the state of active connections and is able to track traffic flows.
•	It is entirely managed and runs as a cloud service, meaning Microsoft handles its maintenance, updates, and scaling.
Comparison with Network Security Groups (NSGs):
•	NSGs (Network Security Groups) provide basic traffic filtering based on IP ranges and protocols and are implemented using the Virtual Filtering Platform (VFP).
•	Unlike NSGs, Azure Firewall is a more comprehensive solution with advanced features like stateful inspection, centralized management, and integration with other Azure services. NSGs are typically used in conjunction with Azure Firewall to further refine traffic control within subnets.


Application Security Groups (ASGs):
Application Security Groups helps to manage the security of the Azure Virtual Machines by grouping them according the applications that runs on them. It is a feature that allows the application-centric use of Network Security Groups.
Application-Centric Security:
•	ASGs allow you to group VMs based on the applications they run, rather than managing security rules based on IP addresses. This approach simplifies security management, particularly in dynamic environments where VMs are frequently added or removed.
•	By grouping VMs based on their roles (e.g., web servers, database servers), security rules can be applied according to the application instead of managing complex IP-based access control lists (ACLs).
Virtual Applications 
Azure network virtual appliance is used in the Azure application to enhance high availability. It is used as an advanced level of control over traffic flows, such as when building a demilitarized zone (DMZ) in the cloud.
Many virtual appliances are available in the azure marketplace
License can be based on: -
	Bring your own license 
	Hourly billing
Essentially a VM pre-configured software and configuration to perform a certain set of functionalities
Common examples include firewall and load balancer

