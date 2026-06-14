# Pipedream GraphQL Schema

## Overview

This is a conceptual GraphQL schema for the Pipedream developer-first workflow automation platform. Pipedream exposes its capabilities today via a REST API at `api.pipedream.com/v1` and a hosted MCP server at `remote.mcp.pipedream.net/v3`. This schema models the same domain — workflows, triggers, actions, sources, components, Connect, auth, usage, and the registry — as a unified GraphQL surface.

Pipedream does not currently publish a public GraphQL endpoint. This schema is derived from the REST API reference (https://pipedream.com/docs/rest-api/), the OpenAPI 3.0.4 specification, and the public component monorepo (https://github.com/PipedreamHQ/pipedream). It is intended as a conceptual reference for teams evaluating Pipedream's data model or planning a GraphQL wrapper.

## Schema Source

- REST API Reference: https://pipedream.com/docs/rest-api/
- OpenAPI Spec (upstream): https://pipedream.com/docs/pipedream_openapi_swagger.json
- Component Monorepo: https://github.com/PipedreamHQ/pipedream
- Connect Documentation: https://pipedream.com/docs/connect
- MCP Documentation: https://pipedream.com/docs/connect/mcp

## Core Domain Areas

### Workflows and Steps

Pipedream workflows are event-driven automation sequences composed of a trigger step followed by one or more action or code steps. Each step has typed props, a version, and runtime execution metadata.

Types: `Workflow`, `Step`, `Trigger`, `Action`, `CodeStep`, `StepResult`, `StepExecution`

### Sources and Events

Sources are deployed event-producing components. They emit events into Pipedream's event store, which workflows and subscribers can consume. Events carry a raw body, headers, and a normalized payload.

Types: `Source`, `EventSource`, `Event`, `EventHistory`, `EventStore`, `LiveEvent`, `TestEvent`, `Emit`

### Executions and Logs

Every workflow run produces an Execution record with status, timing, credit consumption, and per-step log output.

Types: `Execution`, `ExecutionStatus`, `Log`, `LogEntry`

### Components and Registry

Pipedream maintains an open-source registry of 10,000+ pre-built actions and triggers (the component monorepo). Each component has a versioned key, configurable props, and an optional OAuth app association.

Types: `Component`, `ComponentVersion`, `Registry`, `ComponentProp`, `PropOption`, `DeployedComponent`

### Apps and Auth

Apps are the 3,000+ third-party services Pipedream integrates with. Each app has an auth strategy (OAuth 2.0 or API key), scopes, and per-user account credentials stored securely.

Types: `App`, `AppAuth`, `AppCategory`, `OAuth2`, `APIKey`, `Account`, `OAuthToken`

### Connect

Pipedream Connect is the embedded-integration toolkit. It mints short-lived tokens for end users, manages their linked accounts, proxies signed HTTP requests, and tracks per-project usage.

Types: `ConnectToken`, `ExternalUser`, `Project`, `Environment`, `ConnectProxy`, `FileStash`, `ConnectUsage`

### Webhooks and Subscriptions

Deployed triggers emit events; those events can be routed to webhook endpoints or to Pipedream workflows via subscription records.

Types: `WebhookEndpoint`, `Subscription`, `DeployedTrigger`, `TriggerWebhook`, `WorkflowBinding`

### Users, Teams, and Workspaces

Pipedream's identity layer covers individual users, workspaces (formerly teams), API keys, and secrets/environment variables.

Types: `User`, `Workspace`, `Team`, `Key`, `Secret`, `Token`, `ApiCredential`

### Usage and Billing

Pipedream's credit-based billing model is surfaced via usage records keyed by project and environment. Audit logs record control-plane events.

Types: `Usage`, `CreditRecord`, `Billing`, `Plan`, `Audit`, `AuditEvent`

### Streams

Stream types expose paginated list results with cursor-based pagination, mirroring the `limit/after/before` model of the REST API.

Types: `Stream`, `PageInfo`, `Edge`

## Query Capabilities

The schema supports:

- Fetching a single workflow, source, component, app, or account by ID
- Listing resources with cursor pagination
- Filtering components by app slug, trigger/action type, and version
- Searching apps by name or category
- Retrieving execution history and log output for a workflow run
- Pulling Connect usage records by project, environment, and date range
- Introspecting deployed triggers and their event queues

## Mutation Capabilities

The schema supports:

- Creating, updating, and deleting workflows and steps
- Deploying and pausing sources and triggers
- Creating Connect tokens for external users
- Linking and unlinking app accounts
- Minting and rotating API keys and webhook signing keys
- Managing environment variables (secrets) by workspace and project
- Running component actions on behalf of external users
- Proxying signed HTTP requests through Connect Proxy

## Subscription Capabilities

The schema models real-time subscriptions for:

- Live events emitted by a deployed source
- Execution status updates for a running workflow
- Audit log entries in a workspace

## Authentication

All queries require a Bearer token. Pipedream issues OAuth 2.0 client-credential tokens for server-side use and short-lived Connect tokens for end-user sessions. The `x-pd-project-id`, `x-pd-environment`, and `x-pd-external-user-id` headers map to `project`, `environment`, and `externalUserId` arguments on Connect-scoped fields.

## Schema File

See `pipedream-schema.graphql` in this directory for the full type definitions.
