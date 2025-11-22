# Skill: API Design

## Description

The ability to define clear, consistent, and usable interfaces for software components, focusing on RESTful and GraphQL paradigms.

## Triggers

* **Keywords**: "api", "rest", "graphql", "endpoint", "contract", "swagger", "openapi", "grpc"
* **Context**: Creating new services, modifying existing endpoints, integrating with third-party systems, defining service contracts.

## Core Knowledge

### Concepts

* **Resource**: The fundamental unit of information (e.g., `User`, `Order`), identified by a URI.
* **Idempotency**: The property that an operation can be applied multiple times without changing the result beyond the initial application (e.g., `PUT`, `DELETE`).
* **Content Negotiation**: The mechanism for serving different representations of a resource (JSON, XML) based on client request headers.
* **HATEOAS**: (Hypermedia As The Engine Of Application State) Including links in responses to guide clients through the API state machine.

### Principles

* **Statelessness**: Each request from client to server must contain all of the information necessary to understand the request.
* **Uniform Interface**: Resources are manipulated using a fixed set of operations (GET, POST, PUT, DELETE).
* **Resource-Oriented**: URLs should identify resources (nouns), not actions (verbs).
  * *Good*: `POST /users` (Create a user)
  * *Bad*: `POST /createUser`
* **Versioning**: APIs must be versioned to allow evolution without breaking clients (e.g., URI Versioning `/v1/`, Header Versioning).

## Actionable Affordances

### Tool Affordances

#### Scaffold OpenAPI Specification

Creates a standard OpenAPI 3.0 boilerplate for a new service.

```bash
#!/bin/bash
# scaffold-openapi.sh
# Usage: ./scaffold-openapi.sh <ServiceName>
# Creates a basic openapi.yaml for a new service.

SERVICE_NAME=$1

if [ -z "$SERVICE_NAME" ]; then
  echo "Usage: $0 <ServiceName>"
  exit 1
fi

FILENAME="openapi.yaml"

if [ -f "$FILENAME" ]; then
  echo "Error: $FILENAME already exists."
  exit 1
fi

cat <<EOF > "$FILENAME"
openapi: 3.0.3
info:
  title: $SERVICE_NAME API
  description: API definition for $SERVICE_NAME
  version: 1.0.0
servers:
  - url: https://api.example.com/v1
paths:
  /health:
    get:
      summary: Health Check
      responses:
        '200':
          description: Service is healthy
          content:
            application/json:
              schema:
                type: object
                properties:
                  status:
                    type: string
                    example: "ok"
components:
  schemas:
    Error:
      type: object
      properties:
        code:
          type: integer
        message:
          type: string
EOF

echo "Created $FILENAME for $SERVICE_NAME"
```

### Reference Implementation

#### Standard REST Controller Pattern (TypeScript)

```typescript
import { Request, Response } from 'express';

// 1. Use DTOs for input validation
interface CreateUserDto {
  username: string;
  email: string;
}

export class UserController {
  
  // 2. Standard HTTP Methods
  public async createUser(req: Request, res: Response): Promise<void> {
    try {
      const dto: CreateUserDto = req.body;
      
      // 3. Business Logic Delegation
      const user = await this.userService.create(dto);
      
      // 4. Correct Status Code (201 Created) & Location Header
      res.status(201)
         .header('Location', `/users/${user.id}`)
         .json(user);
         
    } catch (error) {
      // 5. Centralized Error Handling
      if (error instanceof ValidationError) {
        res.status(400).json({ code: 400, message: error.message });
      } else {
        res.status(500).json({ code: 500, message: "Internal Server Error" });
      }
    }
  }
}
```

### Libraries

* **TypeScript/Node**: NestJS (First-class OpenAPI support), Express, Fastify.
* **Python**: FastAPI (Auto-generates Swagger), Flask, Django REST Framework.
* **Java**: Spring Boot (Spring Web MVC), Micronaut.
* **C#**: ASP.NET Core Web API.
* **Go**: Gin, Echo.

## Checklist

* [ ] **Nouns not Verbs**: Are endpoints named after resources?
* [ ] **Pluralization**: Are collection resources plural (e.g., `/users`)?
* [ ] **Status Codes**: Are 2xx, 4xx, and 5xx codes used correctly?
* [ ] **Security**: Is TLS enforced? Are sensitive headers (Auth) handled?
* [ ] **Pagination**: Is pagination implemented for list endpoints?
* [ ] **Filtering/Sorting**: Are query parameters used for filtering?
