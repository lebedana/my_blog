# Design Data Intensive Applications

Data Warehouses 

* OLTP - online transaction processing 
  * run on databases supporting high availability, low latency 
* OLAP - online analytic processing 
  * run on data warehouses
  * often dump of the OLTP database \(also, often cleaned up and transformed into analysis-friendy schema - ETL\) 
* Schemas for analysis 
  * start \(more effective\) or snowflake 
  * so-called fact \(items, records\) and dimention tables \(who, hen, where, what...?\)



