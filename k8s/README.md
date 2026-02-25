# 🚀 DevSecOps Game Deployment Project

## 📌 Project Overview
This project demonstrates a complete DevSecOps CI/CD pipeline for deploying a containerized web game application using modern DevOps tools and security practices.

The goal of this project is to automate the full workflow — from code commit to Kubernetes deployment — while integrating security scanning into the pipeline.

---

## 🧱 Architecture Workflow

Developer Push → GitHub → Jenkins CI Pipeline  
        ↓  
Docker Image Build  
        ↓  
Trivy Security Scan  
        ↓  
Push Image to DockerHub  
        ↓  
Kubernetes Deployment (K3s)  
        ↓  
Live Application

---

## 🛠️ Tech Stack

Version Control:
- Git
- GitHub

CI/CD:
- Jenkins (Pipeline as Code)

Containerization:
- Docker
- DockerHub (Container Registry)

Security (DevSecOps):
- Trivy Vulnerability Scanner

Orchestration:
- Kubernetes (K3s Lightweight Cluster)
- kubectl

Application:
- Nginx-based static web game

---

## 📂 Project Structure

devsecops-game/
│
├── app/
│   ├── index.html
│   └── Dockerfile
│
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
│
├── Jenkinsfile
└── README.md

---

## ⚙️ CI/CD Pipeline Stages

1. Source Code Checkout  
   Jenkins automatically pulls source code from GitHub.

2. Docker Image Build  
   Application image is built using Docker.

3. Security Scan (DevSecOps)  
   Trivy scans container images for vulnerabilities.

4. DockerHub Push  
   Secure authentication using Jenkins credentials and image pushed to DockerHub.

5. Deployment  
   Application deployed automatically as container/Kubernetes workload.

---

## 🔐 Security Implementation

- Integrated Trivy vulnerability scanning
- Shift-Left Security approach
- Automated image scanning before deployment

---

## ☸️ Kubernetes Deployment

- Local Kubernetes cluster using K3s
- Deployment with multiple replicas
- Exposed using NodePort service

Access Application:

http://localhost:30007

---

## ▶️ How to Run Locally

Clone Repository:
git clone https://github.com/kkanishk26/devsecops-game.git
cd devsecops-game

Build Docker Image:
docker build -t tetris-game:v1 ./app

Run Container:
docker run -d -p 8090:80 tetris-game:v1

---

## 📸 DevOps Concepts Demonstrated

- CI/CD Automation
- DevSecOps Integration
- Containerization
- Kubernetes Deployment
- Pipeline as Code
- Automated Security Scanning

---

## 🎯 Learning Outcome

This project showcases practical implementation of:

- Continuous Integration
- Continuous Delivery
- Container Security
- Kubernetes Orchestration
- Real-world DevSecOps workflow

---

## 👨‍💻 Author

Kanishk (KK)  
DevOps & Cloud Enthusiast

GitHub:
https://github.com/kkanishk26

---

⭐ If you found this project useful, consider starring the repository.
