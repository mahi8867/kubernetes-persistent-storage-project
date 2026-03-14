# Kubernetes Persistent Storage Project

This project demonstrates how to implement Persistent Storage in Kubernetes using Persistent Volume (PV) and Persistent Volume Claim (PVC).

## Components

- Persistent Volume (PV)
- Persistent Volume Claim (PVC)
- Pod using persistent storage

## Steps

1. Create Persistent Volume
2. Create Persistent Volume Claim
3. Deploy Pod using PVC
4. Store data inside the Pod
5. Delete and recreate the Pod to verify persistence

## Files

- pv.yaml
- pvc.yaml
- pod.yaml

## Commands

Create PV
kubectl apply -f pv.yaml

Create PVC
kubectl apply -f pvc.yaml

Deploy Pod
kubectl apply -f pod.yaml

Check resources
kubectl get pv
kubectl get pvc
kubectl get pods
