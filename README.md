# Pipedream (pipedream)

Pipedream is a developer-centric integration platform with three product lines: **Workflows** (code-level event-driven automation in Node.js, Python, Go, or Bash), **Connect** (embedded integration toolkit with managed OAuth for 3,000+ APIs and customer-facing trigger/action components), and a hosted **MCP server** that exposes 10,000+ tools across 2,800+ apps to AI agents over JSON-RPC. Pipedream announced an acquisition agreement with Workday on 2025-11-19.

**Source URL:** [`apis.yml`](https://raw.githubusercontent.com/api-evangelist/pipedream/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consuming
- **Access:** 3rd-Party
- **Segments:** ProCode API Composition, Workflows, Connect, MCP

## APIs

### Pipedream REST API
The unified REST surface at `api.pipedream.com` covering both the legacy workflow / source / subscription resources and the newer `/v1/connect/*` resources. Authentication via OAuth 2.0 client credentials or a short-lived Connect token. List endpoints use cursor pagination (limit, after, before). The full upstream OpenAPI 3.0.4 spec ships at `pipedream.com/docs/pipedream_openapi_swagger.json` (133 schemas, 61 operations).

- **Base URL:** `https://api.pipedream.com/v1`
- **Docs:** https://pipedream.com/docs/rest-api/
- **OpenAPI (local):** [`openapi/pipedream-openapi.yml`](openapi/pipedream-openapi.yml)
- **OpenAPI (upstream):** https://pipedream.com/docs/pipedream_openapi_swagger.json

### Pipedream Connect
End-to-end developer toolkit for embedding customer-facing integrations and AI-agent capabilities into applications. Managed OAuth for 3,000+ APIs, pre-built components (actions and triggers), a Connect Proxy that signs custom HTTP requests on behalf of end-users, a File Stash for working with user file uploads, deployed-trigger webhooks with signing keys, usage metering, and project-scoped resources with development and production environments.

- **Base URL:** `https://api.pipedream.com/v1/connect`
- **Docs:** https://pipedream.com/docs/connect
- **SDKs:** [TypeScript](https://github.com/PipedreamHQ/pipedream-sdk-typescript) · [Python](https://github.com/PipedreamHQ/pipedream-sdk-python) · [Java](https://github.com/PipedreamHQ/pipedream-sdk-java)

### Pipedream MCP Server
Hosted Model Context Protocol server at `remote.mcp.pipedream.net/v3` exposing 10,000+ tools across 2,800+ integrated apps to AI agents over JSON-RPC. Supports both SSE and streamable HTTP transports dynamically based on the `Accept` header; no client-side transport configuration required. Authentication is OAuth 2.0 Bearer; per-session context (project, environment, external user, app slug) is supplied via `x-pd-*` headers. Native integrations exist for OpenAI Responses API, Anthropic Claude, Google Gemini, and Vercel AI SDK.

- **Base URL:** `https://remote.mcp.pipedream.net/v3`
- **Docs:** https://pipedream.com/docs/connect/mcp
- **Server directory:** https://mcp.pipedream.com/
- **Reference chat:** https://chat.pipedream.com/
- **OpenAPI (local):** [`openapi/pipedream-mcp-openapi.yml`](openapi/pipedream-mcp-openapi.yml)

## Artifacts

| Folder | What's there |
|---|---|
| [`openapi/`](openapi/) | Two OpenAPI specs: full REST/Connect (61 operations, 133 schemas) + MCP server |
| [`capabilities/`](capabilities/) | 16 Naftiko capability YAMLs (one per tag/business surface) including `pipedream-mcp.yaml` |
| [`json-schema/`](json-schema/) | JSON Schemas for Account, App, AppCategory, Component, Project, ConnectToken, ConnectUsage |
| [`json-structure/`](json-structure/) | JSON Structure summaries for the same entities |
| [`json-ld/`](json-ld/) | JSON-LD context mapping Pipedream terms to schema.org |
| [`examples/`](examples/) | Request/response examples for list-apps, Connect tokens, accounts, run-action, deploy-trigger, OAuth, proxy, MCP `tools/list`, MCP `tools/call` |
| [`rules/`](rules/) | Spectral ruleset enforcing Pipedream conventions (Bearer auth, environment header, Title Case summaries, cursor pagination) |
| [`vocabulary/`](vocabulary/) | Domain vocabulary (workflows, connect, mcp, authentication, billing) |
| [`plans/`](plans/) | API Commons Plans 0.1 - Free / Basic ($29) / Advanced ($79) / Business |
| [`rate-limits/`](rate-limits/) | API Commons Rate Limits 0.1 - 60 req/min REST, 100 req/sec HTTP source, 5 MB event |
| [`finops/`](finops/) | FOCUS-aligned FinOps profile (credit-based subscription, monthly billing, USD) |
| [`blogs/`](blogs/) | Cached posts including the 2025-11-19 Workday acquisition announcement |

## SDKs and Tooling (PipedreamHQ org)

| Repo | Purpose | Stars |
|---|---|---|
| [`pipedream`](https://github.com/PipedreamHQ/pipedream) | Components / integrations monorepo | 11,400+ |
| [`mcp-chat`](https://github.com/PipedreamHQ/mcp-chat) | Reference MCP agent app | 184+ |
| [`pipedream-connect-examples`](https://github.com/PipedreamHQ/pipedream-connect-examples) | SDK example apps | 25+ |
| [`pipedream-sdk-typescript`](https://github.com/PipedreamHQ/pipedream-sdk-typescript) | TypeScript SDK | - |
| [`pipedream-sdk-python`](https://github.com/PipedreamHQ/pipedream-sdk-python) | Python SDK | - |
| [`pipedream-sdk-java`](https://github.com/PipedreamHQ/pipedream-sdk-java) | Java SDK | - |
| [`pipedream-go`](https://github.com/PipedreamHQ/pipedream-go) | Go runtime helpers | - |
| [`homebrew-pd-cli`](https://github.com/PipedreamHQ/homebrew-pd-cli) | Homebrew formula for the Pipedream CLI | - |
| [`eslint-plugin-pipedream`](https://github.com/PipedreamHQ/eslint-plugin-pipedream) | ESLint plugin for components | - |

## Common Properties

- [Portal](https://pipedream.com/)
- [Documentation](https://pipedream.com/docs)
- [Getting Started](https://pipedream.com/docs/quickstart/)
- [Authentication](https://pipedream.com/docs/rest-api/auth)
- [Blog](https://pipedream.com/blog/)
- [Changelog](https://pipedream.com/docs/changelog)
- [Status](https://status.pipedream.com/) · [Atom feed](https://status.pipedream.com/history.atom)
- [Pricing](https://pipedream.com/pricing/)
- [Forum](https://pipedream.com/community/)
- [Support](https://pipedream.com/support)
- [GitHub Org](https://github.com/PipedreamHQ)
- [Acquisition Announcement (Workday, 2025-11-19)](https://pipedream.com/blog/pipedream-to-be-acquired-by-workday/)

## Timestamps

- **Created:** 2026-03-03
- **Modified:** 2026-05-22

## Maintainers

- **FN:** Kin Lane
- **Email:** kin@apievangelist.com
