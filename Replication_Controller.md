

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
metadata:   # MetaData contain 2 things name and Label (optional). Name of the replication controller
  name: nginxreplication   # Name of the Replication controller
spec:   #  Specfication contain 2 things 1. Replicas and 2. Pods (Template)
  replicas: 3
  selector:  # Replication controller will know the pods using selector this selector name same as lable name in metadata
    app: nginx  # name of the application in which perticular controller is running
  template:  # In this section we can define the pod configration
    metadata:
      name: nginx
      labels:
        app: nginx
    spec:
      containers:
      - name: nginximage
        image: nginx   # Image Name
        ports:
        - containerPort: 80
      
 ```
 
 ### Commands 
 
##### 1. Command to create the replication controller 
 ```sh
 
 kubectl create -f name_of_replication_menifest_file.yml
 
 ```

##### 2. To See the list of Pods 

```sh

kubectl get pods 
```

##### 3. To See the list of replication controller  

```sh

kubectl get rc 
```

##### 4. Increase the replicas in the replication controller   

```sh

kubectl scale --replicas=<number of pods > rc/controller_name

example : kubectl scale --replicas=10 rc/nginx
```

##### 5. Decribe the replication controller    

```sh

kubectl describe rc/<replication_controller_name>

```

##### 6. Decribe the pds    

```sh

kubectl describe pods <pad_name>

```

##### 6. Delte the replication controller  

```sh

kubectl delete  rc/<name of replication controller > 

```



