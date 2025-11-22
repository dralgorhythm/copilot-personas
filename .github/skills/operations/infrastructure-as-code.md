# Skill: Infrastructure as Code (IaC)

## Description

The ability to design, deploy, and manage infrastructure using code, ensuring reproducibility, scalability, and security.

## Triggers

* **Keywords**: "aws", "azure", "gcp", "terraform", "cloudformation", "kubernetes", "docker", "deploy", "iac", "provision"
* **Context**: Provisioning resources, setting up CI/CD pipelines, containerizing applications, managing cloud environments.

## Core Knowledge

### Concepts

* **Immutable Infrastructure**: Servers are never modified after they are deployed. If something needs to be updated, replaced, or fixed, new servers are built from a common image with the appropriate changes are provisioned to replace the old ones.
* **Idempotency**: The property that applying the same configuration multiple times results in the same state.
* **Drift**: The difference between the desired state (defined in code) and the actual state of the infrastructure.
* **GitOps**: A set of practices to manage infrastructure and application configurations using Git, an open-source version control system.

### Principles

* **Declarative over Imperative**: Define *what* the infrastructure should look like, not *how* to build it step-by-step.
* **Cattle, not Pets**: Treat servers as disposable resources that can be replaced at any time, rather than unique systems that must be nursed back to health.
* **Least Privilege**: Grant only the permissions necessary to perform a task.
* **State Management**: Store state files remotely and securely (encrypted, locked) to enable collaboration and prevent corruption.

## Actionable Affordances

### Tool Affordances

#### Scaffold Terraform Module

Creates a standard Terraform module structure.

```bash
#!/bin/bash
# scaffold-terraform.sh
# Usage: ./scaffold-terraform.sh <ModuleName>

MODULE_NAME=$1

if [ -z "$MODULE_NAME" ]; then
  echo "Usage: $0 <ModuleName>"
  exit 1
fi

mkdir -p "terraform/$MODULE_NAME"

# Create Standard Files
touch "terraform/$MODULE_NAME/main.tf"
touch "terraform/$MODULE_NAME/variables.tf"
touch "terraform/$MODULE_NAME/outputs.tf"
touch "terraform/$MODULE_NAME/versions.tf"
touch "terraform/$MODULE_NAME/README.md"

# Populate versions.tf
cat <<EOF > "terraform/$MODULE_NAME/versions.tf"
terraform {
  required_version = ">= 1.0"
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}
EOF

echo "Scaffolding complete for Terraform module: $MODULE_NAME"
```

### Reference Implementation

#### Secure S3 Bucket (Terraform)

Demonstrates encryption, versioning, and blocking public access.

```hcl
# main.tf

resource "aws_s3_bucket" "secure_bucket" {
  bucket = var.bucket_name

  # Force destroy for dev environments only
  force_destroy = var.environment == "dev"

  tags = {
    Name        = var.bucket_name
    Environment = var.environment
    ManagedBy   = "Terraform"
  }
}

# 1. Enable Versioning (Recovery)
resource "aws_s3_bucket_versioning" "versioning" {
  bucket = aws_s3_bucket.secure_bucket.id
  versioning_configuration {
    status = "Enabled"
  }
}

# 2. Enable Server-Side Encryption (Security)
resource "aws_s3_bucket_server_side_encryption_configuration" "encryption" {
  bucket = aws_s3_bucket.secure_bucket.id

  rule {
    apply_server_side_encryption_by_default {
      sse_algorithm = "AES256"
    }
  }
}

# 3. Block Public Access (Security)
resource "aws_s3_bucket_public_access_block" "public_access" {
  bucket = aws_s3_bucket.secure_bucket.id

  block_public_acls       = true
  block_public_policy     = true
  ignore_public_acls      = true
  restrict_public_buckets = true
}
```

### Libraries

* **Provisioning**: Terraform, OpenTofu, Pulumi, AWS CDK, Azure Bicep.
* **Kubernetes**: Helm, Kustomize, ArgoCD (GitOps).
* **Validation**: TFLint, Checkov, tfsec.

## Checklist

* [ ] **State**: Is remote state configured with locking (e.g., S3 + DynamoDB)?
* [ ] **Secrets**: Are secrets managed externally (e.g., AWS Secrets Manager, Vault) and not committed to Git?
* [ ] **Tagging**: Are resources tagged for cost allocation and ownership?
* [ ] **IAM**: Are policies scoped to least privilege (no `*` actions)?
* [ ] **Backup**: Is backup/recovery configured for stateful resources?
