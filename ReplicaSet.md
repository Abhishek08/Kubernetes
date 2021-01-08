
# ReplicaSet In Kubernets 


#### Replica Set is enhance version of Replication Controller

#### ReplicaSet’s purpose is to maintain a stable set of replica Pods running at any given time.

#### Difference between Replication controller vs ReplicaSet

#### ReplicaSet :- 

Replica Set : Replica Set supports the new set-based selector. This gives more flexibility. 
Ex. environment in (production, qa) This selects all resources with key equal to environment and equal to production or qa

Replication Controller : Replication Controller only supports equality-based selector.
Ex. environment = production
This selects all resources with key equal to environment and value equal to production

#### Operators to use with ReplicaSets

There are three kinds of operator we can use with ReplicaSets:

* In
* Notin
* Exists


#### MatchLabels ReplicaSet Example 

```sh

apiVersion: apps/v1  # our API version
kind: ReplicaSet # # The kind we are creating
metadata: # Specify all Metadata like name, labels
 name: frontend
 labels:
   app: myReplica
spec:
  replicas: 3 # Here is where we tell k8s how many replicas we want
  selector:   # This is our label selector field. 
    matchLabels: 
      app: frontend   # we are using the Equality based operators
  template:
    metadata:
      labels:
        app: frontend   
    spec:
      containers:  
        - name: php-redis
          image: gcr.io/google_samples/gb-frontend:v3
          
          
_______________________________________________________

Creating normal pod 

apiVersion: v1
kind: Pod
metadata:
  name: pod1
  labels:
    app: frontend
spec:
  containers:
  - name: hello1
    image: gcr.io/google-samples/hello-app:2.0
---
apiVersion: v1
kind: Pod
metadata:
  name: pod2
  labels:
    app: frontend
spec:
  containers:
  - name: hello2
    image: gcr.io/google-samples/hello-app:1.0
		  

```
#### Match Selector 

```sh

apiVersion: apps/v1  # our API version
kind: ReplicaSet # # The kind we are creating
metadata: # Specify all Metadata like name, labels
 name: frontend
 labels:
   app: frontend
spec:
  replicas: 3 # Here is where we tell k8s how many replicas we want
  selector:   # This is our label selector field.
    matchExpressions:
      - key: app1
        operator: In
        values:
         - qa
  template:
    metadata:
      labels:
        app1: qa
    spec:
      containers:
        - name: php-redis
          image: gcr.io/google_samples/gb-frontend:v3
_________________________________________________________

Creating normal Pods 

Creating normal pod 

apiVersion: v1
kind: Pod
metadata:
  name: pod1
  labels:
    Enviourment: qa
spec:
  containers:
  - name: hello1
    image: gcr.io/google-samples/hello-app:2.0
---
apiVersion: v1
kind: Pod
metadata:
  name: pod2
  labels:
    Enviourment: test
spec:
  containers:
  - name: hello2
    image: gcr.io/google-samples/hello-app:1.0
		  

