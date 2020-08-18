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

###  **Connect to Databricks from BI/SQL tools using jdbc driver**

{% embed url="https://docs.microsoft.com/en-us/azure/databricks/integrations/bi/jdbc-odbc-bi" %}

### **UDF**

* Hive UDFs are functions written in Java or Scala
* The UDFs can be imported into spark

`%sql DROP TEMPORARY FUNCTION IF EXISTS FtoC;`

`CREATE TEMPORARY FUNCTION FtoC AS "com.databricks.training.examples.FtoCUDF" USING JAR "`[`https://files.training.databricks.com/courses/hadoop-migration/CombinedUDF-1.0-SNAPSHOT.jar`](https://files.training.databricks.com/courses/hadoop-migration/CombinedUDF-1.0-SNAPSHOT.jar)`";`

* What about optimization perspective? \[TODO\]

### Spark UI

* Stage - contains of sequence of tasks executed in parallel
* Job is split into stages - shuffles cause stage boundaries
* UI for aggregations: 
  * total time = **stage execution** + scheduling + ... 
* IMPORTANT NOTE: ****The size of the data is **how large it is in memory, not on disk**. Data in memory provides a more accurate picture rather than using the size of the data on disk. This is because data in memory has been deserialized and decompressed.

Optimization

* Pay attention to GC & tasks distribution 
* 


