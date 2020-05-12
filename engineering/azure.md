# Azure

{% embed url="https://docs.microsoft.com/en-us/azure/aks/kubernetes-walkthrough" %}

{% embed url="https://docs.microsoft.com/en-us/azure/aks/gpu-cluster" %}

By following the doc above:

* Get location names: `az account list-locations -o table`
* Run GPU cluster \(command set\):

  * \[ manually \] create cluster in a new resource group \(west europe region\)
    * the following command [does not work](https://github.com/Azure/azure-cli/issues/5190)`az aks create  --resource-group myResourceGroup  --name myAKSCluster  --node-vm-size Standard_NC6  --node-count 1`
  * `az aks get-credentials --resource-group alekstest --name mainCluster`
  * `az aks install-cli`
  * `kubectl create namespace gpu-resources`
  * create `nvidia-device-plugin-ds.yaml` as in doc
  * `$kubectl apply -f nvidia-device-plugin-ds.yaml`
  * create `samples-tf-mnist-demo.yaml`as in doc 
  * `$kubectl apply -f samples-tf-mnist-demo.yaml` 
  * Watch progress:
    * `$kubectl get jobs samples-tf-mnist-demo --watch`

  `NAME                    COMPLETIONS   DURATION   AGE`

  `samples-tf-mnist-demo   1/1           2m28s      3m36s`

  * `$kubectl get pods --selector app=samples-tf-mnist-demo`
  * `$kubectl logs samples-tf-mnist-demo-j6h9h`

    `2020-05-12 18:40:49.733928: I tensorflow/core/platform/cpu_feature_guard.cc:137] Your CPU supports instructions that this TensorFlow binary was not compiled to use: SSE4.1 SSE4.2 AVX AVX2 FMA`

    `2020-05-12 18:40:49.854974: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1030] Found device 0 with properties:` 

    `name: Tesla K80 major: 3 minor: 7 memoryClockRate(GHz): 0.8235`

    `pciBusID: f639:00:00.0`

    `totalMemory: 11.17GiB freeMemory: 11.11GiB`

    `2020-05-12 18:40:49.855022: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1120] Creating TensorFlow device (/device:GPU:0) -> (device: 0, name: Tesla K80, pci bus id: f639:00:00.0, compute capability: 3.7)`

    `2020-05-12 18:40:54.529359: I tensorflow/stream_executor/dso_loader.cc:139] successfully opened CUDA library libcupti.so.8.0 locally`

    `Successfully downloaded train-images-idx3-ubyte.gz 9912422 bytes.`

    `Extracting /tmp/tensorflow/input_data/train-images-idx3-ubyte.gz`

    `Successfully downloaded train-labels-idx1-ubyte.gz 28881 bytes.`

    `Extracting /tmp/tensorflow/input_data/train-labels-idx1-ubyte.gz`

    `Successfully downloaded t10k-images-idx3-ubyte.gz 1648877 bytes.`

    `Extracting /tmp/tensorflow/input_data/t10k-images-idx3-ubyte.gz`

    `Successfully downloaded t10k-labels-idx1-ubyte.gz 4542 bytes.`

    `Extracting /tmp/tensorflow/input_data/t10k-labels-idx1-ubyte.gz`

    `Accuracy at step 0: 0.1176`

    `Accuracy at step 10: 0.706`

    `Accuracy at step 20: 0.8223`

    `Accuracy at step 30: 0.859`

    `Accuracy at step 40: 0.8817`

    `Accuracy at step 50: 0.8854`

    `Accuracy at step 60: 0.9031`

    `Accuracy at step 70: 0.9023`

    `Accuracy at step 80: 0.9078`

    `Accuracy at step 90: 0.9145`

    `Adding run metadata for 99`

    `Accuracy at step 100: 0.915`

    `Accuracy at step 110: 0.9171`

    `Accuracy at step 120: 0.9195`

    `Accuracy at step 130: 0.9241`

    `Accuracy at step 140: 0.9261`

    `Accuracy at step 150: 0.9276`

    `Accuracy at step 160: 0.9237`

    `Accuracy at step 170: 0.9261`

    `Accuracy at step 180: 0.9283`

    `Accuracy at step 190: 0.9309`

    `Adding run metadata for 199`

    `Accuracy at step 200: 0.9281`

    `Accuracy at step 210: 0.9347`

    `Accuracy at step 220: 0.9338`

    `Accuracy at step 230: 0.9389`

    `Accuracy at step 240: 0.9377`

    `Accuracy at step 250: 0.9398`

    `Accuracy at step 260: 0.9367`

    `Accuracy at step 270: 0.9415`

    `Accuracy at step 280: 0.9407`

    `Accuracy at step 290: 0.9437`

    `Adding run metadata for 299`

    `Accuracy at step 300: 0.9425`

    `Accuracy at step 310: 0.9439`

    `Accuracy at step 320: 0.9443`

    `Accuracy at step 330: 0.9401`

    `Accuracy at step 340: 0.9455`

    `Accuracy at step 350: 0.9495`

    `Accuracy at step 360: 0.9485`

    `Accuracy at step 370: 0.9504`

    `Accuracy at step 380: 0.9506`

    `Accuracy at step 390: 0.9518`

    `Adding run metadata for 399`

    `Accuracy at step 400: 0.951`

    `Accuracy at step 410: 0.9507`

    `Accuracy at step 420: 0.9528`

    `Accuracy at step 430: 0.9534`

    `Accuracy at step 440: 0.9526`

    `Accuracy at step 450: 0.9544`

    `Accuracy at step 460: 0.9549`

    `Accuracy at step 470: 0.9544`

    `Accuracy at step 480: 0.9541`

    `Accuracy at step 490: 0.955`

    `Adding run metadata for 499`

  \`\`

* \[ optional \] open k8s console:  `az aks browse --resource-group alekstest --name mainCluster`



