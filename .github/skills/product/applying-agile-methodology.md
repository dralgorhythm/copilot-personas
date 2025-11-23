---
name: applying-agile-methodology
description: Applying Agile principles (Scrum, Kanban) to the development flow to deliver value iteratively and incrementally.
---

# Applying Agile Methodology

## Workflows
<!-- Checklist for complex tasks -->
- [ ] **Value**: Does this story deliver value to the user?
- [ ] **Clarity**: Is the acceptance criteria clear and testable?
- [ ] **Size**: Is the story small enough to be completed in a sprint?
- [ ] **Dependencies**: Are external dependencies identified and managed?
- [ ] **DoD**: Is the Definition of Done clearly understood?

## Feedback Loops
<!-- Validation steps -->
1. Write User Story.
2. Refine with team (Estimation).
3. Implement.
4. Review (Demo).
5. Retrospective.

## Utility Scripts
<!-- Reference executable scripts -->
- `scaffold-story.sh`: Generates a template for a comprehensive user story.

```bash
#!/bin/bash
# scaffold-story.sh
# Usage: ./scaffold-story.sh <StoryTitle>

TITLE=$1
FILENAME="story-$(date +%s).md"

cat <<EOF > "$FILENAME"
# Story: $TITLE

**As a** [Role]
**I want** [Feature]
**So that** [Benefit]

## Acceptance Criteria
- [ ] Scenario 1: [Description]
- [ ] Scenario 2: [Description]
- [ ] Scenario 3: [Description]

## Technical Notes
- API Endpoint: \`GET /api/v1/resource\`
- Database Schema: [Link]

## Definition of Done
- [ ] Unit Tests Passed
- [ ] Integration Tests Passed
- [ ] Code Reviewed
- [ ] Documentation Updated
EOF

echo "Created User Story Template: $FILENAME"
```

## Reference Implementation
<!-- Code patterns -->

### Scrum Ceremony Checklist

1. **Sprint Planning**: Define the Sprint Goal and select items from the backlog.
2. **Daily Standup**: 15-min sync. What did I do? What will I do? Blockers?
3. **Sprint Review**: Demo the increment to stakeholders.
4. **Sprint Retrospective**: Team improvement discussion.
5. **Backlog Refinement**: Clarify and estimate future items.

## Resources
<!-- Links to external docs or local reference files -->
- [Agile Methodology Instructions](../../instructions/agile-methodology.instructions.md)
