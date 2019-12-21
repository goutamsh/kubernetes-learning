# Kubernetes

Kubernetes is a container orchestration software.

Kubernetes was originally incubated in Google.

Kubernetes = k8s

## Architecture of Kubernetes

Kubernetes architecture consists of Masters and nodes (minions or worker nodes).

Diagram below:



## How to Install Kubernetes:

1. with minikube in developer machines to try, learn and get feel of it.

https://kubernetes.io/docs/tasks/tools/install-minikube/

2. Google Container Engine (GKE)

Google provides the direct support to create the kubernetes cluster in google cloud environment. It provides kubernetes as a service.

3. Installing Kubernetes in AWS using kops

4. Manually install using kubeadm


### Minikube:

Minikube installation steps can be found [here](https://kubernetes.io/docs/tasks/tools/install-minikube/)

In home edition Windows OS we can't use hyper-V instead we can install virtual box (Orcale VM)

####  Commands:
```
minikube start --vm-driver=virtualbox

minikube status

minikube dashboard

kubectl get nodes

kubectl get pods --all-namespaces
```

username/password to connet to minikube in virtualbox: docker/tcuser

#### Kubectl install:

https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-windows

Kubectl is kubernetes client. Independent of undelying infrastracture used. Underlying intra could be minikube, GKE, AWS of physical machine

Atomic unit of scheduling in kubernetes is pod

Pod can contain one or more containers

pods get scheduled on nodes

One pod gets desployed on one node only

Deploy First pod:

```
Create pod :

kubectl create -f pod.yml

Get pods:

kubectl get pods

Delete pod:

kubectl delete pods hello-pod

Add kubernetes service :

kubectl expose rc hello-rc --name=hello-svc --target-port=8080 --type=NodePort


Describe service:

kubectl describe svc hello-svc

Get services:

kubectl get svc

```
pod.yml file is [here]()


