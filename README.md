# AKS-KUBERNETES-INSTRUCTION

# Used Dokcer image which i already created and push  my DockerHub.
<img width="1244" alt="Screen Shot 2021-06-08 at 12 41 05 AM" src="https://user-images.githubusercontent.com/63836841/121124017-37f8d700-c7f2-11eb-8177-4eb340e7e364.png">

Create Kubernetes Cluster on Azure 
# AKS Cluster Azure

## Cloud Shell - Configure kubectl to connect to AKS Cluster

```
# Template
az aks get-credentials --resource-group <Resource-Group-Name> --name <Cluster-Name>

# Replace Resource Group & Cluster Name
az aks get-credentials --resource-group aks-rg1 --name aksdemo1

# List Kubernetes Worker Nodes
kubectl get nodes 
kubectl get nodes -o wide
```
<img width="1279" alt="Screen Shot 2021-06-08 at 12 05 38 AM" src="https://user-images.githubusercontent.com/63836841/121121268-4264a200-c7ed-11eb-98af-8361d4b58871.png">


## Explore Cluster
```
# List Namespaces
kubectl get namespaces
kubectl get ns

# List Pods from all namespaces
kubectl get pods --all-namespaces

# List all k8s objects from Cluster Control plane
kubectl get all --all-namespaces
```

<img width="970" alt="Screen Shot 2021-06-08 at 12 16 24 AM" src="https://user-images.githubusercontent.com/63836841/121122061-c408ff80-c7ee-11eb-87ef-736e306d3a72.png">  

- **VM Scale Sets**
  - Verify Azure VM Instances
  - Verify if **Enhanced Networking is enabled or not** 
<img width="1037" alt="Screen Shot 2021-06-08 at 12 24 56 AM" src="https://user-images.githubusercontent.com/63836841/121122726-f535ff80-c7ef-11eb-84ac-dc15999021bb.png">

## MacOs Local Desktop - Install Azure CLI and Azure AKS CLI
```
# Install Azure CLI (MAC)
brew update && brew install azure-cli

# Login to Azure
az login

# Install Azure AKS CLI
az aks install-cli

# Configure Cluster Creds (kube config)
az aks get-credentials --resource-group aks-rg1 --name aksdemo1

# List AKS Nodes
kubectl get nodes 
kubectl get nodes -o wide
```
<img width="644" alt="Screen Shot 2021-06-08 at 12 32 50 AM" src="https://user-images.githubusercontent.com/63836841/121123342-0f241200-c7f1-11eb-8062-c1ce9383ac8a.png">

```
# Deploy Application
kubectl apply -f kube-aks-manifest/

# Verify Pods
kubectl get pods

# Verify Deployment
kubectl get deployment

# Verify Service (Make a note of external ip)
kubectl get service

# Access Application
http://<External-IP-from-get-service-output>
```
<img width="804" alt="Screen Shot 2021-06-08 at 12 38 14 AM" src="https://user-images.githubusercontent.com/63836841/121123788-d0428c00-c7f1-11eb-81a3-daa35cab112a.png">
## Accessable with External-IP

<img width="996" alt="Screen Shot 2021-06-08 at 12 39 48 AM" src="https://user-images.githubusercontent.com/63836841/121123924-08e26580-c7f2-11eb-925f-a4f6fe74eab9.png">
## Clean-Up
```
# Delete Applications
kubectl delete -f kube-aks-manifest/
```
  
