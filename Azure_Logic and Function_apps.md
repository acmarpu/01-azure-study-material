# Azure Logic Apps
*	Azure Logic Apps is a cloud-based service that helps organizations automate workflows, business processes, and integrate various applications and data systems without managing any infrastructure. It is designed to streamline app integration, data workflows, system interactions, enterprise application integration (EAI), and B2B (business-to-business) communication.
*	By using the visual designer and selecting from prebuilt operations, you can quickly build a workflow that integrates and manages your apps, data, services, and systems.
*	Schedule and send email notifications using Office 365 when a specific event happens, for example, a new file is uploaded.

**Key Features:**
*	*App and Data Integration:* Logic Apps allows users to design scalable solutions that can automate tasks across different applications and data systems, whether they're in the cloud or on-premises.
*	**Business Process Automation:** Automates and orchestrates business processes to improve efficiency and reduce manual effort.
*	**Connectors:** It offers a growing collection of ready-to-use connectors, including:
- Dynamics 365
- Salesforce
- BizTalk
- SAP
- Oracle Database
- And many others, enabling seamless integration with popular business applications.
*	**Deployment Flexibility:** You can deploy your Logic Apps on the cloud, on-premises, or in a hybrid environment.
Serverless Architecture:
*	**No Server Management:** Logic Apps operates on a serverless model, meaning users don't need to worry about managing infrastructure. The platform automatically handles scaling and provisioning of resources.
*	**Automatic Scaling:** The execution engine scales the application dynamically based on the workload, ensuring high availability and performance without any manual intervention.
*	**Parallel Data Processing:** Logic Apps can process large datasets concurrently, allowing for high throughput and efficiency.
*	**Pay-as-You-Go Pricing:** Users are charged only for the resources and services they actually use, offering cost-effective scalability.

**Hosting Models:**
*	**Serverless Hosting:** Logic Apps is fully serverless, meaning there is no need to maintain or configure servers. The service automatically handles scaling and execution.
*	**Self-Hosted Hosting:** You also have the option to host the Logic App components on your premises or in a hybrid configuration depending on your needs.

**Logic app resources**
*	**A Consumption logic app** resource that supports a single workflow, which is hosted and run in global multitenant Azure Logic Apps
*	**A Standard logic app** resource that supports multiple workflows, which are hosted and run in single-tenant Azure Logic App

**The key constructs of Azure Logic Apps are:**

# Workflow:	
A workflow in Azure Logic Apps is a series of operations that automate a task, business process, or workload. It defines a sequence of steps to be executed, typically involving both a trigger (which starts the workflow) and actions (which define what happens after the trigger).

**Trigger**
* The first operation in any workflow that specifies the criteria to meet before running any subsequent operations in that workflow. For example, a trigger event might be getting an email in your inbox or detecting a new file in a storage account.

**Definition:** A trigger is the starting point of a workflow. It defines the event or condition that causes the workflow to begin.


**Example Trigger Events:**
*	When a new file is uploaded to a cloud storage service (e.g., OneDrive, SharePoint, etc.).
*	When an HTTP request is received.
*	When a new record is created in a database.
*	A scheduled time, like every hour or daily.

**Trigger Example:** A common trigger could be "When a new email arrives in Outlook," which starts the workflow whenever an email is received in the specified inbox.

**Polling triggers**
*	checking against the queue and when new message arrives in the queue

**Push triggers**
*	where you create a subscription against an endpoint and endpoint then calls you back if something interesting happens, 
*	so rather than having to go check the queue constantly when new message arives the queue is going to send you a push notofication that will indeed trigger that logic app instance

**Recurrence trigger**
*	which is fired based on a defined schedule.so you can set a future date and time for firing the trigger and based on a frequency you can specify the times and days.

**Manual triggers**
*	which as the name suggests are invoked explicitly by calling an HTTP endpoint that is exposed by your Logic App.


**Action**
*	Each subsequent operation that follows the trigger in the workflow.
*	Definition: After a trigger occurs, one or more actions are performed. Actions are the tasks or operations that follow the trigger. These actions can include things like calling an API, sending an email, processing data, or integrating with other systems.

*types of Actions:*

* **HTTP Requests:** Sending or receiving data via HTTP requests.
* **Data Manipulation:** For example, formatting dates, transforming data, or converting formats.
* **Service Interactions:** Interacting with external services like databases, CRMs, or file storage services (e.g., adding records to a database, sending messages via Slack, etc.).

**Benefits of Workflows:**
*	**Automation of Repetitive Tasks:** Workflows help automate repetitive processes, reducing manual effort and errors.
*	**Integration Across Systems:** By connecting multiple systems (both cloud-based and on-premises), workflows enable seamless integration and data exchange.
*	I**mproved Efficiency: Workflows** streamline business operations by ensuring tasks are carried out consistently and quickly.
*	**Scalability:** Logic Apps workflows can be scaled up or down easily, depending on the requirements of the business process.

# Connectors 
in Azure Logic Apps play a crucial role in enabling the integration of your workflows with a variety of services and applications, both within Azure and outside it. They serve as the bridge between your logic app and other services, systems, or events, enabling you to automate tasks, process data, and trigger actions across different platforms.

**Key Features of Connectors:**
*	**Trigger and Action-Based:** Connectors are implemented through *triggers and actions.* A trigger initiates the workflow based on an event, while an action performs specific operations in response to the workflow's execution.
*	**Cloud and On-Premises Support:** Connectors extend the capabilities of Logic Apps to interact with apps running in other clouds or on-premises, making it highly flexible for hybrid environments.

**Types of Connectors:**
**Built-In Connectors:**
*	**Definition:** These connectors are directly built into your Logic App service and are automatically deployed along with your app. They are included as part of the Logic Apps service, so no separate setup or management is required.
*	**Example:** Common built-in connectors include:

* **HTTP Connector:** Allows integration with any service that can respond to HTTP requests.
* **Recurrence Trigger:** A built-in trigger for scheduling workflows to run at specified times or intervals.
* **Expression Functions:** Used for manipulating and transforming data inside your workflow.

**Benefits:**
*	No additional deployment or management required.
*	They are tightly integrated into the Logic App service, ensuring optimal performance.
Managed Connectors:
*	Definition: Managed connectors are created, deployed, and maintained by Microsoft. These connectors allow integration with third-party services and systems and are fully managed by Azure, ensuring consistent updates, security patches, and scalability.
*	Example: Managed connectors include:
*	**Salesforce:** For integrating with the Salesforce CRM system.
*   **Dynamics 365:** For connecting to Microsoft Dynamics 365 applications.
*	**SQL Server:** For integrating with SQL Server databases.
*   **Office 365:** To interact with Office 365 services like SharePoint, Outlook, and OneDrive.
*   **Dropbox:** To integrate with Dropbox file storage.
*   **SAP:** For connecting with SAP systems.

**Benefits:**
* These connectors are pre-configured and optimized by Microsoft for seamless integration.
* They are regularly updated and maintained by Microsoft, ensuring compatibility with evolving services and systems.
* Microsoft handles authentication, API versioning, and error management, making them easier to use.



# Demo Step 1: Create the Logic App and Set Up Email Trigger
**1.	Create Logic App:**
*	In the Azure portal, go to Create a resource and search for Logic App.
*	Select Logic App and click Create.
*	Choose the appropriate Subscription and Resource Group.
*	Provide a Name for your Logic App.
*	Choose the Region where you want the Logic App to be created.
*	Select Consumption for pricing tier and then click Review + Create to validate and create the Logic App.

**2.	Configure Trigger:**
*	Once the Logic App is created, go to the Logic App Designer.
*	Select Blank Logic App.
*	Search for "When a new email arrives" trigger.
*	Choose Office 365 Outlook as the connector (make sure to authenticate your Office 365 account).
*	Select the trigger When a new email arrives. This will be used to capture incoming emails.

# Demo Step 2: Add Condition to Check the Email Subject
**3.	Add Condition Step:**
*	Click New Step to add another action.
*	Search for Control and choose the Condition action.

*1.	Configure Condition:*
*	In the Condition action, click on Choose a value and select Dynamic content.
*	From the list of dynamic content, select Subject. This is the subject of the incoming email.
*	Change the condition to "Contains".
*	Type #Support in the condition box. This will check if the email's subject contains the phrase "#Support".

# Demo Step 3: Add Action to Post Message to Azure Storage Queue
**4.	Add Action for Queue Message:**
*	Under the If yes branch of the condition (i.e., when the subject contains "#Support"), click Add an Action.
*	Search for Azure Storage Queue and select the Azure Storage Queue connector.
*	Choose the "Put a message on a queue" action. This will send the email message to the specified Azure Storage Queue.

*1.	Set Up the Queue Connection:*

*	If it's the first time using the Azure Storage Queue connector, you'll be prompted to Create a connection to your Azure Storage account.
*	Provide the necessary connection details (like storage account name and key) to authenticate.

*2.	Configure Queue Name and Message:*

*	Once the connection is set, choose the appropriate Queue Name (e.g., "Support").
*	For the Message field, click Dynamic content and select From (this represents the email sender's address).
*	You can include additional dynamic content like Subject, Body, etc., in the message.

# Demo Step 4: Finalizing and Testing the Logic App

*5.	Save the Logic App:*
*	After setting up the trigger, condition, and action, save the Logic App by clicking the Save button at the top.

*1.	Test the Logic App:*
*	To test the Logic App, send an email with the subject containing #Support to the specified email address.
*	If the subject contains "#Support", the workflow will execute and post a message to the Support queue in Azure Storage.



# Azure Functions?
Azure Functions is a serverless compute service provided by Microsoft Azure that allows you to run small, event-driven pieces of code (called "functions") without worrying about the underlying infrastructure. You can write and deploy code that automatically responds to various triggers such as HTTP requests, timer-based schedules, or events like changes in a database or file system.
In a serverless model, you don't have to worry about provisioning or managing servers. Azure Functions takes care of scaling your code based on demand, and you only pay for the actual execution time.
Key Features of Azure Functions:

**1.	Serverless Applications:**
*	Azure Functions allows you to focus on writing code without having to manage or provision servers. This makes it ideal for small, event-driven tasks and microservices.

**2.	Choice of Programming Language:*
*	Azure Functions supports a variety of languages, allowing developers to work with the language they are most comfortable with or best suits the application:
*	C#
*	Java
*	JavaScript
*	Python
*	PowerShell

**3.	Pay-Per-Use Pricing Model:**
*	You are only charged for the execution time and resources consumed by your function, which means cost efficiency, especially for low-traffic scenarios. There's no need to pay for idle time.

**4.	Bring Your Own Dependencies:**
*	You can bring and use external libraries or dependencies that are required for your function. Azure Functions supports custom libraries and packages for the languages it supports, allowing greater flexibility.

**5.	Integrated Security:**
*	Azure Functions integrates easily with Azure Active Directory (AAD), Role-Based Access Control (RBAC), and other security mechanisms to secure the functions and manage authentication.

**6.	Flexible Development:**
*	You can develop and test functions locally, then deploy them to Azure with tools like Visual Studio, Visual Studio Code, or Azure CLI. Azure Functions also supports continuous integration and delivery (CI/CD).

# What Can You Do with Azure Functions?
Azure Functions can be used for a wide variety of tasks, especially where event-driven architecture is useful. Some common use cases include:

**1.	Processing Bulk Data:**
*	Azure Functions can be used to process large volumes of data, such as from logs, files, or streams of data. This is useful for scenarios like data transformations or batch processing.

**2.	Integrating Systems:**
*	You can integrate with other systems by creating functions that trigger based on events in other services. For example, you might trigger a function when a new message is placed on a queue or when an event occurs in another application.

**3.	Working with IoT:**
*	Azure Functions can interact with IoT devices, processing data from sensors or devices and responding to changes. This is particularly useful for applications like real-time monitoring or automating device interactions.

**4.	Building APIs and Microservices:**
*	Azure Functions is well-suited for creating small, stateless APIs or microservices that respond to HTTP requests. This is ideal for building RESTful APIs that scale automatically as demand increases.

**Triggers for Azure Functions**
Azure Functions can be triggered by a wide variety of events. Some common triggers include:
* **1.	HTTP Requests:**
*	Functions can be triggered by HTTP requests, making them ideal for creating REST APIs, webhooks, or other web-based services.

* **2.	Schedule Timer:**
*	Functions can be scheduled to run at specific intervals using time-based triggers. For example, you can set up a function to run daily, weekly, or at a custom time interval.

* **3.	Document Changes in Azure Cosmos DB:**
*	Azure Functions can be triggered when documents are added or modified in Azure Cosmos DB, enabling real-time data processing and synchronization across systems.

* **4.	Queue Messages (Azure Storage Queues):**
*	Functions can be triggered by messages placed in Azure Storage Queues, making them ideal for event-driven architectures where tasks are queued and processed asynchronously.

* **5.	Event Grid Events:**
*	You can trigger functions based on events published to Azure Event Grid, which allows integration with various Azure services and third-party systems for real-time event-driven architecture.

* **6.	Azure Blob Storage Events:**
*	Functions can also be triggered by file uploads or changes in Azure Blob Storage. This can be useful for scenarios like image processing, file conversion, or other storage-related operations.

**Azure Function Code Components**

An Azure Function typically consists of two main components:

* **1.	Your Code:** The actual code you write for the Azure Function, which can be in various programming languages such as C#, Python, JavaScript, PowerShell, etc.

* **2.	Function.json:** This is a configuration file that contains the details about the function, including triggers, bindings, and other configuration settings necessary for the function to run correctly in the Azure environment.


**Understanding the Function.json File**

The function.json file is a crucial component of an Azure Function. It holds configuration information required by the Azure Functions runtime to execute your code. Here’s an overview of how it works:

* **1. Trigger:**
*	The trigger defines how the function is invoked. Each function can have one and only one trigger. The trigger could be based on various events like an HTTP request, a scheduled timer, a message from a queue, or an event from a database or other system.
*	For example, if you're using an HTTP trigger, the function.json will define that the function is triggered whenever an HTTP request is received.

* **2. Bindings:**
*	Bindings define how data is passed into or out of the function. There are two types of bindings:
* Input Bindings: These allow you to pass data to the function. For instance, if you want your function to read from a queue, a storage blob, or a database, you use an input binding.
* Output Bindings: These allow the function to send data out. For example, after processing data, you might write the result to a database or send a response via HTTP.
A function can have multiple input and output bindings. These bindings eliminate the need for the developer to manually handle the connections to external systems or services, simplifying development.

* **3. Configuration Details:**
*	The function.json file also holds various configuration settings that control how the function is executed. This can include settings such as the name of the trigger, queue names, or connection strings for resources like Azure Blob Storage or Cosmos DB
