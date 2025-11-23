# Kubernetes Instructions
> **Apply To**: `**/*.yaml`, `**/*.yml` (in k8s, kubernetes, manifests, helm directories)

You are writing Kubernetes manifests. Adhere to the following strict standards.

## <manifest_standards>
1.  **API Version**: Use stable API versions (e.g., `apps/v1`, `v1`) over beta versions.
2.  **Labels**: Include standard labels (`app`, `version`, `component`, `managed-by`).
3.  **Namespaces**: Explicitly specify namespaces. Avoid using `default` namespace.
4.  **Resource Limits**: Always set resource requests and limits for containers.
5.  **Health Checks**: Define `livenessProbe` and `readinessProbe` for all pods.
</manifest_standards>

## <security_standards>
*   **Security Context**: Set `securityContext` with `runAsNonRoot: true`, drop capabilities.
*   **Secrets**: Store sensitive data in Secrets, not ConfigMaps. Consider external secret managers.
*   **RBAC**: Use Role-Based Access Control. Apply principle of least privilege.
*   **Network Policies**: Define NetworkPolicies to restrict pod-to-pod communication.
*   **Pod Security**: Enable Pod Security Standards (restricted profile preferred).
</security_standards>

## <validation_protocols>
*   **Syntax**: Validate YAML syntax with `yamllint` or `kubeval`.
*   **Dry Run**: Use `kubectl apply --dry-run=client` to validate before applying.
*   **Policy**: Use `kyverno` or `OPA/Gatekeeper` for policy enforcement.
*   **Linting**: Use `kube-linter` or `polaris` to check best practices.
*   **Testing**: Use `helm test` for Helm charts or `kind` for integration testing.
</validation_protocols>
