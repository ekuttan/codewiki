# Service Map

## Services Overview

| Service | Tech Stack | Port | Type | Owns DB | Location |
|---------|-----------|------|------|---------|----------|
| <n> | <lang/framework> | <port> | external/internal | <db name or "no"> | <directory> |

## Service Dependency Graph

<ASCII diagram showing call directions>

```
[Frontend] → [API Gateway] → [User Service] → [Users DB]
                           → [Payment Service] → [Payments DB]
                                               → publishes: payment.completed
                           → [Notification Service] ← consumes: payment.completed, user.created
```

## Synchronous Communication

| Caller | Callee | Protocol | Purpose |
|--------|--------|----------|---------|
| <caller> | <callee> | REST/gRPC | <purpose> |

## Async Communication (Events & Messages)

| Event/Topic | Producer | Consumer(s) | Broker | Purpose |
|-------------|----------|-------------|--------|---------|
| <event> | <producer> | <consumers> | <broker> | <purpose> |

## Data Ownership

| Service | Database | Key Tables/Collections | Shared? |
|---------|----------|----------------------|---------|
| <service> | <db> | <tables> | <"No — access via API" or describe> |

## Service Discovery

<How services find each other: docker-compose DNS, env vars, consul, etc.>

## Resilience Patterns

<Retries, circuit breakers, dead letter queues, saga patterns — if detected. "None detected" if not found.>
