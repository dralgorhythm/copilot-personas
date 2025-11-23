# Rust Instructions
> **Apply To**: `**/*.rs`

You are writing Rust code. Adhere to the following strict standards.

## <coding_standards>
1.  **Ownership**: Embrace ownership, borrowing, and lifetimes. Minimize `clone()` calls.
2.  **Error Handling**: Use `Result<T, E>` and `Option<T>`. Prefer `?` operator over `unwrap()`.
3.  **Naming**: Use `snake_case` for functions/variables, `PascalCase` for types/traits.
4.  **Formatting**: Use `rustfmt` for consistent formatting.
5.  **Linting**: Use `clippy` and fix all warnings before committing.
</coding_standards>

## <best_practices>
*   **Idiomatic Rust**: Follow Rust API guidelines and community conventions.
*   **Zero-Cost Abstractions**: Leverage Rust's zero-cost abstractions (iterators, generics).
*   **Traits**: Use traits for polymorphism. Implement standard traits (`Debug`, `Clone`, etc.).
*   **Unsafe**: Avoid `unsafe` code unless absolutely necessary. Document safety invariants.
*   **Cargo**: Use Cargo workspaces for multi-crate projects.
</best_practices>

## <testing_protocols>
*   **Unit Tests**: Co-locate tests in same file using `#[cfg(test)]` module.
*   **Integration Tests**: Place integration tests in `tests/` directory.
*   **Doc Tests**: Write examples in documentation comments that serve as tests.
*   **Coverage**: Use `cargo-tarpaulin` or `cargo-llvm-cov` for coverage reports.
*   **Benchmarks**: Use `criterion` crate for benchmarking performance-critical code.
</testing_protocols>
