# Kubernetes - Services


- ClusterIP and LoadBalancer Service -  example. 

```
# Create Deployment for Backend Rest App
kubectl create deployment backend-app --image=felixgokmen/mysql:latest 
kubectl get deploy

# Create ClusterIp Service for Backend Rest App
kubectl expose deployment backend-app --port=3306 --target-port=3306 --name=backend-app-service
kubectl get svc 
```


- **Backend DockerHub image Link** https://hub.docker.com/repository/docker/felixgokmen/mysql


- **Docker Image Location:** https://hub.docker.com/repository/docker/felixgokmen/aws-project-maven:0.1
<img width="925" alt="Screen Shot 2021-06-09 at 5 27 38 PM" src="https://user-images.githubusercontent.com/63836841/121431890-fed27b00-c947-11eb-87de-29e0daaa2f18.png">
<img width="752" alt="Screen Shot 2021-06-09 at 7 18 33 PM" src="https://user-images.githubusercontent.com/63836841/121441275-7d82e480-c957-11eb-83d3-1647d5a80b0a.png">
```
```
# Create Deployment for Frontend Nginx Proxy
kubectl create deployment front-end-app --image=felixgokmen/aws-project-maven:0.1
kubectl get deploy

# Create LoadBalancer Service for Frontend Nginx Proxy
kubectl expose deployment front-end-app  --type=LoadBalancer --port=8080 --target-port=8080 --name=frontend-service
kubectl get svc

# Get Load Balancer IP
kubectl get svc
http://<External-IP-from-get-service-output>/webapp



# Test again to view the backend service Load Balancing
http://<External-IP-from-get-service-output>/webapp
```
<img width="1040" alt="Screen Shot 2021-06-09 at 7 19 21 PM" src="https://user-images.githubusercontent.com/63836841/121441337-99868600-c957-11eb-8a66-b871a907e150.png">