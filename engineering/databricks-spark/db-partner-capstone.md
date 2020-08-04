# DB Partner Capstone

Data Lakes

## Delta Lakes

[Delta Lake](https://delta.io/) is an [open source storage layer](https://github.com/delta-io/delta) that brings reliability to [data lakes](https://databricks.com/discover/data-lakes/introduction?_ga=2.117188038.1389713554.1596537962-832704881.1589558889)

{% embed url="https://databricks.com/discover/data-lakes/introduction?\_ga=2.117188038.1389713554.1596537962-832704881.1589558889" %}

{% embed url="https://docs.databricks.com/delta/delta-intro.html\#:~:text=Delta%20Lake%20is%20an%20open,compatible%20with%20Apache%20Spark%20APIs." %}

## Delta Pipeline 

* Bronze, silver and gold tables
  * data ingestion \(“**Bronze**” tables\), transformation/feature engineering \(“**Silver**” tables\), and machine learning training or prediction \(“**Gold**” tables\) ---&gt; together form “multi-hop” architecture 
* Delta Lake 
  * Stream data collection 
    * Azure Event Hubs or AWS Kinesis
  * Stream data storage 
    * Blob storage or S3 buckets
  * Instead, convert data to **delta lake** format 
* Features:
  * Schema enforcement
    * Delta Lake offers **schema validation on write \(**check ****records match the table’s predefined schema.\)
  * Time travel 
    * Delta Lake maintains an ordered transaction log of every operation that is performed on any
  * ACID transactions
    * \[TODO\] [https://blog.knoldus.com/spark-acid-transaction-with-delta-lake/](https://blog.knoldus.com/spark-acid-transaction-with-delta-lake/)
  * MLflow
    * In Databricks, MLflow is automatically enabled as of MLR 5.5, and you can view your MLflow runs using the [MLflow Runs Sidebar](https://databricks.com/blog/2019/04/30/introducing-mlflow-run-sidebar-in-databricks-notebooks.html)



{% embed url="https://databricks.com/blog/2019/08/14/productionizing-machine-learning-with-delta-lake.html" %}







Notes: 

* Terms "data swamps" - mess of data 
* Terms "Delta Lake table", "Delta Lake format"

To check: 

* \(set up\) number of shuffle partitions

