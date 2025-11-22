# Skill: Dependency Management

## Description

The practice of identifying, resolving, and maintaining third-party code libraries to ensure stability, security, and compatibility.

## Triggers

* **Keywords**: "npm", "pip", "maven", "gradle", "dependency", "package", "version upgrade", "lock file", "vulnerability", "cve", "sbom"
* **Context**: Adding new libraries, updating existing ones, fixing security vulnerabilities, auditing licenses.

## Core Knowledge

### Concepts

* **Semantic Versioning (SemVer)**: A versioning scheme (`MAJOR.MINOR.PATCH`) conveying meaning about the underlying changes.
* **Transitive Dependency**: A dependency of a dependency.
* **Lock File**: A file (`package-lock.json`, `poetry.lock`) that records the exact versions of the dependency tree to ensure reproducible builds.
* **Diamond Dependency**: When two dependencies require different versions of the same shared library.
* **SBOM**: (Software Bill of Materials) A comprehensive list of all components in the software.

### Principles

* **Minimalism**: Avoid adding heavy dependencies for simple utility functions (e.g., don't import `lodash` for `Array.map`).
* **Pinning**: Always pin dependencies to specific versions (or tight ranges) in applications to prevent "it works on my machine" issues.
* **Regular Audits**: Frequently check for known vulnerabilities (CVEs).
* **License Compliance**: Ensure all dependencies have licenses compatible with your project's license.

## Actionable Affordances

### Tool Affordances

#### Audit Dependencies

Wrapper script to run the appropriate audit tool based on the project type.

```bash
#!/bin/bash
# audit-deps.sh
# Usage: ./audit-deps.sh

if [ -f "package-lock.json" ]; then
  echo "Detected Node.js project. Running npm audit..."
  npm audit
elif [ -f "yarn.lock" ]; then
  echo "Detected Yarn project. Running yarn audit..."
  yarn audit
elif [ -f "poetry.lock" ]; then
  echo "Detected Python (Poetry) project. Running poetry check..."
  poetry check
elif [ -f "pom.xml" ]; then
  echo "Detected Java (Maven) project."
  mvn dependency:analyze
else
  echo "No supported lock file found."
  exit 1
fi
```

### Reference Implementation

#### Secure `package.json` Configuration

Demonstrates strict versioning and script hooks.

```json
{
  "name": "secure-app",
  "version": "1.0.0",
  "scripts": {
    "preinstall": "npx only-allow npm",
    "audit": "npm audit --audit-level=high"
  },
  "dependencies": {
    "express": "4.18.2", 
    "helmet": "7.1.0"
  },
  "devDependencies": {
    "eslint": "8.56.0"
  },
  "engines": {
    "node": ">=18.0.0"
  }
}
```

### Libraries & Tools

* **Automation**: Renovate, Dependabot.
* **Auditing**: `npm audit`, `pip-audit`, OWASP Dependency-Check, Snyk.
* **License Checking**: FOSSA, License-Checker.

## Checklist

* [ ] **Lock File**: Is the lock file committed to git?
* [ ] **Unused Deps**: Have unused dependencies been removed (`npm prune`)?
* [ ] **Dev vs Prod**: Are build tools correctly categorized as `devDependencies`?
* [ ] **Vulnerabilities**: Are there any critical CVEs unresolved?
* [ ] **Licenses**: Are we using any GPL libraries in a closed-source project?
