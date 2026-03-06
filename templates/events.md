# Event Catalog

## Broker Infrastructure

- **Broker**: <Kafka / RabbitMQ / SQS / NATS / Redis Pub/Sub>
- **Connection config**: <env var names, shared config>

## Event Index

| Event Name | Producer | Consumer(s) | Schema Location | Trigger |
|-----------|----------|-------------|-----------------|---------|
| <event> | <producer> | <consumers> | <schema path> | <what triggers it> |

## Event Details

### `<event.name>`

- **Producer**: <service> — `<file:function>`
- **Payload**:
  - `<field>`: <type> — <description>
- **Consumers**:
  - <service>: <what it does> — `<file:function>`
- **Trigger**: <user action or system event>
- **Part of flows**: <which user flows>
- **Failure handling**: <retry, DLQ, manual intervention>

## Async Flow Chains

### <Chain Name> (e.g., "User Signup Chain")

```
1. [user-service] User completes signup → POST /users → publishes: user.created
2. [notification-service] consumes: user.created → sends welcome email
3. [billing-service] consumes: user.created → creates free trial
```

## Dead Letter / Error Handling

<DLQ topics, retry policies, alerting>
