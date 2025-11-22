# Unified Prompt Engineering & Management Standard (UPEMS) v1.0

> **Purpose**: A comprehensive framework integrating advanced context architecture, rigorous persona research, and lifecycle management for AI agents.
> **Base Models**: Unified Agent Context Standard (UACS), Professional AI Persona Research Framework.

---

## 1. Core Philosophy

This standard merges two critical disciplines:

1. **Architectural Efficiency**: Modular, constraint-based context management (from UACS).
2. **Authentic Expertise**: Deep, research-backed persona development (from Research Framework).

The goal is to create agents that are not only technically optimized for reasoning models (like Gemini 3) but also professionally authentic and industry-aligned.

---

## 2. Context Architecture Strategy

We move away from monolithic "System Prompts" toward a **Modular Context Architecture**.

### 2.1. Directory Structure

The workspace is organized to separate agent definitions, shared rules, and research artifacts.

```text
.github/
├── copilot-instructions.md # Global Constitution
├── agents/                 # Agent Definitions (The "Face")
│   ├── architect.agent.md  # High-level planner
│   └── builder.agent.md    # Implementation specialist
├── skills/                 # Modular Capabilities (The "Hands")
│   ├── skill-rules.json    # Activation logic
│   └── system-design/      # Skill module
├── hooks/                  # Lifecycle Events (The "Reflexes")
│   └── pre-prompt/         # Context injection
└── instructions/           # Context Injection (The "Brain")
    ├── typescript.instructions.md
    └── prompt-engineering.instructions.md
prompt-engineering/
    ├── standards/          # Governing documents
    ├── shared-context/     # Reusable modules (Legacy/Shared)
    └── templates/          # Creation patterns
```

### 2.2. Context Injection (New)

We leverage GitHub Copilot's `.github/instructions/` to inject context based on file types.

*   **Global**: `.github/copilot-instructions.md` applies to all queries.
*   **File-Specific**: `*.instructions.md` applies when specific files are open (e.g., `typescript.instructions.md` for `.ts` files).

### 2.4. Agentic Components (Skills & Hooks)

To support dynamic capabilities, we use:

*   **Skills**: Modular knowledge bases loaded on demand via `skill-rules.json`.
*   **Hooks**: Instructions injected at specific lifecycle points (e.g., Pre-Prompt) to guide agent behavior.

### 2.5. The "Deep Think" Protocol (Gemini 3 Optimized)

For reasoning models, we use **Constraint-Based Prompting** with strict XML structuring.

*   **Structure**: Use XML tags (`<role>`, `<constraints>`, `<plan>`) to delimit sections.
*   **Thinking Level**: High (Native recursive reasoning).
*   **Verbosity**: Low (Action-oriented).
*   **Tool Usage**: Aggressive (Verify assumptions immediately).

---

## 3. The Persona Lifecycle

### Phase 1: Research & Validation (The "Truth" Layer)

*Based on the Professional AI Persona Research Framework.*

Before writing a prompt, we validate the role against industry standards.

1. **Domain Landscape Mapping**: Define the professional ecosystem and boundaries.
2. **Competency Validation**: Cross-reference skills with real-world job descriptions and certifications.
3. **Source Stratification**: Use authoritative sources (Tier 1) over general web content.

### Phase 2: Construction (The "Build" Layer)

*Based on UACS and Persona Creation Process.*

1. **Drafting**: Use the `persona-template.md`.
2. **Modularization**: Link to `shared-context/` files instead of duplicating text.
3. **Cognitive Configuration**: Apply the "Principal Engineer" core constraints for reasoning agents.

### Phase 3: Optimization (The "Refine" Layer)

*Based on Persona Optimization Guide.*

1. **Audit**: Check token counts and remove redundancy.
2. **Extraction**: Move generic rules to shared modules.
3. **Refinement**: Convert prose to strict XML/Markdown constraints.

---

## 4. Agent Swarm Protocols

### 4.1. Handoffs

Agents are designed to collaborate. Handoffs are defined in the `.agent.md` YAML frontmatter.

* **Architect**: Analyzes -> Handoffs to -> **Builder**.
* **Builder**: Implements -> Handoffs to -> **Reviewer** (or User).

### 4.2. Artifact Protocol

Agents communicate through **Artifacts** (files), not just chat.

1. **Plan**: Architect creates `artifacts/plan_[id].md`.
2. **Approve**: User/Reviewer confirms.
3. **Execute**: Builder implements based on the plan.

---

## 5. Implementation Checklist

* [ ] **Research**: Has the persona been validated against the Research Framework?
* [ ] **Architecture**: Does it use the Modular Context structure?
* [ ] **Optimization**: Is it tuned for the specific model (e.g., Gemini 3 vs. GPT-4)?
* [ ] **Compliance**: Does it adhere to Constitutional AI and safety guidelines?
