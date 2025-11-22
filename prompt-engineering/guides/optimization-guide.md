# Persona Optimization Guide

> **Goal**: Refine existing personas to improve performance, reduce token usage, and ensure alignment with the swarm architecture.

## <optimization_steps>

### 1. Audit & Analysis

- **Token Count**: Is the persona over 2000 tokens? If so, it needs trimming.
- **Duplication**: Does it repeat content found in `shared-context/`?
- **Clarity**: Are the instructions ambiguous?

### 2. Extraction & Modularization

- **Move Shared Content**: Extract generic rules to `prompt-engineering/shared-context/`.
- **Link**: Replace the extracted content with a link to the shared file.

### 3. Refinement

- **Use XML**: Ensure the persona uses the standard XML structure.
- **Add Thinking**: Insert `<thinking>` blocks for complex decision points.
- **Cut Fluff**: Remove adjectives and conversational filler. Be direct.

### 4. Validation

- **Check Standards**: Verify against `standards/UnifiedPromptEngineeringStandard.md`.
- **Test**: Run a regression test to ensure the optimization didn't break core functionality.

</optimization_steps>
