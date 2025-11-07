# 🌟 #ThreeTierAppDeployment-EKS Challenge

## 🧩 Overview

Welcome to the **Three-Tier App Deployment Challenge** by **[@AhmadProjects-git](https://github.com/AhmadProjects-git)**!
This repository showcases the deployment of a **Three-Tier Web Application** built with **ReactJS ⚛️**, **NodeJS 🚀**, and **MongoDB 🍃**, deployed on **Amazon EKS ☸️ (Elastic Kubernetes Service)**.

The goal is to demonstrate **modern DevOps practices**, **scalable infrastructure**, and **end-to-end CI/CD automation** using AWS Cloud services.

🎯 **Deploy, Enhance, and Learn!**
Feel free to clone, customize, and extend this setup — perfect for portfolio or production-ready Kubernetes projects.

---

## ⚙️ Prerequisites

Before starting, make sure you have:

* 🐳 Basic knowledge of **Docker**, **Kubernetes**, and **AWS**
* ☁️ An **AWS account** with necessary permissions

---

## 🧱 Project Structure

### 🖥️ **Application Code**

Located in the `Application-Code` directory — contains the **frontend (ReactJS)** and **backend (NodeJS)** source code for the three-tier application.

### 🔁 **Jenkins Pipeline Code**

In the `Jenkins-Pipeline-Code` directory — includes Jenkins pipeline scripts for **CI/CD automation**, ensuring smooth build, test, and deploy processes.

### 🧰 **Jenkins Server Terraform**

Found in `Jenkins-Server-TF` — Terraform scripts that **automate Jenkins server provisioning** on AWS, simplifying infrastructure management.

### ☸️ **Kubernetes Manifests Files**

In `Kubernetes-Manifests-Files` — YAML manifests for **deploying the app on EKS**, managing pods, services, and deployments.

---

## 🧠 Tools & Technologies Explored

🛠️ **Core Tools:**

* **Terraform** & **AWS CLI** for Infrastructure as Code
* **Jenkins**, **SonarQube**, **Kubectl**, and **Helm** for CI/CD setup
* **Prometheus**, **Grafana** for Monitoring
* **ArgoCD** for GitOps

🚢 **Deployment Flow:**

1. IAM user setup & Terraform provisioning 🧩
2. Jenkins deployment with AWS integration ⚙️
3. EKS cluster creation & load balancer setup ☸️
4. Secure Docker image storage in ECR 🐳
5. Helm-based monitoring stack 📊
6. ArgoCD for GitOps automation 🚀

📈 This journey covers **everything from infrastructure to continuous delivery** — the full DevOps lifecycle!

---

## 📘 Getting Started

For a detailed step-by-step guide, check out my [detailed DevSecOps walkthrough](https://amanpathakdevops.medium.com/advanced-end-to-end-devsecops-kubernetes-three-tier-project-using-aws-eks-argocd-prometheus-fbbfdb956d1a).

### Step 1: IAM Configuration

```bash
# Create a user with AdministratorAccess
aws iam create-user --user-name eks-admin
```

Generate and configure access keys.

### Step 2: EC2 Setup

Launch an Ubuntu instance and SSH into it:

```bash
ssh -i "key.pem" ubuntu@<EC2-IP>
```

### Step 3: Install AWS CLI

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install unzip -y
unzip awscliv2.zip
sudo ./aws/install
aws configure
```

### Step 4: Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
sudo usermod -aG docker $USER
docker ps
```

### Step 5: Install kubectl

```bash
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
chmod +x ./kubectl && sudo mv ./kubectl /usr/local/bin
kubectl version --short --client
```

### Step 6: Install eksctl

```bash
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version
```

### Step 7: Create an EKS Cluster

```bash
eksctl create cluster --name three-tier-cluster --region us-west-2 --node-type t2.medium --nodes-min 2 --nodes-max 2
aws eks update-kubeconfig --region us-west-2 --name three-tier-cluster
kubectl get nodes
```

### Step 8: Deploy Manifests

```bash
kubectl create namespace workshop
kubectl apply -f .
```

### Step 9: Setup AWS Load Balancer

```bash
curl -O https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/install/iam_policy.json
aws iam create-policy --policy-name AWSLoadBalancerControllerIAMPolicy --policy-document file://iam_policy.json
```

### Step 10: Install Load Balancer Controller

```bash
helm repo add eks https://aws.github.io/eks-charts
helm repo update
helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=three-tier-cluster --set serviceAccount.create=false --set serviceAccount.name=aws-load-balancer-controller
```

---

## 🧹 Cleanup

```bash
eksctl delete cluster --name three-tier-cluster --region us-west-2
```

Then:

* Stop or terminate EC2 instances
* Delete load balancers and security groups to avoid extra costs

---

## 🤝 Contribution Guidelines

1. 🍴 Fork this repository
2. 🌱 Create your feature branch (`git checkout -b feature/amazing-feature`)
3. 💻 Commit your changes (`git commit -m "Added awesome enhancement"`)
4. 🚀 Push to your branch (`git push origin feature/amazing-feature`)
5. 🔁 Open a Pull Request

---

## 🏆 Rewards

🎁 The best implementations or enhancements may be showcased on this repository!
Share your creative deployments and GitOps workflows.

---

## 💬 Support

Having issues or questions?
Open an [issue here](https://github.com/AhmadProjects-git/ThreeTierAppDeployment-EKS/issues) — let’s troubleshoot together!

---

**Happy Learning!** 🚀👨‍💻👩‍💻
**Maintained by:** [@AhmadProjects-git](https://github.com/AhmadProjects-git)

---

Would you like me to also create a **short version for the GitHub “About” section** (the 1–2 line repo description + tags for visibility like `#AWS #DevOps #Kubernetes #EKS`)?
