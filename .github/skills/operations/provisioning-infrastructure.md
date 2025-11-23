---
name: provisioning-infrastructure
description: The ability to design, deploy, and manage infrastructure using code, following the Graduated Hosting Strategy with SST v3 (Ion).
---

# Provisioning Infrastructure

## Workflows
<!-- Checklist for complex tasks -->
- [ ] **Hosting Tier**: Which tier is this for? (Static/Cloudflare Pages, Agile/Railway, Production/AWS Fargate)
- [ ] **IaC Tool**: Is SST v3 (Ion) being used for AWS infrastructure?
- [ ] **Secrets**: Are secrets managed via Doppler and not committed?
- [ ] **Review**: Has the infrastructure plan been reviewed before deployment?
- [ ] **Tagging**: Are resources tagged with Owner, Environment, and CostCenter?
- [ ] **Backup**: Is deletion protection enabled for stateful resources (DBs, Buckets)?

## Feedback Loops
<!-- Validation steps -->
1. Write IaC code (SST v3 TypeScript or Terraform).
2. Run linter (`biome` for SST, `tflint` for Terraform).
3. Run security scan (`tfsec` for Terraform).
4. Run plan/preview (`sst deploy --stage dev` or `terraform plan`).
5. Apply to staging.
6. Verify.

## Utility Scripts
<!-- Reference executable scripts -->
- `scaffold-sst-project.sh`: Creates a standard SST v3 project structure.

```bash
#!/bin/bash
# scaffold-sst-project.sh
# Usage: ./scaffold-sst-project.sh <ProjectName>

PROJECT_NAME=$1

if [ -z "$PROJECT_NAME" ]; then
  echo "Usage: $0 <ProjectName>"
  exit 1
fi

mkdir -p "$PROJECT_NAME"
cd "$PROJECT_NAME"

# Initialize SST project
pnpm create sst@latest

# Create Doppler config reference
cat <<EOF > .env.example
# Use Doppler for secrets management
# Run: doppler run -- sst deploy
DOPPLER_TOKEN=<your-token>
EOF

echo "SST v3 project scaffolded: $PROJECT_NAME"
echo "Next steps:"
echo "1. Configure Doppler: doppler setup"
echo "2. Deploy to dev: doppler run -- sst deploy --stage dev"
```

## Reference Implementation
<!-- Code patterns -->

### Secure S3 Bucket (SST v3)

Demonstrates encryption, versioning, and blocking public access using SST.

```typescript
// sst.config.ts
import { Bucket } from "sst/constructs";

export default {
  config() {
    return {
      name: "my-app",
      region: "us-east-1",
    };
  },
  stacks(app) {
    app.stack(function Stack({ stack }) {
      // Secure S3 Bucket with SST
      const bucket = new Bucket(stack, "SecureBucket", {
        cdk: {
          bucket: {
            versioned: true,
            encryption: s3.BucketEncryption.S3_MANAGED,
            blockPublicAccess: s3.BlockPublicAccess.BLOCK_ALL,
            removalPolicy: stack.stage === "prod" 
              ? RemovalPolicy.RETAIN 
              : RemovalPolicy.DESTROY,
          },
        },
      });

      stack.addOutputs({
        BucketName: bucket.bucketName,
      });
    });
  },
};
```

### Terraform Alternative (Legacy)

For teams not yet on SST, here's the Terraform equivalent:

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

## Resources
<!-- Links to external docs or local reference files -->
- [Infrastructure as Code Instructions](../../instructions/infrastructure-as-code.instructions.md)
- [SST v3 Documentation](https://sst.dev)
- [Doppler Documentation](https://docs.doppler.com)

