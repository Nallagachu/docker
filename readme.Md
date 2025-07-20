
# 🚀 Terraform-Powered EC2 Instance with Docker Preinstalled

Easily launch a **Docker-ready EC2 instance** on AWS using Terraform — no complex workflows, just a single command.

This repository simplifies the process of provisioning an Amazon EC2 instance with:

- 🐳 Docker pre-installed
- 👤 A dedicated non-root user with Docker access (no need for `sudo`)
- 💾 Extended EBS volume (30 GB) automatically mounted
- ⚙️ Cloud-init configuration for automated setup

---

## 🔧 Why This Project?

Spinning up a Docker environment often involves manual steps, scripts, and post-launch configuration. This repo eliminates that friction by automating the entire process.

Whether you're:

- Testing containers  
- Deploying a dev environment  
- Running training demos  
- Learning infrastructure-as-code (IaC)  

This repo gets you started in **seconds**, not hours.

---

## 📁 What's Inside?

✅ **Terraform scripts** to provision:
- A new EC2 instance (Amazon Linux 2)
- A 30 GB EBS volume with auto-mount
- Docker installation on boot
- A non-root user (e.g., `harga`) with Docker access

---

## 📦 Requirements

Make sure you have these installed before getting started:

- [Terraform](https://developer.hashicorp.com/terraform/downloads)
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)
- An AWS IAM user with EC2 and VPC access permissions
- SSH key pair for instance access

---

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/Nallagachu/docker.git
cd docker
````

### 2. Initialize Terraform

```bash
terraform init
```

### 3. (Optional) Review the Plan

```bash
terraform plan
```

### 4. Apply the Configuration

```bash
terraform apply
```

> Approve the plan when prompted.

---

## 🔐 Access the Instance

Once provisioning is complete:

```bash
ssh -i <your-key>.pem ec2-user@<public-ip>
```

Then switch to the custom user:

```bash
su - harga
```

✅ Docker is ready
✅ Extra storage mounted
✅ No root access needed for Docker

---

## 🧠 What's Configured Automatically?

* Docker Engine installation via `cloud-init`
* Dedicated non-root user (`harga`) with Docker group permissions
* EBS volume expansion to 30 GB and automatic mounting to `/data`

You’re ready to run containers right out of the box.

---

## 📌 Use Cases

* ⚙️ Local containerized app testing
* 🧪 DevOps pipeline experiments
* 📚 Dev environment bootstrapping
* 🚀 Learn Docker & Terraform workflows

---

## 🙋 Author’s Note

This project is a small initiative to help developers and DevOps learners spin up a Docker-ready AWS environment instantly. Use it, improve it, and share your feedback — let’s grow together!

