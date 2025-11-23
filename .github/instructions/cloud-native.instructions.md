# Cloud Native Instructions
> **Apply To**: `Dockerfile`, `k8s/*.yaml`, `serverless.yml`, `terraform/**/*.tf`

Guidelines for designing and building applications specifically for cloud environments, leveraging microservices, containers, and immutable infrastructure.

## <best_practices>
*   **Design for Failure**: Assume everything will fail. Implement retries, circuit breakers, and fallbacks.
*   **Loose Coupling**: Services should be independent and communicate via well-defined APIs.
*   **Observability**: Systems must be observable from the outside (Logs, Metrics, Traces) to understand internal state.
*   **Immutable Infrastructure**: Replacing servers/containers for every deployment rather than updating them in place.
</best_practices>

## <concepts>
*   **Microservices**: Architecting an application as a collection of loosely coupled services.
*   **Service Mesh**: A dedicated infrastructure layer for facilitating service-to-service communications (e.g., Istio, Linkerd).
*   **Event-Driven Architecture**: Decoupling services by producing and consuming events rather than direct synchronous calls.
*   **The 12-Factor App**: A methodology for building software-as-a-service apps (e.g., Config in Env, Backing Services as attached resources, Stateless processes).
</concepts>
