# Security Instructions

## Core Principles
1.  **Least Privilege**: Grant only the permissions necessary to perform a task.
2.  **Defense in Depth**: Implement multiple layers of security controls.
3.  **Fail Securely**: Ensure that failures do not leave the system in an insecure state.
4.  **Secure Defaults**: Default configurations should be secure (e.g., "deny all" firewall rules).

## Coding Standards
*   **Input Validation**: Validate all input at the boundary. Use allow-lists, not block-lists.
*   **Output Encoding**: Encode data before rendering it to prevent XSS.
*   **Authentication**: Use established protocols (OAuth2, OIDC). Never roll your own crypto.
*   **Secrets Management**: Never hardcode secrets. Use environment variables or a secrets manager (Vault, AWS Secrets Manager).
*   **Dependency Management**: Regularly scan dependencies for known vulnerabilities (CVEs).

## Language-Agnostic Patterns
*   **SQL Injection**: Always use parameterized queries or ORMs. Never concatenate strings into SQL.
*   **Command Injection**: Avoid executing shell commands with user input. Use language-specific APIs instead.
*   **Logging**: Do not log sensitive data (PII, passwords, tokens).

## Review Checklist
- [ ] Are secrets externalized?
- [ ] Is input validated?
- [ ] Are dependencies up to date?
- [ ] Is proper error handling in place (no stack traces to users)?
