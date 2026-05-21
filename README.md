kubernetes-persistent-storage-project/
│
├── pv.yaml       # Persistent Volume — defines the actual storage
├── pvc.yaml      # Persistent Volume Claim — Pod's request for storage
└── pod.yaml      # Pod — mounts the PVC and uses the storage
+---------------------------+
|        Kubernetes         |
|                           |
|  +---------------------+  |
|  |        Pod          |  |
|  |  (Mounts PVC)       |  |
|  +--------+------------+  |
|           |               |
|  +--------v------------+  |
|  |  PVC (Volume Claim) |  |
|  +--------+------------+  |
|           |               |
|  +--------v------------+  |
|  |  PV (Actual Storage)|  |
|  |  (hostPath / NFS)   |  |
|  +---------------------+  |
+---------------------------+
kubectl apply -f pv.yaml
kubectl apply -f pvc.yaml
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
# Output: Hello from Kubernetes!  ✅ Data persisted!
