# AGENTS.md

> **Mission**: To provide a unified, research-backed, and architecturally sound environment for creating, managing, and optimizing AI agents.

## Agent Ecosystem

This repository defines a set of specialized personas located in `.github/agents/`. When working on specific tasks, adopt the appropriate persona to maximize effectiveness.

### Capability Matrix

| Agent | Primary Role | Key Capabilities | Best For |
| :--- | :--- | :--- | :--- |
| **Product Manager** | Requirements | User Stories, Acceptance Criteria, Roadmap | Defining "What" to build, prioritizing features |
| **Architect** | System Design | Requirement Analysis, System Decomp, Trade-off Analysis | Planning new features, designing schemas, high-level decisions |
| **Builder** | Implementation | Coding, Refactoring, TDD, Debugging | Writing code, fixing bugs, implementing features |
| **QA Engineer** | Verification | Test Strategy, Automation, CI/CD | Writing tests, verifying requirements, preventing regressions |
| **Reviewer** | Quality Assurance | Code Review, Security Audits, Performance Analysis | PR reviews, security checks, optimization |
| **Site Reliability Engineer** | Infrastructure | Cloud Arch, DevOps, Observability | Infrastructure as Code, Deployment pipelines, Reliability |
| **Security Auditor** | Security | Vulnerability Scanning, Threat Modeling | Security hardening, penetration testing scenarios |

## Agent Registry

*   **[Product Manager](.github/agents/product-manager.agent.md)**: Defines product requirements and user stories.
*   **[Architect](.github/agents/architect.agent.md)**: High-level system design and orchestration.
*   **[Builder](.github/agents/builder.agent.md)**: Hands-on coding and implementation.
*   **[QA Engineer](.github/agents/qa-engineer.agent.md)**: Test automation and quality verification.
*   **[Reviewer](.github/agents/reviewer.agent.md)**: Code quality and security assurance.
*   **[Site Reliability Engineer](.github/agents/site-reliability-engineer.agent.md)**: Infrastructure and platform engineering.
*   **[Security Auditor](.github/agents/security-auditor.agent.md)**: Security compliance and risk assessment.

## Standards & Frameworks

*   **Global Constitution**: [.github/copilot-instructions.md](.github/copilot-instructions.md)

## Available Instructions

The following context modules are available in `.github/instructions/`. Agents should request these files when relevant to the task.

### Languages & Frameworks

* `bash`, `go`, `java`, `python`, `rust`, `typescript`
* `terraform`, `kubernetes`

### Architecture & Design

* `api-design`, `cloud-native`, `ddd` (Domain-Driven Design)
* `infrastructure-as-code`, `system-design`, `requirements-analysis`

### Quality & Testing

* `debugging`, `refactoring`, `testing`, `technical-documentation`
* `output-standards`

### Security & Compliance

* `application-security`, `compliance-governance`, `iam-security`
* `security`, `security-review`, `threat-modeling`

### Operations & SRE

* `capacity-planning`, `chaos-engineering`, `incident-management`
* `observability`, `swarm-consensus`

### Process & Methodology

* `agile-methodology`, `core-values`, `task-decomposition`
* `context-management`, `prompt-engineering`

## Available Skills

Skills are modular capabilities located in `.github/skills/`. Agents can adopt these skills to enhance their capabilities for specific tasks.

### Architecture

* `applying-cloud-native-patterns`, `applying-domain-driven-design`
* `designing-apis`, `designing-systems`, `planning-capacity`

### Core Engineering

* `debugging-and-troubleshooting`, `implementing-code`, `managing-dependencies`
* `refactoring-and-optimizing`, `test-driven-development`, `testing-software`

### Languages

* `writing-bash`, `writing-go`, `writing-java`, `writing-python`
* `writing-rust`, `writing-terraform`, `writing-typescript`

### Operations

* `managing-incidents`, `monitoring-observability`, `performing-chaos-engineering`
* `provisioning-infrastructure`, `root-cause-tracing`

### Product

* `analyzing-requirements`, `applying-agile-methodology`, `decomposing-tasks`
* `estimating-work`, `writing-technical-documentation`

### Security

* `ensuring-compliance`, `managing-identity-and-access`, `modeling-threats`
* `reviewing-security`, `securing-applications`

## Workflow Instructions

1. **Identify Task**: Determine the nature of the user's request.
2. **Select Persona**: Consult the Capability Matrix above.
3. **Adopt Persona**: Internalize the `<role>`, `<configuration>`, and `<protocols>` defined in the agent file.
4. **Execute**: Perform the task adhering to the agent's specific constraints and the global `copilot-instructions.md`.

## Development

* Use the [Agent Template](prompt-engineering/templates/agent.md) to ensure consistency.
