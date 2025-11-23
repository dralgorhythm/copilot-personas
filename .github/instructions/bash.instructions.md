# Bash Scripting Instructions

## <concepts>
1.  **Strict Mode**: `set -euo pipefail` - exit on error, undefined variables, and pipe failures.
2.  **Exit Codes**: Commands return 0 for success, non-zero for failure. Use `$?` to check last exit code.
3.  **Quoting**: Double quotes `"$var"` for variable expansion, single quotes `'literal'` for literals.
4.  **Subshells**: `$(command)` captures command output, runs in subshell (preferred over backticks).
5.  **Process Substitution**: `<(command)` treats command output as a file for reading.
6.  **Test Conditions**: `[[ ]]` for tests (preferred over `[ ]` for portability and features).
7.  **Here Documents**: `<<EOF` for multi-line strings or command input.
8.  **Traps**: `trap` for cleanup on script exit, error, or interrupt signals.
</concepts>

## <best_practices>
1.  **Shebang**: Always use `#!/usr/bin/env bash` for portability.
2.  **Variable Naming**: Use `UPPER_CASE` for exported/global variables, `lower_case` for local variables.
3.  **Local Variables**: Always declare variables as `local` inside functions to avoid polluting the global scope.
4.  **Error Handling**: Check for command existence (`command -v`) and file existence before operations.
5.  **Linting**: Use `shellcheck` to catch common errors and pitfalls.
6.  **Comments**: Document complex logic and regex patterns.
7.  **Idempotency**: Scripts should be safe to run multiple times without side effects.
</best_practices>
