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
- **Access the Application using Public IP**
```
http://<External-IP-from-get-service-output>
```