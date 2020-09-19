# Azure Kubernetes Walk-Through Presentation

## Quick Links

[Kubernetes Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) </br>
[Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) </br>
[Kubectl CLI](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

---

## Quick Azure Command Line Sequences

1. az login

2. az account set --subscription {GUID}

3. az aks get-credentials -g aks -n aks-demo

4. kubectl get nodes

5. kubectl apply -f .\deployment.yml

6. kubectl get deployment

7. kubectl get pods

8. az aks browse -g aks -n aks-demo

## Execute the following sequence if Kubernetes Dashboard not loading correctly

kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard

kubectl get all

kubectl delete deployment.apps/dotnetapi-deployment

kubectl delete service/dotnetapi-service

---

## What is Azure Kubernetes Service

A managed container orchestration service based on the open source Kubernetes system. You can use AKS to deploy, scale, manage containers across a cluster of hosts.

### So what is Kubernetes a.k.a (K8)

It is an open source container orchestrator developed by Google that help manage clusters. It tries to remove the overhead of manual process involved in deploying and scaling application in an infrastructure environment. The development of this software is based on Google Borg which is another orchestrator they use internally that support Google infrastructure.

### Who uses Kubernetes

AirBnb, New York Times, Reddit, and more. Often with one common theme in there implementation which is to rapidly deploy and scale critical services to large volumes of request. In addition to micro service architecture a lot of people are using Kubernetes to help facilitate machine learning by scaling services based on amount of data ingested to be processed by the cluster for models developed on the fly through agile CI/CD process.

## Benefits of using Azure Kubernetes Service

- Reduced management overhead for admins and developers. Such as configuring the master and worker nodes, Azure AD integration, monitoring, network, and routing.
- Managed means that Microsoft handle all upgrades to the underlying software frameworks, and master controller.
- Scaling based on work load density.
- Supports process work loads on GPU (graphic processing units) nodes, great for ML or IoT processing.
- Its free, you only play for the underlying VM compute, storage, networking consumed by the containers. (This may change in the future, as Amazon AWS charges a flat fee for a similar service.)
- Compliant with SOC, ISO, PCI, SDD, and HIPPA.

## What is a Container

A virtual machine provides an (HAL) hardware abstraction layer to an underlying machine/operating system and physically is an image of a system running in an isolated sandbox. A common case is people spinning up a virtual machine to host an application with all the overhead of licensing virtual cpu/ram allocation associated with the process.

A container take this concept one step further by creating an abstraction layer on host operating system kernel, the advantage of this is running multiple application in an ‘isolated’ fashion on a virtualized machine. This enables multiple work loads to run on node as long as compute is available, in addition this makes the application neutral to the environment configuration of the guest operating system.

Many companies leverage this by building container clusters on Azure, AWS, on-premise, on the edge and enable seamless movement between the environment without the need of significant modernization or refactoring. This helps control cost and distribute infrastructure over multiple cloud providers and environments.

## What is Container Registry

When building a container the output is a an image much like a virtual machine image, and often a registry is needed to help distribute to multiple hosts and mange the applications for deployment and versioning.  (Azure Container Registry and Artifactory)

![acr.png](/acr.png)

## Key Concepts for Kubernetes

## Kubernetes Master

The Kubernetes master is responsible for maintaining the desired state for your cluster. When you interact with Kubernetes, such as by using the kubectl command-line interface, you’re communicating with your cluster’s Kubernetes master.
The “master” refers to a collection of processes managing the cluster state. Typically all these processes run on a single node in the cluster, and this node is also referred to as the master. The master can also be replicated for availability and redundancy.

### Kubernetes Nodes

The nodes in a cluster are the machines (VMs, physical servers, etc) that run your applications and cloud workflows. The Kubernetes master controls each node; you’ll rarely interact with nodes directly.

### Basic

Pod – A process running in your cluster, and encapsulates single or multiple “tightly-coupled” containers as a single instance of deployment. Common use cases usually have 1:1 pod/container ratio.

Service – Abstract way to expose an application on a set of “Pods” as a network service, Kubernetes provides an cluster internal ip address/dns for Pod sets to be load balanced across the cluster, and a nodeport for publishing outside.

Volume – Storage is disconnected from containers, because if it crashes and new container is created all files will be lost. So a volume is created for file persistence and also to share files between containers running in a pod.

Namespace – This is another level abstraction as you can create multiple ‘virtual clusters’ within physical cluster to isolate environments. This is to accommodate multiple teams, projects, and environments.

### Abstractions

Deployment – Specify how many replicas of pod should run in a cluster, this ensure that many are running across the cluster.
DaemonSet – A DaemonSet ensures that all (or some) Nodes run a copy of a Pod. As nodes are added to the cluster, Pods are added to them. As nodes are removed from the cluster, those Pods are garbage collected. Deleting a DaemonSet will clean up the Pods it created.

StatefulSet – Manages the deployment and scaling of a set of Pods, and provides guarantees about the ordering and uniqueness of these Pods based on identical container spec.

ReplicaSet – A ReplicaSet’s purpose is to maintain a stable set of replica Pods running at any given time. As such, it is often used to guarantee the availability of a specified number of identical Pods.

Job – A Job creates one or more Pods and ensures that a specified number of them successfully terminate. As pods successfully complete, the Job tracks the successful completions. When a specified number of successful completions is reached, the task (ie, Job) is complete. Deleting a Job will clean up the Pods it created. (other: CronJob scheduled tasks)

![toplogy.png](/toplogy.png)

## Deciding Architectures

Container As-A Platform is complex and is not a replacement or silver bullet for every cloud application architecture. It is a tool that provides more control and flexibility over PaaS and provides a lot of features that current IaaS setups cannot do without significant configuration.

![caas.png](/caas.png)