# Go Development Instructions

## <concepts>
1.  **Goroutines**: Lightweight threads managed by Go runtime for concurrent execution.
2.  **Channels**: Typed conduits for communication between goroutines following "share memory by communicating" principle.
3.  **Interfaces**: Implicit contracts defined by method sets, enabling polymorphism without inheritance.
4.  **Error as Values**: Errors are returned as values (`error` type) rather than thrown as exceptions.
5.  **Defer**: Schedule function calls to execute after surrounding function returns (cleanup, unlocking).
6.  **Composition**: Building complex types by embedding simpler types rather than inheritance.
7.  **Zero Values**: Variables have useful default values (0 for numbers, "" for strings, nil for pointers).
8.  **Receiver Methods**: Methods attached to types via receivers, can be value or pointer receivers.
</concepts>

## <best_practices>
1.  **Project Layout**: Follow the standard Go project layout (`cmd/`, `internal/`, `pkg/`).
2.  **Error Handling**: Always check errors. Wrap errors with context using `fmt.Errorf("%w", err)`.
3.  **Context**: Pass `context.Context` as the first argument to functions that cross API boundaries or involve I/O.
4.  **Concurrency**: Use `sync.WaitGroup` or `errgroup` to manage goroutine lifecycles. Avoid leaking goroutines.
5.  **Linting**: Use `golangci-lint` with a comprehensive configuration.
6.  **Testing**: Write table-driven tests. Use `t.Parallel()` for independent tests.
7.  **Dependency Management**: Use Go Modules (`go.mod`, `go.sum`) for dependency management.
</best_practices>
