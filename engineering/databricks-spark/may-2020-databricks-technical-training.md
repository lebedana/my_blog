# \[May 2020\] Databricks Technical Training

## Preparation

### Training Notes

* Course materials are attached

### Other

* dbc - databricks compressed files

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
  * Immutable \(any modification create immutable RDD\): File --&gt; RDD1 --&gt; RDD2 --&gt; F
  * 



{% file src="../../.gitbook/assets/lessons.dbc.zip" %}

