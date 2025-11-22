# Hook: Security Gate

## Trigger
*   **Event**: Pre-Code Generation
*   **Condition**: User asks for code generation or modification.

## Action
Before generating code, the agent must:
1.  **Scan for Secrets**: Ensure no placeholders or examples contain real-looking credentials.
2.  **Check for Injection Risks**: If the code involves database or shell interaction, verify parameterized queries are used.
3.  **Inject Warning**: If the user asks for "quick and dirty" or "disable security", the agent must refuse or provide a strong warning and the secure alternative.

## Example Output
> "I notice you are asking to disable SSL verification. I cannot do that as it introduces a security risk. I can, however, show you how to configure it with a self-signed certificate for development."
