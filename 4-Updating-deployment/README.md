# Kubernetes - Update Deployments

### Update Deployment
- **Observation:** Please Check the container name in `spec.container.name` yaml output and make a note of it and 
replace in `kubectl set image` command <Container-Name>
<img width="1027" alt="Screen Shot 2021-06-09 at 12 59 11 PM" src="https://user-images.githubusercontent.com/63836841/121397609-7d1c2680-c922-11eb-9651-697386a1eb64.png">


```
# Get Container Name from current deployment
kubectl get deployment webapp-deplyment -o yaml

# Update Deployment - SHOULD WORK NOW
kubectl set image deployment/<Deployment-Name> <Container-Name>=<Container-Image> --record=true
kubectl set image deployment/webapp-deplyment kubenginx=felixgokmen/webapp:2.0 --record=true
```

```
# Verify Rollout Status 
kubectl rollout status deployment/webapp-deplyment

# Verify Deployment
kubectl get deploy
```
### Describe Deployment

```
# Descibe Deployment
kubectl describe deployment webapp-deplyment
```
### Verify ReplicaSet
- **Observation:** New ReplicaSet will be created for new version
```
# Verify ReplicaSet
kubectl get rs
```

### Verify Pods

```
# List Pods
kubectl get po
```

### Verify Rollout History of a Deployment
 

```
# Check the Rollout History of a Deployment
kubectl rollout history deployment/<Deployment-Name>
kubectl rollout history deployment/webapp-deplyment  
```

### Access the Application using Public IP
- We should see `Application Version:V2` whenever we access the application in browser
```
# Get Load Balancer IP
kubectl get svc

# Application URL
http://<External-IP-from-get-service-output>
```


## Step-02: Update the Application from V2 to V3 using "Edit Deployment" Option
### Edit Deployment
```
# Edit Deployment
kubectl edit deployment/<Deployment-Name> --record=true
kubectl edit deployment/webapp-deplyment --record=true
```

```yml
# Change From 2.0.0
    spec:
      containers:
      - image: felixgokmen/webapp:2.0

# Change To 3.0.0
    spec:
      containers:
      - image: felixgokmen/webapp:3.0
```

### Verify Rollout Status
- **Observation:** Rollout happens in a rolling update model, so no downtime.
```
# Verify Rollout Status 
kubectl rollout status deployment/webapp-deplyment
```
### Verify Replicasets
- **Observation:**  We should see 3 ReplicaSets now, as we have updated our application to 3rd version 3.0.0
```
# Verify ReplicaSet and Pods
kubectl get rs
kubectl get po
```
### Verify Rollout History
```
# Check the Rollout History of a Deployment
kubectl rollout history deployment/<Deployment-Name>
kubectl rollout history deployment/webapp-deplyment   
```

### Use Public IP
```
# Get Load Balancer IP
kubectl get svc

# Application URL
http://<External-IP-from-get-service-output>
```