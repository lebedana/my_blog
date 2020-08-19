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

{% embed url="https://spark.apache.org/docs/3.0.0-preview/web-ui.html" %}



### Optimization

* Pay attention to GC & tasks distribution 
* ..

### System monitoring 

* in build - Ganglia 
* watchdog - metrics travel to watchdog server \(free version has limited capabilities\) 

### Partitioning

Spark action tends to be one of three main operations:

1. Read
2. Transform
3. Write

These operations map extremely well to three different types of Spark partitions

* Read - map of how data is going to be split-up so that it can flow into Spark tasks and can then be transformed and sent to future stages.
  * default = total \#of cores
* shuffle - used when shuffling data for joins or aggregations
  * default is 200
  * think about as of join
* write - These partitions send the final data to storage.
  * very often, a write is combined with a final shuffle and the number of output files will be equal to the value of `spark.sql.shuffle.partitions ( the` Write Partitions send the final data to persistent storage. How many files are created on persistent storage is determined by the number of Write Partitions and their contents. \)

## Joins

* Data skew is a condition in which a table's data is unevenly distributed among partitions in the cluster

spark 3 - a flexible way to choose a specific algorithm using strategy hints:

```text
dfA.join(dfB.hint(algorithm), join_condition)
```

### Sort Merge join

* good performance for large tables
* _SMJ_ requires both sides of the join to have **correct partitioning** \(by join key\) and **order** and in __the general case this will be ensured by **shuffle and sort in both branches** of the join
* Note: the shuffle and sort are very expensive operations and in principle, they can be avoided by creating the DataFrames from correctly bucketed tables, which would make the join execution more efficient. 
* is more robust \(camparing to SHJ\) with respect to _OoM_ errors - it will store data on disc if there is not enough memory 

### **BroadcastHashJoin**

* good performance when sides are small enough \(will be stored \) in memory
* spark will choose the algorithm when one of the sides is smaller than _autoBroadcastJoinThreshold \(_10MB is default\)

```text
spark.conf.set("spark.sql.autoBroadcastJoinThreshold", 100*1024*1024)
```

```text
spark.conf.set("spark.sql.broadcastTimeout", time_in_sec)
```

* May require to calculate additional statistics on table 
  * `ANALYZE TABLE cities COMPUTE STATISTICS FOR COLUMNS city_id, state`

### ShuffledHashJoin <a id="7f1e"></a>

* If you switch the preferSortMergeJoin setting to False, it will choose the SHJ only if one side of the join is at least three times smaller then the other side and if the average size of each partition is smaller than the autoBroadcastJoinThreshold \(used also for BHJ\)
* as opposed to SMJ, it doesn’t require the data to be sorted \(hence, t be faster\)  
* use when one side of the join is much smaller than the other

 



