# DevOps Project - Zomato Deployment

## Overview

This project demonstrates the **end-to-end deployment** of a **Zomato Clone** using **DevOps practices**, including **Jenkins, Docker, Kubernetes (EKS), Prometheus, Grafana, ArgoCD**, and **various security tools** such as **SonarQube, OWASP, Trivy, and Docker Scout**.

## Features

- **CI/CD Pipeline**: Implemented using **Jenkins** for automated deployment.
- **Security Integration**: Utilized **SonarQube, OWASP, Trivy, and Docker Scout** for vulnerability scanning.
- **Containerized Deployment**: **Dockerized** the application and deployed it on **AWS EKS (Kubernetes)**.
- **Monitoring**: Configured **Prometheus, Grafana, and Node Exporter** for application and infrastructure monitoring.
- **ArgoCD**: Implemented for GitOps-based Kubernetes application deployment.

## Prerequisites

Before proceeding with the setup, ensure you have:

- **AWS Account** with necessary IAM permissions.
- **Basic knowledge of DevOps tools** such as Jenkins, Docker, and Kubernetes.
- **Installed dependencies**: AWS CLI, Docker, Jenkins, SonarQube, Trivy, Terraform, and Kubernetes CLI (`kubectl`).

## Deployment Steps

### Step 1: Setting up an AWS EC2 Instance

1. **Launch an Ubuntu EC2 instance** (`t2.large`, `30GB` storage).
2. Assign an **IAM role** with necessary permissions.

### Step 2: Install Required Tools

Install **AWS CLI**, **Jenkins**, **Docker**, **Trivy**, **Docker Scout**, and **SonarQube**:

```bash
sudo apt update -y
sudo apt install -y awscli unzip docker.io jenkins terraform
```

Run **SonarQube**:

```bash
docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
```

### Step 3: Configure Jenkins

1. Install **Jenkins Plugins** for Terraform, SonarQube, NodeJS, OWASP, Docker.
2. Configure **Jenkins Pipeline Jobs** to:
   - Checkout the repository.
   - Run **static code analysis** using **SonarQube**.
   - Scan files using **OWASP, Trivy, and Docker Scout**.
   - Build and push **Docker images**.
   - Deploy the application on **Kubernetes (EKS)**.

### Step 4: Kubernetes Deployment

1. Apply Kubernetes **deployment and service manifests**:

```bash
kubectl apply -f deployment.yml
kubectl apply -f service.yml
```

2. Retrieve the **Load Balancer URL** and access the application.

### Step 5: Monitoring Setup

1. Install **Prometheus, Node Exporter, and Grafana** for monitoring.
2. Configure **Jenkins job metrics** scraping using Prometheus.
3. Visualize dashboards in **Grafana**.

### Step 6: ArgoCD Deployment

1. Install **ArgoCD** in Kubernetes:

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.4.7/manifests/install.yaml
```

2. Expose **ArgoCD** via LoadBalancer:

```bash
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
```

### Step 7: Clean-Up

To remove the **EKS cluster**:

```bash
eksctl delete cluster kastrocluster
```

Terminate the **EC2 instance** and delete **IAM Role**.

## Tools & Technologies Used

- **AWS** (EC2, EKS, IAM, S3)
- **Jenkins** (CI/CD Pipeline)
- **Docker & Kubernetes** (Containerization & Orchestration)
- **Terraform** (Infrastructure as Code)
- **SonarQube, OWASP, Trivy, Docker Scout** (Security Analysis)
- **Prometheus, Grafana, Node Exporter** (Monitoring & Logging)
- **ArgoCD** (GitOps-based Kubernetes Deployment)
- **GitHub** (Version Control)

## Project Repository

🔗 [GitHub Repository](https://github.com/KastroVKiran/DevOps-Project-Zomato-Kastro.git)

---

## Credit

This project was **inspired** by the amazing work of [KastroVKiran](https://github.com/KastroVKiran). Their **detailed documentation** and insights significantly helped in understanding and implementing **DevOps best practices** for this deployment. A huge thanks for sharing this **valuable content** with the community!

---

## Connect with Me

For any questions or discussions, feel free to reach out:

- **GitHub**: [Kritagya-web](https://github.com/Kritagya-web/)
- **LinkedIn**: [Kritagya Kumra](https://www.linkedin.com/in/kritagya-kumra/)
- **Portfolio**: [Portfolio](https://kritagyakumraportfolio.netlify.app/)

---
<div align="center">

🚀 **Created with love ❤️ by Kritagya. Happy Learning & Secure Deployments!**

</div>

<div align="center">

🚀  **Show some ❤️ by starring at some of the repositories!**

</div>
