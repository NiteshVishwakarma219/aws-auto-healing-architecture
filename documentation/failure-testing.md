# 🧪 Failure Testing & Auto-Healing Validation
## AWS Production-Ready Web Application

---

# 📌 Objective

The purpose of this testing phase is to validate:

- High Availability
- Auto-Healing
- Dynamic Scaling
- Fault Tolerance
- Monitoring & Alerting
- Infrastructure Reliability

---

# 🏗️ Infrastructure Under Test

| Component | Purpose |
|---|---|
| EC2 | Application Hosting |
| ALB | Traffic Distribution |
| Auto Scaling Group | Automatic Recovery |
| CloudWatch | Monitoring |
| SNS | Notifications |
| RDS | Database |
| VPC | Network Isolation |

---

# 🔥 TEST 1 — EC2 Instance Failure Test

## Objective

Validate automatic recovery when an EC2 instance fails.

---

# Test Procedure

## Step 1

Navigate to:

```bash
EC2 → Instances
```

---

## Step 2

Select one running EC2 instance.

---

## Step 3

Terminate instance:

```bash
Instance State → Terminate
```

---

# Expected Result

| Validation | Expected |
|---|---|
| Instance terminated | ✅ |
| ASG detects unhealthy state | ✅ |
| New instance launched automatically | ✅ |
| Load balancer reroutes traffic | ✅ |
| Downtime minimal | ✅ |

---

# Result

Auto Scaling Group successfully launched a replacement EC2 instance automatically after failure detection.

---

# 📸 Evidence Collection

```bash
screenshots/ec2-termination.png
screenshots/new-instance-created.png
```

---

# 📈 TEST 2 — CPU Stress Scaling Test

## Objective

Validate automatic scaling under high CPU load.

---

# Install Stress Tool

```bash
sudo amazon-linux-extras install epel -y
sudo yum install stress -y
```

---

# Generate CPU Load

```bash
stress --cpu 2 --timeout 300
```

---

# Expected Result

| Validation | Expected |
|---|---|
| CPU exceeds threshold | ✅ |
| CloudWatch alarm triggered | ✅ |
| New EC2 launched | ✅ |
| SNS email received | ✅ |

---

# Result

CloudWatch detected high CPU usage and Auto Scaling Group successfully launched additional EC2 capacity.

---

# 📸 Evidence Collection

```bash
screenshots/high-cpu-scaleout.png
screenshots/cloudwatch-alarm.png
screenshots/sns-alert.png
```

---

# 🌐 TEST 3 — Load Balancer Health Check Test

## Objective

Validate Application Load Balancer health monitoring.

---

# Test Procedure

Stop Apache service:

```bash
sudo systemctl stop httpd
```

---

# Expected Result

| Validation | Expected |
|---|---|
| Health check failure detected | ✅ |
| Target marked unhealthy | ✅ |
| Traffic redirected to healthy targets | ✅ |

---

# Restart Apache

```bash
sudo systemctl start httpd
```

---

# Result

ALB successfully removed unhealthy instance from traffic routing until service recovered.

---

# 🗄️ TEST 4 — Database Security Validation

## Objective

Ensure database is protected inside private network.

---

# Validation Checklist

| Validation | Expected |
|---|---|
| RDS in private subnet | ✅ |
| Public access disabled | ✅ |
| Accessible only from EC2 | ✅ |
| Security group restricted | ✅ |

---

# Result

Database remained inaccessible from public internet while maintaining secure internal connectivity.

---

# ☁️ TEST 5 — Terraform Infrastructure Validation

## Objective

Validate Infrastructure as Code deployment reliability.

---

# Commands Executed

```bash
terraform validate
terraform plan
terraform apply
```

---

# Expected Result

| Validation | Expected |
|---|---|
| No syntax errors | ✅ |
| Infrastructure deployed successfully | ✅ |
| Resources provisioned correctly | ✅ |

---

# Result

Terraform successfully automated infrastructure provisioning with repeatable deployment capability.

---

# 📊 TEST 6 — CloudWatch Monitoring Validation

## Objective

Verify infrastructure monitoring visibility.

---

# Metrics Verified

- CPU Utilization
- Network Traffic
- ALB Request Count
- Instance Health
- Disk Activity

---

# Result

CloudWatch successfully collected infrastructure metrics and generated alarms during failure simulations.

---

# 📧 TEST 7 — SNS Alert Notification Test

## Objective

Validate real-time operational alerts.

---

# Procedure

Trigger CloudWatch alarm manually.

---

# Expected Result

```bash
SNS email notification received successfully
```

---

# Result

SNS delivered real-time operational alerts successfully through email notifications.

---

# 📸 Recommended Screenshots

| Screenshot | Filename |
|---|---|
| EC2 Failure | ec2-termination.png |
| New EC2 Launch | new-instance-created.png |
| CPU Spike | high-cpu-scaleout.png |
| CloudWatch Alarm | cloudwatch-alarm.png |
| SNS Alert | sns-alert.png |
| Healthy Targets | healthy-targets.png |
| Terraform Apply | terraform-apply.png |

---

# 🧠 Root Cause Analysis Summary

| Failure Scenario | Root Cause | Recovery Action |
|---|---|---|
| EC2 Failure | Manual termination | ASG launched replacement |
| CPU Spike | Stress testing | Scale-out triggered |
| Health Check Failure | Apache stopped | Traffic rerouted |
| Monitoring Alert | CPU threshold exceeded | SNS notification sent |

---

# ✅ Final Outcome

The infrastructure successfully demonstrated:

- Automatic Recovery
- Dynamic Scaling
- Production-Level Availability
- Monitoring Visibility
- Fault Tolerance
- Secure Architecture

---

# 🚀 Future Improvements

- Docker Integration
- Kubernetes (EKS)
- Jenkins CI/CD
- GitHub Actions
- Blue/Green Deployment
- Multi-Region Failover
- AWS WAF Integration
- Prometheus & Grafana

---

# 👨‍💻 Author

Nitesh Vishwakarma

Cloud & DevOps Enthusiast