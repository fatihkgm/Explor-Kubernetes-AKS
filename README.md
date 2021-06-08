# AKS-KUBERNETES-INSTRUCTION

Create Kubernetes Cluster on Azure 
# AKS Cluster Azure

## Step-03: Cloud Shell - Configure kubectl to connect to AKS Cluster

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
```
# Deploy Application
kubectl apply -f kube-manifests/

# Verify Pods
kubectl get pods

# Verify Deployment
kubectl get deployment

# Verify Service (Make a note of external ip)
kubectl get service

# Access Application
http://<External-IP-from-get-service-output>
```
## Step-07: Clean-Up
```
# Delete Applications
kubectl delete -f kube-manifests/
```
  
