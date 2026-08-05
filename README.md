# App-Deployment-On-KIND-Cluster
## Prerequisites
Ensure you have the following tools installed:
* Docker
* KIND
* kubectl

## Steps
1. Create a KIND Cluster
 ```
kind create cluster --name django-notes-app
```
2. Prepare Maniifest Files
* namespace.yml
* deployment.yml
* service.yml
  
3. Apply Manifests
```
kubectl apply -f namespace.yml
kubectl apply -f deployment.yml
kubectl apply -f service.yml
```
4. Verify Resources
```
kubectl get all -n my-app-ns
```
5. Expose Traffic (Port Forwarding)
Since KIND nodes run inside Docker containers, forward local port 8000 to the Kubernetes service:
```
kubectl port-forward svc/my-app-service 8000:8000 -n my-app-ns
```
6. Access Application
```http://localhost:8000```
