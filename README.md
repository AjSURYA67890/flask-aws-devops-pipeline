# flask-aws-devops-pipeline
Automated deployment of a Python Flask application using a CI/CD pipeline with Jenkins and Terraform on AWS. Jenkins is hosted on an EC2 instance in eu-west-1, and the Flask application is deployed to eu-central-1 with a managed MySQL RDS database, infrastructure as code (IaC), and multi-region AWS deployment.

# Multi-Region Flask CI/CD on AWS with Jenkins, Terraform, and RDS

This project demonstrates a complete CI/CD pipeline for deploying a Python Flask application to AWS using **Jenkins**, **Terraform**, and **MySQL RDS**, with a focus on DevOps best practices and infrastructure automation.

## 🌍 Architecture Overview

- **Jenkins** runs on an EC2 instance in the `eu-west-1` region and handles CI/CD automation.
- The **Flask application** is deployed to EC2 instances in the `eu-central-1` region.
- A **MySQL RDS** database is provisioned in `eu-central-1` and connected to the Flask app.
- **Terraform** is used to provision all AWS infrastructure as code.

## ⚙️ Technologies Used

- **Python** (Flask)
- **Jenkins** (CI/CD server)
- **Terraform** (Infrastructure as Code)
- **AWS** (EC2, RDS, IAM, VPC)
- **GitHub** (Source control and webhook integration)
- **MySQL** (Database)

## 📦 Project Structure
├── jenkins/
│ └── Jenkinsfile # CI/CD pipeline script
├── terraform/
│ ├── jenkins-ec2/ # Terraform configs for Jenkins EC2 setup (eu-west-1)
│ └── flask-app-rds/ # Terraform configs for Flask app + RDS setup (eu-central-1)
├── flask-app/
│ ├── app.py # Flask application code
│ ├── requirements.txt
│ └── Dockerfile # Optional: containerization
├── scripts/
│ └── deploy.sh # Deployment automation script
└── README.md


## 🚀 Deployment Workflow

1. **Push code to GitHub** ➝ Triggers Jenkins via webhook
2. **Jenkins** builds, tests, and deploys using Terraform
3. **Terraform** provisions or updates:
   - EC2 instance(s) in `eu-central-1` for Flask
   - RDS MySQL database
4. Flask app connects to RDS and is made available via a public IP or Load Balancer.

## 🛡️ DevOps Practices Demonstrated

- Infrastructure as Code (IaC) with Terraform
- CI/CD automation with Jenkins
- Environment separation by region (CI server in `eu-west-1`, app in `eu-central-1`)
- Modular and reusable infrastructure code
- Secure credential handling using AWS IAM and Jenkins credentials

## 📚 Getting Started

> Prerequisites:
> - AWS CLI configured
> - Terraform installed
> - Jenkins running on EC2
> - GitHub webhook configured for Jenkins

```bash
# Clone this repository
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name

# Initialize Terraform
cd terraform/flask-app-rds
terraform init
terraform apply



