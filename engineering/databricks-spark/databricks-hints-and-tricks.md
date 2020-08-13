# Databricks/Spark hints and tricks

* %fs magic command - wrapper around dbutils.fs 

### Schema

* inferSchema - .option\("inferSchema", True\) - otherwice all columns will be string
* provide schema 

`from pyspark.sql.types import DoubleType, IntegerType, StringType, StructField, StructType`

`csvSchema = StructType([ StructField("index", IntegerType()), StructField("sepal_length", DoubleType()), StructField("sepal_width", DoubleType()), StructField("petal_length", DoubleType()), StructField("petal_width", DoubleType()), StructField("species", StringType()) ])`

Pak:

`schema(csvSchema) # Use the specified schema`

### Tables and view

* spark.catalog.listTables\(\) - show tables and views 
* ...

### Secrets

**1**. Create Key Vault & secrete keys in it

**2. Link DBX worskapce with Key Vault** he first step is to open a new web browser tab and navigate to `https://<your_azure_databricks_url>#secrets/createScope`

* The number after the `?o=` is the unique workspace identifier; append `#secrets/createScope` to this.

3. Access the secret by the key - 🔑  print\(dbutils.secrets.get\(scope="students", key="storageread"\)\) - key is a particular secrete ID 

