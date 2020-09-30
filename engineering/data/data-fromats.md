# Data Fromats

## Parquet 

Resource-efficient \(Storage, querying\)

* Binary 
* Encoded & compressed 
* Columnar 
* "Machine friendly"
* Can handle arbitrary nested data  
* `.parquet` is folder 
* `.gz.parquet` is the data file 
* there is a parquet toll for reading parquet file from command line

![Parquet is columnar](../../.gitbook/assets/image%20%285%29.png)

![Structure and pushed filters \(more effective filtering\)](../../.gitbook/assets/image%20%286%29.png)

* Pushed filters - does not work with object stores \(e.g. random access\) 
* Fast reads 
* Immutability of files \(e.g. append will work\) 

