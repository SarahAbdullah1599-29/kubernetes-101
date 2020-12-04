# Kubernetes 101 Workshop cheatsheet

### Docker

Download the docker image:

```bash
docker pull hashicorp/http-echo
```
Create and run the docker container:
```bash
docker run -p 8080:8080 hashicorp/http-echo -listen=:8080 -text="hello world"
```
List all running containers:
```bash
docker ps
```
Stop the running container:
```bash
docker stop <container id>
```
Delete the stopped container:
```bash
docker rm <container id>
```

You can test your app by going to [http://localhost:8080](http://localhost:8080) or running:
```bash
curl localhost:8080
```

### minikube

Start minikube:
```bash
minikube start
```
Get minikube status:
```bash
minikube status
```
Stop minikube (when done with the workshop :-)):
```bash
minikube stop
```
Connect your LoadBalancer to the outside world (this is a blocking call):
```bash
minikube tunnel
```

### kubectl

List all pods:
```bash
kubectl get pods
```
List all pods, services and secrets:
```bash
kubectl get pods,services,secrets
```
List all services across all namespaces:
```bash
kubectl get services -A
```
List all available resource you can interct with:
```bash
kubectl kubectl api-resources 
```
Apply workload resource definition from file:
```bash
kubectl apply -f </path/to/file>
```
Output pod's details in yaml format:
```bash
kubectl get pod <pod-name> -o yaml
```
Listen on port 8080 on your local machine and forward 
to port 8080 of the specified pod:
```bash
kubectl port-forward pod/<pod-name> 8080:8080
```

### gcloud

Configure kubectl to connect to your cluster:
```bash
gcloud config set project <gcp-id>
gcloud container clusters get-credentials <cluster-name>
```
Verifying kubectl is connected to the right cluster:
```bash
kubectl config current-context
```
