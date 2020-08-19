# Partitioning

Get df number of partitions: 

* `print("Partitions: {0:,}".format( alternateDF.rdd.getNumPartitions() ))`

On disk/in data lake: 

* **Spark keeps persistent RDDs in memory by default, but it can spill them to disk if there is not enough RAM.**
* repartition\(5\) in memory, than `partitionBy` on disk
* `spark.sql.shuffle.partitions -` configures the number of partitions that are used when shuffling data for joins or aggregations.
*  from [artcl](https://mungingdata.com/apache-spark/partitionby/#:~:text=Spark%20writers%20allow%20for%20data,partitioned%20data%20lake%20is%20hard.) "In order to write data on disk properly, you’ll almost always need to repartition the data in memory first."
* .option\("maxRecordsPerFile", 10\)
* Partitioned data lakes can be much faster to query \(when **filtering** on the partition keys\)
* `UnsafeRow` is the in-memory storage format for Spark SQL, DataFrames & Datasets.
* wide transformations \(e.g. groupBy\) required shuffle: 

  * It's not possible to group all records across all partitions until every task is complete \(it is the point at which all the tasks must synchronize\)
  * this is also a significant performance hit: disk IO, network IO and more disk IO.

**TODO** Go through to understand disc vs memory partitioning: 

**TODO**: how to read/write parquete ? How to modify data on disk \(aka ewrite df in disc\)

**write**

`(retail.write.format("parquet") .mode("overwrite") .partitionBy("Country") .save(parquet_path))` 

**retail\_parquet = \(spark.read.format\("parquet"\) .load\(parquet\_path\)\)**

\*\*\*\*

read 

retail\_parquet = \(spark.read.format\("parquet"\) .load\(parquet\_path\)\)





{% embed url="https://mungingdata.com/apache-spark/partitionby/" %}

{% embed url="https://stackoverflow.com/questions/45704156/what-is-the-difference-between-spark-sql-shuffle-partitions-and-spark-default-pa" %}



