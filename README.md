# 🚀 Kubernetes Apache Deployment (Docker + Kubernetes)

This project demonstrates how to **containerize an Apache web application using Docker and deploy it on Kubernetes**.
It includes Kubernetes resources such as **Deployment, Service, ConfigMap, PersistentVolumeClaim, and Docker Registry Secret**.

---

# 📌 Project Overview

The goal of this project is to understand the **end-to-end workflow of deploying containerized applications in Kubernetes**.

The application is packaged in a Docker container, pushed to Docker Hub, and deployed to a Kubernetes cluster using YAML manifests.

---

# 🏗 Architecture

```
Docker Image (Docker Hub)
        ↓
Kubernetes Secret (Docker Registry)
        ↓
Deployment
        ↓
ReplicaSet
        ↓
Pods
        ↓
Service (NodePort)
        ↓
Browser Access
```

---

# 🛠 Technologies Used

* Docker
* Kubernetes
* Docker Hub
* YAML Configuration
* Apache Web Server

---

# 📂 Project Structure

```
k8-kubernetes-project
│
├── Dockerfile
├── deployment.yaml
├── services.yml
├── pvc.yaml
├── configmap.yaml
└── README.md
```

---

# 🐳 Step 1: Build Docker Image

Build the Docker image for the Apache application.

```
docker build -t <dockerhub-username>/myapp-test:latest .
```

---

# 📤 Step 2: Push Image to Docker Hub

Login and push the image.

```
docker login
docker push <dockerhub-username>/myapp-test:latest
```

---

# ☸ Step 3: Create Docker Registry Secret

This allows Kubernetes to pull images from a private Docker repository.

```
kubectl create secret docker-registry accesskey-nov-2025 \
--docker-username=<dockerhub-username> \
--docker-password=<dockerhub-password> \
--docker-email=<email>
```

---

# ☸ Step 4: Deploy Application to Kubernetes

Apply the deployment configuration.

```
kubectl apply -f deployment.yaml
```

Check deployment status.

```
kubectl get deployments
```

---

# ☸ Step 5: Verify Pods

```
kubectl get pods
```

Example output:

```
myapp-test-xxxx   1/1   Running
myapp-test-yyyy   1/1   Running
```

---

# 🌐 Step 6: Expose the Application

Create a NodePort service.

```
kubectl apply -f services.yml
```

Check service:

```
kubectl get svc
```

Example:

```
myapp-test-service   NodePort   80:30007/TCP
```

---

# 🌍 Access the Application

Open the application in your browser:

```
http://localhost:30007
```

---

# 🧰 Useful Kubernetes Debugging Commands

Check running pods:

```
kubectl get pods
```

Describe pod details:

```
kubectl describe pod <pod-name>
```

View container logs:

```
kubectl logs <pod-name>
```

---

# 📸 Screenshots

I add screenshots of:

* Running pods
* Kubernetes services
* Application running in the browser

---

# 🎯 Learning Outcomes

Through this project, I learned:

* Containerizing applications with Docker
* Managing deployments in Kubernetes
* Using Kubernetes services to expose applications
* Troubleshooting common errors like `ImagePullBackOff`
* Managing configuration using ConfigMaps and PVCs

---

# 📚 Future Improvements

* Add Ingress for external routing
* Deploy application to a cloud Kubernetes cluster (EKS / GKE / AKS)
* Implement CI/CD pipeline with GitHub Actions

---

# 👩‍💻 Author

**Anuja Ayare**

DevOps Enthusiast | Learning Docker & Kubernetes

---

# ⭐ If you found this project helpful, consider giving it a star!
