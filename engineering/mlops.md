# MLOps

{% embed url="https://tecton.ai/blog/devops-ml-data/" %}

ML data \(features and labels\) challenging arias:

* Accessing the right raw data source
* Building features from raw data
* Combining features into training data
* Calculating and serving features in production
* Monitoring features in production

### [Tecton](https://tecton.ai/blog/data-platform-ml/)

* Data Managing Platform 
* Has api integration with ML platforms \(DB, Sagemaker, Kubeflow\) 
* Is in preview 
* consists of:
  1. **Feature Pipelines** for transforming your raw data into features or labels
  2. A **Feature Store** for storing historical feature and label data
  3. A **Feature Server** for serving the latest feature values in production
  4. An **SDK** for retrieving training data and manipulating feature pipelines
  5. A **Web UI** for managing and tracking features, labels, and data sets
  6. A **Monitoring Engine** for detecting data quality or drift issues and alerting

