
# ☸️ Kubernetes Persistent Storage Project



![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)




![YAML](https://img.shields.io/badge/YAML-CB171E?style=for-the-badge&logo=yaml&logoColor=white)




![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)



## 📌 Overview

This project demonstrates how to implement **Persistent Storage in Kubernetes** using **Persistent Volumes (PV)**, **Persistent Volume Claims (PVC)**, and **Pods**. It ensures that data survives even when a Pod is deleted or restarted — a critical concept for stateful applications like databases.

---

## 🧠 What Problem Does This Solve?

By default, storage inside a Kubernetes Pod is **ephemeral** — when the Pod dies, all data is lost.

This project solves that by:

- Provisioning a **Persistent Volume (PV)** — actual storage on the node
- Claiming that storage with a **Persistent Volume Claim (PVC)** — a request for storage by a Pod
- Mounting the PVC inside a **Pod** — so data persists across restarts

---

## 🗂️ Project Structure

| File | Purpose |
|------|---------|
| `pv.yaml` | Persistent Volume — defines the actual storage |
| `pvc.yaml` | Persistent Volume Claim — Pod's request for storage |
| `pod.yaml` | Pod — mounts the PVC and uses the storage |

---

## 🚀 How to Deploy

### Prerequisites
- Kubernetes cluster running (Minikube / kubeadm / EKS)
- `kubectl` configured and connected

### Step 1 — Create the Persistent Volume
```bash
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
kubectl apply -f pod.yaml
# Check PV status (should be Bound)
kubectl get pv

# Check PVC status (should be Bound)
kubectl get pvc

# Check Pod status (should be Running)
kubectl get pods
# Step 1: Exec into the Pod and write data
kubectl exec -it <pod-name> -- /bin/sh
echo "Hello from Kubernetes!" > /data/test.txt
exit

# Step 2: Delete the Pod
kubectl delete pod <pod-name>

# Step 3: Recreate the Pod
kubectl apply -f pod.yaml

# Step 4: Check if data still exists
kubectl exec -it <pod-name> -- cat /data/test.txt
# Output: Hello from Kubernetes! ✅ Data persisted!
