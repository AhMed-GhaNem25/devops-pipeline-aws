# 🚀 Full DevOps Pipeline on AWS

> A production-style CI/CD pipeline that automatically builds, pushes, and deploys a Node.js + MongoDB application to AWS EC2 — triggered by every Git push.
---
![Tech Stack](https://img.shields.io/badge/Stack-Node.js%20%7C%20Docker%20%7C%20Jenkins%20%7C%20Ansible%20%7C%20AWS-blue)
![CI/CD](https://img.shields.io/badge/CI%2FCD-Jenkins-orange)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📌 What This Project Does

Most Node.js apps stop at writing code. This project goes further — it automates the entire journey from **code commit to live deployment**:

1. Developer pushes code to GitHub
2. Jenkins detects the push via Webhook and triggers the pipeline
3. Docker image is built and pushed to Docker Hub
4. Ansible provisions the AWS EC2 instance (installs Docker, sets up environment)
5. Updated container is deployed automatically — zero manual steps

---

## 🏗️ Architecture Overview

```
Developer
    │
    ▼
GitHub (Push)
    │
    ▼ (Webhook)
Jenkins CI/CD Pipeline
    ├── Build Docker Image
    ├── Push to Docker Hub
    └── SSH → EC2 Instance
              │
              ▼
         Ansible Playbook
              ├── Install Docker
              ├── Pull Image
              └── Run Containers
                    ├── Node.js App  :3000
                    └── MongoDB      :27017
```

---

## 🔧 Tech Stack

| Layer | Technology |
|-------|-----------|
| Application | Node.js + Express.js |
| Database | MongoDB |
| Containerization | Docker + Docker Compose |
| CI/CD | Jenkins (Pipeline as Code) |
| Infrastructure Automation | Ansible |
| Cloud | AWS EC2 (Ubuntu) |
| Orchestration (bonus) | Kubernetes manifests included |

---

## ✅ Pipeline Features

- **Auto-trigger** on every push via GitHub Webhook
- **Dockerized build** — consistent across all environments
- **Docker Hub integration** — image versioning and storage
- **Ansible automation** — no manual SSH setup needed
- **Kubernetes-ready** — deployment and service manifests included for scaling

---

## 📂 Project Structure

```
devops-pipeline-aws/
├── app/
│   ├── server.js           # Express.js backend
│   └── package.json
├── Dockerfile              # Node.js app image
├── docker-compose.yml      # App + MongoDB services
├── Jenkinsfile             # Pipeline as code
├── ansible/
│   ├── deploy-docker.yaml  # Install Docker + deploy containers
│   └── db-setup.yaml       # MongoDB provisioning
├── hosts                   # Ansible inventory
├── app-deployment.yaml     # Kubernetes Deployment
├── app-service.yaml        # Kubernetes Service
└── README.md
```

---

## 🚀 How to Deploy

### Prerequisites
- AWS EC2 instance (Ubuntu 20.04+)
- SSH key pair
- Ansible installed locally
- Jenkins server running (local or cloud)

### Step 1 — Clone the repo
```bash
git clone https://github.com/AhMed-GhaNem25/Final-DEPI-Project.git
cd devops-pipeline-aws
```

### Step 2 — Configure Ansible inventory
Edit `hosts`:
```ini
[app]
YOUR_EC2_PUBLIC_IP ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/your-key.pem
```

### Step 3 — Run Ansible to provision and deploy
```bash
ansible-playbook -i hosts ansible/deploy-docker.yaml
```

### Step 4 — Access the app
```
http://YOUR_EC2_IP:3000
```

---

## 🐳 Run Locally with Docker Compose

```bash
docker-compose up --build
```
App available at: `http://localhost:3000`

---

## 🔐 Security Notes

- EC2 access restricted to SSH key pair only
- MongoDB not exposed externally
- Only ports 22 and 3000 open in security group
- Services isolated via Docker Compose network

---

## 🎓 Context

Built as the graduation project for the **Digital Egypt Pioneers Initiative (DEPI)** — a national program focused on practical tech skills.

This project reflects real-world DevOps practices: infrastructure as code, automated deployments, and containerized applications.

---

## 📬 Contact

**Ahmed Ghanem**
- 🔗 [LinkedIn](https://linkedin.com/in/ghanem-g23/)
- 💻 [GitHub](https://github.com/AhMed-GhaNem25)

---

*Built with ❤️ as part of DEPI — Digital Egypt Pioneers Initiative*
