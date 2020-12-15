
# Setup kubernetes with MiniKube on Ubuntu AWS Ec2 Instance 

### MiniKube 

MiniKube used to Run the Kubernetes Locally. 

Minikube is a single-node Kubernetes cluster that you can use locally in your own development machine to test your Kubernetes deployment scripts,
explore and study Kubernetes etc.

MiniKube is used for Development Purposes.

Minikube can’t be used in Production, as It’s One Node Machine.


### Steps to Setup kubernetes with MiniKube

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
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

chmod +x ./kubectl

sudo mv ./kubectl /usr/local/bin/kubectl

 kubectl version

```

#### Step 3 Install MiniKube
```sh

curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

chmod +x ./minikube

sudo mv ./minikube /usr/local/bin/minikube

sudo apt-get install conntrack  // this is dependecy for minicube 
```

#### Step 4 Execute MiniKube & Create Cluster

```sh

minikube start --vm-driver=none  // 

```

#### Step 5 Interact Cluster Using KubeCtl

```sh

Let’s create a Kubernetes Deployment using an existing image named
nginx, which is a simple HTTP server and expose it on port 80
using --port.

sudo kubectl create deployment nginx --image=nginx

Create the Service 
sudo kubectl create service nodeport nginx --tcp=80:80 

kubectl get svc

kubectl patch svc nginx -p '{"spec":{"externalIPs":["ipaddress"]}}'

```



#### Step 6 Inspect the pods and the deployments

```sh

kubectl get pods -A
kubectl get deployment

```


#### Step 7 Delete the Service and Deployment

```sh

kubectl delete services nginx
kubectl delete deployment nginx

```

#### Step 8 Stop MiniKube

```sh
Stop the local Minikube cluster:
minikube stop

```
