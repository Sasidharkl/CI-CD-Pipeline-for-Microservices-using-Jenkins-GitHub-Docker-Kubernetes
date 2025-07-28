# CI-CD-Pipeline-for-Microservices-using-Jenkins-GitHub-Docker-Kubernetes

# CI/CD Pipeline with Jenkins, Docker, Kubernetes

This project demonstrates a complete CI/CD pipeline using:
- Jenkins
- Docker
- Kubernetes
- GitHub

## Features
- Automatic build & test on code commit
- Docker image creation and push to DockerHub
- Kubernetes deployment with rolling updates
- Slack notification integration

## Setup
1. Clone the repository.
2. Replace `yourdockerhubusername` with your actual DockerHub username.
3. Configure Jenkins with required credentials and plugins.
4. Deploy to a Kubernetes cluster using the files in `kubernetes/`.

## Requirements
- Jenkins
- Docker
- Kubernetes Cluster (minikube, EKS, AKS, etc.)
- Maven (for Java projects)
