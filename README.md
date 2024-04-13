# Main kubectl Commands

This repository serves as a guide for using various kubectl commands to manage Kubernetes clusters and resources. It includes instructions for creating and debugging pods, deploying applications, applying configuration files, and more.

## Table of Contents

1. [Create and Debug Pods in Minikube Cluster](#create-and-debug-pods-in-minikube-cluster)
2. [Debugging Pods](#debugging-pods)
3. [Delete Deployment](#delete-deployment)
4. [Apply Configuration File](#apply-configuration-file) 

---

## Create and Debug Pods in Minikube Cluster

### Get Status of Components

```sh
kubectl get nodes
kubectl get pods
kubectl get services
```

<img src="https://i.imgur.com/pRZMqL4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

---

### Create and Edit a Pod

```sh
kubectl create deployment nginx-depl --image=nginx
kubectl edit deployment nginx-depl
```

<img src="https://i.imgur.com/1WS7Q6Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>


<img src="https://i.imgur.com/esRaFg1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

---

### Debugging Pods

```sh
kubectl create deployment mongo-deployment --image=mongo
kubectl get pod
kubectl describe pod mongo-deployment-555654868f-hnllp
kubectl logs mongo-deployment-555654868f-hnllp
kubectl exec -it mongo-deployment-555654868f-hnllp -- bin/bash
```

<img src="https://i.imgur.com/BbKYM2h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<img src="https://i.imgur.com/EVRQdPM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

---


### Delete Deployment

```sh
kubectl delete deployment mongo-deployment
kubectl delete deployment nginx-depl
```

<img src="https://i.imgur.com/0JrExfN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

---

### Apply Configuration File

```sh
touch nginx-deployment.yaml
vim nginx-deployment.yaml
```

**Add the following YAML configuration:**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 1
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.25
        ports:
        - containerPort: 80
```

<img src="https://i.imgur.com/rXC3Y17.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

---

**Save the YAML file and apply it:**

```sh
kubectl apply -f nginx-deployment.yaml
```

<img src="https://i.imgur.com/smfKHGM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
