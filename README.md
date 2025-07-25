# 🚀 Final-DEPI-Project

A cloud-ready web application built with Node.js and MongoDB, containerized using Docker and deployed on AWS EC2.  
This project was created as part of the **Digital Egypt Pioneers Initiative (DEPI)** to demonstrate hands-on DevOps practices such as containerization, automation, and cloud deployment.

## 🔁 CI/CD Pipeline with Jenkins

This project includes a CI/CD pipeline configured via **Jenkins**.

### ✅ Pipeline Features:

- Auto-build on every code push (via GitHub Webhook)
- Build a Docker image of the Node.js application
- Push the Docker image to **Docker Hub**
- Deploy the updated container to AWS EC2

### 🔧 Jenkins Components Used:

- `Jenkinsfile` for pipeline as code
- GitHub Webhook trigger
- Docker plugin for image build and push
- SSH deployment to remote EC2 instance

> This automation ensures smooth, repeatable, and zero-downtime deployments with every update.


## 🔧 Tech Stack

- Node.js – Express.js backend  
- MongoDB – NoSQL database  
- Docker – Containerization of services  
- Docker Compose – Service orchestration  
- Jenkins – CI/CD pipeline automation  
- Ansible – Infrastructure automation  
- AWS EC2 – Cloud hosting


## 📦 Features

- Fully containerized (Node.js + MongoDB)
- Easily reproducible environment via Docker Compose
- Automated provisioning and deployment with Ansible
- Deployment to AWS EC2 Ubuntu instance
- Modular and maintainable structure

## 📂 Project Structure

Final-DEPI-Project/
├── app/                           # Node.js application code
│   ├── server.js
│   └── package.json

├── Dockerfile                     # Docker image for Node.js app

├── docker-compose.yml             # Defines app and MongoDB services

├── ansible/

│   ├── db-setup-deployment.yaml  # Ansible playbook to install MongoDB

│   └── deploy-docker.yaml        # Ansible playbook to run Docker Compose
├── hosts                          # Ansible inventory file

└── README.md                      # Project documentation

## 🧰 Prerequisites

- AWS EC2 instance (Ubuntu-based)
- SSH key pair to access EC2
- Docker & Docker Compose (will be installed via Ansible)
- Ansible installed on your local machine (for automation)

## 🚀 How to Deploy

### Step 1: Clone the repository

git clone https://github.com/AhMed-GhaNem25/Final-DEPI-Project.git
cd Final-DEPI-Project

### Step 2: Configure Ansible inventory

Edit the `hosts` file and replace with your actual EC2 IP and key path:

[app]
your-ec2-public-ip ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/your-key.pem

### Step 3: Run Ansible playbooks

Install MongoDB and deploy containers via Docker Compose:

ansible-playbook -i hosts ansible/deploy-docker.yaml

Ansible will:
- Install Docker & Docker Compose
- Clone the repo on the EC2
- Deploy the app and MongoDB containers

### Step 4: Access the Application

Once deployed, open your browser and visit:

http://your-ec2-ip:3000

## 🐳 Running Locally with Docker Compose

docker-compose up --build

App will be available at:

http://localhost:3000

## 🛠 Optional: Run Without Docker (Dev Only)

cd app
npm install
node server.js

> Requires MongoDB installed locally on your machine

## 🔐 Security Measures

- EC2 instance secured via SSH key pair  
- Docker Compose isolates services  
- MongoDB is not exposed externally  
- Only necessary ports (e.g. 22, 3000) are open in security group  
- Ansible used with limited, secure access



> Built with ❤️ as part of the Digital Egypt Pioneers Initiative
