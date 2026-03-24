# Project 01 — S3 Static Website with Terraform

![AWS](https://img.shields.io/badge/AWS-S3-orange?logo=amazonaws)
![Terraform](https://img.shields.io/badge/IaC-Terraform-7B42BC?logo=terraform)
![Status](https://img.shields.io/badge/Status-Live%20Demo-brightgreen)

## Overview

Deploys a fully hosted static website to AWS S3 using Terraform. No servers, no maintenance — pure infrastructure as code. One command provisions the bucket, configures public access, enables static hosting, and uploads the HTML file.

## Architecture

```

Browser → S3 Bucket (Static Website Hosting) → index.html
```

Terraform provisions:

- S3 bucket with static website hosting enabled
- Public access block settings
- Bucket policy (public read)
- `index.html` uploaded as an S3 object

## AWS Services Used

| Service | Purpose |
|---------|---------|
| Amazon S3 | Static file hosting |

## Prerequisites

- [Terraform](https://developer.hashicorp.com/terraform/downloads) >= 1.3.0
- [AWS CLI](https://aws.amazon.com/cli/) configured (`aws configure`)
- AWS account (free tier eligible)

## Repo Structure

```

project-01-s3-static-website/
├── main.tf          # S3 bucket, policy, website config, file upload
├── variables.tf     # Region, bucket name, tags
├── outputs.tf       # Live website URL
├── provider.tf      # AWS provider + Terraform version
├── website/
│   └── index.html   # Static site content
└── README.md
```

## Quick Start

```bash
# 1. Clone the repo
git clone https://github.com/YOUR_USERNAME/project-01-s3-static-website
cd project-01-s3-static-website

# 2. Update bucket name in variables.tf (must be globally unique)

# 3. Deploy
terraform init
terraform plan
terraform apply -auto-approve

# 4. Open the URL printed in the output
```

## Outputs

| Output | Description |
|--------|-------------|
| `website_url` | Live S3 website endpoint URL |
| `bucket_name` | Name of the created S3 bucket |

## Cost

| Resource | Monthly Cost |
|----------|-------------|
| S3 storage (< 1MB) | ~$0.00 |
| S3 requests | < $0.01 |
| **Total** | **Free tier / near-zero** |

## Cleanup

```bash
terraform destroy -auto-approve
```

## What This Demonstrates

- Infrastructure as Code (IaC) with Terraform
- AWS S3 static website hosting
- Bucket policy and public access configuration
- Automated file upload via `aws_s3_object`
- Zero manual console interaction

---

*Built as part of a Cloud Engineer portfolio — provisioned 100% with Terraform.*