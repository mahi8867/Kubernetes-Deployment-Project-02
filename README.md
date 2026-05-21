# ☸️ Kubernetes Deployment Project 02



![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)




![YAML](https://img.shields.io/badge/YAML-CB171E?style=for-the-badge&logo=yaml&logoColor=white)




![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)



## 📌 Overview

This project demonstrates how to deploy an application on **Kubernetes** using a **Deployment** manifest. A Kubernetes Deployment ensures your application is always running, automatically restarts failed Pods, and supports rolling updates with zero downtime.

---

## 🧠 What Problem Does This Solve?

Running containers manually is not reliable — if a container crashes, it stays down.

Kubernetes Deployment solves that by:

- **Auto-healing** — If a Pod crashes, Kubernetes automatically restarts it
- **Scaling** — Easily scale up or down by changing replica count
- **Rolling Updates** — Deploy new versions with zero downtime
- **Rollback** — Instantly go back to the previous version if something breaks

---

## 🗂️ Project Structure

| File | Purpose |
|------|---------|
| `deployment.yaml` | Defines the Deployment — replicas, image, labels, and container config |

---

## ⚙️ Key Concepts in deployment.yaml

| Field | Description |
|-------|-------------|
| `replicas` | Number of Pod copies to run |
| `selector` | Identifies which Pods this Deployment manages |
| `template` | Pod blueprint — defines container image and settings |
| `image` | Docker image used to run the container |
| `containerPort` | Port the container listens on |

---

## 🚀 How to Deploy

### Prerequisites
- Kubernetes cluster running (Minikube / kubeadm / EKS)
- `kubectl` configured and connected

### Step 1 — Apply the Deployment
```bash
kubectl apply -f deployment.yaml
# Check Deployment status
kubectl get deployments

# Check Pods created by Deployment
kubectl get pods

# Check detailed info
kubectl describe deployment
kubectl logs <pod-name>
# Scale up to 5 replicas
kubectl scale deployment <deployment-name> --replicas=5

# Verify scaling
kubectl get pods
# Update to a new image version
kubectl set image deployment/<deployment-name> <container-name>=<new-image>

# Check rollout status
kubectl rollout status deployment/<deployment-name>

# Rollback to previous version
kubectl rollout undo deployment/<deployment-name>
