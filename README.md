# 🚀 Three-Tier Scalable Web Deployment

## 📝 Introduction:
This project focuses on deploying a robust, **Three-Tier Architecture** using modern DevOps practices. By leveraging **Docker** for containerization and **Kubernetes (K8s)** for orchestration, we ensure that the frontend, backend, and database layers are isolated, scalable, and easy to manage in a production environment.

---

## 🏗️ Detailed Workflow Description:

* **Frontend (User Interaction):**
    * The presentation layer is containerized and served to the user's browser. It handles all UI logic and communicates with the backend via RESTful APIs.
* **Backend (Logic Layer):**
    * The server-side application processes requests, handles authentication, and manages business logic. It serves as the bridge between the user interface and the data persistence layer.
* **MongoDB (Database Tier):**
    * A dedicated MongoDB instance stores all application data. It is deployed as a separate service within the cluster to ensure data integrity and focused performance.

---

## ✨ Features:
* **Three-Tier Isolation**: Each component (Frontend, Backend, DB) has its own dedicated Docker image and container.
* **Kubernetes Orchestrated**: Managed using K8s Deployments and Services for high availability.
* **Containerized Workflow**: Standardized environment using Docker to eliminate "it works on my machine" issues.
* **Scalable Architecture**: Easily scale horizontal replicas for the frontend or backend tiers based on traffic.
* **Persistent Storage**: Configured to handle database states securely within a containerized environment.

---

## 🛠️ Tech Stack:
* **Containerization:** Docker
* **Orchestration:** Kubernetes (K8s)
* **Database:** MongoDB
* **Backend:** Node.js / Express (or your specific tech)
* **Frontend:** React / TailwindCSS (or your specific tech)
* **Infrastructure:** YAML Manifests (Deployments, Services, ConfigMaps)

---

## 🔧 Prerequisites:
* **[Docker](https://www.docker.com/)** (v20.10 or higher)
* **[Kubernetes Cluster](https://kubernetes.io/)** (Minikube, Kind, or Cloud provider like AWS EKS)
* **[Kubectl](https://kubernetes.io/docs/tasks/tools/)** (Configured to access your cluster)

---

## 🏗️ Build and Run the Application

### 1. Build Docker Images
Navigate to each tier and build the respective images:

```bash
# Apply Database resources
kubectl apply -f k8s/mongodb-deployment.yaml
kubectl apply -f k8s/mongodb-service.yaml

# Apply Backend resources
kubectl apply -f k8s/backend-deployment.yaml
kubectl apply -f k8s/backend-service.yaml

# Apply Frontend resources
kubectl apply -f k8s/frontend-deployment.yaml
kubectl apply -f k8s/frontend-service.yaml
# Build Frontend
cd frontend && docker build -t my-frontend:v1 .

# Build Backend
cd ../backend && docker build -t my-backend:v1 .
