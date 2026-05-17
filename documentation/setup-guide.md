# 🚀 AWS Auto-Healing Scalable Web Application
## Complete Deployment Setup Guide

---

# 📌 Project Overview

This project demonstrates a production-ready, highly available, fault-tolerant, and scalable web application architecture on AWS.

The infrastructure includes:

- Multi-Tier VPC Architecture
- Public and Private Subnets
- EC2 Web Servers
- Application Load Balancer
- Auto Scaling Group
- Amazon RDS (Private Database)
- CloudWatch Monitoring
- SNS Alerting
- S3 Storage
- Terraform Automation
- Auto-Healing Infrastructure

---

# 🏗️ Architecture Diagram

> Add architecture image here

```bash
screenshots/architecture.png
```

---

# 📦 AWS Services Used

| Service | Purpose |
|---|---|
| EC2 | Application Hosting |
| ALB | Traffic Distribution |
| Auto Scaling | Dynamic Scaling |
| VPC | Network Isolation |
| RDS | Managed Database |
| CloudWatch | Monitoring |
| SNS | Notifications |
| S3 | Static Storage |
| IAM | Secure Permissions |
| Terraform | Infrastructure Automation |

---

# 🧰 Prerequisites

Before starting:

## Required Accounts & Tools

- AWS Account
- AWS CLI Installed
- Terraform Installed
- Git Installed
- VS Code Recommended

---

# 📁 Project Structure

```bash
aws-auto-healing-webapp/
│
├── terraform/
├── app/
├── screenshots/
├── documentation/
└── README.md
```

---

# ⚙️ STEP 1 — Configure AWS CLI

## Install AWS CLI

Verify installation:

```bash
aws --version
```

---

## Configure Credentials

Run:

```bash
aws configure
```

Provide:

```bash
AWS Access Key ID
AWS Secret Access Key
Region: ap-south-1
Output Format: json
```

---

# 🌐 STEP 2 — Create VPC Infrastructure

## Create VPC

| Setting | Value |
|---|---|
| Name | Production-VPC |
| CIDR | 10.0.0.0/16 |

---

## Create Subnets

| Subnet | CIDR | Type |
|---|---|---|
| Public-1 | 10.0.1.0/24 | Public |
| Public-2 | 10.0.2.0/24 | Public |
| Private-1 | 10.0.3.0/24 | Private |
| Private-2 | 10.0.4.0/24 | Private |

---

## Configure Internet Gateway

Attach Internet Gateway to VPC.

---

## Configure Route Tables

### Public Route Table

```bash
0.0.0.0/0 → Internet Gateway
```

### Private Route Table

```bash
0.0.0.0/0 → NAT Gateway
```

---

# 🖥️ STEP 3 — Launch EC2 Web Server

## EC2 Configuration

| Setting | Value |
|---|---|
| AMI | Amazon Linux 2 |
| Instance Type | t2.micro |
| Storage | 8 GB |
| Security Group | Web-SG |

---

# 🔐 STEP 4 — Configure Security Groups

## ALB Security Group

Allow:

```bash
HTTP 80 from Anywhere
```

---

## EC2 Security Group

Allow:

```bash
HTTP 80 from ALB Security Group
SSH 22 from My IP
```

---

## RDS Security Group

Allow:

```bash
MYSQL 3306 from EC2 Security Group
```

---

# 🌍 STEP 5 — Install Web Application

SSH into EC2:

```bash
ssh -i key.pem ec2-user@PUBLIC-IP
```

Update packages:

```bash
sudo yum update -y
```

Install Apache:

```bash
sudo yum install httpd -y
```

Start Apache:

```bash
sudo systemctl start httpd
sudo systemctl enable httpd
```

---

# 📝 STEP 6 — Deploy Website

Create webpage:

```bash
sudo nano /var/www/html/index.html
```

Paste:

```html
<h1>AWS Auto-Healing Web Application</h1>
```

Verify:

```bash
http://PUBLIC-IP
```

---

# ⚖️ STEP 7 — Configure Load Balancer

## Create Target Group

Health Check Path:

```bash
/
```

---

## Create Application Load Balancer

Attach:

- Public Subnets
- ALB Security Group
- Target Group

---

# 📈 STEP 8 — Configure Auto Scaling

## Create Launch Template

Include:

- AMI
- Security Group
- User Data Script

---

## User Data Script

```bash
#!/bin/bash
yum update -y
yum install httpd -y
systemctl start httpd
systemctl enable httpd
echo "<h1>Production AWS App</h1>" > /var/www/html/index.html
```

---

## Create Auto Scaling Group

| Setting | Value |
|---|---|
| Desired Capacity | 2 |
| Minimum Capacity | 2 |
| Maximum Capacity | 4 |

Enable:

```bash
ELB Health Checks
```

---

# 🗄️ STEP 9 — Create RDS Database

| Setting | Value |
|---|---|
| Engine | MySQL |
| Deployment | Free Tier |
| Public Access | Disabled |

Deploy inside:

- Private Subnets

---

# 📊 STEP 10 — Configure Monitoring

## Create CloudWatch Alarm

Metric:

```bash
CPUUtilization > 70%
```

---

## Configure SNS Notifications

- Create SNS Topic
- Subscribe Email
- Confirm Subscription

---

# ☁️ STEP 11 — Configure S3 Storage

Create S3 bucket for:

- Static assets
- Logs
- Backup files

Enable:

```bash
Versioning
```

---

# 🤖 STEP 12 — Deploy Infrastructure with Terraform

Navigate:

```bash
cd terraform
```

Initialize:

```bash
terraform init
```

Validate:

```bash
terraform validate
```

Deploy:

```bash
terraform apply
```

---

# ✅ Deployment Verification Checklist

| Check | Status |
|---|---|
| VPC Created | ✅ |
| EC2 Running | ✅ |
| ALB Accessible | ✅ |
| Auto Scaling Active | ✅ |
| RDS Private | ✅ |
| SNS Alerts Working | ✅ |
| CloudWatch Monitoring | ✅ |
| Terraform Success | ✅ |

---

# 📸 Required Screenshots

| Screenshot | Filename |
|---|---|
| VPC | vpc.png |
| ALB | alb.png |
| EC2 | ec2-running.png |
| Auto Scaling | autoscaling.png |
| CloudWatch | cloudwatch.png |
| SNS Email | sns-alert.png |
| Terraform Apply | terraform-apply.png |
| Final Output | final-output.png |

---

# 🚀 Future Enhancements

- Docker Containerization
- Jenkins CI/CD Pipeline
- GitHub Actions
- Kubernetes (EKS)
- AWS WAF
- CloudFront CDN
- HTTPS using ACM
- Prometheus & Grafana

---

# 👨‍💻 Author

Nitesh Vishwakarma

Cloud & DevOps Enthusiast