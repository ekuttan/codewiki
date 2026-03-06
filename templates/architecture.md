# Architecture

## System Overview

<Text-based architecture diagram using ASCII or description>

## Architecture Type

<Single app / Modular monolith / Microservices / Monorepo with shared packages>

## Components

### <Component Name>

- **Tech stack**: <languages, frameworks, key libraries>
- **Location**: <directory path>
- **Entry point**: <main file>
- **Purpose**: <what it does>
- **Owns data**: <database/tables owned> (microservices only)
- **Exposes**: <external API / internal API / events> (microservices only)

## Component Communication

<How components talk — API calls, message queues, shared DB, etc.>
<For microservices, reference service-map.md and events.md>

## Shared Infrastructure

<Databases, message brokers, caches, CDNs, object storage>

## Authentication & Authorization

<How auth works across the system. For microservices: token propagation, where auth is enforced, service-to-service auth>

## Data Flow

<How data moves through the system for key operations>
