# Design Data Intensive Applications

Data Warehouses 

* OLTP - online transaction processing 
  * run on databases supporting high availability, low latency 
* OLAP - online analytic processing 
  * run on **data warehouses**
  * often it is a dump of the OLTP database \(often cleaned up and transformed into analysis-friendy schema - ETL\) 
* Schemas for analysis 
  * start \(more effective\) or snowflake 
  * so-called fact \(items, records\) tables - huge; and dimention tables \(who, hen, where, what...?\) - much smaller
* Column-oriented storage 
  * easier/more effective to compress
  * implies more effective in-memory operations \(load from disk to memory\) **\(?\)** 
  * more efficient use of CPU cycles **\(?\)**
  * effective indexing 



