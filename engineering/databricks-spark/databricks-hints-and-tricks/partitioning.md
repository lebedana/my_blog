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

### Partitioning \(from adv course\)

Spark action tends to be one of three main operations:

1. Read
2. Transform
3. Write

These operations map extremely well to three different types of Spark partitions

* **Read** - map of how data is going to be split-up so that it can flow into Spark tasks and can then be transformed and sent to future stages
  * default = total \#of cores
  * determined by spark depending on 
    * `spark.default.parallelism` \(default: Total \#of exec. cores\)
    * `spark.sql.files.maxPartitionBytes` \(default: 128 MB\) 
    * `spark.sql.files.openCostInBytes` \(default: 4 MB\)
  * Note: the cost `openCostInBytes` is added while reading each file \(\#files\*openCostInBytes\), hence greater number of files on disk will end up in a greater number of RDD partitions
* shuffle - used when shuffling data for joins or aggregations
  * default is 200
  * `spark.conf.get("spark.sql.shuffle.partitions")`
* write - These partitions send the final data to storage.
  * very often, a write is combined with a final shuffle and the number of output files will be equal to the value of `spark.sql.shuffle.partitions` \(the writepPartitions send the final data to persistent storage. How many files are created on persistent storage is determined by the number of Write Partitions and their contents. \)
  * write start with scanning files in the current location \(\#tasks = number of partitions there\)

**Data skew:**

**Solution:**

* **Adding Salt**

**TODO** Go through to understand disc vs memory partitioning: 

**TODO**: how to read/write parquete? How to modify data on disk \(aka ewrite df in disc\)

**write**

`(retail.write.format("parquet") .mode("overwrite") .partitionBy("Country") .save(parquet_path))` 

**read** 

Generic API:

`SparkSession.read.format(String fileformat).load(String path or List of paths)`

Example \(dbx\):

`retail_parquet = spark.read.format("parquet").load(parquet_path)`

**convert to delta** 

`spark.sql("CONVERT TO DELTA parquet.{} PARTITIONED BY (Country string)".format(parquet_path))`

{% embed url="https://mungingdata.com/apache-spark/partitionby/" %}

{% embed url="https://stackoverflow.com/questions/45704156/what-is-the-difference-between-spark-sql-shuffle-partitions-and-spark-default-pa" %}

### **Adaptive Query Execution - Spark 3**



### **Dynamic** partitionOverwriteMode

`.option('partitionOverwriteMode', 'dynamic')`

###  ****

### \*\*\*\*

### **Tools**

```text
# number of partitions 
print("Partitions: {0:,}".format(df_small.rdd.getNumPartitions()))

# size of each parition 
def printRecordsPerPartition(df):
    def countInPartition(iterator): yield __builtin__.sum(1 for _ in iterator)
    results = (df.rdd
             .mapPartitions(countInPartition)
             .collect()
             )
    print("Per-Partition Counts")
    i = 0
    for result in results:
      i = i + 1
      print("#{}: {:,}".ormat(i, result))
      
printRecordsPerPartition(df_small)

```

