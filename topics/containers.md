# What are Containers? Introduction to Docker, and Kubernetes.

## Table of Contents
# What are containers?
```
Containers are lightweight packages of your application code together
with dependencies such as specific versions of programming language
runtimes and libraries required to run your software services.

In the simplest terms, a container includes both an application's code and
everything that code needs to run properly.
```

**Containers help Build, Ship, Deploy, and Scale with ease.**

## Comparing Traditional Deployment with Container Deployment

### Traditional Deployment
In traditional deployment, applications were deployed on VMs or on physical machines.    
![Screen Shot 2022-07-08 at 11.23.34 AM.png](https://i.imgur.com/r32j25S.png)  
In this instance, we have a a dependency hell and moving this application to another machine will result in a lot of time-consuming tasks and headhache.

### Containerized Deployment
In containerized deployments, the application comes along with all its dependencies so if it's moved from one machine to another, there is no installation time and ensures that the proper library and dependency versions are installed.
![Containerized-Deployment-Diagram](https://i.imgur.com/gofxEa0.png)  
In this case, **we see that each small component of the application and its respective libraries and dependencies are isolated from one another and moving the application instance to another machine is seamless as it allows for all the required tools to come together within a container.**
## Benefits of Containers
* **Separation of Responsibility**: Software Developers can focus more on application logic and IT specialists are able to focus more on deployment and management rather than minute software details.
* **Workload Portability**: Containers are able to be ran anywhere, allowing it to be highly accessible.
* **Application Isolation**: Software Developers are able to view CPU, memory, storage, and network usage from their application in isolation from other applications.

# Containers vs VMs
The main similarity between Containers and VMs are that they allow the packaging of application required dependencies and that they run in an isolated environment.

But the **main difference between containers and VMs** are that **containers are isolated/abstracted away from the underlying operating system and infrastructure that they run on.**

Key Differences between the two are:
* Containers are much more lightweight than VMs 
* Containers show hardware usage at the OS level (so for your specific application instance) while VMs will show hardware usage at the hardware level (with the potential of other operations outside of your application being accounted for)
* Containers share the OS kernel and use a fraction of the memory VMs require

# What are Containers used for?
Containers are a **logical packaging mechanism** that abstracts the application from the actual environment that it runs in.

* **Agile Development**: Developers aren't wasting time on ensuring that the proper dependencies and tools are installed to run and work on the application.
* **Efficient Operations**: Containers are lightweight and only have you use the computing resources that you need.
* **Run Anywhere**: Wherever you want to run your software, just use a container.

# Docker
## What is Docker?
**Docker is a platform that helps build containers.** It separates the applications from the underlying infrastructure and helps reduce the time of the build, ship, test, and deploy life cycle.

## Docker Architecture
![Docker Architecture Digram](https://i.imgur.com/IUvgj43.png)  
A client communicates with the Docker daemon (that can be on the same system or on a remote system). The daemon does the heavy lifting of building, running, and distributing your Docker containers.  

## Docker Daemon (dockerd)
Listens for Docker API requests and is responsible for managing Docker objects (images, containers, volumes, etc).
## Docker Client (docker)
Sends Docker API requests.  
  
### Example of `docker run` command:
```
 docker run -i -t ubuntu /bin/bash
```  
The following command runs an `ubuntu` container, attaches interactively to your local command-line session, and runs /bin/bash.
# Container Orchestration
## What is Container Orchestration?
It is the automation of the operational effort needed to run containerized workloads and services (i.e of operational workloads: provisioning, deployment, scaling, load balancing, etc).

## Benefits of Container Orchestration
* **Simplified Operations**: Having hundreds or thousands of containers in your containerized application can get messy; container orchestration helps manage all that.
* **Easily Reset and Scale Containers**: Container orchestration allows for containers to be easily reset or scaled.
* **Extra Security**: Removes the chance of human error that may leave security vulnerabilities.

# Kubernetes
## What is Kubernetes?
**Kubernetes is the industry standard for container orchestration.** It helps streamline the process of creating containerized applications and services, as well as scale and monitor those containers.

**Kubernetes is also very nice due to its highly-declarative nature**; allowing for developers to describe how they want a system to behave with Kubernetes knowing how to create that for them.
# Resources Utilized  
[Google Cloud: What are containers?](https://cloud.google.com/learn/what-are-containers)  
[Cloud Native  Wiki: Container Cloud Computing](https://www.aquasec.com/cloud-native-academy/docker-container/container-cloud-computing/)  
[Containers - Explained in 4 Minutes](https://www.youtube.com/results?search_query=containers+cloud+computing+explained)  
[VMWare - What is container orchestration?](https://www.vmware.com/topics/glossary/content/container-orchestration.html?resource=cat-1848410832#cat-1848410832)  
[How to explain Kubernetes in plain English](https://enterprisersproject.com/article/2017/10/how-explain-kubernetes-plain-english)  
[What is container orchestration?](https://www.vmware.com/topics/glossary/content/container-orchestration.html?resource=cat-1848410832#cat-1848410832)  
[Docker Overview](https://docs.docker.com/get-started/overview/)  
