# Databricks hints and tricks

* %fs magic command - wrapper around dbutils.fs 
* **Link DBX worskapce with Key Vault** he first step is to open a new web browser tab and navigate to `https://<your_azure_databricks_url>#secrets/createScope`

  The number after the `?o=` is the unique workspace identifier; append `#secrets/createScope` to this.

