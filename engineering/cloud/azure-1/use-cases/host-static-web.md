# Host static web

## App Service - [overview](https://docs.microsoft.com/en-us/azure/app-service/overview) <a id="app-service-overview"></a>

* .NET, .NET Core, Java, Ruby, Node.js, PHP, or Python.
* Windows and Linux-based environments
* security, load balancing, autoscaling, and automated management.
* CI/CD
  * Azure DevOps, GitHub, Docker Hub

from the overview "Besides App Service, Azure offers other services that can be used for hosting **websites** and **web applications**. For most scenarios, App Service is the best choice.

Q to concern: 

* **websites** and **web applications**
* $ - there will be VM behind 
* build new version --&gt; build new image \(time, costs, complexity\)
* who is responsible for app health check 

How to: 

* [https://docs.microsoft.com/en-us/azure/app-service/app-service-web-get-started-html](https://docs.microsoft.com/en-us/azure/app-service/app-service-web-get-started-html)

## Azure Storage[ ](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website-how-to?tabs=azure-portal) <a id="host-a-static-website-in-azure-storage"></a>

* [enable hosting ](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website-how-to?tabs=azure-portal)
* [host static web ](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website)

## Azure Static Web Apps <a id="what-is-azure-static-web-apps-preview"></a>

* Once you've enabled metrics, traffic statistics on files in the **$web** container are reported in the metrics dashboard.
* To "build a **web applicatio**n using your preferred front-end **framework** from a GitHub repository."  - franeworks: angular, react, vue, no framework 
* result is static \(no blackened runs\)

{% embed url="https://docs.microsoft.com/en-us/azure/static-web-apps/overview\#:~:text=Static%20web%20apps%20are%20commonly,alongside%20any%20required%20API%20endpoints." %}















