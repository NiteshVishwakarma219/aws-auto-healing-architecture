# 🛠️ Troubleshooting Guide
## AWS Auto-Healing Scalable Web Application

---

# 📌 Common Issues and Solutions

This document contains common deployment, networking, scaling, monitoring, and infrastructure issues encountered during the project deployment.

---

# 🌐 ISSUE 1 — Website Not Accessible

## Symptoms

- Browser timeout
- ALB DNS not loading
- EC2 public IP inaccessible
- Website shows connection refused

---

## Possible Causes

- Apache service not running
- Incorrect security group rules
- Instance failed health checks
- ALB target group unhealthy

---

## Solution

Check Apache service:

```bash
sudo systemctl status httpd
```

Start Apache:

```bash
sudo systemctl start httpd
```

Enable Apache on boot:

```bash
sudo systemctl enable httpd
```

Verify website files:

```bash
ls /var/www/html/
```

---

# 🔐 ISSUE 2 — Security Group Blocking Traffic

## Symptoms

- Unable to access website
- SSH connection timeout
- Load balancer unhealthy

---

## Solution

Verify ALB Security Group:

```bash
HTTP 80 → Anywhere
```

Verify EC2 Security Group:

```bash
HTTP 80 → ALB Security Group
SSH 22 → My IP
```

Verify RDS Security Group:

```bash
MYSQL 3306 → EC2 Security Group
```

---

# ⚖️ ISSUE 3 — Load Balancer Health Check Failed

## Symptoms

- Targets marked unhealthy
- ALB returns 503 error
- Traffic not routed properly

---

## Solution

Verify health check path:

```bash
/
```

Restart Apache:

```bash
sudo systemctl restart httpd
```

Verify webpage:

```bash
curl localhost
```

Check target group health:

```bash
EC2 → Target Groups → Targets
```

---

# 📈 ISSUE 4 — Auto Scaling Not Working

## Symptoms

- New instances not launching
- CPU increases but scaling does not happen

---

## Possible Causes

- CloudWatch alarm missing
- Scaling policy not attached
- Wrong threshold configured

---

## Solution

Verify scaling policy attached to ASG.

Check CloudWatch metrics:

```bash
CPUUtilization
```

Lower threshold for testing:

```bash
70% → 30%
```

---

# 🔥 ISSUE 5 — Auto-Healing Not Triggering

## Symptoms

- Terminated instance not replaced
- Desired capacity mismatch

---

## Solution

Enable:

```bash
ELB Health Checks
```

inside Auto Scaling Group settings.

Verify ASG configuration:

| Setting | Value |
|---|---|
| Desired Capacity | 2 |
| Minimum Capacity | 2 |

---

# 🗄️ ISSUE 6 — Unable to Connect to RDS

## Symptoms

- Database connection timeout
- MySQL connection refused

---

## Solution Checklist

| Check | Status |
|---|---|
| RDS running | ✅ |
| RDS in private subnet | ✅ |
| Public access disabled | ✅ |
| Security group configured | ✅ |
| Correct DB endpoint used | ✅ |

---

# ☁️ ISSUE 7 — Terraform Errors

## Common Error

```bash
Error: Provider configuration not present
```

---

## Solution

Initialize Terraform:

```bash
terraform init
```

Validate configuration:

```bash
terraform validate
```

Preview infrastructure changes:

```bash
terraform plan
```

Apply configuration:

```bash
terraform apply
```

---

# 📧 ISSUE 8 — SNS Email Notifications Not Received

## Symptoms

- No email alerts
- CloudWatch alarm triggered but email missing

---

## Solution

Verify:

- Email subscription confirmed
- Correct email address used
- Spam folder checked

Recreate SNS subscription if required.

---

# 📊 ISSUE 9 — CloudWatch Alarm Not Triggering

## Symptoms

- CPU high but no alarm generated

---

## Solution

Verify:

- Correct metric selected
- Proper threshold configured
- EC2 generating load

Generate CPU stress manually:

```bash
stress --cpu 2 --timeout 300
```

---

# 🌍 ISSUE 10 — NAT Gateway Internet Issue

## Symptoms

- Private instances cannot download packages
- Yum update fails

---

## Solution

Verify NAT Gateway exists inside Public Subnet.

Verify route table:

```bash
0.0.0.0/0 → NAT Gateway
```

Ensure Elastic IP attached to NAT Gateway.

---

# 🧪 Diagnostic Commands

## Check Apache Status

```bash
systemctl status httpd
```

---

## Check Open Ports

```bash
netstat -tulnp
```

---

## Check Running Processes

```bash
top
```

---

## Check Disk Usage

```bash
df -h
```

---

## View Apache Logs

```bash
sudo tail -f /var/log/httpd/error_log
```

---

## Check EC2 Metadata

```bash
curl http://169.254.169.254/latest/meta-data/
```

---

# 📘 Best Practices

- Use least privilege IAM policies
- Enable monitoring on all services
- Keep RDS inside private subnets
- Regularly test failover scenarios
- Use Auto Scaling health checks
- Enable CloudWatch logging

---

# ✅ Validation Checklist

| Validation | Status |
|---|---|
| Website Accessible | ✅ |
| ALB Working | ✅ |
| Auto Scaling Active | ✅ |
| Auto-Healing Functional | ✅ |
| CloudWatch Monitoring | ✅ |
| SNS Alerts Working | ✅ |
| Terraform Successful | ✅ |

---

# 📸 Recommended Screenshots

| Screenshot | Filename |
|---|---|
| ALB Health Check | alb-health.png |
| Auto Scaling Group | autoscaling.png |
| CloudWatch Alarm | cloudwatch-alarm.png |
| SNS Email Alert | sns-alert.png |
| Terraform Apply | terraform-apply.png |
| EC2 Running | ec2-running.png |

---

# 👨‍💻 Author

Nitesh Vishwakarma

Cloud & DevOps Enthusiast