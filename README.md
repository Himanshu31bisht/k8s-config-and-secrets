# k8s-config-and-secrets

This repository contains example Kubernetes manifests to demonstrate how to use ConfigMaps, Secrets, and Persistent Volume Claims (PVCs) together with a MySQL deployment.

# 📂 Project Structure
k8s-config-and-secrets/
├── configmap/                  # Example ConfigMaps (if any)
│   └── ...yaml
├── mysql_k8s/                  # MySQL deployment resources
│   ├── secret.yml              # Secret for MySQL root user password
│   ├── persistentVolumeClaim.yaml # PVC for persisting MySQL data
│   ├── deployment.yaml         # MySQL Deployment
│   └── service.yaml            # Service to expose MySQL
└── README.md

# ✅ Features / What You’ll Learn

🔐 Secrets → Securely store sensitive data (e.g., MySQL root password).

💾 PersistentVolumeClaim (PVC) → Ensure database data persists across pod restarts / rescheduling.

🐬 MySQL Deployment → Using Deployment + Service + volume mounts + secret injection.

🛡 Best Practices → Avoid hardcoding passwords, keep credentials out of plain YAML, use Kubernetes resources properly.

# 🚀 How to Use
1. Clone the Repo
git clone https://github.com/Himanshu31bisht/k8s-config-and-secrets.git
cd k8s-config-and-secrets/mysql_k8s

2. (Optional) Encode Your Password

If your secret.yml expects Base64 encoding:

echo -n "your-password-here" | base64

3. Apply the Manifests
# Apply Secret
kubectl apply -f secret.yml

# Apply PVC
kubectl apply -f persistentVolumeClaim.yaml

# Deploy MySQL
kubectl apply -f deployment.yaml

# Expose MySQL
kubectl apply -f service.yaml

4. Verify Deployment
kubectl get pods
kubectl get svc
kubectl describe pod <mysql-pod-name>

⚠️ Troubleshooting

✅ Namespace → Ensure you are applying manifests in the correct namespace.

✅ YAML Indentation → Even a single space mistake can break the manifest.

✅ Secrets → Values must be Base64-encoded (unless created using kubectl create secret command).

✅ Pod Issues → If MySQL pod doesn’t start, check logs:

kubectl logs <mysql-pod-name>

👤 About Me

Hi, I’m Himanshu Bisht 👋
I’m learning Kubernetes, Cloud-Native, and DevOps practices.
This repo is part of my learning-by-doing journey.
💡 Feedback and suggestions are always welcome!
