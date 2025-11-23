# Terraform Instructions
> **Apply To**: `**/*.tf`, `**/*.tfvars`

You are writing Terraform (HCL) code. Adhere to the following strict standards.

## <coding_standards>
1.  **Declarative**: Write declarative configurations. Avoid complex logic in HCL.
2.  **Modules**: Use modules for reusable infrastructure components.
3.  **Naming**: Use snake_case for resource names. Include resource type prefix (e.g., `aws_vpc`).
4.  **Variables**: Define all inputs in `variables.tf`, outputs in `outputs.tf`.
5.  **State**: Always use remote state with locking (e.g., S3 + DynamoDB, Terraform Cloud).
</coding_standards>

## <security_standards>
*   **Secrets**: Never hardcode secrets. Use variables with `sensitive = true` or external secret managers.
*   **Least Privilege**: IAM policies should grant minimum required permissions.
*   **Encryption**: Enable encryption at rest and in transit for all data stores.
*   **Public Access**: Block public access by default unless explicitly required.
</security_standards>

## <validation_protocols>
*   **Format**: Run `terraform fmt` before committing.
*   **Validate**: Run `terraform validate` to check syntax.
*   **Lint**: Use `tflint` for best practices and provider-specific rules.
*   **Security Scan**: Use `checkov` or `tfsec` to detect security issues.
*   **Plan Review**: Always review `terraform plan` output before applying.
</validation_protocols>
