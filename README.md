# k8s-config-and-secrets

This repository contains example Kubernetes manifests to demonstrate how to use **ConfigMaps**, **Secrets**, and **Persistent Volume Claims (PVCs)** together with a MySQL deployment.  

---

## 📂 Project Structure

k8s-config-and-secrets/
├── configmap/ # (if you have any ConfigMap examples)
│ └── ...yaml
├── mysql_k8s/ # MySQL deployment folder
│ ├── secret.yml # Holds secret (password) for MySQL root user
│ ├── persistentVolumeClaim.yaml # PVC to persist MySQL data
│ ├── deployment.yaml # MySQL deployment manifest
│ └── service.yaml # Service to expose MySQL
└── README.md

yaml
Copy code

---

## ✅ What You’ll Learn / Features

- How to create and use **Secrets** in Kubernetes to securely store sensitive data (e.g., MySQL root password).  
- How to create a **PersistentVolumeClaim (PVC)** to ensure database data persists across pod restarts / rescheduling.  
- How to deploy **MySQL** using a Deployment + Service + volume mounts + secret injection.  
- Best practices: avoid hardcoding passwords, keep credentials out of plain YAML, use Kubernetes resources properly.

---

## 🚀 How to Use

Here is a step-by-step guide to run the setup:

1. Clone the repo  
   ```bash
   git clone https://github.com/Himanshu31bisht/k8s-config-and-secrets.git
   cd k8s-config-and-secrets/mysql_k8s
(Optional) Encode your secret/password in Base64 (if using secret.yml that requires encoding)

bash
Copy code
echo -n "your-password-here" | base64
Apply the Secret manifest

bash
Copy code
kubectl apply -f secret.yml
Create the PersistentVolumeClaim

bash
Copy code
kubectl apply -f persistentVolumeClaim.yaml
Deploy MySQL

bash
Copy code
kubectl apply -f deployment.yaml
Create the Service

bash
Copy code
kubectl apply -f service.yaml
Check that everything is working

bash
Copy code
kubectl get pods
kubectl get svc
kubectl describe pod <mysql-pod-name>

⚠️ Things to Note / Troubleshooting
Make sure the namespace is correct (if you're using one).

Ensure YAML indentation is correct — even one space off can cause errors.

Secret values must be Base64‑encoded, unless you use kubectl create secret … commands which handle that for you.

If MySQL pod doesn’t start, check logs with:

bash
Copy code
kubectl logs <pod-name>



👤 About Me
Hi, I’m Himanshu! I’m learning Kubernetes, cloud-native, and DevOps practices, and this repo is part of my “learning by doing” journey. Feedback is welcome!

