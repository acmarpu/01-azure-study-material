# Azure Storage

Azure storage provides storage that is highly available, secure, durable, scalable and redundant.

**Azure Storage Options**
**General Purpose V2 (GPv2)**
*Features:*
*	Supports a variety of storage services, including blobs, files, queues, and tables.
*	Supports blob-level tiering, allowing you to store data in different tiers (hot, cool, archive) based on access patterns.
*	Enhanced features such as higher scalability, storage events, and archive storage.
*	Allows block blob tier selection (hot, cool, and archive) either at the account level or blob level.
*	Supports archive storage, ideal for rarely accessed data, and higher scalability for large datasets.
*	Upgrade path: A General Purpose V1 (GPv1) account can be upgraded to GPv2 via portal, CLI, or PowerShell.

**General Purpose V1 (GPv1)**
*Features:*
*	Provides access to all Azure storage services (blobs, files, queues, tables).
*	May not have the latest features or pricing optimizations.
*	Limitations: Does not support cool and archive storage tiers

**Azure Storage Pricing Model*
Azure Storage uses a pricing model based on multiple factors, such as storage tier, data access frequency, and geo-replication configuration.

**1. Storage Costs**
*Tier-Based Pricing:*
*	The cost of storing data depends on the storage tier: hot, cool, and archive.
*	Storage in the hot tier costs more per gigabyte compared to the cool and archive tiers.
*	The cool and archive tiers provide cheaper storage but are designed for data that is infrequently or rarely accessed.

**2. Data Access Costs**
*	Hot Tier: Low data access cost since it is designed for frequently accessed data.
*	Cool and Archive Tiers: Higher data access costs for reading data from these tiers. These costs apply to reads from the cool and archive tiers and are typically higher than for the hot tier.
*	Access Patterns: It is essential to evaluate access patterns when choosing between tiers to optimize both storage and access costs.

**3. Transaction Costs**
* There is a per-transaction charge for all storage tiers, meaning the more operations you perform (e.g., reading, writing, deleting), the higher the costs.

**4. Geo-Replication Data Transfer Costs**
* Geo-replication: If your storage account is configured with Geo-redundant storage (GRS) or Read-Access Geo-Redundant Storage (RA-GRS), there are data transfer costs for replicating data across regions.
* The per-gigabyte charge applies for the replication of data to other regions.



**Azure Storage: Security Features**
Azure Storage provides a range of security capabilities to ensure that your data remains secure, both at rest and in transit. Below are the key security features available for Azure Storage:

* **1. Role-Based Access Control (RBAC) and Azure Active Directory (AAD) Integration**
RBAC allows administrators to assign specific roles to users, groups, and applications to define who can access resources and what actions they can perform. This is a granular level of control over who can access and manage your Azure Storage resources.
Azure Active Directory (AAD) is integrated with Azure Storage, enabling identity-based access control. This ensures that access to storage is tied to users and service principals with permissions granted through AAD.

* **2. Data Encryption in Transit**
Client-Side Encryption: Azure Storage supports client-side encryption, where data is encrypted before it is sent to the cloud and only decrypted when it is accessed by authorized users or applications.
HTTPS: Data can be secured in transit between the application and Azure using HTTPS, ensuring that data transferred over the network is encrypted during transmission.
SMB 3.0: When using Azure Files, SMB 3.0 (Server Message Block) provides encrypted communication for file shares. This protocol offers encryption and integrity for data in transit, ensuring secure file access.

* **vv3. Storage Service Encryption (SSE)**
SSE is a built-in encryption mechanism for data at rest in Azure Storage. Data is automatically encrypted when it is written to the storage account and remains encrypted while stored in Azure.
Server-Side Encryption (SSE): This encryption is managed by Azure, and it occurs automatically when data is stored in the platform. Users do not need to manually configure this.
Encryption keys used by SSE can be managed by Microsoft (default) or by the user through Azure Key Vault for additional control over encryption key management.

* **4. Azure Disk Encryption (ADE)**
Azure Disk Encryption (ADE) provides encryption for OS disks and data disks used by virtual machines (VMs).
Encryption at the OS level: ADE is more focused on encrypting disks associated with VMs and provides encryption for the operating system and data volumes.
ADE uses BitLocker (for Windows) and dm-crypt (for Linux) to secure data on disks and ensures that the data is encrypted both at rest and during disk snapshots.

* **5. Shared Access Signatures (SAS)**
Shared Access Signatures (SAS) allow delegated access to specific storage resources, such as blobs or files, without providing full access to the storage account.
A SAS token is generated with specific permissions (read, write, delete, etc.) and an expiration time, allowing controlled and temporary access to data.
This is useful for scenarios where you want to grant external applications or users access to storage resources without exposing your account keys or providing broad permissions.



# Azure Disks
Azure Disks are an essential component in managing storage for virtual machines (VMs) within Microsoft Azure. Below is a breakdown of the key concepts mentioned:

**Key Concepts of Azure Disks:**
* **1.	Data Disks:**
*	Data disks are used for storing application data, logs, or other information that needs to persist beyond the VM's lifespan.
*	Each data disk is represented as a Virtual Hard Disk (VHD), which can be attached to a virtual machine.
*	Capacity: A standard data disk has a maximum capacity of 4,095 GB. However, with managed disks, the maximum capacity is significantly larger at 32,767 GiB.
*	The storage type (e.g., SSD or HDD) you can use for data disks depends on the VM size and the specific storage account configuration.

* **2.	Managed vs. Unmanaged Disks:**
*	Managed disks are Azure-managed resources, where Azure handles the storage management, including replication and availability. These disks are typically recommended for simplicity and reliability.
*	Unmanaged disks are VHDs stored in your Azure storage account, where you need to manage aspects like replication, availability, and redundancy yourself.

* **3.	Operating System (OS) Disk:**
*	When you create a virtual machine (VM) from an image, Azure automatically creates an operating system disk for the VM.
*	If the image you use for creating the VM includes predefined data disks, those data disks are also created alongside the OS disk.
*	Otherwise, data disks can be added to the VM after creation.

* **4.	Attaching Data Disks:**
*	Data disks can be attached to a VM at any time after the VM is created.
*	You can attach an existing VHD, either from your storage account or a custom VHD you've uploaded, or you can create a new empty VHD that Azure will generate for you.
*	When a data disk is attached to a VM, Azure places a lease on the VHD file to prevent it from being deleted or modified while still in use by the VM.

* **5.	Virtual Machine (VM) Size and Disk Limitations:**
*	The size of the VM (e.g., Standard DS1, Standard D4, etc.) dictates how many data disks you can attach. Larger VMs can support more data disks and offer better performance for heavy workloads.

* **6.	SCSI Drives and Disk Labeling:**
*	Data disks are registered as SCSI drives (Small Computer System Interface), and you can assign a letter to each data disk (such as D:, E:, etc.) to easily reference and manage them within the VM’s operating system.



**Unmanaged Disks**
* Unmanaged disks are the traditional type of disks that have been used by VMs. With these disks, you create your own storage account and specify that storage account when you create the disk. Make sure you don't put too many disks in the same storage account, because you could exceed the scalability targets of the storage account (20,000 IOPS, for example), resulting in the VMs being throttled. With unmanaged disks, you must figure out how to maximize the use of one or more storage accounts to get the best performance out of your VMs.

**Managed Disks**
* Managed Disks handles the storage account creation/management in the background for you and ensures that you do not have to worry about the scalability limits of the storage account. You simply specify the disk size and the performance tier (Standard/Premium), and Azure creates and manages the disk for you. As you add disks or scale the VM up and down, you don't have to worry about the storage being used.


**Standard HDD disks**
* Standard HDD disks are backed by HDDs and deliver cost-effective storage. Standard HDD storage can be replicated locally in one datacenter or be geo-redundant with primary and secondary data centers. For more information about storage replication, see Azure Storage replication.

**Standard SSD disks**
* Standard SSD disks are designed to address the same kind of workloads as Standard HDD disks, but offer more consistent performance and reliability than HDD. Standard SSD disks combine elements of Premium SSD disks and Standard HDD disks to form a cost-effective solution best suited for applications like web servers that do not need high IOPS on disks. Where available, Standard SSD disks are the recommended deployment option for most workloads. Standard SSD disks are available as Managed Disks in all regions but are currently only available with the locally redundant storage (LRS) resiliency type

* **Premium SSD disks**
Azure Premium Storage delivers high-performance, low-latency disk support for virtual machines (VMs) with input/output (I/O)-intensive workloads. VM disks that use Premium Storage store data on solid-state drives (SSDs). To take advantage of the speed and performance of premium storage disks, you can migrate existing VM disks to Premium Storage


* **Azure Storage: Tiers**
Azure Storage offers different storage tiers designed to optimize cost and performance based on how frequently data is accessed. Here's a breakdown of the available tiers and their specific use cases:

* **1. Premium Storage (Preview)**
*	Use Case: Premium storage is designed for workloads that require high-performance storage. It is typically used for applications that need low-latency and high-throughput performance, such as databases or transactional workloads.
*	Performance: Provides high-performance hardware (based on SSDs) to support demanding workloads.
*	Access Frequency: Best suited for frequently accessed data that needs fast read/write operations.
*	Status: Currently in preview, meaning it might still be evolving or unavailable in some regions.

* **2. Hot Storage**
*	Use Case: Hot storage is optimized for storing data that is accessed frequently or needs to be readily available for use. Common examples include data used in applications, websites, and active data processing.
*	Performance: Offers lower latency for read/write operations and is ideal for scenarios where performance is a key requirement.
*	Access Frequency: Best for frequent access scenarios, where data needs to be accessed regularly.
*	Cost: The cost of storage in the hot tier is higher compared to cool and archive storage due to its optimized performance for frequent access.

* **3. Cool Storage**
*	Use Case: Cool storage is designed for data that is infrequently accessed but still needs to be available for occasional use. This is suitable for data that you don’t access often but still want to retain for compliance, backup, or archival purposes.
*	Access Frequency: This tier is best for data that is infrequently accessed and intended for storage for at least 30 days.
*	Cost: Cool storage is more cost-effective than hot storage, offering lower prices in exchange for slower access times and less frequent use. However, there are retrieval costs and higher write operations costs.

* **4. Archive Storage**
*	Use Case: Archive storage is optimized for long-term storage of data that is rarely accessed, such as historical data, old backups, or compliance-related data that must be retained for extended periods.
*	Access Frequency: Archive is best suited for data that is rarely accessed and stored for a minimum of 180 days.
*	Performance: This tier offers high latency and is designed for scenarios where access to data can take hours or even days, making it unsuitable for real-time or frequent data retrieval.
*	Cost: Archive storage is the most cost-effective option for long-term storage. However, it incurs higher retrieval costs, and latency is much higher compared to other tiers, making it suitable only for data that doesn’t need to be accessed frequently.



**Azure Storage Replication Options**
* Azure provides various replication options to ensure that your data is available, durable, and fault-tolerant, depending on your business needs, cost considerations, and level of redundancy required. The replication options fall into several categories, each with different levels of availability and resilience.
Here is a detailed breakdown of the different Azure storage replication types:

**Locally Redundant Storage (LRS)**
*	LRS synchronously replicates data to three separate disks within a single Azure data center in the primary region. This ensures data durability and protection from local hardware failures within the same data center.
*	If one disk or server fails, the data can still be retrieved from the other two replicas in the same data center.

*Key Features:*
*	Availability: Offers moderate availability within a single region.
*	Cost: Lower-cost option since replication is contained within one data center.
*	Limitations: Does not protect against data center failures or regional outages.

*Use Cases:*
*	Suitable for scenarios where data is not mission-critical or where geographic redundancy is not required.
*	Often used for non-critical data storage or development/testing environments.

*Zone Redundant Storage (ZRS)*
*	ZRS replicates your data across three Azure Availability Zones within a single region. Each availability zone is a separate data center with independent power, networking, and cooling.
*	ZRS ensures that data is protected not just from disk failures, but also from hardware failures in individual data centers. This provides higher resiliency and availability.
Key Features:
*	Availability: Offers higher resiliency and availability compared to LRS because it replicates data across multiple data centers in the same region.
*	Cost: Higher cost than LRS due to the increased resilience.
*	Protection: More robust against data center outages but still does not provide cross-region redundancy.

*Use Cases:*
*	Suitable for scenarios where high availability is needed but geographic redundancy is not required.
*	Ideal for applications that demand higher uptime and resilience within a specific region.

**Geo-Redundant Storage (GRS)**
*	GRS provides additional redundancy by storing data in two geographically separate regions. It replicates data three times in the primary region (like LRS) and then copies the data to a secondary, paired Azure region.
*	This ensures data is highly durable even if there’s a regional outage.
*	In the event of a failure in the primary region, Azure can failover to the secondary region.

*Key Features:*
*	Availability: Provides a high level of data durability with disaster recovery across regions.
*	Cost: Higher cost than LRS or ZRS due to the cross-region replication.
*	Protection: Offers resilience against regional failures (e.g., data center or region-wide outages).

Use Cases:
*	Best suited for critical applications where downtime is not acceptable, such as financial transactions or healthcare data.
*	Used in disaster recovery scenarios where data needs to be available even in the case of regional failures.

**Read-Access Geo-Redundant Storage (RA-GRS)**
*	RA-GRS is essentially the same as GRS, but with one major difference: it allows read access to data from the secondary region.
*	In case of a failure in the primary region, while the data is being replicated and restored, RA-GRS allows you to read data from the secondary region, thus providing more availability during an outage.
*	Write operations are still only possible in the primary region, but read operations are allowed from the secondary region at all times.

*Key Features:*
*	Availability: Provides read-only access to data even if the primary region is down.
*	Cost: More expensive than GRS due to the added read functionality in the secondary region.
*	Protection: Provides both high availability and resilience, allowing continued access to data even during a primary region failure.

*Use Cases:*
*	Ideal for applications that need continuous read access to data during region-wide outages.
*	Suitable for globally distributed applications that cannot afford read access interruptions but can tolerate write delays.

**Object Replication for Block Blob Storage**

*	Object Replication is a feature available for Block Blob storage that allows you to replicate data between two storage accounts, either in the same or different regions.
*	You define a source account and a destination account. Azure replicates the data in the background, ensuring that the blobs in the source account are copied to the destination account.
*	Object replication is used only for Block Blobs, not for other types of blobs like Page Blobs or Append Blobs.
Key Features:
*	Granular Replication: Replicates only block blobs between source and target accounts, making it ideal for scenarios where you need to copy specific data (e.g., media files, backups).
*	Consistency: Supports different consistency models, allowing you to choose whether replication is done asynchronously or synchronously based on your use case.
*	Cross-region: Allows replication across regions, offering additional redundancy in case of regional outages.
Use Cases:
*	Ideal for applications that require cross-region replication of block blob data (e.g., media file distribution, large-scale backup solutions).
*	Suitable for disaster recovery or backup strategies where replicating block blob data across regions is important.


# Azure Storage Containers
*What is an Azure Storage Container?*
*A container is a fundamental concept within Azure Blob Storage. It acts as a logical grouping for a set of blobs (files) in Azure Storage. Containers are used to organize blobs and are the first level of storage within a storage account. You can think of containers as similar to folders on your local file system.

**Key Features of Containers:**
*	Grouping Blobs: All blobs in Azure Storage must be stored in a container. A container can contain an unlimited number of blobs.
*	Names: Containers must have globally unique names across all of Azure. The name must also conform to specific naming rules, such as using lowercase letters, numbers, and hyphens.
*	Storage Account: A single Azure Storage account can contain an unlimited number of containers.
*	Permissions: Containers can be set with different access levels:
* Private: Only the account owner can access the blobs in the container.
* Blob: Blobs can be publicly accessed, but container and account metadata remain private.
* Container: Both the blobs and the container metadata can be accessed publicly.

*Accessing: https://<storage_account_name>.blob.core.windows.net/<container_name>*

**Azure File System (Azure Files)**
*What is Azure Files?*
* Azure File Storage offers fully managed, cloud-based file shares that support the Server Message Block (SMB) protocol. It allows users to store files that can be accessed by cloud-based or on-premises applications, supporting common file system operations.

*Key Features of Azure Files:*
*	SMB Protocol Support: You can mount Azure File shares on Windows, Linux, and macOS systems via the SMB protocol. This makes it a good replacement for traditional on-premises file servers and network-attached storage (NAS).
*	Managed Shares: Azure Files provides fully managed file shares, meaning that Microsoft handles infrastructure management, such as scaling and redundancy.
*	Capacity: Each file share in Azure can scale up to 5 TiB (terabytes) of data, with a total storage capacity of 500 TiB per storage account.
*	Access Control: You can control access to Azure Files using Azure Active Directory (Azure AD) authentication or Shared Access Signatures (SAS).
*	Snapshots: Azure File shares support snapshots, allowing you to capture point-in-time versions of your file shares for backup and disaster recovery purposes

*Accessing: https://<storage_account_name>.file.core.windows.net/<file_share_name>/<file_path>*


**Azure Queue Storage**
*What is Azure Queue Storage?*
Azure Queue Storage is a service used for storing large numbers of messages that can be accessed from anywhere globally via authenticated HTTP or HTTPS requests. It is primarily used to implement messaging queues for building asynchronous workflows, decoupling components, and ensuring scalable, durable systems.

**Key Features of Azure Queue Storage:**
*	Message Size: A single queue message can be up to 64 KB in size.
*	Queue Capacity: A single queue can store millions of messages, subject to the total capacity limits of the storage account.
*	Durability: Queue messages are stored durably, and the system guarantees that the messages are not lost.
*	Visibility Timeout: Messages that are read from the queue become invisible to other consumers for a specified period (visibility timeout), ensuring that only one consumer processes a message at a time.
*	Peeking: You can peek into the queue without removing the message to inspect its contents.
*	Polling and Long-Polling: Consumers can retrieve messages using long-polling for better efficiency in real-time systems.

**Advantages:**
*	Decoupling: Queue storage allows you to decouple different parts of your application, improving scalability and reliability.
*	Scalability: Queue Storage can scale to handle millions of messages.
*	Durability: Ensures message persistence, making it ideal for reliable message-based communication.
*	Rich Libraries: Azure provides rich client libraries for languages such as Java, C#, Python, PHP, etc.
Use Cases for Azure Queue Storage:
*	Background task processing: For asynchronous workflows like image processing or email notifications.
*	Distributed systems: Enabling communication between decoupled components in microservices architectures.
*	Buffering requests: Storing requests for processing at a later time, such as in event-driven architectures.

*Accessing: https://<storage_account_name>.queue.core.windows.net/<queue_name>*


**Azure Table Storage**
*What is Azure Table Storage*

* Azure Table Storage is a NoSQL key-value store used for storing structured data in the cloud. It provides a highly scalable and cost-effective solution for storing large amounts of semi-structured data, such as application logs, sensor data, or other key-value pairs.

*Key Features of Azure Table Storage:*
*	Schema-less: Table Storage is schema-less, allowing you to store different types of data with flexible structures.
*	Entities: Data is organized in entities, which consist of a partition key and a row key. These keys make data retrieval very fast and efficient.
*	Partition Key: A unique identifier for the partition.
*	Row Key: A unique identifier within the partition.
*	Scalability: Table Storage is highly scalable and can handle millions of entities across large tables.
*	Cost-Effective: Compared to relational databases, Table Storage is cheaper for storing large amounts of data with simple access patterns.
*	Data Model: Table Storage uses a key-value store, with each entity representing a single row, and each property of the entity representing a column in the table.
Accessing Data in Table Storage:
To interact with Table Storage, you use a combination of Partition Key and Row Key to access data. A single partition can contain up to 2^64 entities, providing flexibility in storing large datasets.

