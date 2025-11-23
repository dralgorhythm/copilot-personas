# Python Development Instructions

## <concepts>
1.  **Type Hints**: Using type annotations (`typing` module) to improve code clarity and enable static analysis with `mypy`.
2.  **PEP 8**: Python Enhancement Proposal 8 - the official style guide for Python code emphasizing readability.
3.  **List Comprehensions**: Concise syntax for creating lists from iterables, more Pythonic than traditional loops.
4.  **Context Managers**: Using `with` statements to ensure proper resource cleanup (files, locks, connections).
5.  **Decorators**: Functions that modify behavior of other functions or classes (e.g., `@property`, `@staticmethod`).
6.  **Generator Expressions**: Memory-efficient iteration using `yield` instead of building full lists in memory.
7.  **Duck Typing**: "If it walks like a duck and quacks like a duck, it's a duck" - focus on object behavior over type.
8.  **EAFP**: "Easier to Ask for Forgiveness than Permission" - use try/except rather than checking conditions first.
</concepts>

## <best_practices>
1.  **Modern Python**: Use Python 3.11+ features. Use `pyproject.toml` for configuration.
2.  **Type Safety**: Use strict type hints. Run `mypy` in strict mode.
3.  **Formatting**: Use `black` or `ruff` for auto-formatting.
4.  **Linting**: Use `ruff` for fast and comprehensive linting.
5.  **Testing**: Use `pytest` for testing. Avoid `unittest` style classes unless necessary.
6.  **Dependency Management**: Use `poetry` or `uv` for dependency management.
7.  **Virtual Environments**: Always use a virtual environment (`venv`, `.venv`) to isolate dependencies.
</best_practices>
