# IAM Security Instructions

## <concepts>
1.  **Authentication (AuthN)**: Verifying *who* you are (e.g., Password, MFA).
2.  **Authorization (AuthZ)**: Verifying *what* you can do (e.g., Read, Write).
3.  **RBAC (Role-Based Access Control)**: Assigning permissions to roles, and roles to users.
4.  **ABAC (Attribute-Based Access Control)**: Assigning permissions based on attributes (e.g., Time of day, Location).
5.  **Least Privilege**: Granting only the minimum permissions necessary to perform a task.
6.  **Zero Trust**: Never trust, always verify. Assume the network is hostile.
</concepts>

## <best_practices>
1.  **MFA Everywhere**: Enforce Multi-Factor Authentication for all human users and sensitive operations.
2.  **Short-Lived Credentials**: Use short-lived tokens (e.g., OIDC) instead of long-lived static keys whenever possible.
3.  **Centralized Identity**: Use a centralized Identity Provider (IdP) like Okta or Auth0 instead of managing users in each application.
4.  **Audit Logging**: Log all authentication and authorization events for security monitoring.
5.  **Secure Hashing**: Use strong, slow hashing algorithms (Argon2, bcrypt) for password storage.
</best_practices>
