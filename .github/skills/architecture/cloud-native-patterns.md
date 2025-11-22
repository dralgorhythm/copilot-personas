# Skill: Cloud Native Patterns

## Description

Designing and building applications specifically for cloud environments, leveraging microservices, containers, and immutable infrastructure.

## Triggers

* **Keywords**: "cloud native", "microservice", "serverless", "lambda", "kubernetes", "container", "12-factor", "stateless", "sidecar", "circuit breaker"
* **Context**: Designing scalable, resilient applications for the cloud, migrating legacy apps, breaking down monoliths.

## Core Knowledge

### Concepts

* **Microservices**: Architecting an application as a collection of loosely coupled services.
* **Service Mesh**: A dedicated infrastructure layer for facilitating service-to-service communications (e.g., Istio, Linkerd).
* **Event-Driven Architecture**: Decoupling services by producing and consuming events rather than direct synchronous calls.
* **Immutable Infrastructure**: Replacing servers/containers for every deployment rather than updating them in place.

### Principles

* **The 12-Factor App**: A methodology for building software-as-a-service apps (e.g., Config in Env, Backing Services as attached resources, Stateless processes).
* **Design for Failure**: Assume everything will fail. Implement retries, circuit breakers, and fallbacks.
* **Loose Coupling**: Services should be independent and communicate via well-defined APIs.
* **Observability**: Systems must be observable from the outside (Logs, Metrics, Traces) to understand internal state.

## Actionable Affordances

### Tool Affordances

#### Scaffold 12-Factor Checklist

Creates a checklist to audit an application against 12-Factor principles.

```bash
#!/bin/bash
# audit-12factor.sh
# Usage: ./audit-12factor.sh <AppName>

APP_NAME=$1

if [ -z "$APP_NAME" ]; then
  echo "Usage: $0 <AppName>"
  exit 1
fi

FILENAME="12factor-audit-$APP_NAME.md"

cat <<EOF > "$FILENAME"
# 12-Factor Audit: $APP_NAME

| Factor | Description | Status | Notes |
| :--- | :--- | :--- | :--- |
| **1. Codebase** | One codebase tracked in revision control, many deploys. | [ ] | |
| **2. Dependencies** | Explicitly declare and isolate dependencies. | [ ] | |
| **3. Config** | Store config in the environment. | [ ] | |
| **4. Backing Services** | Treat backing services as attached resources. | [ ] | |
| **5. Build, Release, Run** | Strictly separate build and run stages. | [ ] | |
| **6. Processes** | Execute the app as one or more stateless processes. | [ ] | |
| **7. Port Binding** | Export services via port binding. | [ ] | |
| **8. Concurrency** | Scale out via the process model. | [ ] | |
| **9. Disposability** | Maximize robustness with fast startup and graceful shutdown. | [ ] | |
| **10. Dev/Prod Parity** | Keep development, staging, and production as similar as possible. | [ ] | |
| **11. Logs** | Treat logs as event streams. | [ ] | |
| **12. Admin Processes** | Run admin/management tasks as one-off processes. | [ ] | |

EOF

echo "Created Audit File: $FILENAME"
```

### Reference Implementation

#### Circuit Breaker Pattern (TypeScript)

Prevents cascading failures by stopping calls to a failing service.

```typescript
enum CircuitState {
  CLOSED,   // Normal operation
  OPEN,     // Failing, block requests
  HALF_OPEN // Testing recovery
}

class CircuitBreaker {
  private state: CircuitState = CircuitState.CLOSED;
  private failureCount = 0;
  private lastFailureTime = 0;
  
  constructor(
    private threshold: number = 5, 
    private timeout: number = 10000
  ) {}

  public async call(action: () => Promise<any>): Promise<any> {
    if (this.state === CircuitState.OPEN) {
      if (Date.now() - this.lastFailureTime > this.timeout) {
        this.state = CircuitState.HALF_OPEN;
      } else {
        throw new Error("Circuit is OPEN");
      }
    }

    try {
      const result = await action();
      this.reset();
      return result;
    } catch (error) {
      this.recordFailure();
      throw error;
    }
  }

  private recordFailure() {
    this.failureCount++;
    this.lastFailureTime = Date.now();
    if (this.failureCount >= this.threshold) {
      this.state = CircuitState.OPEN;
    }
  }

  private reset() {
    this.failureCount = 0;
    this.state = CircuitState.CLOSED;
  }
}
```

### Libraries

* **Resilience**: Resilience4j (Java), Polly (.NET), CockroachDB/CircuitBreaker (Go).
* **Service Mesh**: Istio, Linkerd, Consul.
* **Serverless**: AWS Lambda, Google Cloud Functions, Azure Functions.

## Checklist

* [ ] **Stateless**: Is local disk storage avoided for persistent data?
* [ ] **Config**: Are secrets and config loaded from ENV vars?
* [ ] **Logs**: Are logs written to `stdout`/`stderr`?
* [ ] **Health Checks**: Does the app expose `/health` and `/ready` endpoints?
* [ ] **Graceful Shutdown**: Does the app handle `SIGTERM` to finish in-flight requests?
