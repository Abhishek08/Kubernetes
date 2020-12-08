
# Setup Kuberneted with MiniKube 

### MiniKube 

MiniKube used to Run the Kubernetes Locally. 

Minikube is a single-node Kubernetes cluster that you can use locally in your own development machine to test your Kubernetes deployment scripts,
explore and study Kubernetes etc.

MiniKube is used for Development Purposes.

Minikube can’t be used in Production, as It’s One Node Machine.


### Steps to Setup Kuberneted with MiniKube

#### Step 1 Install Docker 

```sh

sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
    
 curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
 
 sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io

````

#### Step 2 Install KubeCtl 

```sh

 curl -LO https://storage.googleapis.com/kubernetes-release/
release/$(curl -s https://storage.googleapis.com/kubernetes-release/
release/stable.txt)/bin/linux/amd64/kubectl

chmod +x ./kubectl

sudo mv ./kubectl /usr/local/bin/kubectl

 kubectl version

```

#### Step 3 Install MiniKube
```sh

curl -Lo minikube https://storage.googleapis.com/minikube/
releases/latest/minikube-linux-amd64 && chmod +x minikube

 sudo install minikube /usr/local/bin

```

#### Step 4 Execute MiniKube & Create Cluster

```sh

minikube start

```

#### Step 5 Interact Cluster Using KubeCtl

```sh

Let’s create a Kubernetes Deployment using an existing image named
echoserver, which is a simple HTTP server and expose it on port 8080
using --port.

kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.10 --
port=8080


In order to access the hello-minikube service, we must first expose
the deployment to an external IP via the command:

kubectl expose deployment hello-minikube --type=NodePort
kubectl get services

Get the URL of the exposed Service to view the Service details:
minikube service hello-minikube --url

Delete the Service 
kubectl delete services hello-minikube
kubectl delete deployment hello-minikube

Stop the local Minikube cluster:
minikube stop

```



#### Step 6 Inspect the pods and the deployments

```sh

kubectl get pod
kubectl get deployments

```


#### Step 7 Create the Service 

```sh

In order to access the hello-minikube service, we must first expose
the deployment to an external IP via the command:

kubectl expose deployment hello-minikube --type=NodePort
kubectl get services

Get the URL of the exposed Service to view the Service details:
minikube service hello-minikube --url

```


#### Step 9 Delete the Service and Deployment

```sh

kubectl delete services hello-minikube
kubectl delete deployment hello-minikube

```

#### Step 10 Stop MiniKube

```sh
Stop the local Minikube cluster:
minikube stop

```
