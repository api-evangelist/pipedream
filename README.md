# Pipedream (pipedream)

Pipedream is a developer-centric integration platform providing three product lines: Workflows (code-level event-driven automation in Node.js/Python/Go/Bash), Connect (an embedded integration toolkit for adding customer-facing integrations and AI agents to applications, with managed OAuth for 3,000+ APIs), and a hosted MCP server exposing 10,000+ tools over JSON-RPC for AI agents. Pipedream announced an acquisition agreement with Workday on 2025-11-19.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/pipedream/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/pipedream/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- ProCode_API_Composition
- Workflows
- Connect
- MCP
- Embedded Integrations
- Managed Auth
- AI Agents

## Timestamps

- **Created:** 2026-03-03
- **Modified:** 2026-05-22

## APIs

### Pipedream REST API

The Pipedream REST API at api.pipedream.com is the unified surface for both the legacy workflow / source / subscription resources and the newer /v1/connect/* resources. Authentication is via OAuth 2.0 client credentials or a short-lived Connect token. List endpoints use cursor pagination (limit, after, before). The full OpenAPI 3.0.4 spec is published at pipedream.com/docs/pipedream_openapi_swagger.json (133 schemas, 61 operations as of 2026-05-22).

- **Human URL:** [https://pipedream.com/docs/rest-api/](https://pipedream.com/docs/rest-api/)
- **Base URL:** `https://api.pipedream.com/v1`

#### Tags

- Apps
- App Categories
- OAuth
- Connect
- Accounts
- Components
- Actions
- Triggers
- Deployed Triggers
- Webhooks
- Projects
- Proxy
- File Stash
- Tokens
- Usage
- Users

#### Properties

- [Documentation](https://pipedream.com/docs/rest-api/)
- [Authentication](https://pipedream.com/docs/rest-api/auth)
- [OpenAPI](https://raw.githubusercontent.com/api-evangelist/pipedream/refs/heads/main/openapi/pipedream-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Open A P I Upstream](https://pipedream.com/docs/pipedream_openapi_swagger.json)
- [Spectral Rules](rules/pipedream-rules.yml)
- [JSON Schema](json-schema/pipedream-app-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/pipedream-account-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/pipedream-component-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/pipedream-project-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/pipedream-connecttoken-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/pipedream-connectusage-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/pipedream-app-structure.json)
- [Example](examples/pipedream-list-apps-example.json)
- [Example](examples/pipedream-create-connect-token-example.json)
- [Example](examples/pipedream-list-accounts-example.json)
- [Example](examples/pipedream-run-action-example.json)
- [Example](examples/pipedream-deploy-trigger-example.json)
- [Example](examples/pipedream-oauth-token-example.json)
- [Example](examples/pipedream-proxy-request-example.json)
- [Postman Collection](collections/pipedream-mcp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/pipedream-mcp.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/pipedream.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/pipedream.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Pipedream Connect

Pipedream Connect is the end-to-end developer toolkit for embedding customer-facing integrations and AI-agent capabilities into applications. It provides managed OAuth for 3,000+ APIs, pre-built components (actions and triggers), a Connect Proxy that signs custom HTTP requests on behalf of end-users, a File Stash for working with user file uploads, deployed-trigger webhooks, usage metering, and project-scoped resources with development and production environments. Endpoints live under /v1/connect/* on api.pipedream.com.

- **Human URL:** [https://pipedream.com/docs/connect](https://pipedream.com/docs/connect)
- **Base URL:** `https://api.pipedream.com/v1/connect`

#### Tags

- Connect
- Embedded Integrations
- Managed Auth
- AI Agents
- Proxy
- Webhooks

#### Properties

- [Documentation](https://pipedream.com/docs/connect)
- [Getting Started](https://pipedream.com/docs/connect/quickstart)
- [S D Ks](https://pipedream.com/docs/connect/api-reference/sdks)
- [OpenAPI](https://raw.githubusercontent.com/api-evangelist/pipedream/refs/heads/main/openapi/pipedream-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [SDK](https://github.com/PipedreamHQ/pipedream-sdk-typescript)
- [SDK](https://github.com/PipedreamHQ/pipedream-sdk-python)
- [SDK](https://github.com/PipedreamHQ/pipedream-sdk-java)
- [Samples Repo](https://github.com/PipedreamHQ/pipedream-connect-examples)
- [Postman Collection](collections/pipedream-mcp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/pipedream-mcp.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/pipedream.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/pipedream.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Pipedream MCP Server

Pipedream's hosted Model Context Protocol server at remote.mcp.pipedream.net exposes 10,000+ tools across 2,800+ integrated apps to AI agents over JSON-RPC. The server supports both SSE and streamable HTTP transports dynamically based on the Accept header, with no client-side configuration required. Authentication is OAuth 2.0 Bearer; per-session context (project, environment, external user, app slug) is supplied via x-pd-* headers. Native integrations exist for OpenAI Responses API, Anthropic Claude, Google Gemini, and Vercel AI SDK.

- **Human URL:** [https://pipedream.com/docs/connect/mcp/developers](https://pipedream.com/docs/connect/mcp/developers)
- **Base URL:** `https://remote.mcp.pipedream.net/v3`

#### Tags

- MCP
- AI Agents
- Tool Calling
- JSON-RPC

#### Properties

- [Documentation](https://pipedream.com/docs/connect/mcp)
- [Documentation](https://pipedream.com/docs/connect/mcp/developers)
- [Documentation](https://pipedream.com/docs/connect/mcp/openai)
- [Server Directory](https://mcp.pipedream.com/)
- [Chat Client](https://chat.pipedream.com/)
- [OpenAPI](https://raw.githubusercontent.com/api-evangelist/pipedream/refs/heads/main/openapi/pipedream-mcp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Samples Repo](https://github.com/PipedreamHQ/mcp-chat)
- [Example](examples/pipedream-mcp-tools-list-example.json)
- [Example](examples/pipedream-mcp-tools-call-example.json)
- [Postman Collection](collections/pipedream-mcp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/pipedream-mcp.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Postman Collection](collections/pipedream.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/pipedream.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Arazzo Workflows](arazzo/) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)
- [Portal](https://pipedream.com/)
- [Documentation](https://pipedream.com/docs)
- [Getting Started](https://pipedream.com/docs/quickstart/)
- [Authentication](https://pipedream.com/docs/rest-api/auth)
- [OpenAPI](https://pipedream.com/docs/pipedream_openapi_swagger.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Blog](https://pipedream.com/blog/)
- [Changelog](https://pipedream.com/docs/changelog)
- [Status Page](https://status.pipedream.com/)
- [Status Feed](https://status.pipedream.com/history.atom)
- [Support](https://pipedream.com/support)
- [Forum](https://pipedream.com/community/)
- [Pricing](https://pipedream.com/pricing/)
- [Sign Up](https://pipedream.com/auth/signup)
- [Login](https://pipedream.com/auth/login)
- [Terms of Service](https://pipedream.com/terms)
- [Privacy Policy](https://pipedream.com/privacy)
- [Security](https://pipedream.com/docs/privacy-and-security)
- [LinkedIn](https://www.linkedin.com/company/pipedreamhq)
- [Git Hub Org](https://github.com/PipedreamHQ)
- [Source Repo](https://github.com/PipedreamHQ/pipedream)
- [SDK](https://github.com/PipedreamHQ/pipedream-sdk-typescript)
- [SDK](https://github.com/PipedreamHQ/pipedream-sdk-python)
- [SDK](https://github.com/PipedreamHQ/pipedream-sdk-java)
- [SDK](https://github.com/PipedreamHQ/pipedream-go)
- [C L I](https://github.com/PipedreamHQ/homebrew-pd-cli)
- [Samples Repo](https://github.com/PipedreamHQ/pipedream-connect-examples)
- [Samples Repo](https://github.com/PipedreamHQ/mcp-chat)
- [Plans](plans/pipedream-plans-pricing.yml)
- [Rate Limits](rate-limits/pipedream-rate-limits.yml)
- [Fin Ops](finops/pipedream-finops.yml)
- [J S O N L D Context](json-ld/pipedream-context.jsonld)
- [Vocabulary](vocabulary/pipedream-vocabulary.yml)
- [Spectral Rules](rules/pipedream-rules.yml)
- [Acquisition Announcement](https://pipedream.com/blog/pipedream-to-be-acquired-by-workday/)
- [Features](undefined)
- [L L Ms Txt](https://pipedream.com/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
