# DevOps Course Project
This repo contains my work for the DevOps course, organized by phase.

## Project Structure
```
DevOps_Ben/
├── Phase1/          # Docker & containerization
│   └── Flask_Bens/
│       ├── app.py
│       ├── Dockerfile
│       ├── docker-compose.yml
│       ├── requirements.txt
│       └── README.md
├── Phase2/          # Kubernetes orchestration
│   └── kubernetes/
│       ├── flask_deploy.yaml
│       ├── service.yaml
│       ├── hpa.yaml
│       ├── configmap.yaml
│       ├── cronjob.yaml
│       └── README.md
└── Phase3/          # Automation - Helm, Git workflows & CI/CD
    ├── helm/
    │   └── flask-ben/
    │       ├── Chart.yaml
    │       ├── values.yaml
    │       └── templates/
    │           ├── deployment.yaml
    │           ├── service.yaml
    │           ├── hpa.yaml
    │           ├── configmap.yaml
    │           └── cronjob.yaml
    └── jenkins/
        └── Jenkinsfile
```

## Phases

### Phase 1 - Docker
A simple Python Flask application containerized with Docker. The image is published on Docker Hub at `chico871/flask-ben:latest`.

See (Phase1/Flask_Bens/README.md) for setup instructions.

### Phase 2 - Kubernetes
The same Flask application deployed on a Kubernetes cluster using Minikube. Includes autoscaling, configuration management, health monitoring and scheduled jobs.

See (Phase2/kubernetes/README.md) for setup instructions.

### Phase 3 - Automation
Packaged the Kubernetes manifests into a Helm chart and deployed it on Minikube. Set up Git workflows with multiple branches, demonstrated conflict resolution and pull requests. Built a Jenkins CI/CD pipeline with 3 stages: build the Docker image, test the live app, and deploy with Helm.

See (Phase3/jenkins/Jenkinsfile) for the pipeline.

## Tech Stack
- Python / Flask
- Docker / Docker Hub
- Kubernetes / Minikube
- kubectl
- Helm
- Git / GitHub
- Jenkins
