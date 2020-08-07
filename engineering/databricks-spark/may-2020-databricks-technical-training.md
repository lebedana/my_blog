# \[May 2020\] Databricks Technical Training

## Preparation

### Training Notes

* Course materials are attached

### Other

* dbc - databricks compressed files
* DB creates Spark session

### Cluster creation

* Concurrent - migth be used by multiple users 
* Pulling - keeps some ready pre-hitted instances \(launching takes 15sec - vs 5-8 minutes-\) - you do not pay DB, but Azure for the instance

## Introduction/History

Challenges: 

* Storage - distributed file systems
  * First GFS - google file system \(2005-?\) 
  * Later: ...
* Computing capacity 
  * Cloud \(VMs\)
* How to use the data - tools, competition power
  * \[2004\] Map Reduce - process data on cluster of VMs
    * Does not evolve much
    * Problem 1: do a lot of READ/WRITE operations to the Disk 
    * Problem 2: complexity of writing code
  * \[2005\] Hadoop = GDS + MR
  * \[2009\] Spark - in-memory distributed computing engine 
    * Problem 1 resolved by computing in-memory
    * Thanks to OS Spark nature, collaborators solved problem 2
    * Spark can work with huge amount of data source \(vs MR only HDFS\) - e.g. Kafka, MySQL, PG, hadoop, mongoDB ...
  * \[2013 \] Databricks

    * Features on top of Spark 
      * Spark is managed  - 2 to 5 times faster than OS Spark 
      * Interactive notebooks
      * Natively Distributed 
      * Autoscaling 
      * Serverless
      * DB runtime is extended with TF, PyTorch and other libraries
      * Monitoring 
    * Integrations
      * Integration with Google and Alibaba - end of the 2020/2021
      * Can be used with private cloud 
      * Will be used on-prem

 

![MR Problem 1](../../.gitbook/assets/image%20%281%29.png)

## Databricks

![Multiple laters of DB](../../.gitbook/assets/image%20%282%29.png)



Apache Spark:

* Core = Spark engine \(RUNS in worker and runner\) 

  * Load data to RAM \(using RDD code - resilient distributed dataset\)
  * Distribution - if required \(when required - ?\)
  * Scheduling task and provide the workers with tasks
  * Monitoring 
  * Getting results from workers 

* APIs 
  * Scala, Python, Java
  * For data there are RDD API  - low level APIs - complex 
    * it is collection of API to query and transform in Scala, Python, SQL, R. Options for DF API calls \(they are translated to RDD API\)
      * SQL/DataFrame API 
      * Structure streaming 
      * Graphics 
      * MLlib 
* RDDs
  * Distributed 
  * Immutable \(any modification create immutable RDD\): File1 --&gt; RDD1 --&gt; RDD2 --&gt; File2
  * Lineage
  * Resilient \(?\)

    * Map
    * Transofrm

  * Dataframe vs RDD

    * Dataframe is faster then RDD \(uses optimization when translated\)
* Cluster:
  * Master-slave arcitecture 
  * Master=Driver \(Driver VM\)
  * Every application needs own driver process in the Driver JVM
  * The same for the executed point of view - multiple executor processes
  * Slot - core in the executor VM
  * Distribution of data defined based on **data partitioning.** User can give number of partitions \(but spark has default configuration\)  - there is default value 
  * Components \(Orchestrated by the driver\)
    * Job  = set of tasks
    * Stage \(set of tasks which can be executed in parallel\) 
    * Task \(read, filter, select, groupby, rename column, drop column..\) 
  * Cluster manager - responsable for cluster provisioning 
* Notebooks:
  * %sh is executed on driver 
  * Variable are not translated between languages 
  * %run magic \(run notebook from other notebook\)
  * %fs - dbutils and sh combined
  * dbutils
    * mount does not mean coping 
    * modifying \(including removal\) of the mounted data will modify data in source 
    * dbutils.fs.help\(\)



* connected to dbfs - drivers do not have file system 
* dbfs - driver and workers use same filesystem 

## Data

### DF

* If schema is not provided data are **unstructured** 
  * csv -reads unstructured data 
* Spark will try to guess the structure \(if inferSchema is true\) 
  * Spark job will be run 
* We can also declare schema by ourselves \(using pyspark.sql.types\) 
  * Faster 
  * Do not use spark jobs \( performed on driver\)
* To get data to dbfs, we need to read it \(including file system as a source\) 
* saveAsTable - registers the data currently referenced in the DataFrame to the metastore and saves a copy of the data

### Tables

* Are persistent between notebooks and sessions
* Are available to all users \(having permissions\)
* A tmp table can be created from a table 

### Temporary tables/view

* Exits 
  * only in the notebook
  * only in the spark session 
* Can be transformed to permanent table

### Managed/External

* Weather it will be registered in metastore or not
* DF.write.option\(\) - will register table to MS
* What are other options? 
* If we drop data, data are deleted 
* External data drop will remove data only from the metastore 
* ??

### Formats

* Delta - ?
* Parque  
  * structured \(has schema attached\) 
* Snappy - impression - \(?\)

### Tips:%who DataFrame - show existing in the NB dataframes

* DF.explain\(extended=True\) - explain plan 
* %sql describe history TB

### Summary

* DataFrames, tables, and views provide robust access to optimized Spark computations.
* DataFrames and views provide similar temporary access to data; tables persist these access patterns to the workspace.
* No job is executed when creating a DataFrame from a table - the schema is stored in the table definition on Databricks.



## Actions

* Any transformation results in a dataframe 
* Transformation are executed only when action is called on the dataframe 
* Without Trasfomration beeing lazy optimisation can not be created 
* COMPLETE!!!!!!

## Transformations 

* Wide vs narrow transformation 
* 
## Delta Lake 

Problems with Data Lakes:

* no guarantee data are in correct format 
* no corruption/consistency information 

Delta Lakes features: 

* Allows to get rid of Lambda architecture
* Created by DB \(now donated as OS\) 

### Managed DL

* optimize - optimize sizes of files \(app 1GB\)
* zorder - reorganize file to increase querying  



## Streaming application

### Complexity: 

* Complex data 
  * diverse data format 
  * Can be dirty 
  * Can be out of order 
* Complex workfloads 
  * data processing 
* Complex systems 
  * diverse storage 
  * system failures 

### Features: 

* Data frame is continuously increasing 
* Spark before: incremental micro batch processing
  * clusters are shared for parallel multiple streams 
* New Spark 3.0: structure streaming  processing 
  * one cluster dedicated to one stream 
  * 









 





## Questions: 

* Delta vs Parque

From a developer's and student's perspective my primary focus is on...

* The number of **Partitions** my data is divided into.
* The number of **Slots** I have for parallel execution.
* How many **Jobs** am I triggering?
* And lastly the **Stages** those jobs are divided into.



{% file src="../../.gitbook/assets/lessons.dbc.zip" %}

