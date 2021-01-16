
# Deployment in Kubernetes

#### Simple YML file for deployment 

```sh

apiVersion: apps/v1  # our API version
kind: Deployment # # The kind we are creating
metadata: # Specify all Metadata like name, labels
 name: deployment
 labels:
   app: deploymentlabel
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
        - name: nginx
          image: nginx:1.19.6
          
          
 ---------------------------------------------------------------------
 
 Service YML file 
 
apiVersion: v1
kind: Service
metadata:
  name: nginxservice
  labels:
    name: nginxservice
spec:
  ports:
    - port: 80
      nodePort: 30225
      protocol: TCP
  selector:
    app: frontend
  type: NodePort


```


#### Commands for Deployments 

```sh

To deploy the deployments 
kubectl create -f "name_of_deployment_yml_file"

List of running deployments 
kubectl get deployments

List of Running Pods 
kubectl get pods 

List of running ReplicaSet 
kubectl get rs

To see the labels automatically generated for each Pod.
kubectl get pods --show-labels

Get The list of Service 
kubectl get service

Upgrade the app in deployments 
kubectl set image deployment/<deployment name> appname=<newimage>

Check the Rollout Status 
kubectl rollout status deployment/<deployment_name>

Verify Rollout History
kubectl rollout history deployment/<deployment_name>

To Rollback the changes 
kubectl rollout undo deployment/<deployment_name>

Edit Deployment, add Revision History
kubectl edit deployment/<deployment_name>
```
