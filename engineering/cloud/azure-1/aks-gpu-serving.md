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
* Error: waiting for creation of Managed Kubernetes Cluster "gpucluster" \(Resource Group "gpuAksResourceGroup"\): Code="CreateVMSSAgentPoolFailed" Message="We are unable to serve this request due to an internal error, Correlation ID: 2973e2ed-9219-356b-2319-867aba0a988b, Operation ID: 45b70663-069a-4e99-a710-5c144226e26f, Timestamp: 2020-06-09T07:29:59Z." 
  *  [https://github.com/Azure/AKS/issues/1189](https://github.com/Azure/AKS/issues/1189) 
* Fails: 
  * Release 18.09 is based on CUDA 10, which requires [NVIDIA Driver](http://www.nvidia.com/Download/index.aspx?lang=en-us) release 410.xx. However, if you are running on Tesla \(Tesla V100, Tesla P4, Tesla P40, or Tesla P100\), you may use NVIDIA driver release 384. For more information, see [CUDA Compatibility and Upgrades](https://docs.nvidia.com/cuda/cuda-c-best-practices-guide/index.html#cuda-compatibility-and-upgrades). - from [https://docs.nvidia.com/deeplearning/tensorrt/container-release-notes/rel\_18.09.html](https://docs.nvidia.com/deeplearning/tensorrt/container-release-notes/rel_18.09.html)
  * set k8s version - [https://www.gitmemory.com/issue/Azure/AKS/937/533069544](https://www.gitmemory.com/issue/Azure/AKS/937/533069544)

