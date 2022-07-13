# AWS ECS (Elastic Container Service)

# What is ECS?
**Container orchestration tool** that allows you to run applications in the cloud without the need to configure or maintain the infrastructure.

AWS ECS supports the integration with various other AWS services (i.e: IAM, AWS EBS, and AWS ELB)

# Amazon ECS Architecture
**Example**: Amazon ECS with containers running on AWS Fargate
![Amazon ECS Diagram](https://i.imgur.com/MCzOXJy.png)
## Containers and Images
Containers are created from read-only templates called **images.**

**Images are usually built from a Dockerfile** that specifies what components are needed to run in the container. Once built, images can be stored in a container registry (i.e: AWS ECR) which then can be downloaded and ran on the cluster.

## AWS ECS Task Definitions
In order to prepare an application to be ran on Amazon ECS, you must specify **task definitions which (JSON format) that describes one or more containers that make up your application.**

**Job definition can specify parameters to configure your application** (i.e: what ports should be opened, exactly what containers should be ran, etc)

## AWS ECS Tasks and Scheduling
**Tasks are an instance of a task definition** that was created.  
  
The **Amazon ECS Task Scheduler is responsible for placing tasks in a cluster.**  
  
### Two Types of Scheduler Strategies:
* **The Replica Strategy**: Define a set number of tasks to be ran for the cluster and the scheduler will always ensure that at least that amount of tasks are running.
* **The DAEMON Strategy**: places one task on each active container instance that meets the relevant criteria.

## AWS ECS Cluster
An **AWS ECS Cluster is a logical group of tasks or services (which are made up of one or more tasks).**

Two options to run cluster resources:
* EC2 instances
* Amazon Fargate

### Container Agent
The container agent runs on EACH container instance. **It's main job is to communicate with ECS which will take information about currently running tasks and resource utilization and start and stop tasks accordingly.**

![Container Agent Diagram](https://i.imgur.com/RmoXfaS.png)
### AWS ECS Deployment Options: EC2 vs Fargate
**ECS can use EC2 instances to run containers.**
1. An EC2 instance is created and defined within a ECS cluster, allowing for that EC2 instance to deploy containers defined in the cluster.
2. These EC2 instances are also able to be defined in a VPC which allows them to access AWS resources running in that VPC.

**Fargate can also be used to run containers and Fargate is easier in that you aren't required to manage these servers/EC2 instances**, that work is now put on Amazon; meaning that the provisioning, configuring, and managing work is AWS' work now.
* Note: You cannot attach a storage volume to containers that are ran via Fargate so an external storage service (i.e: AWS S3) must be used.

### When to use EC2 vs Fargate
![EC2 or Fargate Diagram](https://i.imgur.com/FsXs7pB.png)
# How is Amazon ECS different from AWS Elastic Beanstalk?
AWS Elastic Beanstalk is up another rung in the ladder of automation in that it manages and automates the deployment, management, and scaling of your applications and services. AWS Elastic Beanstalk will automatically provision ECS clusters, do load balancing, etc. after you define the configuration.

# How is Amazon ECS different from AWS Lambda?
ECS supports the management of containers but **doesn't fully automate the process.** You're required to know the process of provisioning and must constantly configure and scale resources. The EC2 instances exposes servers and provides information needed to determine whether to scale and to optimize your environment.

AWS Lambda allows for the creation of a serverless application in that it lets you write the code that responds to an event-driven task (i.e: a website click, data change, etc).

# Optimizing Containers Storage with Cloud Volumes ONTAP
**NetApp Cloud Volumes ONTAP**: storage management solution that provides storage management services on AWS, Azure, and Google Cloud.  

Benefits of Cloud Volumes ONTAP
* Supports various use cases (file system, database, DevOPs, etc)
* High availability
* Data protection
* Storage efficiencies
* Kubernetes integration

# Resources Utilized
* [AWS ECS in Depth: Architecture and Deployment Options](https://cloud.netapp.com/blog/aws-cvo-blg-aws-ecs-in-depth-architecture-and-deployment-options#h_h2)