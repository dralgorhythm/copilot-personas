# Security Review Instructions

## <concepts>
1.  **Code Analysis (SAST)**:
    *   **Injection Flaws**: SQLi, XSS, Command Injection.
    *   **Broken Authentication**: Weak passwords, session management issues.
    *   **Sensitive Data Exposure**: Hardcoded secrets, weak encryption.
    *   **XML External Entities (XXE)**: Improper XML parsing.
    *   **Broken Access Control**: IDOR, missing role checks.
2.  **Configuration Analysis**:
    *   **Cloud Security**: Open S3 buckets, overly permissive IAM roles.
    *   **Container Security**: Running as root, unpatched base images.
    *   **Network Security**: Open ports, weak TLS configurations.
3.  **Dependency Analysis (SCA)**:
    *   Check for known CVEs in `package.json`, `pom.xml`, `requirements.txt`.
    *   Verify license compliance.
</concepts>

## <best_practices>
1.  **Constructive Feedback**: Frame security findings as risks and provide actionable recommendations.
2.  **Risk-Based Prioritization**: Focus on high-severity vulnerabilities first (e.g., RCE, SQLi).
3.  **Automated First**: Use automated tools (SAST/SCA) to catch low-hanging fruit before manual review.
4.  **Context Matters**: Understand the business context and threat model of the application being reviewed.
5.  **Verify Fixes**: Always verify that the remediation actually fixes the vulnerability without introducing regressions.
</best_practices>
