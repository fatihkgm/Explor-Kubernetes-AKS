# Integrate Azure Container Registry ACR with AKS

## For azure pipeline - used github repository link :
Link for the source code : https://github.com/fatihkgm/azure-aks-devops-cluster
```
# Command Line Credentials
az aks get-credentials --name aksvncluster --resource-group aks-vn-ca

# Verify Nodes
kubectl get nodes 
kubectl get nodes -o wide

# Verify aci-connector-linux
kubectl get pods -n kube-system


```

<img width="1311" alt="Screen Shot 2021-06-11 at 1 50 54 AM" src="https://user-images.githubusercontent.com/63836841/121637512-780cc380-ca57-11eb-9e48-84e0f0aba8fb.png">

<img width="916" alt="Screen Shot 2021-06-11 at 1 52 49 AM" src="https://user-images.githubusercontent.com/63836841/121637663-bd30f580-ca57-11eb-9b41-3c007fbcd537.png">

<img width="1002" alt="Screen Shot 2021-06-11 at 2 03 18 AM" src="https://user-images.githubusercontent.com/63836841/121638563-31b86400-ca59-11eb-9796-6946fd1ef54d.png">

<img width="730" alt="Screen Shot 2021-06-11 at 2 37 47 AM" src="https://user-images.githubusercontent.com/63836841/121642071-03895300-ca5e-11eb-9146-bd5992c71cd8.png">


## Build Docker Image Locally
```
# Change Directory
cd docker-manifests
 
# Docker Build
docker build -t azure-nginx:0.1 .

# List Docker Images
docker images
docker images kazure-nginx:0.1
```

## Run Docker Container locally
```
# Run locally
docker run --name azure-nginx --rm -p 80:80 -d azure-nginx:0.1

# Access Application locally
http://localhost:80

# Stop Docker Image
docker stop azure-nginx:0.1
```
<img width="848" alt="Screen Shot 2021-06-11 at 2 30 13 AM" src="https://user-images.githubusercontent.com/63836841/121641260-f4ee6c00-ca5c-11eb-9a3d-809267eba489.png">



## Azure DevOps Build Push to ACR
Link for the source code : https://github.com/fatihkgm/azure-aks-devops-cluster



<img width="1179" alt="Screen Shot 2021-06-11 at 3 16 54 AM" src="https://user-images.githubusercontent.com/63836841/121646588-7a751a80-ca63-11eb-96b2-497b61942a9a.png">

## Build succeeded
<img width="949" alt="Screen Shot 2021-06-11 at 3 40 32 AM" src="https://user-images.githubusercontent.com/63836841/121649658-c7a6bb80-ca66-11eb-8e4d-4cff48f80c4b.png">

## Image created in Azure docker registery
<img width="1274" alt="Screen Shot 2021-06-11 at 3 42 18 AM" src="https://user-images.githubusercontent.com/63836841/121649932-09376680-ca67-11eb-9187-9c726748415a.png">

