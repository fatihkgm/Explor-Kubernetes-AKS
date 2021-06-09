# Kubernetes  - PODs
1. Kubernetes - created a pod.
2. Pulled the docker image from docker hub.
3. Created the container in the pod.
4. Started the container present in the pod.

# Create Pods
kubectl run <pod-name> --image <Container-Image> 
# Sample website downloaded and created image in DockerHub
DockerHub image link : https://hub.docker.com/repository/registry-1.docker.io/felixgokmen/webapp/tags?page=1&ordering=last_updated
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
# Namespaces
<img width="1092" alt="Screen Shot 2021-06-08 at 10 41 16 PM" src="https://user-images.githubusercontent.com/63836841/121284302-a4cfa800-c8aa-11eb-9d6c-840e0b95f09d.png">
### Connect in a POD
```
# Nginx Container in a POD
kubectl exec -it <pod-name> -- /bin/bash

```

### Create ReplicaSet <felix-repicants.yaml>

```
kubectl create -f replicaset-demo.yml
```
- **felix-repicants.yaml.yml**
```yml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: webapp-ca
  labels:
    app: webapp
spec:
  replicas: 3
  selector:
    matchLabels:
      app: webapp
  template:
    metadata:
      labels:
        app: webapp
    spec:
      containers:
      - name: mwebapp-app
        image: felixgokmen/webapp:0.1
```

### List ReplicaSets
- Get list of ReplicaSets
```
kubectl get replicaset
kubectl get rs
```

### Describe ReplicaSet
- Describe the created ReplicaSet
```
kubectl describe rs/<replicaset-name>

```

### List of Pods
- Get list of Pods
```
#Get list of Pods
kubectl get pods
kubectl describe pod <pod-name>

# Get list of Pods with Pod IP and Node in which it is running
kubectl get pods -o wide
```

# Get Service Info
kubectl get service
kubectl get svc

```
- **Access the Application using External or Public IP**
http://<External-IP-from-get-service-output>/webapp
```


```
## Namespaces
kubernetes get namespace

## Clean-Up
```
# Delete ReplicaSet
kubectl delete rs <ReplicaSet-Name>

# Sample Commands
kubectl delete rs/name
[or]
kubectl delete rs name

# Verify if ReplicaSet got deleted
kubectl get rs

# Delete Service
kubectl delete svc <service-name>

# Sample Commands
kubectl delete svc servicename
[or]
kubectl delete svc/servicename

# Verify if Service got deleted
kubectl get svc
```
