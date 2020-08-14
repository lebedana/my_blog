# Fundamentals of Delta Lake

### Q to check: 

* Column-like data format 
* Partitioning \(and physical plan\)

### Terms and key concepts

* Cloud data platform 

![](../../../.gitbook/assets/image%20%283%29.png)

Warehouses 

* mainly deal with structured data 
* not able to handle high variety, velocity and volume 
* not cost-efficient 

Data lakes

* repos for raw data in variety of formats 
* do not support ACID transactions
* do not enforce data quality 

Data lakehouse 

* storage decoupled from compute 
* support diverse data types 
* support diverse workloads \(SQL, analytics, data science...\)  
* end-to-end streaming 
* transaction support 

### Delta Lake

For intro to delta lake see "DB Partner Capstone" page

Delta data format  - based on parquet + log + meta = versining +  ACID features

* Delta Files
* Delta log 
* Delta table registered in a metastore

**Delta optimization engine** provides several **optimization** features,  applied when reading and writing to Delta Lake 

Users interact with Delta tables \(registered\) as with **any SQL table**  

### **The Power of Delta Lake**

* separation of compute and storage \(scalability, availability, and cost\)

**The Inmon Architecture -** Enterprise Decision Support Sytems \(EDSS\).

![](../../../.gitbook/assets/image%20%284%29.png)

Challenges of on-prem data warehouses: 

* scalability 
* associated cost
* limited data types \(structured\)
* high data gravity 
* data duplication **\(?\)**

### **Cloud-based data warehouse**

* Sep of compute and storage 
* Elastic resource allocation 
* CDWs are optimized for concurrent queries
* Less maintenance required 

Challenges

* Structured data only 
* Medium data gravity \(because of data types & associated ETL costs\)
* CDWs often are not flexible in optimizing \(e.g. do not allow custom indexing, ...\) 
* Data Lake in \(mostly\) not queryable \(only ETL\) 

### Cloud data platform

* all adv of data warehouses 
* low data gravity \(any format\)
* mix batch and streaming 

Challenges: 

* poor interactive query experience 
* limited concurrence handling capability   

### Managed delta

* **Optimize -** combine small files into big one \(1Gb\) 
* **Data Skipping** is a performance optimization that aims at speeding up queries that contain filters \(WHERE clauses\).
* **ZOrdering** is a technique to colocate related information in the same set of files.

Q: 

* Data platform includes processing framework \(spark\) + possible analytic platform + BI - ?  

\*\*\*\*

