# Java Development Instructions

## <concepts>
1.  **Records**: Immutable data carriers introduced in Java 14+ (compact syntax for data classes).
2.  **Sealed Classes**: Restrict which classes can extend/implement (Java 17+), enabling exhaustive pattern matching.
3.  **Pattern Matching**: Enhanced `instanceof` and switch expressions for cleaner conditional logic.
4.  **Stream API**: Functional-style operations on collections (map, filter, reduce) for declarative code.
5.  **Optional**: Container for values that may be null, avoiding `NullPointerException`.
6.  **Dependency Injection**: Automatic wiring of dependencies, primarily via Spring's IoC container.
7.  **Bean Lifecycle**: Spring manages object creation, configuration, and destruction.
8.  **Aspect-Oriented Programming**: Cross-cutting concerns (logging, transactions) separated from business logic.
</concepts>

## <best_practices>
1.  **Modern Java**: Use the latest LTS version (currently Java 17 or 21). Use `var` for local variable type inference.
2.  **Immutability**: Prefer immutable objects (Records) and `final` variables.
3.  **Constructor Injection**: Use constructor injection for Spring beans instead of `@Autowired` on fields.
4.  **Lombok**: Use Lombok sparingly; prefer Records for data classes.
5.  **Testing**: Use JUnit 5 and Mockito. Write integration tests with `@SpringBootTest` and Testcontainers.
6.  **Logging**: Use SLF4J. Do not use `System.out.println`.
7.  **Exception Handling**: Use `@ControllerAdvice` for global exception handling in Spring Boot.
</best_practices>
