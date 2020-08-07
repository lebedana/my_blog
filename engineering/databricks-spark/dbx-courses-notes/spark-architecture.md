# Spark Architecture

### Terms and concepts

Driver

* one per cluster 
* maintaining info about spark application \(?\)
* communicating with user program
* scheduling tasks among executors 

Executor

* Hold a partition \(a chunk of data\)
* Responsible for: execute assigned code, communicate state to the driver
* Each executor has a number of slots

Job

* each job is broken down into **stages** \(set of **tasks** which can be executed in parallel\)

Task

* assigned to **slots** for parallel execution 
* action which can be executed in separate - read, filter, select, groupby, rename column, drop column..

### Transformations, actions and execution

Dataframe

* immutable
* carry metadata allowing to Spark to optimize queries 

Lazy evaluation

* allows to build a plan of **transformations**, which is executed only when an action is called
* Required for optimization

Transformations 

* Narrow 
* Wide - require data shuffle = redisribution over the system \(moved between executors\) 

Partition

* collection of raws 

Actions

* 


