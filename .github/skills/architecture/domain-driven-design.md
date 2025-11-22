# Skill: Domain-Driven Design (DDD)

## Description
Modeling software to match a domain (Entities, Aggregates, Bounded Contexts).

## Triggers
*   Keywords: "ddd", "domain driven", "bounded context", "aggregate", "entity", "value object", "ubiquitous language"
*   Context: Designing complex business logic or breaking down a monolith.

## Concepts
*   **Bounded Context**: Explicit boundary within which a domain model exists.
*   **Ubiquitous Language**: Common language shared by developers and domain experts.
*   **Aggregate**: Cluster of domain objects that can be treated as a single unit.
*   **Entity**: Object defined by its identity.
*   **Value Object**: Object defined by its attributes (immutable).

## Tool Affordances
### Scaffold Bounded Context
Description: Creates a standard directory structure for a new Bounded Context.
```bash
#!/bin/bash
# scaffold-bounded-context.sh
# Usage: ./scaffold-bounded-context.sh <ContextName>
# Creates a standard DDD directory structure for a Bounded Context.

CONTEXT_NAME=$1

if [ -z "$CONTEXT_NAME" ]; then
  echo "Usage: $0 <ContextName>"
  exit 1
fi

echo "Scaffolding Bounded Context: $CONTEXT_NAME"

mkdir -p "src/$CONTEXT_NAME/domain/model"
mkdir -p "src/$CONTEXT_NAME/domain/service"
mkdir -p "src/$CONTEXT_NAME/application/service"
mkdir -p "src/$CONTEXT_NAME/infrastructure/repository"
mkdir -p "src/$CONTEXT_NAME/infrastructure/api"
mkdir -p "src/$CONTEXT_NAME/tests"

touch "src/$CONTEXT_NAME/README.md"

echo "Done. Structure created in src/$CONTEXT_NAME"
```

## Reference Implementation
### Aggregate Root Pattern
```typescript
// Generic Aggregate Root with Event Sourcing capabilities
abstract class AggregateRoot {
  private _domainEvents: IDomainEvent[] = [];

  protected addDomainEvent(event: IDomainEvent): void {
    this._domainEvents.push(event);
  }

  public get domainEvents(): IDomainEvent[] {
    return this._domainEvents;
  }

  public clearDomainEvents(): void {
    this._domainEvents = [];
  }
}

// Example Usage
class Order extends AggregateRoot {
  private items: OrderItem[] = [];
  private status: OrderStatus;

  constructor(public readonly id: string) {
    super();
    this.status = OrderStatus.Created;
  }

  public addItem(item: OrderItem): void {
    this.items.push(item);
    this.addDomainEvent(new OrderItemAdded(this.id, item));
  }
}
```

## Libraries
*   **Java**: Spring Data JDBC (Aggregates), jMolecules
*   **C#**: MediatR (CQRS), Ardalis.Specification
*   **TypeScript**: NestJS (Modules as Contexts)
*   **Python**: Cosmic Python patterns

## Resources
*   [Value Object Template](./resources/value-object-template.md)

