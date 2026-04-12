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
└── Phase2/          # Kubernetes orchestration
    └── kubernetes/
        ├── flask_deploy.yaml
        ├── service.yaml
        ├── hpa.yaml
        ├── configmap.yaml
        ├── cronjob.yaml
        └── README.md
```

## Phases

### Phase 1 - Docker
A simple Python Flask application containerized with Docker. The image is published on Docker Hub at `chico871/flask-ben:1.0.0`.

See (Phase1/Flask_Bens/README.md) for setup instructions.

### Phase 2 - Kubernetes
The same Flask application deployed on a Kubernetes cluster using Minikube. Includes autoscaling, configuration management, health monitoring and scheduled jobs.

See (Phase2/kubernetes/README.md) for setup instructions.

## Tech Stack

- Python / Flask
- Docker / Docker Hub
- Kubernetes / Minikube
- kubectl
