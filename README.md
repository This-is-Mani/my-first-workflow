# my-first-workflow
github-actions-learning

-----------------------

🧭 📊 Interview-Ready Architecture Diagram
                 ┌────────────────────┐
                 │   Developer (You)  │
                 │  VS Code / Git     │
                 └─────────┬──────────┘
                           │ push code
                           ▼
                 ┌────────────────────┐
                 │     GitHub Repo     │
                 └─────────┬──────────┘
                           │ trigger workflow
                           ▼
                 ┌────────────────────┐
                 │ GitHub Actions CI   │
                 │ - Build Docker Img  │
                 │ - Push to Registry  │
                 └─────────┬──────────┘
                           │ docker push
                           ▼
                 ┌────────────────────┐
                 │    Docker Hub       │
                 │  (Image Registry)   │
                 └─────────┬──────────┘
                           │ image pull
                           ▼
                 ┌────────────────────────────┐
                 │        AWS EKS Cluster      │
                 │                            │
                 │   ┌───────────────┐        │
                 │   │   Node (EC2)  │        │
                 │   │               │        │
                 │   │   Pod         │        │
                 │   │ (Container)   │        │
                 │   └───────────────┘        │
                 └─────────┬──────────────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │   Service (NodePort)│
                 └─────────┬──────────┘
                           │
                           ▼
                 ┌────────────────────┐
                 │      Browser        │
                 │  http://IP:PORT     │
                 └────────────────────┘
🧾 📄 One-Page Summary (PDF Style Content)

You can copy this directly into Word / Notion / README.

🚀 Project: End-to-End DevOps Pipeline using Docker, GitHub Actions & EKS
🧭 Objective

To build and deploy a containerized application using:

Docker (containerization)
GitHub Actions (CI/CD)
Docker Hub (image registry)
AWS EKS (Kubernetes deployment)
🧱 Architecture Flow
Code → GitHub → GitHub Actions → Docker Image → Docker Hub → EKS → Pods → Service → Browser
🟢 Implementation Steps
1. Application Development
Created a simple Node.js app (app.js)
App runs on port 3000
2. Containerization (Docker)
Created Dockerfile
Built Docker image
Verified container locally
3. CI/CD Setup (GitHub Actions)
Created workflow (.github/workflows/main.yml)
Automated:
Docker build
Docker push to Docker Hub
Used GitHub Secrets for secure login
4. Image Storage (Docker Hub)
Stored image as:
<username>/my-app
5. Kubernetes Setup (AWS EKS)
Created EKS cluster
Added worker nodes (EC2)
Connected using kubectl
6. Deployment
Created deployment.yml
Deployed application using Docker image
Verified pods are running
7. Service Exposure
Created service.yml
Used NodePort to expose application
Opened port in AWS Security Group
8. Access Application
Used:
http://<EC2-IP>:<NodePort>
Verified app is accessible in browser
🧠 Key Concepts Learned
Docker Image vs Container
CI/CD automation using GitHub Actions
Kubernetes components:
Pod
Deployment
Service
Node vs Cluster
Debugging:
CrashLoopBackOff
Logs analysis
AWS networking (Security Groups)
🧹 Cleanup
Deleted Kubernetes resources:
kubectl delete -f service.yml
kubectl delete -f deployment.yml
Deleted:
Node group
EKS cluster
EC2 instances
🎯 Outcome

Successfully built and deployed a full pipeline:

Application → Container → CI/CD → Cloud Deployment → Public Access
