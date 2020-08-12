# Spark Architecture

Components of Spark ecosystem

* Cluster manager
  * keeps track of resources availability 
  * e.g. Mesos, Hadoop YARN..
* Databricks has its own 
* Spark engine 
  * DBX has optimized

Notes:

* Spark is primarily written in scala

Questions:

* \#of partitions vs number of slots/tasks \("Slot - core in the executor VM"\)
  * A **core** contains a unit containing an L1 cache and functional units needed to run applications. Cores can independently run applications or threads. One or more cores can exist on a single CPU.

### Terms and concepts

Driver

* one per application \(per cluster - ?\)
* maintaining info about spark application 
* communicating with users program
* scheduling tasks among executors 
* Can be driven by codes in many languages \(for which APIs are available\) 

Executor = node

* Hold a partition \(a chunk of data\)
* Responsible for: execute assigned code, communicate state to the driver
* Each executor has a number of slots
* _How many executors falls in each node in DBX \(can I specify it, ...\)_
* Are driven mostly by codes in Scala 

Job

* each job is broken down into **stages** 
* stages consists of a set of **tasks** which can be executed in parallel

Task

* assigned to **slots** for parallel execution 
* operations \(e.g. transofmrations\) which can be executed in separate - read, filter, select, groupby, rename column, drop column..
* 1 task 1 partition 1 slot 1 core

### Transformations, actions and execution

Dataframe

* immutable
* carry metadata allowing to Spark to optimize queries 

Lazy evaluation

* allows to build a plan of **transformations**, which is executed only when an action is called
* Required for optimization

Transformations 

* Lazy
* Two types
  * Narrow 
  * Wide - require data shuffle = redisribution over the system \(moved between executors\) 
* Examples: select, distinct, groupBy, sum, orderBy, filter, limit

Partition

* collection of raws 

Actions

* Statements which are computed AND **executed** 
* Are eager
* Examples: show, count, collect, save 

### Pipelining

* Several transformations are performed at once \(e.g. map and filter\)
* No write on disc
* The pipelines are formed by stages \(set of transoformations which will be applied at once\) 

### Catalyst Optimizer

{% embed url="https://blog.knoldus.com/understanding-sparks-logical-and-physical-plan-in-laymans-term/" %}

* Finds plan for applying transformations and actions 
* Stages:
  * Unresolved logical plan - converted codes
  * logical plan - created only if the plan from above is valid \(columns exist, types valid...\)
  * Optimized logical plan - shuffle transformations \(e.g. joins\), group transf into stages..
    * You can add your own optimization rule 
  * Physical plan - how the plan from above will be executed on a cluster 
  * Selected physical plan 

### Caching 





