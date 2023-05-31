## Data Management Systems
- In an application, data is modeled as objects
- Those objects and, by extension the data, can be manipulated via APIs
#### Distributed Data Management
- Data management systems follow the distributed architecture
###### Architecture
- The distributed system consits of a controller node and worder nodes
- The worker nodes manage data, whereas the controller node manages the workers
![[Pasted image 20230531141017.png]]
###### Access
- The client sends a request to the controller on the control path, who provides it with loopkup metadata
- Using this data, the desired worker can be accessed on the data path
![[Pasted image 20230531141246.png]]
#### Key-Value Stores
- A key is a unique identifier and is associated with a value
- Key-value stores can be either in-memory or persisted
###### API
- Data can be retrieved using Get and stored using Put
###### Advantages
- Caching can be utilized to accelerate responses
- Querying data is kept simple
- System can be scaled out easily
##### Example
![[Pasted image 20230525095446.png]]
#### File Systems
- In a file system, data can be persited on storage devices in a hierarchical structure with directories and files
###### API
- Files can be read, written to and delted
- Metadata of files, such as access permissions can be changed
###### Advantages
- Some data formats can only be stored in file systems
- Other data management systems are built on the storage services provided by file systems
###### Example
![[Pasted image 20230531215645.png]]
#### Shared Logs
- A log is an append-only file, containing time-ordered records
- Records can be retrieved using their unique timestamp
###### API
- Data can be appended, read and deleted via trimming
###### Advantages
- Sequential append and read operations can be performed very efficiently
- Shared logs are ideal for storing data streams
###### Example
![[Pasted image 20230525101408.png]]
#### Databases
- Data is stored in tables and organized using predefined relationships
- Relationships betweend tables are defined using common attributes
###### API
- Relational databases are accessed using SQL
- With SQL queries, data can be created, read, updated and deleted
###### Advantages
- SQL enables complex analytics
- [[Transactions]] are supported
###### Example
![[Pasted image 20230525102216.png]]