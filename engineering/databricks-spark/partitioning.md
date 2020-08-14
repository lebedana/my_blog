# Partitioning

On disk/in data lake: 

* repartition\(5\) in memory, that `partitionBy` on disk
* from [artcl](https://mungingdata.com/apache-spark/partitionby/#:~:text=Spark%20writers%20allow%20for%20data,partitioned%20data%20lake%20is%20hard.) "In order to write data on disk properly, you’ll almost always need to repartition the data in memory first."
* .option\("maxRecordsPerFile", 10\)
* Partitioned data lakes can be much faster to query \(when **filtering** on the partition keys\)
* `UnsafeRow` is the in-memory storage format for Spark SQL, DataFrames & Datasets.
* wide transformations \(e.g. groupBy\) required shuffle: 
  * It's not possible to group all records across all partitions until every task is complete \(it is the point at which all the tasks must synchronize\)
  * this is also a significant performance hit: disk IO, network IO and more disk IO.

