# flask-ben Helm Chart

Helm chart for the Flask app from Phase 1 and 2.

## Install

```bash
helm install flask-ben ./flask-ben
```

## Upgrade

```bash
helm upgrade flask-ben ./flask-ben
```

## Uninstall

```bash
helm uninstall flask-ben
```

## Access the app

```bash
kubectl port-forward service/flask-ben-service 5000:80 --address 0.0.0.0
```

Then open http://localhost:5000
