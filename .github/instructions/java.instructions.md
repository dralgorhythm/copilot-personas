# Java Development Instructions
> **Apply To**: `**/*.java`

You are writing Java code following the 2025 Golden Path for Enterprise. Adhere to the following strict standards.

## <coding_standards>
1.  **Runtime**: Use **Java 25 (LTS)**. Enable **Generational ZGC** for low-latency garbage collection.
2.  **Concurrency**: Use **Virtual Threads** (Project Loom). Replace reactive stacks with blocking, virtual-threaded code.
3.  **Framework**: Use **Spring Boot 4** for general applications. Use **Quarkus** for serverless/native image support.
4.  **Build Tool**: Use **Maven 4** (Consumer/Build POM separation) or **Gradle 9** (Configuration Cache).
5.  **Immutability**: Prefer immutable objects (Records) and `final` variables.
</coding_standards>

## <best_practices>
*   **Modern Java**: Use latest LTS features. Use `var` for local variable type inference where it improves readability.
*   **Constructor Injection**: Use constructor injection for Spring beans instead of `@Autowired` on fields.
*   **Lombok**: Use Lombok sparingly; prefer Records for data classes.
*   **Testing**: Use JUnit 5 and Mockito. Write integration tests with `@SpringBootTest` and Testcontainers.
*   **Logging**: Use SLF4J with Logback. Do not use `System.out.println`.
*   **Exception Handling**: Use `@ControllerAdvice` for global exception handling in Spring Boot.
*   **Security**: Generate **CycloneDX** SBOM in every build for supply chain security.
</best_practices>

## <testing_protocols>
*   **Unit Tests**: Use JUnit 5 with `@Test` annotations. Use Mockito for mocking.
*   **Integration Tests**: Use `@SpringBootTest` with Testcontainers for real dependencies.
*   **Coverage**: Maintain high test coverage. Use JaCoCo for coverage reporting.
*   **Virtual Threads**: Test concurrent code with Virtual Threads enabled.
</testing_protocols>

## <tooling>
*   **Build Tool**: **Maven 4** or **Gradle 9**
*   **Test Framework**: JUnit 5
*   **Mocking**: Mockito
*   **SBOM**: **CycloneDX** plugin for Maven/Gradle
*   **GC**: Enable Generational ZGC with `-XX:+UseZGC -XX:+ZGenerational`
</tooling>

## <concepts>
1.  **Records**: Immutable data carriers introduced in Java 14+ (compact syntax for data classes).
2.  **Sealed Classes**: Restrict which classes can extend/implement (Java 17+), enabling exhaustive pattern matching.
3.  **Pattern Matching**: Enhanced `instanceof` and switch expressions for cleaner conditional logic.
4.  **Stream API**: Functional-style operations on collections (map, filter, reduce) for declarative code.
5.  **Optional**: Container for values that may be null, avoiding `NullPointerException`.
6.  **Virtual Threads**: Lightweight threads (Project Loom) that enable high-concurrency blocking code.
7.  **Dependency Injection**: Automatic wiring of dependencies, primarily via Spring's IoC container.
8.  **Bean Lifecycle**: Spring manages object creation, configuration, and destruction.
</concepts>
