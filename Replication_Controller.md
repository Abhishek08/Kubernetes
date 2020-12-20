

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
metadata:
  name: nginx
spec:
  replicas: 3
  selector:
    app: nginx
  template:
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
