# Data \(Storage, Databases\)

## Azure Storages 

* Azure Blob storage
* Azure data lake Gen1
* Azure data lake Gen2

### Azure data Lake storage

* Hadoop access \(no in blob storage\)
* performance 
* cost 
* Easily collaborate with big data services \(Databricks, ..\) 
* Hierarchical namespace \(increase performance\) - blob have only flat namespace

## Databases

Cosmos DB

*  multimodule database service 
  * Easy codes migration 
  * API
    * Core \(SQL\) 
    * Mango API
    * Casandra 
    * ...
* [Capacity mode](https://docs.microsoft.com/en-us/azure/cosmos-db/throughput-serverless)
  * Provisioned throughput - specific number of RU is allocation
  * Serverless \(using synapse?\) - is in preview, not recommended for production workloads
* Request Unit \(RU\)
  * Expected load is defined in RUs
  * Each operation \(read, write, update...\) has a cost in RU \(azure defined\) per KB of data
*  Partitioning \(partition key\)
  * Range of values
  * Review Top Queries \(what data and how it accesses\)
  * Transactional workloads \(for write\)
  * Non-cluster index - \[meaning?\] - composite key 
* performance \(under 10ms in 99 percentile\)
* high availability \(multiple locations\)
* Multi-master
  * Advantages
    * **Accessibility**: If one master fails, other masters continue to update the [database](https://en.wikipedia.org/wiki/Database).
    * **Distributed Access**: Masters can be located in several physical sites, i.e. distributed across the network.
    * ? multi writes = faster writes
  * Disadvantages
    * **Consistency**: Most multi-master replication systems are only loosely consistent, i.e. lazy and asynchronous, violating [ACID](https://en.wikipedia.org/wiki/ACID) properties.
    * **Performance**: Eager replication systems are complex and increase communication [latency](https://en.wikipedia.org/wiki/Latency_%28engineering%29).
    * **Integrity**: Issues such as conflict resolution can become intractable as the number of nodes involved rises and latency increases.
* Unlimited storage
* Available confiurations
  * You can configure autoscaling 
  * Configure resolution to write/update conflicts 
* [Consistency level](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels)  - always a [trade-off](https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels-tradeoffs) 
  * Strong \(linearizability guarantee\)
  * Bounded Staleness \(linearizability not garanteed for an interval - time or \#of version of the item\)
  * Session \(linearizability withtin session independently on the region, otherwise the order is preserved\)
  * Consistent Prefix \(reads never see out-of-order writes\)
  * Eventual \(there's no ordering guarantee for reads. In the absence of any further writes, the replicas eventually converge\)

## Azure SQL Database

* First time you create database, you have to create a logical SQL server 
* Parametrs:
  * **\#vCores**
  * **..**
* Automatic tuning \(e.g. index creation\)

DataFactory 

* Can detect data structure drift 

## Azure Data Warehouse = SQL Data Warehouse 

* How it is a warehouse 





Questions: 

* When I prefer Azure data Lake Gen 1 
* When I prefer Blob Storage 
* Data type for which Cosmos DB is not the best choice 
* Best storage for images if there any difference between storages? 
* Why we set up index for container & not for a table? 
* Drift in data or drift in data structure? 

