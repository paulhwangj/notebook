# Containers in Cloud Computing

# What are containers?
```
Containers are lightweight packages of your application code together
with dependencies such as specific versions of programming language
runtimes and libraries required to run your software services.
```

**Containers help Build, Ship, Deploy, and Scale with ease.**

## Comparing Traditional Deployment with Container Deployment

### Traditional Deployment
In traditional deployment, applications were deployed on VMs or on physical machines.    
![Screen Shot 2022-07-08 at 11.23.34 AM.png](oAH9fmnC8-Screen Shot 2022-07-08 at 11.23.34 AM.png)  
In this instance, we have a a dependency hell and moving this application to another machine will result in a lot of time-consuming tasks and headhache.

### Containerized Deployment
In containerized deployments, the application comes along with all its dependencies so if it's moved from one machine to another, there is no installation time and ensures that the proper library and dependency versions are installed.
![Screen Shot 2022-07-08 at 11.28.33 AM.png](CJaqjK_tD-Screen Shot 2022-07-08 at 11.28.33 AM.png)  
In this case, we see that each small component of the application and its respective libraries and dependencies are isolated from one another and moving the application instance to another machine is seamless as it allows for all the required tools to come together within a container.
## Benefits of Containers
* **Separation of Responsibility**: Software Developers can focus more on application logic and IT specialists are able to focus more on deployment and management rather than minute software details.
* **Workload Portability**: Containers are able to be ran anywhere, allowing it to be highly accessible.
* **Application Isolation**: Software Developers are able to view CPU, memory, storage, and network usage from their application in isolation from other applications.

# Containers vs VMs
The main similarity between Containers and VMs are that they allow the packaging of application required dependencies and that they run in an isolated environment.

Key Differences between the two are:
* Containers are much more lightweight than VMs 
* Containers show hardware usage at the OS level (so for your specific application instance) while VMs will show hardware usage at the hardware level (with the potential of other operations outside of your application being accounted for)
* Containers share the OS kernel and use a fraction of the memory VMs require

# What are Containers used for?
Containers are a **logical packaging mechanism** that abstracts the application from the actual environment that it runs in.

* **Agile Development**: Developers aren't wasting time on ensuring that the proper dependencies and tools are installed to run and work on the application.
* **Efficient Operations**: Containers are lightweight and only have you use the computing resources that you need.
* **Run Anywhere**: Wherever you want to run your software, just use a container.

# What is Container Orchestration?
It is the automation of the operational effort needed to run containerized workloads and services (i.e of operational workloads: provisioning, deployment, scaling, load balancing, etc).

# What is Kubernetes?
some text here
# Resources Utilized  
[Google Cloud: What are containers?](https://cloud.google.com/learn/what-are-containers)  
[Cloud Native  Wiki: Container Cloud Computing](https://www.aquasec.com/cloud-native-academy/docker-container/container-cloud-computing/)  
[Containers - Explained in 4 Minutes](https://www.youtube.com/results?search_query=containers+cloud+computing+explained)  
[VMWare - What is container orchestration?](https://www.vmware.com/topics/glossary/content/container-orchestration.html?resource=cat-1848410832#cat-1848410832)  
[How to explain Kubernetes in plain English](https://enterprisersproject.com/article/2017/10/how-explain-kubernetes-plain-english)  
