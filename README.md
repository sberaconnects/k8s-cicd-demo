# 🚀 CI/CD Demo: Docker + GitHub Actions + Kubernetes

This project demonstrates a full DevOps pipeline:
- Dockerized app (NGINX + static HTML)
- GitHub Actions workflow for CI/CD
- Auto-deployment to Kubernetes on push to `main`
- Public exposure via Kubernetes LoadBalancer

## 🔧 Stack Used
- Docker
- GitHub Actions
- Kubernetes (Minikube, k3s, or a cloud provider like DigitalOcean)
- DigitalOcean K8s (for public deployment demo)

## 🚀 How It Works
1. Push to `main` branch
2. GitHub Actions builds Docker image
3. Pushes it to Docker Hub
4. Applies Kubernetes manifests (`deployment.yaml` and `service.yaml`)
5. Your app is automatically deployed and publicly accessible!

## 🔐 GitHub Secrets Required
- `DOCKER_USERNAME`
- `DOCKER_PASSWORD`
- `KUBECONFIG_BASE64` (base64-encoded kubeconfig from your cluster)

## 💡 What I Learned
- How to integrate GitHub Actions with Kubernetes
- Proper way to store and decode secrets securely in CI
- Handling kubectl errors due to inaccessible local clusters
- Using DigitalOcean to host a public K8s cluster for CI/CD demos
- Challenges of base64 encoding and decoding kubeconfig across platforms
- Testing workflows with `workflow_dispatch` and self-hosted runners

## 📈 Challenges Faced
- GitHub runners can't access local clusters like Minikube (used cloud-based K8s instead)
- `.kube/config` path didn't exist initially on runners (added `mkdir -p $HOME/.kube`)
- Docker image name consistency was key to avoid redeployment issues
- Had to properly base64 encode `kubeconfig` with `-w 0` for single-line format
- DNS/public IP provisioning via LoadBalancer required patience and a retry or two

## 🌐 Live Demo (if configured with LoadBalancer)
After deployment, use:
```bash
kubectl get svc cicd-demo-service
```
to retrieve the EXTERNAL-IP and access your running app.

---

Happy shipping! 🚀