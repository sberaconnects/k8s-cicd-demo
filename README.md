# 🚀 CI/CD Demo: Docker + GitHub Actions + Kubernetes

This project demonstrates a full DevOps pipeline:
- Dockerized app (NGINX + static HTML)
- GitHub Actions workflow for CI/CD
- Auto-deployment to Kubernetes on push to `main`

## 🔧 Stack Used
- Docker
- GitHub Actions
- Kubernetes (Minikube, k3s, EKS, or GKE)

## 🚀 How It Works
1. Push to `main` branch
2. GitHub Actions builds Docker image
3. Pushes it to Docker Hub
4. Applies Kubernetes manifests
5. Your app is automatically deployed!

## 📦 Setup

### GitHub Secrets Required:
- `DOCKER_USERNAME`
- `DOCKER_PASSWORD`
- `KUBECONFIG_BASE64` (your kubeconfig file base64-encoded)

Happy shipping! 🚀