# AKS GPU serving

{% embed url="https://docs.microsoft.com/en-us/azure/machine-learning/how-to-deploy-inferencing-gpus" %}

### 

* Create application workspace 
* Create AKS cluster 

### Using Azure ML

* create entry script 
* define env. configuration \(conda environment\)
* define deployment configuration \(e.g. \#of nodes, resources for container the application\)
* define the inference configuration 
  * provide yaml with conda env confg, and the entry\_script
  * the environment should also container docker image which will be used as base \(myenv.docker.base\_image\)
* Create a model or used a registerd model \(e.g. "tf-dnn-mnist"\)
* deploy the model to an AKS cluster

  `aks_service = Model.deploy(ws, models=[model],  inference_config=inference_config, deployment_config=gpu_aks_config, deployment_target=aks_target, name=aks_service_name)`

Advantages:

Disadvantages:

### Using a general docker image

{% embed url="https://docs.microsoft.com/en-us/azure/devops/pipelines/apps/cd/deploy-aks?view=azure-devops&tabs=python" %}

{% embed url="https://docs.microsoft.com/en-us/azure/aks/cluster-container-registry-integration" %}

{% embed url="https://dwaiba.github.io/aks-terraform/\#aks-gpu-cluster" %}

{% embed url="https://docs.microsoft.com/en-us/azure/container-instances/container-instances-gpu" caption="Description of container images and requirements " %}

Try without enabling GPU drivers: 

{% embed url="https://docs.microsoft.com/en-us/azure/aks/gpu-cluster" %}



Fails: 

* TF 1.12 fails with \(e.g. combination with version of cuda [https://github.com/tensorflow/tensorflow/issues/26209](https://github.com/tensorflow/tensorflow/issues/26209)\) - mportError: libcuda.so.1: cannot open shared object file: No such file or directory
* conda run output result of command only after command is finished - is the only working option for container
* AKS deploy cluster - sometimes fails on internal error when creating a cluster in western europe [https://github.com/Azure/AKS/issues/1189](https://github.com/Azure/AKS/issues/1189) 

