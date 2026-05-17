# 🚀 AWS Auto-Healing Scalable Web Application

<div align="center">

![AWS](https://img.shields.io/badge/AWS-Cloud-orange?style=for-the-badge&logo=amazonaws)
![Terraform](https://img.shields.io/badge/Terraform-IaC-blueviolet?style=for-the-badge&logo=terraform)
![Linux](https://img.shields.io/badge/Linux-Server-black?style=for-the-badge&logo=linux)
![CloudWatch](https://img.shields.io/badge/Monitoring-CloudWatch-blue?style=for-the-badge&logo=amazoncloudwatch)
![DevOps](https://img.shields.io/badge/DevOps-Project-success?style=for-the-badge)

### 🌍 Production-Ready | Highly Available | Fault-Tolerant | Auto-Healing Infrastructure

</div>

---

# 📌 Project Overview

This project demonstrates a **production-grade cloud infrastructure** built on AWS using modern DevOps and Cloud Engineering best practices.

The application is designed to provide:

✅ High Availability  
✅ Dynamic Scaling  
✅ Automatic Recovery  
✅ Infrastructure Automation  
✅ Secure Multi-Tier Networking  
✅ Monitoring & Alerting  
✅ Fault Tolerance  

The architecture uses multiple AWS services integrated together to simulate a **real-world scalable enterprise deployment**.

---

# 🏗️ Architecture Diagram

> Add architecture image inside screenshots folder

```bash
screenshot/architecture.png
```

---

# ⚡ Key Features

## 🌐 Highly Available Infrastructure

- Multi-AZ deployment
- Multiple EC2 instances
- Load-balanced architecture
- Fault-tolerant networking

---

## 🔥 Auto-Healing Mechanism

- Automatic unhealthy instance replacement
- ELB health checks enabled
- Self-recovery during failures
- Minimal downtime architecture

---

## 📈 Dynamic Auto Scaling

- Automatic scale-out during high traffic
- Automatic scale-in during low utilization
- CloudWatch-based scaling policies

---

## 🔐 Secure Multi-Tier VPC Design

- Public and Private Subnets
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups
- Private RDS Database

---

## 📊 Monitoring & Alerts

- CloudWatch Metrics
- CloudWatch Alarms
- SNS Email Notifications
- Infrastructure Visibility

---

## 🤖 Infrastructure as Code

- Terraform-based provisioning
- Automated infrastructure deployment
- Repeatable environment setup

---

# 🧰 AWS Services Used

| AWS Service | Purpose |
|---|---|
| Amazon EC2 | Web Application Hosting |
| Application Load Balancer | Traffic Distribution |
| Auto Scaling Group | Dynamic Scaling |
| Amazon RDS | Managed Database |
| Amazon VPC | Network Isolation |
| Amazon S3 | Static Content Storage |
| CloudWatch | Monitoring & Logging |
| SNS | Alert Notifications |
| IAM | Secure Permissions |
| Terraform | Infrastructure Automation |

---

# 🏛️ Infrastructure Architecture

## 🌍 Networking Layer

- Custom VPC
- Public Subnets
- Private Subnets
- Internet Gateway
- NAT Gateway
- Route Tables

---

## ⚙️ Compute Layer

- EC2 Instances
- Launch Templates
- Auto Scaling Group
- Apache Web Server

---

## ⚖️ Load Balancing Layer

- Application Load Balancer
- Target Groups
- Health Checks

---

## 🗄️ Database Layer

- Amazon RDS MySQL
- Private Deployment
- Restricted Security Access

---

## 📊 Monitoring Layer

- CloudWatch Metrics
- CloudWatch Alarms
- SNS Email Alerts

---

# 📁 Project Structure

```bash
aws-auto-healing-webapp/
│
├── terraform/
│   ├── provider.tf
│   ├── vpc.tf
│   ├── ec2.tf
│   ├── alb.tf
│   ├── autoscaling.tf
│   ├── rds.tf
│   ├── securitygroups.tf
│   ├── outputs.tf
│   └── variables.tf
│
├── app/
│   ├── index.html
│   ├── styles.css
│   └── healthcheck.html
│
├── screenshots/
│   ├── architecture.png
│   ├── vpc.png
│   ├── alb.png
│   ├── autoscaling.png
│   ├── cloudwatch.png
│   ├── sns-alert.png
│   ├── ec2-termination.png
│   └── final-output.png
│
├── documentation/
│   ├── setup-guide.md
│   ├── troubleshooting.md
│   └── failure-testing.md
│
└── README.md
```

---

# 🚀 Deployment Workflow

## STEP 1 — Configure AWS Environment

- AWS CLI Setup
- IAM Configuration
- Terraform Installation

---

## STEP 2 — Build Networking Infrastructure

- Create VPC
- Configure Public & Private Subnets
- Setup Internet & NAT Gateway

---

## STEP 3 — Deploy Compute Resources

- Launch EC2 Instances
- Configure Apache Web Server
- Deploy Web Application

---

## STEP 4 — Configure Load Balancing

- Create Target Group
- Configure Application Load Balancer
- Attach Instances

---

## STEP 5 — Enable Auto Scaling

- Create Launch Template
- Configure Scaling Policies
- Enable Auto-Healing

---

## STEP 6 — Configure Monitoring

- Setup CloudWatch Alarms
- Configure SNS Notifications
- Enable Operational Visibility

---

## STEP 7 — Deploy Database

- Create RDS MySQL Instance
- Restrict Public Access
- Configure Security Groups

---

## STEP 8 — Automate Infrastructure

- Initialize Terraform
- Validate Terraform Files
- Deploy Infrastructure Automatically

---

# 🧪 Failure Simulation Testing

## 🔥 EC2 Failure Testing

Validated automatic instance replacement during instance termination.

---

## 📈 High CPU Load Testing

Validated automatic scaling during CPU spikes using stress testing.

---

## 🌐 Health Check Failure Testing

Validated traffic rerouting during unhealthy instance scenarios.

---

## 📧 Alert Notification Testing

Validated operational notifications using SNS email alerts.

---

# 📸 Project Screenshots

| Screenshot | Description |
|---|---|
| architecture.png | Complete AWS Architecture |
| vpc.png | VPC Infrastructure |
| alb.png | Load Balancer Setup |
| autoscaling.png | Auto Scaling Configuration |
| cloudwatch.png | Monitoring Dashboard |
| sns-alert.png | Email Alert Notification |
| ec2-termination.png | Failure Simulation |
| final-output.png | Final Web Application |

---

# ⚙️ Terraform Commands

## Initialize Terraform

```bash
terraform init
```

---

## Validate Configuration

```bash
terraform validate
```

---

## Preview Infrastructure

```bash
terraform plan
```

---

## Deploy Infrastructure

```bash
terraform apply
```

---

# 📊 Production-Level Features Demonstrated

✅ High Availability  
✅ Fault Tolerance  
✅ Auto-Healing Infrastructure  
✅ Dynamic Scaling  
✅ Monitoring & Logging  
✅ Infrastructure Automation  
✅ Secure Architecture  
✅ Multi-Tier Deployment  

---

# 🚀 Future Improvements

## DevOps Enhancements

- Jenkins CI/CD Pipeline
- GitHub Actions
- Docker Containerization
- Kubernetes (EKS)

---

## Security Enhancements

- AWS WAF
- HTTPS using ACM
- Secrets Manager
- IAM Least Privilege Policies

---

## Scalability Enhancements

- CloudFront CDN
- Multi-Region Deployment
- Route 53 Failover
- Redis Caching

---

# 🧠 Key Learning Outcomes

Through this project, the following skills were demonstrated:

- AWS Cloud Architecture
- DevOps Automation
- Infrastructure as Code
- Monitoring & Alerting
- Linux Administration
- Networking & Security
- High Availability Design
- Failure Recovery Mechanisms

---

# 👨‍💻 Author

# Nitesh Vishwakarma

### Cloud & DevOps Enthusiast

- AWS Cloud
- Terraform
- Linux
- DevOps
- Infrastructure Automation

---

# ⭐ If you found this project useful, consider giving it a star!

