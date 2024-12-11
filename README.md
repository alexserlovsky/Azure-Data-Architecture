# Azure-Data-Architecture
This is the Microsoft Azure Architecture that I would work in, end-to-end as an Azure Data [Analytics] Engineer. In this architecture, data is extracted from the datasource, transformed to clean and make sense of the data, and loaded into a new platform for end-user consumption. This data can either be batched or streamed. All while maintaining data governance, security and SRE in Microsoft Azure.  


## The Architecture Overview
![Azure-Data-Architecture](https://github.com/user-attachments/assets/beb9266d-419b-4061-aa74-bdb461d46cf9)

https://learn.microsoft.com/en-us/azure/architecture/example-scenario/dataplate2e/data-platform-end-to-end 

On the left, is the data coming in from the datasource this can be any source of data. This could be for instance unstructured data (images, audio files, etc.), semi-structured data (JSON objects from an API, XML, CSV, etc.), or a relational database (i.e. MS SQL Server, Azure SQL Server, Azure SQL Database, Postgres, MySQL,etc.), or other services in Azure or other Cloud Service Providers (CSP). 

On the Top Center is for streaming and transforming real-time data with low-latency. Azure Event Hubs is the Kafka compatable service in Azure, which data is sent to and routed to where it needs to go. Before the data gets to it's destination, some transformations may need to take place. These transformations can include providing additional real-time aggregations (Sums, Counts, Averages), changing data groupings (stats by individual, teams, departments, etc.), altering data types and or formats (date formating defaults, changing string to int, MM-DD-YYY --> YYYY-MM-DD, etc.). To do this within the architecture, Azure Stream Analytics provides this capability via SQL editor before the data is shipped to the desired location/platform.  

In the center of the Architecture is the Datalake. The datalake is a Binary Large Object (BLOB) storage, with a filing system. This is the cheapest stoage offered in the cloud, allowing for petabytes worth of data that can be stored in essentially any format. 
