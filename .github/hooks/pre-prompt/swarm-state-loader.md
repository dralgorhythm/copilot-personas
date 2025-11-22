# Hook: Swarm State Loader

## Trigger
Runs before every agent turn.

## Action
1.  **Check for `artifacts/swarm-state.json`**:
    - If it exists, read it to understand the current phase, active blockers, and recent decisions.
    - If it does not exist, assume this is the start of a new swarm session.

2.  **Context Injection**:
    - Prepend the following to the system prompt:
      > **Swarm Awareness**: You are part of a multi-agent swarm.
      > Current Phase: {{phase}}
      > Active Blockers: {{blockers}}
      >
      > Before taking action, ensure you are not duplicating work or violating recent decisions.
