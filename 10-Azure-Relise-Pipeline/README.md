---
Relase: Azure Release Pipelines for AKS
---
# Azure DevOps Release Pipelines



## Create Namespaces
```
# List Namespaces
kubectl get ns

# Create Namespaces
kubectl create ns developement
kubectl create ns quality
kubectl create ns staging
kubectl create ns prod

# List Namespaces
kubectl get ns
```

## Create Service Connections for each namespaces
<img width="1049" alt="Screen Shot 2021-06-11 at 12 30 57 PM" src="https://user-images.githubusercontent.com/63836841/121719383-e0d45a00-cab0-11eb-872c-bde39c3c335c.png">

### Continuous Deployment Trigger
- Continuous deployment trigger: Enabled


## Release Pipeline 


<img width="1409" alt="Screen Shot 2021-06-11 at 1 04 57 PM" src="https://user-images.githubusercontent.com/63836841/121724273-a02b0f80-cab5-11eb-974e-c41e7486cc7a.png">

<img width="1040" alt="Screen Shot 2021-06-11 at 1 42 41 PM" src="https://user-images.githubusercontent.com/63836841/121728178-e8006580-caba-11eb-9689-1d339714ccbe.png">