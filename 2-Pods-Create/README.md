# Kubernetes  - PODs
1. Kubernetes - created a pod.
2. Pulled the docker image from docker hub.
3. Created the container in the pod.
4. Started the container present in the pod.

# Create Pods
kubectl run <pod-name> --image <Container-Image> 
# Sample website downloaded and created image in DockerHub
<img width="1250" alt="Screen Shot 2021-06-08 at 9 03 12 PM" src="https://user-images.githubusercontent.com/63836841/121276604-f07b5500-c89c-11eb-920a-351b3c00b9c1.png">

# Replace Pod Name, Container Image
kubectl run my-first-pod --image felixgokmen/webapp:01
```  

# List Pods
kubectl get pods

```
# To get list of pod names
kubectl get pods

# Describe the Pod
kubectl describe pod <Pod-Name>
kubectl describe pod my-first-pod 
```


# Delete Pod
kubectl delete pod <Pod-Name>
```
<img width="678" alt="Screen Shot 2021-06-08 at 5 44 12 PM" src="https://user-images.githubusercontent.com/63836841/121262681-85248980-c882-11eb-9c07-c94a2e14ff1a.png">
##Load Balancer Service 

```
# Create  a Pod
kubectl run <pod-name> --image <Container-Image> 
kubectl run my-first-pod --image stacksimplify/kubenginx:1.0.0 


# Expose Pod as a Service
kubectl expose pod <Pod-Name>  --type=LoadBalancer --port=80 --name=<Service-Name>

# Get Service Info
kubectl get service
kubectl get svc

# Describe Service
kubectl describe service service

# Access Application
http://<External-IP-from-get-service-output>
```

### Pod Logs
```
# Get Pod Name
kubectl get pod

# Pod logs
kubectl logs <pod-name>


# Stream pod logs 
kubectl logs <pod-name>
kubectl logs -f my-first-pod
```

### Connect in a POD
```
# Nginx Container in a POD
kubectl exec -it <pod-name> -- /bin/bash

```

```
kubectl exec -it <pod-name> -- env

```

## Clean-Up
```
# Get all Objects
kubectl get all

# Delete Services
kubectl delete svc service

# Delete Pod
kubectl delete pod mypod

# Get all Objects in default namespace
kubectl get all
```
