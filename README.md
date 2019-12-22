# Kubernetes

Kubernetes is a container orchestration software.

Kubernetes was originally incubated in Google.

Kubernetes = k8s

## Architecture of Kubernetes

Kubernetes architecture consists of Masters and nodes (minions or worker nodes).

Diagram and expalination [here](https://phoenixnap.com/kb/understanding-kubernetes-architecture-diagrams)



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

Add kubernetes service (this can also be done via manifest file see svc.yml):

kubectl expose rc hello-rc --name=hello-svc --target-port=8080 --type=NodePort


Describe service:

kubectl describe svc hello-svc

Get services:

kubectl get svc

To get the service url from minikube:

minikube service hello-svc --url

Get endpoints:

kubectl get ep


```
pod.yml file is [here](https://github.com/goutamsh/kubernetes-learning/blob/master/pod_manifest/pod.yml)

With minikube we can create only cluster with only one node.

Creating service in declarative way via manifest file  (i.e svc.yml)
```
kubectl create -f svc.yml
```

#### Kubernetes Deployments:

Deployment is another type of kubernetes object, helpful for updates and rollbaks
```
kubectl create -f deployment.yml

Get replication sets:
kubectl get rs

```

