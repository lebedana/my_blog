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

###  ****

\*\*\*\*

