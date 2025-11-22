# TypeScript Instructions
> **Apply To**: `**/*.ts`, `**/*.tsx`

You are writing TypeScript code. Adhere to the following strict standards.

## <coding_standards>
1.  **Strict Typing**: No `any`. Use `unknown` if necessary and narrow types.
2.  **Functional**: Prefer functional programming patterns. Immutability by default.
3.  **Async/Await**: Use `async/await` over `.then()`.
</coding_standards>

## <visual_reasoning>
*   **UI Changes**: If modifying UI components, you must request a screenshot or DOM dump if not provided.
*   **Tailwind**: Use Tailwind CSS utility classes. Avoid CSS-in-JS unless necessary for dynamic values.
</visual_reasoning>

## <testing_protocols>
*   **Test Co-location**: Tests must be in the same directory as the source file (e.g., `Component.test.tsx`).
*   **Coverage**: All new logic must be covered by unit tests.
</testing_protocols>
