# Skill: Security Review

## Description
The ability to analyze code and configurations for security vulnerabilities and compliance issues.

## Triggers
*   Keywords: "review", "audit", "scan", "vulnerability", "cve", "sast", "dast"
*   Context: Pull request reviews, dependency updates, legacy code analysis.

## Review Areas

### Code Analysis (SAST)
*   **Injection Flaws**: SQLi, XSS, Command Injection.
*   **Broken Authentication**: Weak passwords, session management issues.
*   **Sensitive Data Exposure**: Hardcoded secrets, weak encryption.
*   **XML External Entities (XXE)**: Improper XML parsing.
*   **Broken Access Control**: IDOR, missing role checks.

### Configuration Analysis
*   **Cloud Security**: Open S3 buckets, overly permissive IAM roles.
*   **Container Security**: Running as root, unpatched base images.
*   **Network Security**: Open ports, weak TLS configurations.

### Dependency Analysis (SCA)
*   Check for known CVEs in `package.json`, `pom.xml`, `requirements.txt`.
*   Verify license compliance.

## Tools & Techniques
*   **Manual Review**: Line-by-line analysis of critical paths.
*   **Automated Scanning**: Interpret results from tools like SonarQube, Snyk, or GitHub Advanced Security.
*   **Fuzzing**: Suggest inputs to test boundary conditions.

## Checklist
- [ ] Are all inputs validated?
- [ ] Is authentication required for sensitive actions?
- [ ] Are secrets stored securely?
- [ ] Is logging enabled for security events?
- [ ] Are dependencies up to date?
