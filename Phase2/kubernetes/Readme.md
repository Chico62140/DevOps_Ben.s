# Phase 2 - Kubernetes

Deploying the Flask app on a Kubernetes cluster using Minikube.

## Requirements

- Docker
- Minikube
- kubectl

## Setup

### 1. Start the cluster

```bash
minikube start --driver=docker --force
```

### 2. Apply all manifests

```bash
kubectl apply -f configmap.yaml
kubectl apply -f flask_deploy.yaml
kubectl apply -f service.yaml
kubectl apply -f hpa.yaml
kubectl apply -f cronjob.yaml
```

### 3. Access the app

Since we're running Minikube with the Docker driver, use port-forward to access the app:

```bash
kubectl port-forward service/flask-ben-service 5000:80 --address 0.0.0.0 &
```

Then open: http://localhost:5000

## Project files

- `flask_deploy.yaml` — Deployment with 2 replicas, resource limits, ConfigMap injection, liveness and readiness probes
- `service.yaml` — NodePort Service exposing the app on port 30000
- `hpa.yaml` — Horizontal Pod Autoscaler, scales between 2-5 Pods when CPU exceeds 50%
- `configmap.yaml` — App configuration (APP_NAME, APP_ENV, APP_VERSION)
- `cronjob.yaml` — Runs every 5 minutes, checks if Flask is responding and logs the result

## Verifying the setup

Check everything is running:
```bash
kubectl get all
```

Check the ConfigMap is injected:
```bash
kubectl exec -it $(kubectl get pod -l app=flask-ben -o jsonpath='{.items[0].metadata.name}') -- env | grep APP
```

Check HPA status:
```bash
kubectl get hpa
```

Check CronJob logs:
```bash
kubectl logs -l job-name=$(kubectl get jobs -o jsonpath='{.items[0].metadata.name}')
```

## How HPA works

HPA watches CPU usage across all Pods. When average usage crosses 50%, it automatically adds Pods up to a maximum of 5. When load drops, it scales back down to the minimum of 2.

To test it, run a load generator inside the cluster:
```bash
kubectl run -it --rm load-generator --image=busybox --restart=Never -- /bin/sh
```

Then inside the container:
```bash
while true; do wget -q -O- http://flask-ben-service:80; done
```

Watch HPA react in a second terminal:
```bash
watch kubectl get hpa
```
