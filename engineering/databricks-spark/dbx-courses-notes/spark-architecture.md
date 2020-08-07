# Spark Architecture

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

* each job is broken down into **stages** \(set of steps\)

Task

* assigned to **slots** for parallel execution 





