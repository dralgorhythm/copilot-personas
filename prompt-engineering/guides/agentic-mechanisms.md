# Agentic Mechanisms: Skills and Hooks

This guide explains the "Skills" and "Hooks" architecture used to augment agent capabilities and manage context efficiently.

## 1. Skills

Skills are modular, reusable capabilities that agents can load on demand. They follow a **Progressive Disclosure** pattern to minimize token usage.

### Skill Structure

Skills are located in `.github/skills/`.

- **`skill-rules.json`**: Maps user query patterns (regex) to skill paths.
- **`<skill-name>/SKILL.md`**: The entry point for a skill. Contains high-level context.
- **`<skill-name>/resources/`**: Detailed documentation loaded only when referenced by `SKILL.md`.

### Creating a Skill

1. Create a folder `.github/skills/<name>`.
2. Add `SKILL.md` with `Overview`, `Capabilities`, and `Resources`.
3. Add detailed markdown files in `resources/`.
4. Register the skill in `.github/skills/skill-rules.json`.

## 2. Hooks

Hooks are instructions or scripts that run at specific lifecycle events.

### Hook Structure

Hooks are located in `.github/hooks/`.

- **`pre-prompt/`**: Instructions injected *before* the agent processes the user's query.
  - Example: `skill-loader.md` instructs the agent to check `skill-rules.json`.
- **`post-tool/`**: Instructions for validating or processing tool outputs.

### Using Hooks

Hooks are typically included in the agent's system prompt or executed by the orchestration layer (if available).

## 3. Integration

To give an agent access to skills:

1. Ensure the agent's definition includes the `skills` field (optional, for explicit loading).
2. The `skill-loader` hook (if active) will automatically suggest skills based on the user's query.

