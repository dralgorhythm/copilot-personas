# Incident Management Instructions
> **Apply To**: `post-mortems/*.md`, `runbooks/*.md`

Guidelines for handling outages, on-call procedures, and post-mortems to minimize downtime and learn from failures.

## <best_practices>
*   **Mitigate First**: Focus on restoring service first, not finding the root cause.
*   **Communicate**: Update stakeholders regularly (e.g., every 30 minutes for SEV1).
*   **Blameless Post-Mortem**: Focus on process and technology failures, not human error.
*   **Actionable Follow-up**: Ensure all lessons learned result in tracked action items.
</best_practices>

## <concepts>
*   **Severity Levels**:
    *   **SEV1 (Critical)**: System down, data loss, or major business impact. Immediate response required.
    *   **SEV2 (Major)**: Significant degradation, workaround available. Response within 30 mins.
    *   **SEV3 (Minor)**: Minor bug or annoyance. Handle during business hours.
*   **MTTR (Mean Time To Recovery)**: The average time it takes to restore service after a failure.
*   **Incident Commander**: The person responsible for coordinating the response effort.
</concepts>
