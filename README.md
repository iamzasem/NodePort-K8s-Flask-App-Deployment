# Flask App Deployment on Kubernetes using NodePort

This project shows how to containerize a simple Flask application, push it to Docker Hub, and deploy it on a Kubernetes cluster using a NodePort service.

## Prerequisites

- Docker installed and running
- Docker Hub account
- Minikube or any Kubernetes cluster
- kubectl installed

## Step 1: Clone the repository

```
git clone https://github.com/zsmops/flaskapp-k8s.git
cd flaskapp-k8s
```

## Step 2: Build and Push Docker Image

Make sure you are in the project directory that contains the Dockerfile.

```
docker build -t yourusername/flaskapp:latest .
docker login
docker push yourusername/flaskapp:latest
```

Replace `yourusername` with your Docker Hub username.

## Step 3: Start Minikube (if using Minikube)

```
minikube start
```

## Step 4: Apply Kubernetes YAML files

```
kubectl apply -f k8s-deploy.yaml
kubectl apply -f k8s-service.yaml
```

## Step 5: Access the Flask App

Get the Minikube IP

```
minikube ip
```

Visit the app in your browser using the following format:

```
http://<minikube-ip>:30080
```

Example:

```
http://192.168.49.2:30080
```

## Project Structure

```
.
├── app.py
├── requirements.txt
├── Dockerfile
├── k8s-deploy.yaml
└── k8s-service.yaml
```

## Notes

- The NodePort is set to 30080 in `k8s-service.yaml`
- The image is pulled from Docker Hub: `zsmops/flaskapp:latest`
- The app returns a simple message from a Flask route
