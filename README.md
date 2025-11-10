# terraform-aws-infra

> Infrastructure as Code (IaC) using Terraform on Amazon Web Services (AWS)

Automate and manage your AWS infrastructure in a scalable, repeatable, and version-controlled way using Terraform modules and best practices.

---

## 🚀 Project Overview

This repository contains Terraform code written in HCL to **provision, configure, and manage AWS resources** for your cloud workloads. It focuses on:

* Modular architecture (reusable AWS component modules)
* Infrastructure consistency across environments
* Clear separation of environments (e.g., dev, staging, prod)
* Infrastructure versioning and collaboration

---

## 🧩 Key Features

* Modular directory structure: each major component (VPC, EC2, IAM, networking, security, etc) is defined as a reusable module
* Environment-specific configurations (e.g., variables, backend settings)
* State management using remote backends (e.g., S3 + DynamoDB locking)
* Outputs for integration with downstream pipelines or applications
* Secure handling of secrets and sensitive variables (Terraform variables, AWS Secrets Manager, etc)
* Clear documentation and examples for usage

---

## 📁 Project Structure

```
terraform-aws-infra/
│
├── /                  # Reusable Terraform modules (e.g., vpc, network, compute, iam)
│   ├── ec2/
│   ├── subnets/
└── .gitignore
```

---

## 🛠 Getting Started

### Prerequisites

* AWS account with appropriate permissions (IAM, VPC, EC2, S3, etc)
* Terraform installed (version specified in `versions.tf`)
* AWS CLI or other means to authenticate and set AWS credentials

### Setup Steps

```bash
# Clone this repository
git clone https://github.com/KAVI-DEV-ui/terraform-aws-infra.git
cd terraform-aws-infra/envs/dev

# Initialize Terraform (backend, modules)
terraform init

# Preview what will be created/changed
terraform plan -var-file="terraform.tfvars"

# Apply changes
terraform apply -var-file="terraform.tfvars"
```

### Destroy (when you want to clean up)

```bash
terraform destroy -var-file="terraform.tfvars"
```

---

## 🔧 Usage & Configuration

* Modify `terraform.tfvars` in each environment (dev, staging, prod) to adjust variables like region, size, tags, etc
* Add or update modules in `modules/` for new AWS services or components
* Use `terraform workspace select <env>` or separate folders per environment to manage multiple deployments
* Use remote backend S3 + DynamoDB table for state locking to support collaboration

---

## ✅ Best Practices Applied

* Infrastructure as Code (IaC) for improved reproducibility
* Use of modules for DRY (Don’t Repeat Yourself) and modularization
* Remote state with locking to prevent concurrent state corruption
* Meaningful naming conventions and tagging for cost allocation
* Separate configurations for environments to enable proper lifecycle management

---

## 📚 References & Resources

* Terraform documentation: [https://www.terraform.io/docs](https://www.terraform.io/docs)
* AWS Provider for Terraform: [https://registry.terraform.io/providers/hashicorp/aws/latest/docs](https://registry.terraform.io/providers/hashicorp/aws/latest/docs)
* AWS best practices for tagging, security, networking
* Module design conventions: [https://www.terraform.io/docs/language/modules/develop/index.html](https://www.terraform.io/docs/language/modules/develop/index.html)

---

## 🙋 Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/<feature-name>`
3. Make your changes (e.g., new module, variable, environment)
4. Commit your changes: `git commit -m "Add <feature-name> module"`
5. Push to the branch and open a Pull Request


---

## 🧑‍💻 Author & Maintainers

**Author**: KAVI-DEV-ui
For any issues, questions or suggestions, feel free to open GitHub issues or pull requests.
