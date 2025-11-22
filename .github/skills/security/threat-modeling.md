# Skill: Threat Modeling

## Description

The ability to systematically identify and mitigate potential security threats in a system design or implementation.

## Triggers

* **Keywords**: "security", "threat", "risk", "vulnerability", "attack", "hack", "auth", "encryption", "stride"
* **Context**: Architecture reviews, API definition changes, authentication logic updates, design phase.

## Core Knowledge

### Concepts

* **STRIDE**: A mnemonic for security threats (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege).
* **Trust Boundary**: A location where program data or execution changes its level of "trust" (e.g., between the internet and a web server).
* **Attack Surface**: The sum of the different points (the "attack vectors") where an unauthorized user (the "attacker") can try to enter data to or extract data from an environment.
* **Defense in Depth**: A layered security approach where multiple controls are used to protect the system.

### Principles

* **Secure by Design**: Security is a primary concern during the design phase, not an afterthought.
* **Least Privilege**: Every module (such as a process, a user, or a program) must be able to access only the information and resources that are necessary for its legitimate purpose.
* **Fail Secure**: When a system fails, it should default to a secure state (e.g., denying access).

## Actionable Affordances

### Tool Affordances

#### Scaffold Threat Model

Creates a standard Threat Model document.

```bash
#!/bin/bash
# scaffold-threat-model.sh
# Usage: ./scaffold-threat-model.sh <ComponentName>

COMPONENT_NAME=$1

if [ -z "$COMPONENT_NAME" ]; then
  echo "Usage: $0 <ComponentName>"
  exit 1
fi

FILENAME="threat-model-$COMPONENT_NAME.md"

cat <<EOF > "$FILENAME"
# Threat Model: $COMPONENT_NAME

## 1. System Description
*   **Description**: [What does it do?]
*   **Data Sensitivity**: [Public/Internal/Confidential]

## 2. Data Flow Diagram (Mermaid)
\`\`\`mermaid
graph LR
    User -->|HTTPS| LoadBalancer
    LoadBalancer -->|HTTP| WebServer
    WebServer -->|SQL| Database
\`\`\`

## 3. STRIDE Analysis

| Threat Category | Description | Mitigation | Status |
| :--- | :--- | :--- | :--- |
| **S**poofing | Attacker impersonates admin | MFA, Strong Auth | Open |
| **T**ampering | SQL Injection in search | Parameterized Queries | Mitigated |
| **R**epudiation | User denies deleting data | Audit Logs | Open |
| **I**nformation Disclosure | API leaks PII | Encryption, Masking | Mitigated |
| **D**enial of Service | API flooding | Rate Limiting | Open |
| **E**levation of Privilege | IDOR in profile edit | Access Control Checks | Open |

## 4. Security Requirements
1.  [Requirement 1]
2.  [Requirement 2]
EOF

echo "Created Threat Model template: $FILENAME"
```

### Reference Implementation

#### STRIDE Analysis Example (Login Flow)

| Category | Threat | Mitigation |
| :--- | :--- | :--- |
| **Spoofing** | Attacker guesses user's password. | Implement Account Lockout, Enforce Strong Passwords, MFA. |
| **Tampering** | Attacker modifies the JWT token. | Sign tokens with a strong secret (HS256/RS256). Verify signature on every request. |
| **Repudiation** | User claims they didn't log in. | Log IP address, User Agent, and Timestamp of login events. |
| **Info Disclosure** | Error messages reveal valid usernames. | Return generic error messages ("Invalid username or password"). |
| **DoS** | Attacker floods login endpoint. | Implement Rate Limiting (e.g., 5 attempts per minute). |
| **Elevation** | Admin login bypass. | Ensure admin routes are protected by specific role checks, not just authentication. |

### Libraries & Tools

* **Frameworks**: OWASP ASVS (Application Security Verification Standard).
* **Tools**: OWASP Threat Dragon, Microsoft Threat Modeling Tool.
* **Scanners**: OWASP ZAP, Burp Suite.

## Checklist

* [ ] **Trust Boundaries**: Are boundaries between trusted and untrusted zones clearly defined?
* [ ] **Data Flows**: Are all data flows across boundaries identified?
* [ ] **Secrets**: Are secrets (keys, passwords) stored securely (Vault, HSM)?
* [ ] **Input Validation**: Is all input from untrusted sources validated?
* [ ] **Output Encoding**: Is output encoded to prevent injection (XSS)?
* [ ] **Logging**: Are security-critical events logged (without sensitive data)?
