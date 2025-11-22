# Skill: Context Management

## Description
Managing shared knowledge, state, and handoffs between agents to ensure continuity and reduce hallucinations.

## Triggers
*   Keywords: "handoff", "context", "shared state", "knowledge transfer", "summary", "status"
*   Context: When switching active agents or resuming a session.

## Protocols

### 1. Swarm State
Read/Write to `artifacts/swarm-state.json` (virtual or real) to track:
- **Current Phase**: (Design, Dev, Test, Deploy)
- **Active Blockers**: Issues stopping progress.
- **Recent Decisions**: Links to ADRs.

### 2. Handoff Summary
When passing control to another agent, provide:
- **What was done**: Brief summary of actions.
- **What is next**: Specific request for the next agent.
- **Relevant Files**: List of files modified or needed.

### 3. Context Pruning
- Summarize long conversation histories into key points before handoff.
- Archive outdated scratchpad notes.
