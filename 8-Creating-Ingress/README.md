# Ingress


![aks-create-svc](https://user-images.githubusercontent.com/63836841/121617836-c1e3b280-ca33-11eb-88b3-57403e36495f.png)

##Docker image :Link
https://hub.docker.com/repository/docker/felixgokmen/portfoli-app-1
<img width="1263" alt="Screen Shot 2021-06-10 at 9 03 49 PM" src="https://user-images.githubusercontent.com/63836841/121615639-5c8dc280-ca2f-11eb-8a59-478ecef70d75.png">

<br>
<img width="618" alt="Screen Shot 2021-06-10 at 9 58 47 PM" src="https://user-images.githubusercontent.com/63836841/121619730-0a509f80-ca37-11eb-845c-122d38cf5582.png">
<br>
<br>
<img width="1137" alt="Screen Shot 2021-06-10 at 11 49 11 PM" src="https://user-images.githubusercontent.com/63836841/121628020-7686cf80-ca46-11eb-9646-e639cf859807.png">
<br>

<img width="1421" alt="Screen Shot 2021-06-10 at 11 53 03 PM" src="https://user-images.githubusercontent.com/63836841/121628339-00369d00-ca47-11eb-90ab-21ba26ceca2f.png">
<br>
### Instructions
- Created a **Static Public IP** for Ingress in Azure AKS
- Associated that Public IP to **Ingress Controller** during installation.
- Create / Review Ingress Manifest
- Deployed a simple Nginx App with Ingress manifest


## Created Static Public IP
```
# Get the resource group name of the AKS cluster 


az aks show --resource-group aks-devops-ca1 --name devops-aks --query nodeResourceGroup -o tsv


# Created Public IP: Replace Resource Group value
az network public-ip create --resource-group MC_aks-devops-ca1_devops-aks_canadacentral --name akspublicforingress --sku Standard --allocation-method static --query publicIp.ipAddress -o tsv
```



```
#Public IP created for Ingress
20.63.60.83
```
<img width="1097" alt="Screen Shot 2021-06-10 at 11 28 50 PM" src="https://user-images.githubusercontent.com/63836841/121626546-9ec0ff00-ca43-11eb-81b0-5719837bc5ae.png">
<br>
## Installed Ingress Controller
<img width="1177" alt="Screen Shot 2021-06-10 at 9 39 56 PM" src="https://user-images.githubusercontent.com/63836841/121618209-68c84e80-ca34-11eb-83d7-c6aad8f64135.png">
```
# Install Helm3 
brew install helm

# Create a namespace for resources
kubectl create namespace ingress-controller


#  Customizing the Chart. 
helm show values ingress-nginx/ingress-nginx

# Replace Static IP 
helm install ingress-nginx ingress-nginx/ingress-nginx \
    --namespace ingress-controller \
    --set controller.replicaCount=2 \
    --set controller.nodeSelector."beta\.kubernetes\.io/os"=linux \
    --set defaultBackend.nodeSelector."beta\.kubernetes\.io/os"=linux \
    --set controller.service.externalTrafficPolicy=Local \
    --set controller.service.loadBalancerIP="20.63.60.83" 


# List Services 
kubectl get service -l app.kubernetes.io/name=ingress-nginx --namespace ingress-controller

# List Pods
kubectl get pods -n ingress-controller
kubectl get all -n ingress-controller



# Deploy
kubectl apply -f manifests/

# List Pods
kubectl get pods

# List Services
kubectl get svc

# List Ingress
kubectl get ingress

# Access Application
Public-IP-created-for-Ingress


# Ingress Controller Logs
kubectl get pods -n ingress-controller
kubectl logs -f <pod-name> -n ingress-controller
```

#Clean-Up 
```
# Delete Apps
kubectl delete -f manifests/
# Access Application
<img width="1519" alt="Screen Shot 2021-06-11 at 12 20 15 AM" src="https://user-images.githubusercontent.com/63836841/121630306-e26b3700-ca4a-11eb-9b0f-9d86db50882c.png">

