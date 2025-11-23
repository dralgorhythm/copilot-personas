# Dependency Management Instructions
> **Apply To**: `package.json`, `pom.xml`, `build.gradle`, `requirements.txt`, `pyproject.toml`, `Cargo.toml`, `go.mod`

Guidelines for identifying, resolving, and maintaining third-party code libraries to ensure stability, security, and compatibility.

## <best_practices>
*   **Minimalism**: Avoid adding heavy dependencies for simple utility functions (e.g., don't import `lodash` for `Array.map`).
*   **Pinning**: Always pin dependencies to specific versions (or tight ranges) in applications to prevent "it works on my machine" issues.
*   **Regular Audits**: Frequently check for known vulnerabilities (CVEs).
*   **License Compliance**: Ensure all dependencies have licenses compatible with your project's license.
</best_practices>

## <concepts>
*   **Semantic Versioning (SemVer)**: A versioning scheme (`MAJOR.MINOR.PATCH`) conveying meaning about the underlying changes.
*   **Transitive Dependency**: A dependency of a dependency.
*   **Lock File**: A file (`package-lock.json`, `poetry.lock`) that records the exact versions of the dependency tree to ensure reproducible builds.
*   **Diamond Dependency**: When two dependencies require different versions of the same shared library.
*   **SBOM**: (Software Bill of Materials) A comprehensive list of all components in the software.
</concepts>

## <tooling>
*   **Automation**: Renovate, Dependabot.
*   **Auditing**: `npm audit`, `pip-audit`, OWASP Dependency-Check, Snyk.
*   **License Checking**: FOSSA, License-Checker.
</tooling>
