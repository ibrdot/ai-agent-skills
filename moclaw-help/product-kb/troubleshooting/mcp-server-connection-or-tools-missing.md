---
id: moclaw.troubleshooting.mcp_server_connection_or_tools_missing
title: MCP Server Connection Or Tools Missing
type: troubleshooting
product_area: connectors
audience: support
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/src/components/connectors/mcp-connector.tsx
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/server/app-server/app/domains/connector/mcp_router.py
  - maxgent/server/app-server/app/domains/connector/mcp_schema.py
  - maxgent/server/app-server/app/domains/connector/services/mcp_access.py
  - maxgent/server/app-server/app/domains/connector/services/mcp_security.py
  - maxgent/server/app-server/app/domains/connector/services/mcp_client.py
  - maxgent/server/app-server/app/domains/connector/services/mcp_hub.py
  - maxgent/server/app-server/app/domains/connector/services/skills/mcp-hub/SKILL.md
  - product-kb/how-to/manage-mcp-servers.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# MCP Server Connection Or Tools Missing

## Symptom

The user cannot see the **MCP** connector row, cannot save a server, sees an MCP
server in **Draft**, **Testing**, **Error**, or **Disabled**, test/sync fails,
tool count stays at `0`, or the AI cannot find tools from a configured MCP
server.

## Direct Answer

Current MCP management is for **remote HTTPS Streamable HTTP MCP servers** when
the MCP connector is enabled for the user's account/environment. A server must
test/sync successfully and have at least one usable tool before MoClaw can expose
it to the agent.

## How MCP Availability Works

- The **MCP** connector row may be account/environment gated and is not proven
  by old docs alone.
- When visible, the management dialog lives at **left sidebar > Connectors >
  MCP > Manage**.
- Adding a server creates a draft configuration.
- **Test** fetches tools without necessarily activating a draft server.
- **Refresh/Sync** fetches tools and can activate the server.
- **Enable** requires a synced usable tool cache.
- **Disable** keeps the configuration but stops exposing it.
- **Delete** removes the server from the user's active management list.
- Agent context receives active server ids/names first; the agent should inspect
  a server and tool schema before calling tools.

## Endpoint Requirements

- Endpoint URL must use `https`.
- Endpoint host must resolve publicly.
- Endpoint must not point to `localhost`, private/reserved IP ranges, or cloud
  metadata addresses.
- Endpoint URL must not include username/password or a URL fragment.
- Redirects are rejected.
- V1 expects Streamable HTTP JSON responses; streaming/SSE responses are not
  supported in current MCP calls.
- A single remote response is capped; very large tool lists or tool schemas can
  fail sync.
- Current sync supports up to 200 tools and caps synced tool descriptions,
  schemas, annotations, and total tool-cache size.

## Supported Auth Modes

- None.
- Bearer token.
- API key in a header.
- API key in a query parameter.

API key body injection is not supported for standard MCP JSON-RPC. The current
web UI does not represent arbitrary local command-line or stdio MCP server
configs.

## Save, Test, Sync, Enable

| Step | Support Meaning |
|---|---|
| Save | Creates or updates a draft configuration. This does not expose tools to the agent. |
| Test | Fetches tools to verify endpoint and auth behavior. A successful test can leave a draft/error server inactive and does not guarantee all future calls will succeed. |
| Refresh/Sync | Fetches and caches usable tools; successful sync can activate the server. |
| Enable | Requires an existing synced usable tool cache. |
| Disable | Keeps the config but stops exposing tools. |
| Delete | Removes the server from the user's active management list. |

## Tool Call Statuses

After a server is active, an individual tool call can still fail or require
another step:

| Status | Meaning |
|---|---|
| `needs_input` | Required tool input is missing. Ask the user for the missing non-secret field or retry with a fuller prompt. |
| `needs_confirmation` | The tool may write or destructively change external state and needs confirmation before calling. |
| `auth_required` | The remote MCP server returned an auth failure; the user should verify auth mode/secret in the MCP dialog, not paste the secret into support chat. |
| `stream_not_supported` | The requested streaming MCP path is not supported in V1. |
| `failed` | The remote endpoint, input schema, URL policy, network, timeout, response format, or remote MCP error blocked the call. |

## Likely Causes

- MCP is hidden because the account/environment is not enabled for MCP preview.
- The user is trying to add a local command-line/stdio MCP config.
- The URL is `http`, localhost, private network, DNS-unresolvable, redirects, or
  includes forbidden URL userinfo/fragments.
- The selected auth mode, header/query name, or token is wrong.
- The remote server returns 401/403, invalid JSON, streaming responses, no tools,
  too many tools, oversized schemas, or times out.
- The server is disabled or has not been synced after edits.
- The AI is asked to use a server before the server is active with a nonzero tool
  count.
- The tool call is missing required input, needs confirmation for a write or
  destructive action, or the remote server requires updated auth.

## Recovery Steps

1. Ask the user to open **left sidebar > Connectors** and check whether **MCP**
   is visible.
2. If the MCP row is missing, explain that MCP availability depends on
   account/environment and collect account email for support.
3. If the row is visible, open **MCP > Manage**.
4. Confirm the server is a remote HTTPS Streamable HTTP MCP endpoint, not a
   local command-line config.
5. Check auth mode and secret placement. Do not ask the user to paste the secret
   into chat.
6. Save the server, then run **Test**.
7. If **Test** succeeds, run **Refresh/Sync** and confirm the server is
   **Active** with `tool_count > 0`.
8. If status is **Error**, use the visible `last_error` copy to identify whether
   it is URL policy, DNS, auth, timeout, invalid response, empty tools, or size
   limits.
9. If the server is **Disabled**, enable it after successful sync.
10. Ask the user to retry the prompt after sync/enable completes.
11. If the tool call says `needs_input`, ask for the missing non-secret input
    and retry.
12. If the tool call says `needs_confirmation`, explain the external-state
    change and ask the user to confirm before retrying.
13. If the tool call says `auth_required`, ask the user to update the auth mode
    or secret inside the MCP dialog. Do not collect the secret in support chat.

## Escalate When

- MCP should be enabled for the account, but the row is missing.
- A public HTTPS endpoint repeatedly fails test/sync with unclear `last_error`.
- The server is active with a nonzero tool count, but the agent cannot discover
  or call the tools.
- The remote server returns auth failures even after the user verifies auth mode
  and secret placement.
- Tool calls require confirmation, missing input, or return errors that the user
  cannot resolve from the visible message.

Collect account email, approximate time/timezone, MCP server id/name, status,
tool count, last sync time, visible `last_error`, endpoint hostname/path with
secrets redacted, auth mode, and whether the issue happens during save, test,
sync, enable, or tool use. Do not collect tokens, API key values, full secret
query strings, passwords, or OAuth tokens.

## Do Not Say

- Do not say all users can see MCP.
- Do not tell users to paste arbitrary local stdio/command MCP configs into the
  remote MCP UI.
- Do not ask users to send bearer tokens, API keys, or secret query strings.
- Do not say a successful save means the server is usable; it still needs test
  and sync.
- Do not say a successful test guarantees every tool call will succeed.
- Do not say an active server means every tool is safe to call without
  confirmation.
- Do not ask users to bypass `needs_confirmation` for write or destructive MCP
  tools.
- Do not tell users to paste missing secret inputs into support chat.
- Do not expose internal broker endpoints or sandbox tokens in normal support
  answers.

## Related Cards

- `moclaw.how_to.manage_mcp_servers`
- `moclaw.reference.connectors_status`
- `moclaw.ui.connectors_panel`
- `moclaw.playbooks.security_privacy_answering`
- `moclaw.playbooks.ask_for_screenshot_or_reference_id`
