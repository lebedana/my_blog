# Advanced Tech

## Arch overview 

  
Hadoop - collection of OS software - provides a software framework for distributed storage and processing of big data using the **MapReduce** programming model

* can be on-prem or in cloud 

Metastore

* which database and table can be queried by Spark 
* functionality 
  * maps dbs name and default location 
  * maps tables to database/location/format/schema 
  * you can set permissions for table and database livel ACLs - **\(?\)**
  * statistics for cost based optimizer - used by spark optimisation
* one metastore per workspace 

#### The Dataframe API

* from spark 2.0 spark has supported **Dataframe** \(or **structured**\) **API**

### Useful queries to get metadata

| Information Needed | Query |
| :--- | :--- |
| What database am I using? | SELECT current\_database\(\); |
| How do I switch databases? | USE database\_name; |
| Where is this table located? | DESCRIBE EXTENDED table\_name |
| What functions are available? | SHOW FUNCTIONS |
| How do I query across databases? | SELECT \* FROM database1.table JOIN database2.table2 |
| How do I see all databases? | SHOW databases |

 ****



