# Application Security Instructions

## <concepts>
1.  **OWASP Top 10**: The standard awareness document for developers and web application security.
2.  **Input Validation**: Ensure all input is syntactically correct and safe before processing.
3.  **Output Encoding**: Convert data into a safe form where the interpreter (browser, DB) does not execute it as code.
4.  **Principle of Least Privilege**: Granting only the minimum permissions necessary to perform a task.
5.  **Defense in Depth**: Layering security controls so that if one fails, others are in place.
6.  **Shift Left**: Integrating security testing early in the development process (e.g., in the IDE or CI/CD).
</concepts>

## <best_practices>
1.  **Parameterization**: Always use parameterized queries to prevent SQL Injection.
2.  **Secure Headers**: Use security headers (CSP, HSTS, X-Frame-Options) to protect against common attacks.
3.  **Dependency Management**: Regularly scan and update dependencies to patch known vulnerabilities.
4.  **Secrets Management**: Never commit secrets to version control; use environment variables or secret managers.
5.  **Authentication**: Use established authentication libraries (e.g., Passport, Spring Security) instead of rolling your own.
</best_practices>
