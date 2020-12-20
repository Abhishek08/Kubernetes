

# Replication Controller RC  in Kubernetes

A replication controller (RC) is a supervisor for long-running pods. An RC will launch a specified number of pods called replicas and makes sure that they keep running

Ensure that specified number of pords running at any time.

If any extra pods are running it will kill that pod and vice varsa.

New Pod get launch when they get fail, get deleted or terminited. 


### Advantage of Replication Controller 

1. High Availability 
2. Load Balancing 


### Relication Controller Manifest file

Below are the segments need to define in Relication Controller Manifest file.

1. API verion 
2. MetaData
3. Speficaication
4. Template 

```sh
apiVersion: v1
kind: ReplicationController
metadata:   // MetaData contain 2 things name and Label (optional). Name of the replication controller 
  name: nginx
spec:  // Specfication contain 2 things 1. Replicas and 2. Pods (Template)
  replicas: 3
  selector: // Replication controller will know the pods using selector this selector name same as lable name in metadata 
    app: nginx
  template:   // In this section we can define the pod configration
    metadata:
      name: nginx
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
      - containerPort: 80
 ```
