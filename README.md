# Streaming Application CI/CD Pipeline

## Project Overview

This project demonstrates an end-to-end CI/CD pipeline for a microservices-based Streaming Application using Jenkins, Docker, Amazon ECR, Amazon EKS, Kubernetes, and Helm.

---

## Architecture

GitHub
↓

Jenkins

↓

Docker Build

↓

Amazon ECR

↓

Amazon EKS

↓

Helm

↓

Streaming Application

---

## Technologies

- Git
- GitHub
- Jenkins
- Docker
- Amazon ECR
- Amazon EKS
- Kubernetes
- Helm
- AWS CLI

---

## Services

- Frontend
- Auth Service
- Admin Service
- Chat Service
- Streaming Service
- MongoDB

---

## Jenkins Pipeline

- Checkout Source
- Verify AWS
- Login to Amazon ECR
- Build Docker Images
- Tag Images
- Push Images
- Update kubeconfig
- Helm Deployment
- Verify Deployment

---

## Commands

Build Docker Images

docker build

Push Images

docker push

Deploy

helm upgrade --install streaming-app ./helm

Verify

kubectl get pods

kubectl get svc

---

## Application

Frontend

AWS LoadBalancer URL

Replace with your ELB URL

---

## Author

Saravanan G

DevOps Project

HeroVired
