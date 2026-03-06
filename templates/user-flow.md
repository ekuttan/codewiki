# <Flow Name>

## User Story

> As a <user type>, I want to <action> so that <benefit>.

## Entry Point

<How the user starts this flow>

## Steps

1. **<Step name>**
   - Screen/Page: <route or screen>
   - User action: <what the user does>
   - API call: <endpoint triggered>
   - Service chain: <service A → service B → service C> (microservices only)
   - Data changed: <what gets created/modified, in which service's DB>

2. **<Step name>**
   ...

## Async Side-Effects (microservices only)

| Trigger | Event | Consumer | Effect |
|---------|-------|----------|--------|
| <which step> | <event name> | <consumer service> | <what happens> |

## Error States

- <error scenario and handling>
- <microservices: what if service X is down during step Y>

## Permissions

- <role requirements>

## Related Code

- Frontend: <key files>
- Backend: <key files/services>
- Models: <relevant models and owner service>
