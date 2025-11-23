# Domain-Driven Design Instructions
> **Apply To**: `src/**/domain/**/*`, `src/**/application/**/*`, `src/**/infrastructure/**/*`

Guidelines for modeling software to match a domain (Entities, Aggregates, Bounded Contexts).

## <best_practices>
*   **Ubiquitous Language**: Use the same terminology in the code as the domain experts use in conversation.
*   **Rich Domain Models**: Encapsulate business logic within domain entities, not in "anemic" service classes.
*   **Bounded Contexts**: Clearly define the boundaries of each model to prevent ambiguity.
</best_practices>

## <concepts>
*   **Bounded Context**: Explicit boundary within which a domain model exists.
*   **Ubiquitous Language**: Common language shared by developers and domain experts.
*   **Aggregate**: Cluster of domain objects that can be treated as a single unit.
*   **Entity**: Object defined by its identity.
*   **Value Object**: Object defined by its attributes (immutable).
</concepts>
