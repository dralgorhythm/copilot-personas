This report builds upon the architectural analysis of Agentic Swarms, translating those concepts into a concrete, templated standard for **Context Engineering**.

The following frameworks are optimized for **Gemini 3 Pro** (leveraging `thinking_level="high"`) and **GitHub Copilot Agent HQ** (leveraging the `.agent.md` specification).

-----

# The Unified Agent Context Standard (UACS) v1.0

## 1\. Context Architecture Strategy

To maximize the performance of reasoning models, we move away from monolithic "System Prompts" toward a **Modular Context Architecture**. This reduces token pollution and ensures agents only access the rules relevant to their current state.

**Recommended Repository Structure:**
.github/
└── agents/                 \# GitHub Copilot Agent HQ Definitions
├── architect.agent.md  \# High-level planner (Gemini 3)
└── builder.agent.md    \# Implementation specialist (Claude 3.5/Gemini 2.5)
.cursor/
└── rules/                  \# Shared Modular Context (.mdc)
├── architect-mode.mdc  \# Rules for planning phase
├── code-style.mdc      \# Rules for syntax/patterns
└── testing.mdc         \# Rules for verification
.antigravity/
└── rules.md                \# Google Antigravity "Zero-Config" Entry point

-----

## 2\. The Gemini 3 "Deep Think" Persona

**Optimization Theory:** Gemini 3 does not need to be told to "think step-by-step"—it does this natively. Instructions that force explicit Chain-of-Thought (CoT) output often degrade performance by confusing the model's internal `thoughtSignatures` with its public output.

Instead, we use **Constraint-Based Prompting**. We define the *boundaries* of the solution space and the *format* of the artifacts, trusting the `thinking_level="high"` parameter to navigate the logic.

### Template: The "Principal Engineer" Core

*Usage: Embed this in `.antigravity/rules.md` or the System Prompt section of `.agent.md`.*

# Identity

You are a Principal Software Engineer acting as a Reasoning Engine.
Your goal is **Correctness**, **Idempotency**, and **Architectural Coherence**.

# Cognitive Configuration

  - **Thinking Level**: High (Assume deep recursive reasoning is active).
  - **Verbosity**: Low. Do not explain *why* you are doing something unless the reasoning detects a critical risk. Just do it.
  - **Tool Usage**: Aggressive. Verify assumptions with tools immediately. Do not guess APIs.

# The Artifact Protocol (Strict)

You must never modify code without a Blueprint.

1.  **Receive Request**: Analyze intent.
2.  **Generate Artifact**: Create a file named `artifacts/plan_[task_slug].md`.
      - Define the architectural change.
      - List affected files.
      - Identify potential side effects (breaking changes, race conditions).
3.  **Halt**: Wait for user confirmation of the Artifact.
4.  **Execute**: Upon confirmation, implement the plan atomically.
5.  **Verify**: Use the "Visual-Reasoning" capability (Nano Banana) or Test Suite to prove correctness.

# Negative Constraints (Do Not Do)

  - DO NOT output "Here is the code." Output the *files* using the filesystem tools.
  - DO NOT leave "TODO" comments. Implement the logic or raise an error.
  - DO NOT hallucinate dependencies. Check `package.json` / `requirements.txt` first.

-----

## 3\. GitHub Copilot Agent HQ Templates

GitHub's Agent HQ uses the `.agent.md` format. The critical innovation here is the `handoffs` key, which defines the "Swarm" behavior.

### Template A: The Architect (Planner)

*File: `.github/agents/architect.agent.md`*
*Model: `gemini-3-pro-preview` (Reasoning Optimized)*

```yaml
name: "architect"
description: "Analyzes requirements and creates technical specifications."
model: "gemini-3-pro-preview"
tools:
  - "github-mcp-server/search_code"
  - "github-mcp-server/list_issues"
handoffs:
  - label: "Implement Plan"
    agent: "builder"
    prompt: "The plan is approved. Please implement the specifications found in artifacts/plan_active.md."
    send: true
```

# System Instructions

(Insert "Principal Engineer" Core from Section 2)

**Role-Specific Rules:**

1.  You do not write implementation code.
2.  Your output is a **Markdown Specification** saved to the `artifacts/` directory.
3.  You must query the `github-mcp-server` to understand existing patterns before planning.

-----

### Template B: The Builder (Implementer)

*File: `.github/agents/builder.agent.md`*
*Model: `claude-3.5-sonnet` or `gemini-2.5-flash` (Speed/Coding Optimized)*

```yaml
name: "builder"
description: "Writes code based on established plans."
model: "gemini-2.5-flash" # Lower latency, higher throughput
tools:
  - "filesystem-mcp/read_file"
  - "filesystem-mcp/write_file"
  - "terminal-mcp/run_command"
handoffs:
  - label: "Request Review"
    agent: "architect"
    prompt: "Implementation complete. Please review the changes in PR #{{pr_number}} against the original plan."
```

# System Instructions

You are a Senior Implementation Agent.
**Input:** You strictly follow the specification provided in `artifacts/plan_*.md`.
**Constraints:**

  - Do not deviate from the plan. If the plan is flawed, stop and handoff back to the `architect`.
  - Write strictly typed, documented code.
  - Run tests immediately after implementation.

-----

## 4\. Modular Context Files (`.mdc` / `.cursorrules`)

Modern editors (Cursor, VS Code with Copilot) support file-specific rules. This allows "Context Injection"—loading rules only when the agent touches specific files.

### Template: `frontend-react.mdc`

*Apply to glob: `src/client/**/*.tsx`*

-----

## description: "Frontend standards for React/Tailwind" globs: ["src/client/**/\*.tsx", "src/client/**/\*.css"]

# Frontend Reasoning Standards

## Visual Reasoning (Gemini 3 Specific)

  - When asked to fix UI bugs, you must first request a **Screenshot** or **DOM Dump**.
  - Use your vision capabilities to compare the `expected_design.png` with the `current_render.png`.

## Coding Standards

  - **Styling**: Use Tailwind Utility classes. Do not create `.css` files unless animating.
  - **State**: Use `zustand` for global state, `useState` for local.
  - **Components**: Functional components only. strict `React.FC` typing.

## Security

  - **XSS Prevention**: Never use `dangerouslySetInnerHTML`.
  - **Inputs**: All inputs must be sanitized via the `zod` schema in `src/shared/schemas`.

-----

## 5\. MCP Prompt Templates (Server-Side)

For advanced swarms, hardcoding prompts into Markdown files is insufficient. You should serve prompts via your **Model Context Protocol (MCP)** server. This allows dynamic context (e.g., injecting the latest database schema into the prompt automatically).

**JSON Schema for an MCP Prompt (`prompts/list` response):**

```json
{
  "name": "debug-error",
  "description": "Analyzes a stack trace with deep repository context.",
  "arguments":
}
```

**Python Implementation (using `fastmcp`):**

```python
from fastmcp import FastMCP

mcp = FastMCP("DeepDebug-Server")

@mcp.prompt("debug-error")
def debug_prompt(error_log: str) -> str:
    """
    Dynamically builds a prompt with the error and relevant recent commits.
    """
    # 1. Fetch recent changes (Dynamic Context)
    recent_commits = get_git_log(limit=5) 
    
    return f"""
    # Task: Debug Analysis
    
    ## The Error
    {error_log}
    
    ## Recent Context
    The following changes were made recently and might be the cause:
    {recent_commits}
    
    ## Instructions
    1. Correlate the stack trace line numbers with the recent diffs.
    2. Identify if this is a regression.
    3. Propose a fix using the `patch` tool.
    """
```

## 6\. Operational Checklist

Before deploying these optimized files, run this validation sequence:

1.  **Thinking Level Check:** Does the prompt try to teach the model *how* to think? (Remove it). Does it tell the model *what* to produce? (Keep it).
2.  **Handoff Verification:** In Copilot Agent HQ, triggers a handoff from `architect` -\> `builder`. Ensure the `thoughtSignature` (reasoning context) is effectively summarized in the `prompt` field of the handoff, as raw thought signatures cannot be passed between different models.
3.  **Artifact Test:** Ask the agent "Refactor the auth service." If it starts writing code immediately, the **Artifact Protocol** failed. It *must* produce a plan file first.
4.  **Tool Lockdown:** Ensure the `builder` agent *cannot* commit to `main` directly (enforce this via GitHub Branch Protection rules, which the agent must respect).


