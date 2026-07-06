# 🚀 Deploy Café Website on Kubernetes using Docker & Minikube on AWS EC2

# 📖 Project Overview

This project demonstrates the complete deployment lifecycle of a static Café Website using **Docker** and **Kubernetes**. The application was containerized using Docker, pushed to Docker Hub, and deployed on a Kubernetes cluster running on **Minikube** inside an **AWS EC2 Ubuntu instance**.

The primary goal of this project was to understand:

- Docker containerization
- Docker Hub image management
- Kubernetes Deployments
- Kubernetes Services
- Labels & Selectors
- Namespace creation
- ConfigMaps
- Secrets
- Persistent Storage (PVC)
- Ingress
- Horizontal Pod Autoscaler (HPA)
- Network Policies
- Kubernetes troubleshooting
- Minikube networking on AWS EC2

During the implementation, I encountered several real-world Kubernetes issues and resolved them through debugging using `kubectl logs`, `kubectl describe`, and Kubernetes Events.

---

# 🎯 Project Objectives

- Containerize a web application using Docker.
- Push the Docker image to Docker Hub.
- Deploy the application on Kubernetes.
- Learn Kubernetes core objects.
- Understand Kubernetes networking.
- Troubleshoot deployment issues.
- Simulate a production-style deployment using Minikube.

---

# 🏗️ Architecture

```
                   Developer

                        │

                        ▼

             HTML + CSS Website

                        │

                        ▼

                Docker Build

                        │

                        ▼

               Docker Image

                        │

                        ▼

                 Docker Hub

                        │

                        ▼

                AWS EC2 (Ubuntu)

                        │

                        ▼

              Docker Engine

                        │

                        ▼

                  Minikube

                        │

                        ▼

              Kubernetes Cluster

                        │

        ┌───────────────┼───────────────┐
        │               │               │
        ▼               ▼               ▼

 Namespace      ConfigMap/Secret      PVC

        │

        ▼

    Deployment

        │

        ▼

     ReplicaSet

        │

        ▼

        Pods

        │

        ▼

      Service

        │

        ▼

      Ingress

        │

        ▼

 Port Forward / Browser
```

---

# 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| AWS EC2 | Virtual Machine |
| Ubuntu 22.04 | Operating System |
| Docker | Containerization |
| Docker Hub | Image Registry |
| Kubernetes | Container Orchestration |
| Minikube | Local Kubernetes Cluster |
| kubectl | Kubernetes CLI |
| HTML | Website |
| CSS | Website Styling |
| Git | Version Control |
| GitHub | Source Code Repository |

---

# 📁 Project Structure

```
food-ordering-kubernetes/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── Dockerfile
├── index.html
├── styles.css
│
├── screenshots/
│
├── docs/
│
└── k8s/
      │
      ├── 01-namespace.yaml
      ├── 02-resource-limit.yaml
      ├── 03-configmap.yaml
      ├── 04-secret.yaml
      ├── 05-mysql-pvc.yaml
      ├── 06-mysql-deployment.yaml
      ├── 07-mysql-service.yaml
      ├── 08-app-deployment.yaml
      ├── 09-app-service.yaml
      ├── 10-ingress.yaml
      ├── 11-hpa.yaml
      └── 12-network-policy.yaml
```

---

# 📋 Prerequisites

Before starting this project, ensure the following software is installed.

- AWS Account
- Ubuntu EC2 Instance
- Docker
- Docker Hub Account
- Kubernetes CLI (kubectl)
- Minikube
- Git
- GitHub Account

---

# ☁️ Step 1: Launch AWS EC2 Instance

Create an EC2 instance using the following configuration.

| Configuration | Value |
|--------------|-------|
| AMI | Ubuntu 22.04 LTS |
| Instance Type | t3.medium |
| Storage | 20 GB |
| Authentication | Key Pair (.pem) |

### Security Group

Allow the following inbound ports.

| Port | Purpose |
|------|---------|
| 22 | SSH |
| 80 | HTTP |
| 8080 | Port Forward |
| 30000-32767 | NodePort Services |

### Connect to EC2

```bash
ssh -
