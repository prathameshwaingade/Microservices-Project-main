# 🚀 End-to-End CI/CD Pipeline for Microservices Application

A production-style DevOps project demonstrating a complete CI/CD workflow using **Docker, Jenkins, and Kubernetes** for automated build, containerization, and deployment of microservices.

---

## 📌 Project Overview

This project simulates a real-world enterprise deployment pipeline where multiple services are:

- Built automatically
- Tested
- Containerized
- Pushed to a registry
- Deployed to Kubernetes
- Updated with zero downtime

It showcases practical implementation of modern DevOps practices and infrastructure automation.

---

## 🧱 Architecture

```
Developer → Git Push → Jenkins Pipeline → Build → Docker Image → Registry → Kubernetes Deploy → Rolling Update
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|-----|--------|
Git | Version control |
Jenkins | CI/CD automation |
Docker | Containerization |
Kubernetes | Container orchestration |
Maven | Java build |
Node.js | Backend service |
kubectl | Cluster control |

---

## 📁 Project Structure

```
microservices-project/
│
├── service-user/
├── service-order/
├── k8s/
├── Jenkinsfile
└── README.md
```

---

## ⚙️ Pipeline Workflow

### Stage 1 — Source Code Checkout
Jenkins pulls latest code from Git repository.

### Stage 2 — Build
- Maven builds Java service
- npm installs dependencies

### Stage 3 — Test
Automated tests run before image creation.

### Stage 4 — Docker Build
Each service is containerized separately.

### Stage 5 — Image Push
Images are pushed to DockerHub registry.

### Stage 6 — Deployment
Kubernetes applies manifests and deploys containers.

### Stage 7 — Rolling Updates
Application updates occur with zero downtime.

---

## 🐳 Docker Build Commands

```
docker build -t user-service ./service-user
docker build -t order-service ./service-order
```

---

## ☸️ Kubernetes Deployment

Deploy services:

```
kubectl apply -f k8s/
```

Check pods:

```
kubectl get pods
```

---

## 🔁 Rolling Update Example

```
kubectl set image deployment/user-service \
user=yourdockerhub/user-service:v2
```

Kubernetes automatically:
- spins new pods
- verifies health
- removes old pods

---

## 🔐 Jenkins Credentials Setup

Add credentials in Jenkins:

```
Manage Jenkins → Credentials → Add → Username/Password
ID: dockerhub-creds
```

---

## 📊 Key DevOps Concepts Demonstrated

- CI/CD automation
- Container lifecycle management
- Infrastructure as Code
- Immutable deployments
- Service discovery
- High availability architecture
- Automated rollback capability
- Multi-service orchestration

---

## ⭐ Advanced Improvements (Future Scope)

Possible enhancements to extend project:

- Helm charts for deployments
- Horizontal Pod Autoscaler
- Prometheus monitoring
- Grafana dashboards
- GitOps using ArgoCD
- Canary deployments
- Secrets management

  ---
  ## Made by:
  Prathamesh Waingade
