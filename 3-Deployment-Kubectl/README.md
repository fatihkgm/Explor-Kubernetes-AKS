# Kubernetes - Deployment

- **Docker Image Location:** https://hub.docker.com/repository/registry-1.docker.io/felixgokmen/webapp/tags

<img width="1250" alt="Screen Shot 2021-06-08 at 9 03 12 PM" src="https://user-images.githubusercontent.com/63836841/121276604-f07b5500-c89c-11eb-920a-351b3c00b9c1.png">


```
# Create Deployment
kubectl create deployment <Deplyment-Name> --image=<Container-Image>
kubectl create deployment webapp-deplyment --image=felixgokmen/webapp:0.1

# Verify Deployment
kubectl get deployments
kubectl get deploy 

# Describe Deployment
kubectl describe deployment <deployment-name>
kubectl describe deployment webapp-deplyment

# Verify ReplicaSet
kubectl get rs

# Verify Pod
kubectl get po
```
<img width="853" alt="Screen Shot 2021-06-09 at 12 46 35 PM" src="https://user-images.githubusercontent.com/63836841/121395741-ba7fb480-c920-11eb-93b8-418475f7130c.png">
<br><br>
<img width="956" alt="Screen Shot 2021-06-09 at 12 47 55 PM" src="https://user-images.githubusercontent.com/63836841/121395975-eac75300-c920-11eb-98fa-65dfa932fdf1.png">

## Scaling a Deployment
- Scale the deployment to increase the number of replicas (pods)
```
# Scale Up the Deployment
kubectl scale --replicas=10 deployment/<Deployment-Name>
kubectl scale --replicas=10 deployment/webapp-deplyment 

# Verify Deployment
kubectl get deploy

# Verify ReplicaSet
kubectl get rs

# Verify Pods
kubectl get po

# Scale Down the Deployment
kubectl scale --replicas=2 deployment/webapp-deplyment 
kubectl get deploy
```


## Expose Deployment as a Service
- Expose **Deployment** with a service (LoadBalancer Service) to access the application externally (from internet)
```
# Expose Deployment as a Service
kubectl expose deployment <Deployment-Name>  --type=LoadBalancer --port=80 --target-port=80 --name=<Service-Name-To-Be-Created>
kubectl expose deployment webapp-deplyment --type=LoadBalancer --port=80 --target-port=80 --name=webapp-deplyment-service

# Get Service Info
kubectl get svc



```
<img width="1022" alt="Screen Shot 2021-06-09 at 12 50 19 PM" src="https://user-images.githubusercontent.com/63836841/121396316-40036480-c921-11eb-9ba2-3a070a0ffe71.png">
- **Access the Application using Public IP**
```
http://<External-IP-from-get-service-output>
```
<img width="877" alt="Screen Shot 2021-06-09 at 12 51 14 PM" src="https://user-images.githubusercontent.com/63836841/121396446-61645080-c921-11eb-89eb-08a7259c0039.png">
