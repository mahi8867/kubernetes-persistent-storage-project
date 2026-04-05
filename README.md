# Kubernetes Persistent Storage Project

## 📌 Overview
This project demonstrates how to implement persistent storage in Kubernetes using:
- Persistent Volume (PV)
- Persistent Volume Claim (PVC)
- Pod integration

## ⚙️ Technologies Used
- Kubernetes
- YAML
- Docker

## 📁 Project Files
- pod.yaml → Pod configuration
- pv.yaml → Persistent Volume
- pvc.yaml → Persistent Volume Claim

## 🚀 Steps to Execute

### 1. Create Persistent Volume
kubectl apply -f pv.yaml

### 2. Create Persistent Volume Claim
kubectl apply -f pvc.yaml

### 3. Deploy Pod
kubectl apply -f pod.yaml

### 4. Verify Resources
kubectl get pods
kubectl get pv
kubectl get pvc

## 🎯 Key Learning
- Understanding Kubernetes storage
- PV & PVC configuration
- Real-time DevOps implementation
