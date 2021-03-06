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
* _Sort Merge Joins send all records with the same join key to the same partition_

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

### Data Skew

* when key column values is unevenly distributed 
  * mb cause OOM or long processing for a job 
* Solution is managed spark - hint 
  * `joined_df = sales_df.hint("skew", "item_id", "100").join(item_df, "item_id") joined_df.count()`

### Streaming 

#### Bronze table

Multiplex table

* A single stream supports ingestion from multiple external data sources
* Multiple silver tables are generated via parallel queries against this single bronze table

Singleplex tables

* Each source has its own bronze table where data is stored in raw format.
* Multiple streams will need to be configured and managed to keep a current view of our raw data
* Silver tables will generally map 1:1 with bronze tables

Some important considerations:

* **Multiple concurrent streams on a shared cluster will contend for driver resources**
* Singleplex maintains [stream/table duality](https://docs.confluent.io/current/streams/concepts.html#duality-of-streams-and-tables)
* Decisions may be driven by how [Kakfa events and topics have been organized](https://www.confluent.io/blog/put-several-event-types-kafka-topic/)

#### Batch vs Streaming workloads

The main trade-off when comparing batch and streaming workloads are the latency requirements.

### Checkpointing 

{% embed url="https://spark.apache.org/docs/latest/streaming-programming-guide.html\#checkpointing" %}







