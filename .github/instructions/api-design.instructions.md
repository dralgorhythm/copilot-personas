# API Design Instructions
> **Apply To**: `openapi.yaml`, `swagger.json`, `**/*controller*`, `**/*route*`, `**/*.proto`

Guidelines for defining clear, consistent, and usable interfaces for software components, focusing on RESTful and GraphQL paradigms.

## <best_practices>
*   **Statelessness**: Each request from client to server must contain all of the information necessary to understand the request.
*   **Uniform Interface**: Resources are manipulated using a fixed set of operations (GET, POST, PUT, DELETE).
*   **Resource-Oriented**: URLs should identify resources (nouns), not actions (verbs).
*   **Versioning**: APIs must be versioned to allow evolution without breaking clients (e.g., URI Versioning `/v1/`, Header Versioning).
</best_practices>

## <concepts>
*   **Resource**: The fundamental unit of information (e.g., `User`, `Order`), identified by a URI.
*   **Idempotency**: The property that an operation can be applied multiple times without changing the result beyond the initial application (e.g., `PUT`, `DELETE`).
*   **Content Negotiation**: The mechanism for serving different representations of a resource (JSON, XML) based on client request headers.
*   **HATEOAS**: (Hypermedia As The Engine Of Application State) Including links in responses to guide clients through the API state machine.
</concepts>
