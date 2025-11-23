# Infrastructure as Code Instructions
> **Apply To**: `**/*.tf`, `**/*.tfvars`, `**/sst.config.ts`, `**/Pulumi.yaml`

Guidelines for designing, deploying, and managing infrastructure using code, following the 2025 Graduated Hosting Strategy.

## <coding_standards>
1.  **IaC Tool**: Use **SST v3 (Ion)** as the standard. TypeScript-based, bridges easy local dev with robust AWS primitives.
2.  **Secrets Management**: Use **Doppler** as the unified control plane. Syncs to GitHub Actions, Railway, and AWS SSM.
3.  **Authentication**: Use **OIDC** (OpenID Connect) for AWS/Cloudflare access. No long-lived keys.
4.  **State Management**: SST manages state automatically. For raw Terraform, store state remotely and securely (encrypted, locked).
5.  **Tagging**: Tag all resources with Owner, Environment, and CostCenter for cost attribution.
</coding_standards>

## <best_practices>
*   **Declarative over Imperative**: Define *what* the infrastructure should look like, not *how* to build it step-by-step.
*   **Cattle, not Pets**: Treat servers as disposable resources that can be replaced at any time.
*   **Least Privilege**: Grant only the permissions necessary to perform a task.
*   **Immutable Infrastructure**: Servers are never modified after they are deployed.
*   **GitOps**: Manage infrastructure and application configurations using Git as the source of truth.
*   **Deletion Protection**: Enable deletion protection for stateful resources (databases, buckets).
</best_practices>

## <testing_protocols>
*   **Drift Detection**: Regularly check for drift between code and actual infrastructure.
</testing_protocols>

## <tooling>
*   **IaC**: **SST v3 (Ion)** (TypeScript)
*   **Secrets**: **Doppler**
*   **CI/CD**: **GitHub Actions** with OIDC
*   **Local S3**: **MinIO**
*   **Local DB**: **Neon Local** (Docker)
</tooling>

## <concepts>
### Graduated Hosting Strategy
1.  **Static Tier (Frontend/Edge)**: Use **Cloudflare Pages** for SPAs and static sites. Maximum performance, zero maintenance.
2.  **Agile Tier (PoC/MVP)**: Use **Railway** for rapid prototyping, internal tools, ephemeral environments. Zero-config deployment.
3.  **Production Tier (Scale)**: Use **AWS Fargate** (serverless containers) for long-running services and compliance workloads.

### Core Concepts
1.  **Idempotency**: The property that applying the same configuration multiple times results in the same state.
2.  **Drift**: The difference between the desired state (defined in code) and the actual state of the infrastructure.
3.  **GitOps**: A set of practices to manage infrastructure and application configurations using Git.
</concepts>

## <additional_section>
### Data Storage Strategy
*   **Relational Database**: Use **Neon** (serverless PostgreSQL) with scale-to-zero and branching. Use **AWS RDS** for strict compliance.
*   **Object Storage**: Use **Cloudflare R2** (zero egress fees, S3-compatible). Use **AWS S3 Glacier** for long-term archive.
*   **Edge Data**: Use **Cloudflare Workers KV** for high-read config. Use **Cloudflare D1** (SQLite) for region-specific data.

### Local Development
*   **S3 Emulation**: Use **MinIO** for S3-compatible local testing.
*   **Database**: Use **Neon Local** (Docker) to support branching workflow locally.
*   **Secrets**: Use `doppler run -- command` to inject secrets into local processes.
</additional_section>


