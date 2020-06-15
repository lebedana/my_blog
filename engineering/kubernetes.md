# Kubernetes

* Pod
  * a group of containers sharing resources
  * is assigned with a single IP address
  * is a minimal deployment unit
  * has to be deployed within a single Node
  * Within the pod, all containers can reference each other on localhost
* Node

## Commands

#### Service

* `kubectl expose deployment fors --type=LoadBalancer --name=fors-service` -expose ip for a deployment \(app\)
* `kubectl get services fors-service` - get service description 

#### Log/info

* `kubectl describe pod -n gpu-resources` - describe specific pod 
* `kubectl describe all` - describe all resources 
* `kubectl get pods` - git all pods
* `kubectl logs fors-69d57685c8-g7zls` - get logs for a pod

#### Create/update resource 

`kubectl apply -f deploy/config/fors_gpu_deployment.yaml` - create a resource from file 

#### Redeploy 

`kubectl delete pod fors-69d57685c8-wsrff --grace-period=0 --force` - delete pod \(do we need all those parameters and why?\)

#### Delete a resource 

* `kubectl get all`  - get resource ref
*  `kubectl delete deployment.apps/fors`

