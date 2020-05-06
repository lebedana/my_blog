# \[May 2020\] Databricks Technical Training

## Preparation

### Training Notes

* Course materials are attached

### Other

* dbc - databricks compressed files

### Cluster creation

* Concurrent - migth be used by multiple users 
* Pulling - keeps some ready pre-hitted instances \(launching takes 15sec - vs 5-8 minutes-\) - you do not pay DB, but Azure for the instance

## Introduction 

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
  * \[2009\] Spark - in-memory distributed computing 
    * 

![MR Problem 1](../../.gitbook/assets/image%20%281%29.png)





{% file src="../../.gitbook/assets/lessons.dbc.zip" %}

