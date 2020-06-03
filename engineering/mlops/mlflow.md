# MLflow

## Overview 

* [MLflow Tracking](https://mlflow.org/docs/latest/tracking.html): An **API** to log parameters, code, and results in machine learning experiments and compare them using an interactive **UI.**
* [MLflow Projects](https://mlflow.org/docs/latest/projects.html): **A code packaging format** for reproducible runs using Conda and Docker, so you can share your ML code with others.
* [MLflow Models](https://mlflow.org/docs/latest/models.html): **A model packaging format** and tools that let you easily deploy the same model \(from any ML library\) to batch and real-time scoring on platforms such as Docker, Apache Spark, Azure ML and AWS SageMaker.
* [MLflow Model Registry](https://mlflow.org/docs/latest/model-registry.html): A centralized **model store**, set of APIs, and UI, to collaboratively manage the full lifecycle of MLflow Models.



* [Artifacts location](https://www.mlflow.org/docs/latest/tracking.html)

## MLflow + DBs

**Databricks provides a fully managed and hosted version of MLflow**

[Milan Berka](https://app.slack.com/team/U76HG61EY) [11:05 AM](https://datasentics.slack.com/archives/C7K7WJUMS/p1552212359037200?thread_ts=1552212359.037200) **- MLflow**  
Vcera jsem si asi hodku hral s MLflow. Je to fajn vec, mozna i zneuzitelna pro dalsi veci nez jenom logovani/persistovani/servovani ML modelu. Rozhodne ji doporucuju zacit inkorporovat do nasich ML projektu.**Dobre zdroje**:  
1. MLflow guide on Databricks:

> - [https://docs.databricks.com/applications/mlflow/index.html](https://docs.databricks.com/applications/mlflow/index.html)

2. MLflow oficialni dokumentace:

> -[https://www.mlflow.org/docs/latest/index.html](https://www.mlflow.org/docs/latest/index.html)

3. MLflow webinar od Databricks:

> - video: [http://mkto-ab270090.com/gS0BgCh06007MS0oY000Pxt](http://mkto-ab270090.com/gS0BgCh06007MS0oY000Pxt)  
> - slides: [http://mkto-ab270090.com/a0000h076Y0B00OSRMCxgto](http://mkto-ab270090.com/a0000h076Y0B00OSRMCxgto)  
> - sample notebook: [http://mkto-ab270090.com/O0x0tg6S0000CYhU0R0o7BM](http://mkto-ab270090.com/O0x0tg6S0000CYhU0R0o7BM)

**MLflow v nasem Databricks**:  
1. Cluster: TEST\_MLFLOW:

> - [https://dbc-5eaec41d-ac28.cloud.databricks.com/\#/setting/clusters/0301-155526-relay4/](https://dbc-5eaec41d-ac28.cloud.databricks.com/#/setting/clusters/0301-155526-relay4/)  
> - slaboucky cluster, na kterem si muzete otestovat mlflow. To znamena: ma pripnutou knihovnicku "mlflow' \(viz `/Libraries`\) a bezi na nem Datatabricks ML Runtime.  
> - diky [@Richard](https://datasentics.slack.com/team/UDSR45F5X) za vytvoreni

2. Ukazka notebooku, co inkorporuje mlflow:

> - [https://dbc-5eaec41d-ac28.cloud.databricks.com/\#notebook/134378/](https://dbc-5eaec41d-ac28.cloud.databricks.com/#notebook/134378/)

## MLflow + SageMaker

* [API](https://www.mlflow.org/docs/latest/python_api/mlflow.sagemaker.html)
* [Quick start deployment](https://docs.databricks.com/_static/notebooks/mlflow/mlflow-quick-start-deployment-aws.html)



\*\*\*\*

\*\*\*\*

