# Copilot Personas

> **Drop-in agentic framework for GitHub Copilot**

Transform your repository into an AI-powered development environment with specialized agents, reusable skills, and standardized workflows.

## Quick Start

1. **Copy** `.github/` folder to your repository
2. **Copy** `AGENTS.md` to your repository root
3. **Customize** agents and instructions to match your tech stack

## What's Inside

### `.github/agents/` — 8 Specialized AI Personas
Pre-configured agents for every phase of development:
- **Product Manager** → Requirements & user stories
- **Architect** → System design & technical decisions
- **UI/UX Designer** → Visual design & accessibility
- **Builder** → Implementation & coding
- **QA Engineer** → Testing & verification
- **Reviewer** → Code review & quality assurance
- **Site Reliability Engineer** → Infrastructure & operations
- **Security Auditor** → Security compliance & audits

### `.github/skills/` — Modular Workflows
Reusable capabilities organized by domain:
- `architecture/` — System design, API patterns, cloud architecture
- `core-engineering/` — Coding standards, testing, debugging
- `design/` — UI/UX workflows, accessibility, visual design
- `languages/` — Language-specific best practices
- `operations/` — DevOps, observability, incident response
- `product/` — PRDs, roadmaps, user stories
- `security/` — Threat modeling, compliance, auditing

### `.github/instructions/` — Context-Aware Guidance
Technical standards that auto-activate based on file type and context:
- **Tech Strategy** → Golden Path for technology choices
- **Language Guides** → Go, Rust, Python, TypeScript standards
- **Architecture Patterns** → API design, event-driven systems
- **Security Policies** → Authentication, secrets management

### `templates/` — Extensibility
Create new resources using standardized templates:
- `agent.md` — Define new AI personas
- `skill.md` — Add reusable workflows
- `instruction.md` — Create context-aware rules

## Key Concepts

### Agents & Handoffs
Agents collaborate through **handoffs**—structured transitions that pass work between personas with explicit artifacts.

**Example Flow**:
```
Product Manager → Architect → Builder → QA Engineer → Reviewer
     (PRD)      →  (Design) →  (Code)  →  (Tests)  → (Approval)
```

Each handoff includes:
- **Artifact path** (e.g., `./artifacts/prd_feature.md`)
- **Clear prompt** for the next agent
- **Verification step** to ensure artifact quality

### Artifacts & Naming
All planning documents use standardized naming in `./artifacts/`:
- `prd_[feature].md` — Product requirements
- `adr_[topic].md` — Architecture decisions
- `design_spec_[component].md` — Visual designs
- `roadmap_[project].md` — Execution roadmaps
- `plan_[task].md` — Implementation plans

### Skill Activation
Skills auto-load based on patterns defined in `.github/skills/skill-rules.json`. Agents check this file at initialization to discover relevant capabilities.

## Adding New Resources

### New Agent
1. Copy `templates/agent.md`
2. Define identity, responsibilities, and handoffs
3. Register in `AGENTS.md`

### New Skill
1. Copy `templates/skill.md`
2. Define workflow and patterns
3. Add activation rules to `skill-rules.json`

### New Instruction
1. Copy `templates/instruction.md`
2. Define standards and compliance requirements
3. Reference from relevant agents

## Learn More

- **[AGENTS.md](AGENTS.md)** — Complete agent registry and capability matrix
- **[.github/copilot-instructions.md](.github/copilot-instructions.md)** — Global AI governance
- **[Tech Strategy](.github/instructions/tech-strategy.instructions.md)** — Golden Path for technology choices
