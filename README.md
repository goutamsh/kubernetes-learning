# Kubernetes

Kubernetes is a container orchestration software.

Kubernetes was originally incubated in Google.

Kubernetes = k8s

K8s allows us to-
1. orchestrate containers
2. View dataceneter as one computer, as a developer we don't care about which node our conatiner/app runs


## Architecture of Kubernetes

Kubernetes architecture consists of Masters and nodes (minions or worker nodes).
Kubernetes Cluster = masters + nodes

Diagram and expalination [here](https://phoenixnap.com/kb/understanding-kubernetes-architecture-diagrams)


### Master:
master = apiserver + cluster store (Key-value store, NoSQL) + Controller manager + Scheduler 
apiserver : is the front-end of the cluster and is the only component we talk to from outside
scheduler : is responsible for scheduling work to nodes, maintains resources etc
cluster store : is the memory of k8s cluster
Controller manager : controls nodes, endpoints etc

### Node:
Node = Kubelet + container Engine + kube proxy
Kubelet : k8s agent for node, observes apiserver (of master) for work assignements, reports back to master about the status
Conatiner Engine: Container mangement, pulls images, starts/stops container
Kube proxy : kubernetes networking, assigning IP for individual pod, one IP per pod, all containers within the pod share same IP.
			Also does the load balancing for services

### POD:
POD : atomic unit of deployment/scheduling and can contain one or more containers, also atomic unit for scaling,
It's only available when it's completely ready.
A pod resides only on one node, it can't be on multiple nodes at the same time, meaning it can't be like half of the pod is in one node and another half in another node. 
container always runs inside the pods.
All the conatiners in a pod share single IP and they can't share same port inside same pod. Those containers also share same network namespace, cgroup and namespace.
The inter pod communication takes place through pod network.
Intra pod communication within the same pod between the conatiner happens using localhost.
Pods get defined declaratively in the manefest file.


### Replication Controller:
k8s objects used to scale pods and maintain desired state.
K8s continuously run background reconciliation loop to check and match the actual state to the desired state.

### Services:
Services k8s REST objects just like pod and deployment, that provide stable IP, dns name and port in the world of uncertain pods. 
The IP, dns name and port do not change for a service.
It just provides abstraction. Services provide the stable way of accessing the pods using single IP, dns and port.

They leverage the labels to route traffic to pods.
load balances the traffic to multiple pods

### Deployments:
Replication Controller + Rolling updates and rollback

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


Deploy First pod:

```
Create pod :

kubectl create -f pod.yml

Get pods:

kubectl get pods
kubectl get pods/hello-pod
kubectl get pods --all-namespaces

Delete pod:

kubectl delete pods hello-pod

Get replication controllers:

kubectl get rc

Update changes to yml file:

kubectl apply -f replicationController.yml

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


Stop minikube:
minikube stop

```

