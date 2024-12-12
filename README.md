# Azure-Data-Architecture
This is the Microsoft Azure Architecture that I would work in, end-to-end as an Azure Data [Analytics] Engineer. In this architecture, data is extracted from the datasource, transformed to clean and make sense of the data, and loaded into a new platform for end-user consumption. This data can either be batched or streamed. All while maintaining data governance, security and SRE in Microsoft Azure.  


## Overview
![Azure-Data-Architecture](https://github.com/user-attachments/assets/beb9266d-419b-4061-aa74-bdb461d46cf9)

https://learn.microsoft.com/en-us/azure/architecture/example-scenario/dataplate2e/data-platform-end-to-end 

On the left, is the data coming in from the datasource this can be any source of data. This could be for instance unstructured data (images, audio files, etc.), semi-structured data (JSON objects from an API, XML, CSV, etc.), or a relational database (i.e. MS SQL Server, Azure SQL Server, Azure SQL Database, Postgres, MySQL,etc.), or other services in Azure or other Cloud Service Providers (CSP). 

![image](https://github.com/user-attachments/assets/41790b1b-72c8-4c8c-a5af-a87c7b9f6890)


On the Top Center is for streaming and transforming real-time data with low-latency. Azure Event Hubs is the Kafka compatable service in Azure, which data is sent to and routed to where it needs to go. Before the data gets to it's destination, some transformations may need to take place. These transformations can include providing additional real-time aggregations (Sums, Counts, Averages), changing data groupings (stats by individual, teams, departments, etc.), altering data types and or formats (date formating defaults, changing string to int, MM-DD-YYY --> YYYY-MM-DD, etc.). To do this within the architecture, Azure Stream Analytics provides this capability via SQL editor before the data is shipped to the desired location/platform.  

![image](https://github.com/user-attachments/assets/d6034590-118b-4048-8a85-0779ac55ba90)


In the center of the Architecture is the Datalake. The datalake is a Binary Large Object (BLOB) storage, with a filing system. This is the cheapest stoage offered in the cloud, allowing for petabytes worth of data that can be stored in essentially any format. 

![image](https://github.com/user-attachments/assets/cbdc3c33-c0b2-40bb-a76e-6ce86b0f53ce)

On the center right is the Azure AI Services which include Azure Cognitive Services (a suite of Azure AI low-code services) and Azure Machine Learning (a suite of Azure ML Services: including ML Studio and Auto ML (low-code/no-code ML engineering tool))

![image](https://github.com/user-attachments/assets/705f2b8a-11de-4d0d-a0bb-bb5a971fde86)

On the right is the destination. This is where the data is going to. This is how the end-user will access/interact with the data, now that it is clean and ready for them to use! This can be via BI tools (like Power BI, Tableau, Qlik,etc), Applications, or shared Azure Containers. 

![image](https://github.com/user-attachments/assets/254014a7-0ede-47b9-af8d-e04913b01f0d)

On the bottom is all the services running in the backgorund for security, IAM, DevOps and more!

![image](https://github.com/user-attachments/assets/4ea17211-b114-47d8-8e50-99668d484ba4)

# Databricks Medallion Architecture 
This is an architecture for staging data. 

## Overview
![image](https://github.com/user-attachments/assets/5f9c87f1-65de-4bd9-b2bd-e886a363eada)
https://www.databricks.com/glossary/medallion-architecture

### Bronze
When the data comes in from the source it is often raw. This is typically saved as is in what is known as the Bronze stage. This data remains exactly as it is in the source. As an example of raw data in the bronze stage, when working in Azure Entra (fka Azure Active Directory), the fields on the back-end might have a schema with field names similar to "ExtentionAttribute5" and this can be a customizable field added to a user's profile defined by the organization. In reality this might be "sales team" or "sales territory" or anything really. 

### Silver
As an engineer, I would have to make this makes sense of this data and relay to the end-users what this field actually means. However, I still want to keep a copy with majority of data as it comes in through the datasource to give it just enough structure to be able to analyze the state of the system. This is known as the Silver Stage. This would typically include joining other tables that are relates (SQL joins, dropping duplicated or unwanted records, correcting formatting and innaccurate data).   










