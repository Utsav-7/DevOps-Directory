# Kubernetes Fundamentals

Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. It provides a framework for deploying, managing, and scaling applications across a cluster of machines.

## Key Concepts

### 1. Pods
   - Pods are the smallest deployable units in Kubernetes, representing one or more containers that share networking and storage.
   
### 2. ReplicaSets
   - ReplicaSets ensure that a specified number of pod replicas are running at any given time. They help in scaling and ensuring high availability.
   
### 3. Deployments
   - Deployments manage the lifecycle of pods and ReplicaSets. They enable rolling updates and rollbacks of application changes.
   
### 4. Services
   - Services define a logical set of pods and a policy by which to access them. They provide a stable IP address and DNS name for accessing the pods.
   
### 5. Ingress
   - Ingress exposes HTTP and HTTPS routes from outside the cluster to services within the cluster. It offers routing rules for directing incoming traffic to the appropriate services.
   
### 6. ConfigMaps and Secrets
   - ConfigMaps store non-sensitive configuration data, while Secrets store sensitive data such as passwords or API keys. They allow decoupling configuration from container images.

## Basic Operations

### 1. Deployment
   - Create a deployment: `kubectl create deployment <deployment-name> --image=<image-name>`
   - Scale a deployment: `kubectl scale deployment <deployment-name> --replicas=<replica-count>`
   - Update a deployment: `kubectl set image deployment/<deployment-name> <container-name>=<new-image>`
   - Rollback a deployment: `kubectl rollout undo deployment/<deployment-name>`

### 2. Service
   - Expose a deployment: `kubectl expose deployment <deployment-name> --port=<port>`
   - List services: `kubectl get services`

### 3. Pod
   - Create a pod: `kubectl run <pod-name> --image=<image-name>`
   - List pods: `kubectl get pods`
   - Describe a pod: `kubectl describe pod <pod-name>`
   
## Getting Started

To get started with Kubernetes, you can:
- Install Minikube for local development and testing.
- Use managed Kubernetes services like Google Kubernetes Engine (GKE), Amazon Elastic Kubernetes Service (EKS), or Microsoft Azure Kubernetes Service (AKS).
- Explore Kubernetes documentation and tutorials to learn more about its features and best practices.

## Resources:
- Lens: [https://k8slens.dev/](https://k8slens.dev/)
- Kubescape - [https://hubs.la/Q012KVqQ0](https://github.com/kubescape/kubescape)
- Monokle: [https://github.com/kubeshop/monokle](https://github.com/kubeshop/monokle)
- Datree: [https://www.datree.io/](https://www.datree.io/)
- Teleport: [http://goteleport.com/](https://goteleport.com/)
- Civo: [https://www.civo.com/academy](https://www.civo.com/academy)
