

# Basic Commands of Kubernetes


##### Start the minikube 
minikube start --vm-driver=none 


##### To check the list of nodes or Verify Minikube is runnung
kubectl get nodes 

##### Start the Deployment on Kubernetes Cluster.
kubectl create deployment <deployment_name> --image=<imagename>
  
Example : kubectl create deployment nginx --image=nginx

##### Get Information of Running Deployments
kubectl get deployments

##### Get the help all the available commands
kubectl get --help  

##### Describe the Running Deployment
kubectl describe deployment <name_of_deployment>
Example: kubectl describe deployment nginx

##### Make the  ontainer accessible via the internet:
kubectl create service nodeport <deplymentname> --tcp=80:80
Example: kubectl create service nodeport nginx --tcp=80:80

##### Get the list of running Service 
kubectl get svc

##### Get Service access point 
minikube service <name_of_service> --url
example: minikube service nginx --url

##### Get the list of Pods 
kubectl get pods 

##### Get the list of Pods 
kubectl get pods -A

##### Setup the external IP address to access the service from outerworld
kubectl patch svc nginx -p '{"spec":{"externalIPs":["ipaddress"]}}'

##### Delete the service 
kubectl delete services <name_of_service>

##### Remove Deployment 
kubectl delete deployment <name_of_deployment>

