# Template
<img width="1480" alt="Screen Shot 2021-06-10 at 12 37 33 PM" src="https://user-images.githubusercontent.com/63836841/121563662-a30bfe80-c9e8-11eb-9edd-eaff1e277dff.png">
<br>

<img width="1268" alt="Screen Shot 2021-06-10 at 12 39 38 PM" src="https://user-images.githubusercontent.com/63836841/121563950-ecf4e480-c9e8-11eb-9c2b-d7b440886891.png">

<br>

<img width="897" alt="Screen Shot 2021-06-10 at 1 34 45 PM" src="https://user-images.githubusercontent.com/63836841/121571131-a0ada280-c9f0-11eb-88e7-cc2d2a7800b2.png">



## Deploy User Management 
```
# Deploy all Manifests
kubectl apply -f storage-manifest/

# List Pods
kubectl get pods

# Stream pod logs to verify DB Connection
kubectl logs -f <pod-name>
```
## Access Application
```
# Get Public IP
kubectl get svc

# Access Application
http://<External-IP-from-get-service-output>
Username: 
Password: 
```

## Clean Up 
```
# Delete all Objects created
kubectl delete -f storage-manifest/

# Verify current Kubernetes Objects
kubectl get all

# Delete Azure Database
```