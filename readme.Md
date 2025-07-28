# 🚀 Kubernetes EKS Cluster Setup — RoboShop Project

Welcome to the **RoboShop Kubernetes Cluster Setup** guide! This documentation walks you through setting up a fully functional Kubernetes cluster on AWS using **Terraform**, **Docker**, **eksctl**, and **kubectl**.

Whether you're just starting out or need a reliable and repeatable method to deploy Kubernetes, this guide is crafted for ease, clarity, and automation.

---

## 📌 Overview

This setup is tailored for our project **RoboShop**, a microservices-based application running on Amazon EKS.

It covers:

* Automating EC2 provisioning with Terraform
* Setting up Docker and system requirements
* Installing Kubernetes tooling (eksctl, kubectl, AWS CLI)
* Creating and managing your EKS cluster

---

## 🧰 Prerequisites

Before you begin, ensure you have:

* ✅ An AWS account with IAM permissions for EKS and EC2
* ✅ Terraform installed locally
* ✅ Git installed
* ✅ It has be accessed with password

---

## 🏗️ Step 1: Provision EC2 with Terraform

### 🔁 Clone the Repository

```bash
git clone https://github.com/Nallagachu/docker.git
cd docker
```

### ⚙️ Initialize and Apply Terraform

```bash
terraform init
terraform plan
terraform apply
```

Terraform will:

* Launch an EC2 instance based on your config
* Output the public IP of the instance

### 🔐 SSH into EC2

Use the IP provided:

```bash
password auth
```

---

## 🐳 Step 2: Install Docker and Setup Environment

Inside your EC2 instance:

```bash
chmod +x docker.sh
./docker.sh
```

This script:

* Installs Docker
* Mounts volumes for extended disk space (if needed)

---

## 🔐 Step 3: Configure AWS CLI

Configure credentials and default region:

```bash
aws configure
```

> ⚠️ Ensure the IAM credentials have permissions for EKS provisioning.

---

## ☸️ Step 4: Create the EKS Cluster

Run the following command to create your cluster from the provided config file:

```bash
eksctl create cluster --config-file=eks.yaml
```

This will:

* Read configuration from `eks.yaml`
* Spin up the EKS control plane and worker nodes

🕒 Wait 10–15 minutes for cluster provisioning to complete.

---

## ✅ Step 5: Verify the Cluster

Once the cluster is up, verify node status:

```bash
kubectl get nodes
```

Expected output: List of worker nodes in `Ready` status.

---

## 📂 Project Structure

```
docker/
├── docker.sh         # Script to install Docker and prepare disk space
├── eks.yaml          # Cluster configuration for eksctl
├── main.tf           # Terraform file for provisioning EC2 instance
```

---

## 💡 Notes & Tips

* Use consistent AWS region settings across AWS CLI, Terraform, and eksctl
* Validate IAM roles and VPC configuration if EKS provisioning fails
* Customize `eks.yaml` for cluster size, node groups, and Kubernetes version

---

## 📎 Repository Link

🔗 [https://github.com/Nallagachu/docker](https://github.com/Nallagachu/docker)

Clone, configure, deploy — and contribute if you'd like!

---



