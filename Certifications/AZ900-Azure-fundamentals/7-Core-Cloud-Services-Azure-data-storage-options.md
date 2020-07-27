[< Previous](6-Core-Cloud-Services-Azure-compute-options.md) - [Next >](8-Core-Cloud-Services-Azure-networking-options.md)
# 7 - Core Cloud Services - Azure data storage options
## Intro[^1]

Azure provides storage features that will meet all of your business needs.

## Benefits of using Azure to store data[^2]

To address the storage problem for your online learning portal, you're considering storing your data in the cloud. But you're concerned about security, backup, and disaster recovery. On top of those issues, you're worried about how difficult it could be to manage cloud-hosted data. So, here's what you need to know.

Video (3:20) _Why store your data in the cloud?_ - https://www.microsoft.com/en-us/videoplayer/embed/RE2yzjI

### Benefits of using Azure to store data

- Automated backup and recovery
- Replication across the globe
- Support for data analytics
- Encryption capabilities
- Multiple data types
- Data storage in virtual disks
- Storage tiers

### Types of data

There are three primary types of data that Azure Storage is designed to hold.

1. __Structured data__. Structured data is data that adheres to a schema, so all of the data has the same fields or properties. Structured data can be stored in a database table with rows and columns. Structured data relies on keys to indicate how one row in a table relates to data in another row of another table. Structured data is also referred to as relational data, as the data's schema defines the table of data, the fields in the table, and the clear relationship between the two. Structured data is straightforward in that it's easy to enter, query, and analyze. All of the data follows the same format. Examples of structured data include sensor data or financial data.

2. __Semi-structured data__. Semi-structured data doesn't fit neatly into tables, rows, and columns. Instead, semi-structured data uses tags or keys that organize and provide a hierarchy for the data. Semi-structured data is also referred to as non-relational or NoSQL data.

3. __Unstructured data__. Unstructured data encompasses data that has no designated structure to it. This lack of structure also means that there are no restrictions on the kinds of data it can hold. For example, a blob can hold a PDF document, a JPG image, a JSON file, video content, etc. As such, unstructured data is becoming more prominent as businesses try to tap into new data sources.

## How Azure data storage can meet your business storage needs[^3]

### Azure SQL Database

Azure SQL Database is a relational database as a service (DaaS) based on the latest stable version of the Microsoft SQL Server database engine. SQL Database is a high-performance, reliable, fully managed and secure database. You can use it to build data-driven applications and websites in the programming language of your choice without needing to manage infrastructure.

### Azure Cosmos DB

Azure Cosmos DB is a globally distributed database service. It supports schema-less data that lets you build highly responsive and Always On applications to support constantly changing data. You can use this feature to store data that is updated and maintained by users around the world. The following illustration shows a sample Azure Cosmos DB database that's used to store data that's accessed by people located across the globe.

### Azure Blob storage

Azure Blob Storage is unstructured, meaning that there are no restrictions on the kinds of data it can hold. Blobs are highly scalable and apps work with blobs in much the same way as they would work with files on a disk, such as reading and writing data. Blob Storage can manage thousands of simultaneous uploads, massive amounts of video data, constantly growing log files, and can be reached from anywhere with an internet connection.

### Azure Data Lake Storage

The Data Lake feature allows you to perform analytics on your data usage and prepare reports. Data Lake is a large repository that stores both structured and unstructured data.

### Azure Files

Azure Files offers fully managed file shares in the cloud that are accessible via the industry standard Server Message Block (SMB) protocol. Azure file shares can be mounted concurrently by cloud or on-premises deployments of Windows, Linux, and macOS. Applications running in Azure virtual machines or cloud services can mount a file storage share to access file data, just as a desktop application would mount a typical SMB share. Any number of Azure virtual machines or roles can mount and access the file storage share simultaneously. Typical usage scenarios would be to share files anywhere in the world, diagnostic data, or application data sharing.

### Azure Queue

Azure Queue Storage can be used to help build flexible applications and separate functions for better durability across large workloads. When application components are decoupled, they can scale independently. Queue storage provides asynchronous message queueing for communication between application components, whether they are running in the cloud, on the desktop, on-premises, or on mobile devices.

### Disk Storage

Disk storage provides disks for virtual machines, applications, and other services to access and use as they need, similar to how they would in on-premises scenarios. Disk storage allows data to be persistently stored and accessed from an attached virtual hard disk. The disks can be managed or unmanaged by Azure, and therefore managed and configured by the user. Typical scenarios for using disk storage are if you want to lift and shift applications that read and write data to persistent disks, or if you are storing data that is not required to be accessed from outside the virtual machine to which the disk is attached.

### Storage tiers

1. __Hot storage tier__: optimized for storing data that is accessed frequently.

2. __Cool storage tier__: optimized for data that are infrequently accessed and stored for at least 30 days.

3. __Archive storage tier__: for data that are rarely accessed and stored for at least 180 days with flexible latency requirements.

### Encryption and replication

Azure provides security and high availability to your data through encryption and replication features.

1. _Azure Storage Service Encryption (SSE)_ for data at rest helps you secure your data to meet the organization's security and regulatory compliance. It encrypts the data before storing it and decrypts the data before returning it. The encryption and decryption are transparent to the user.

2. _Client-side encryption_ is where the data is already encrypted by the client libraries. Azure stores the data in the encrypted state at rest, which is then decrypted during retrieval.


## Comparison between Azure data storage and on-premises storage[^4]

Now that you know about the benefits and features of Azure data storage, let's see how it differs from on-premises storage.

### Cost effectiveness

An on-premises storage solution requires dedicated hardware that needs to be purchased, installed, configured, and maintained. This requirement can be a significant up-front expense (or capital cost). Change in requirements can require investment in new hardware. Your hardware needs to be capable of handling peak demand, which means it may sit idle or be under-utilized in off-peak times.

### Reliability

On-premises storage requires data backup, load balancing, and disaster recovery strategies. These requirements can be challenging and expensive as they often each need dedicated servers requiring a significant investment in both hardware and IT resources.

### Storage types

Sometimes multiple different storage types are required for a solution, such as file and database storage. An on-premises approach often requires numerous servers and administrative tools for each storage type.

### Agility

Requirements and technologies change. For an on-premises deployment, these changes may mean provisioning and deploying new servers and infrastructure pieces, which are a time consuming and expensive activity.

### Compare on-premises storage to Azure data storage

|                        Needs                       |                            On-premises                            |                         Azure data storage                        |
|:--------------------------------------------------:|:-----------------------------------------------------------------:|:-----------------------------------------------------------------:|
| Compliance and security                            | Dedicated servers required for privacy and security               | Client-side encryption and encryption at rest                     |
| Store structured and unstructured data             | Additional IT resources with dedicated servers required           | Azure Data Lake and portal analyzes and manages all types of data |
| Replication and high availability                  | More resources, licensing, and servers required                   | Built-in replication and redundancy features available            |
| Application sharing and access to shared resources | File sharing requires additional administration resources         | File sharing options available without additional license         |
| Relational data storage                            | Needs a database server with database admin role                  | Offers database-as-a-service options                              |
| Distributed storage and data access                | Expensive storage, networking, and compute resources needed       | Azure Cosmos DB provides distributed access                       |
| Messaging and load balancing                       | Hardware redundancy impacts budget and resources                  | Azure Queue provides effective load balancing                     |
| Tiered storage                                     | Management of tiered storage needs technology and labor skill set | Azure offers automated tiered storage of data                     |

[< Previous](6-Core-Cloud-Services-Azure-compute-options.md) - [Next >](8-Core-Cloud-Services-Azure-networking-options.md)

[^1]: https://docs.microsoft.com/en-us/learn/modules/intro-to-data-in-azure/1-introduction
[^2]: https://docs.microsoft.com/en-us/learn/modules/intro-to-data-in-azure/2-benefits-of-using-azure-to-store-data
[^3]: https://docs.microsoft.com/en-us/learn/modules/intro-to-data-in-azure/3-how-azure-storage-meets-your-business-storage-needs
[^4]: https://docs.microsoft.com/en-us/learn/modules/intro-to-data-in-azure/4-comparison-azure-and-on-prem-storage