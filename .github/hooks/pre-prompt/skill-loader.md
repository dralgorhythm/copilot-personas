# Hook: Skill Loader

**Trigger**: Pre-Prompt (Before processing user query)

## Instructions

1. **Analyze User Query**: Check the user's input against the patterns defined in `.github/skills/skill-rules.json`.
2. **Load Skills**: If a pattern matches, read the corresponding `SKILL.md` file to gain context.
3. **Progressive Disclosure**: If the `SKILL.md` references specific resources that are highly relevant to the query, read those resources as well.
4. **Context Injection**: Use the loaded skill information to inform your response.
5. **Tool Affordances**: If the loaded skill contains a "Tool Affordances" section with bash scripts:
    *   Inform the user that a script is available to assist with the task.
    *   Display the script content for review if requested or if relevant to the immediate next step.

## Example

If the user asks "Design a scalable system for...", and `skill-rules.json` has a pattern "scalable system" pointing to `system-design`, you should:

1. Read `.github/skills/system-design/SKILL.md`.
2. Use the knowledge from that file to answer the question.

