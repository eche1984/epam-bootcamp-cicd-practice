# CI/CD Pipeline Practice — GitHub Actions + Docker + Kubernetes (Minikube)

A hands-on CI/CD pipeline built during the EPAM DevOps bootcamp. On every push, GitHub Actions 
spins up an ephemeral Minikube cluster, builds a Docker image for a simple Node.js application, 
deploys it to Kubernetes, and verifies the deployment is live and reachable.

## Stack

- **CI/CD:** GitHub Actions
- **Containerization:** Docker
- **Orchestration:** Kubernetes (Minikube)
- **App:** Node.js (minimal HTTP server)

## Pipeline Flow

1. **Checkout** the repository code
2. **Start Minikube** as an ephemeral local Kubernetes cluster within the runner
3. **Build** the Docker image directly inside Minikube's Docker environment
4. **Deploy** the image to the cluster via `kubectl apply`, using the manifest in 
   `k8s-node-app.yaml`
5. **Wait** for the deployment to reach `available` status
6. **Verify** the service is reachable by listing active Minikube services and resolving 
   the app's URL

## Files

- `server.js` — minimal Node.js HTTP server (sample app for the pipeline)
- `Dockerfile` — container image definition for the Node.js app
- `k8s-node-app.yaml` — Kubernetes Deployment/Service manifest
- `.github/workflows/` — GitHub Actions workflow definition

## Context

This repository was built as a practical exercise during the EPAM DevOps bootcamp, focused on 
understanding end-to-end CI/CD flow: build → containerize → deploy → verify, using a disposable 
Kubernetes environment for fast iteration.
