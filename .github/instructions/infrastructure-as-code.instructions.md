# Infrastructure as Code Instructions
> **Apply To**: `**/*.tf`, `**/*.tfvars`, `**/cloudformation.yaml`, `**/Pulumi.yaml`

Guidelines for designing, deploying, and managing infrastructure using code, ensuring reproducibility, scalability, and security.

## <best_practices>
*   **Declarative over Imperative**: Define *what* the infrastructure should look like, not *how* to build it step-by-step.
*   **Cattle, not Pets**: Treat servers as disposable resources that can be replaced at any time.
*   **Least Privilege**: Grant only the permissions necessary to perform a task.
*   **State Management**: Store state files remotely and securely (encrypted, locked) to enable collaboration and prevent corruption.
</best_practices>

## <concepts>
*   **Immutable Infrastructure**: Servers are never modified after they are deployed.
*   **Idempotency**: The property that applying the same configuration multiple times results in the same state.
*   **Drift**: The difference between the desired state (defined in code) and the actual state of the infrastructure.
*   **GitOps**: A set of practices to manage infrastructure and application configurations using Git.
</concepts>
