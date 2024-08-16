Full-Stack Application with Kubernetes
Overview
This repository contains a full-stack application deployed using Kubernetes. The stack includes:

Frontend: Nginx serving static files.
Backend: Node.js application connected to MongoDB.
Database: MongoDB.

Build and Push Docker Images
Frontend
Navigate to the frontend directory:
cd frontend
Build the Docker image:
docker build -t your-dockerhub-username/nginx-frontend:latest .

Push the Docker image to Docker Hub:

docker push your-dockerhub-username/nginx-frontend:latest

Backend
Navigate to the backend directory:

cd ../backend

Build the Docker image:

docker build -t your-dockerhub-username/node-backend:latest .

Push the Docker image to Docker Hub:


docker push your-dockerhub-username/node-backend:latest

Alternatively, deploy with Docker Compose:

docker-compose up -d

docker build -t kajibaa/node-backend:latest .
docker push kajibaa/node-backend 

docker build -t kajibaa/nginx-frontend:latest .
docker push kajibaa/nginx-frontend:latest

Kubernetes Deployment
Create the namespace:

kubectl create namespace fullstack-app
Deploy the Kubernetes files:
cd kubernetes
kubectl apply -f mongo-configmap.yaml
kubectl apply -f mongo-deployment.yaml
kubectl apply -f mongo-pv-pvc.yaml
kubectl apply -f mongo-secret.yaml
kubectl apply -f nginx-configmap.yaml
kubectl apply -f nginx-deployment.yaml
kubectl apply -f node-configmap.yaml
kubectl apply -f node-deployment.yaml

Get the frontend Nginx URL:

minikube service nginx-frontend -n fullstack-app --url

Check the deployment status:

kubectl deescribe pod mongodb -n fullstack-app


To clean up the deployed resources:

cd kubernetes
kubectl delete -f mongo-configmap.yaml
kubectl delete -f mongo-deployment.yaml
kubectl delete -f mongo-pv-pvc.yaml
kubectl delete -f mongo-secret.yaml
kubectl delete -f nginx-configmap.yaml
kubectl delete -f nginx-deployment.yaml
kubectl delete -f node-configmap.yaml
kubectl delete -f node-deployment.yaml

to clear everything all deployements and to delete minikube deployments
minikube delete