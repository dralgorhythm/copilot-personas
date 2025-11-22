# Skill: Application Security (AppSec)

## Description
Securing application code and dependencies (OWASP Top 10).

## Triggers
*   Keywords: "appsec", "owasp", "vulnerability", "xss", "injection", "sast", "dast", "sql injection", "csrf"
*   Context: Reviewing code for security flaws or designing secure features.

## Checklist
*   **Input Validation**: Validate all inputs (sanitize HTML, parameterized queries).
*   **Authentication**: Never roll your own crypto. Use standard libraries.
*   **Authorization**: Implement Principle of Least Privilege.
*   **Dependencies**: Scan for known vulnerabilities (CVEs).
*   **Secrets**: Never commit secrets to git. Use environment variables or vaults.
