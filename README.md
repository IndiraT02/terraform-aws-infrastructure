# Project 2 — Terraform AWS Infrastructure (IaC)

## What is This Project?
This project provisions a complete AWS infrastructure 
using **Terraform (Infrastructure as Code)**.
Instead of clicking in AWS Console, everything is 
created automatically by running one command.

---
---

## Resources Created by Terraform

| Resource | Name | Details |
|---|---|---|
| VPC | indira-tf-vpc | CIDR: 10.1.0.0/16 |
| Public Subnet | indira-tf-public-subnet | 10.1.1.0/24 — us-east-1a |
| Private Subnet | indira-tf-private-subnet | 10.1.2.0/24 — us-east-1b |
| Internet Gateway | indira-tf-igw | Attached to VPC |
| Route Table | indira-tf-public-rt | Routes internet traffic via IGW |
| Security Group | indira-tf-web-sg | Allows HTTP port 80, SSH port 22 |
| S3 Bucket | indira-tf-app-bucket | Versioning enabled |

---
---

## How to Use This Project

### Prerequisites
- Terraform installed (v1.0 or higher)
- AWS CLI installed and configured
- AWS account with Free Tier access

### Step 1 — Clone the Repository
```bash
git clone https://github.com/IndiraT02/terraform-aws-infrastructure.git
cd terraform-aws-infrastructure
```

### Step 2 — Initialize Terraform
```bash
terraform init
```
Downloads the AWS provider plugin.

### Step 3 — Preview Infrastructure
```bash
terraform plan
```
Shows exactly what will be created — no changes made yet.

### Step 4 — Create Infrastructure
```bash
terraform apply
```
Type `yes` when prompted.
All 8 resources are created in ~30 seconds.

### Step 5 — View Outputs
After apply completes, you'll see:

Outputs:
vpc_id             = "vpc-xxxxxxxxx"
public_subnet_id   = "subnet-xxxxxxxxx"
private_subnet_id  = "subnet-xxxxxxxxx"
internet_gateway_id = "igw-xxxxxxxxx"
security_group_id  = "sg-xxxxxxxxx"
s3_bucket_name     = "indira-tf-app-bucket"

### Step 6 — Destroy Infrastructure
```bash
terraform destroy
```
Type `yes` to delete all resources cleanly.

---

## Why Terraform? (Key Concept)

| Manual AWS Console | Terraform (IaC) |
|---|---|
| Click through menus | Write code once |
| Takes 20-30 minutes | Runs in 30 seconds |
| Easy to make mistakes | Consistent every time |
| Hard to reproduce | Run anywhere, anytime |
| No record of what was done | Full history in Git |
| Delete manually one by one | `terraform destroy` — done |

---

## Key Concepts Demonstrated

- **Infrastructure as Code (IaC)** — infrastructure defined in `.tf` files
- **Variables** — reusable values across all resources
- **Outputs** — display important values after deployment
- **Resource dependencies** — Terraform auto-detects order
  (e.g. IGW needs VPC to exist first)
- **Tags** — all resources tagged with Name, Environment, ManagedBy
- **State management** — Terraform tracks what exists on AWS
- **.gitignore** — state files excluded to protect sensitive data

---

## What I Learned
- How to write HCL (HashiCorp Configuration Language)
- How Terraform providers connect to AWS
- Resource referencing — `aws_vpc.main.id` passes VPC ID 
  automatically to subnets
- The plan → apply → destroy workflow
- Why IaC is preferred over manual setup in real cloud jobs

---

## Certifications & Skills
- AWS Certified Cloud Practitioner (Mar 2026)
- Terraform — Currently Learning

## Author
**Indira Tiruveedhula**
- LinkedIn: linkedin.com/in/indira-tiruveedhula-b01000379
- Email: indiratiruveedhula02@gmail.com
- GitHub: github.com/IndiraT02