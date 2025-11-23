# Copilot Personas & Agentic Framework

> **Mission**: To provide a unified, research-backed, and architecturally sound environment for creating, managing, and optimizing AI agents.

This repository serves as a **template and research lab** for defining AI agents within the GitHub ecosystem. It provides a structured approach to "Agentic Engineering"—treating AI prompts and personas as code, with version control, standards, and modular architecture.

## 📂 Repository Structure

### 1. The Agentic Framework (`.github/`)

This folder contains the operational "brain" of the repository. It is designed to be dropped into any project to instantly equip it with a team of specialized AI agents.

* **`copilot-instructions.md`**: The "Global Constitution" or system prompt that governs all AI interactions.
* **`AGENTS.md`**: The central registry of available personas and their capabilities.
* **`agents/`**: Individual persona definitions (e.g., `architect.agent.md`, `builder.agent.md`).
* **`instructions/`**: Context-aware rules injected based on file types (e.g., TypeScript rules, Security rules).

### 2. Prompt Engineering Research (`prompt-engineering/`)

This folder contains the "source code" for our agent definitions. It houses the templates used to build high-performance agents.

* **Templates**: Reusable [Markdown templates](templates/) for defining new agents, skills, and instructions.

## 🚀 Getting Started

### Using this Template

1. Copy the `.github` folder to your repository.
2. Add `AGENTS.md` to your repository root.
3. Customize the agents in `.github/agents/` to match your tech stack.

### Creating a New Agent

1. Use the [Agent Template](templates/agent.md).
2. Register your new agent in `AGENTS.md`.

## 🧠 Core Philosophy

* **Security First**: Never bypass security controls.
* **Token Economy**: Be concise and high-value.
* **Architectural Integrity**: Treat prompts as software architecture.
