# Flask Hello World

A simple Flask app that returns "Hello, World!" — containerized with Docker for Phase 1 of the DevOps course.

## Requirements

Make sure you have Docker Desktop installed and running before anything else.

## Running the app

The easiest way is to pull the image from Docker Hub and run it directly:

```bash
docker run -p 5000:5000 chico871/flask-ben:1.0.0
```

Then go to http://localhost:5000 in your browser.

If you want to build it yourself from the source code, clone the repo and run:

```bash
docker compose up --build
```

Same result, same URL.

## Project files

- `app.py` — the Flask app, listens on port 5000
- `Dockerfile` — instructions to build the image
- `docker-compose.yml` — makes running the container easier
- `requirements.txt` — just Flask

## Docker Hub

Image is available at: `chico871/flask-ben:1.0.0`
