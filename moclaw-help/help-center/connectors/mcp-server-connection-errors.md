---
id: help.connectors.mcp_server_connection_errors
title: MCP Server Connection Errors
audience: user
status: verified
source_cards:
  - moclaw.troubleshooting.mcp_server_connection_or_tools_missing
  - moclaw.how_to.manage_mcp_servers
  - moclaw.reference.connectors_status
  - moclaw.reference.connector_cli_local_login
  - moclaw.playbooks.ask_for_screenshot_or_reference_id
last_reviewed_at: 2026-06-09
---

# MCP Server Connection Errors

MoClaw's MCP connector is for remote HTTPS Streamable HTTP MCP servers when MCP
is available for your account and environment.

This is different from `connector-cli local login`, which is a local development
handoff and not a production MCP server setup path.

## If You Cannot See MCP

Open **left sidebar > Connectors**. If the **MCP** row is missing, MCP may not be
enabled for your account or environment, or the current UI may not expose MCP
management.

## If A Server Will Not Test Or Sync

Check these first:

- The endpoint starts with `https://`.
- The endpoint is public, not `localhost` or a private network address.
- The endpoint is a Streamable HTTP MCP endpoint, not a local command-line MCP
  config.
- The endpoint does not redirect.
- The endpoint returns JSON for the current V1 path, not an SSE/streaming-only
  response.
- The auth mode matches the server: **None**, **Bearer token**, **Header**, or
  **Query parameter**.
- API key body injection is not exposed by the current UI and is not supported
  for standard MCP JSON-RPC calls.
- The server returns tools from `tools/list`.
- The tool list and schemas are not too large for sync.

After saving, click **Test**. If that works, click **Refresh/Sync** and confirm
the server becomes **Active** with at least one tool. A successful **Test** can
leave a draft server in **Draft** until sync/refresh is run.

## If Tools Do Not Appear In Chat

If **MCP** is visible, open **left sidebar > Connectors > MCP > Manage** and
check:

- server status is **Active**;
- tool count is greater than `0`;
- the server is not **Disabled**;
- there is no visible error message on the server row.

Then retry your prompt.

## If A Tool Call Still Fails

An active server with tools can still fail during an individual tool call.

- **Missing input** means the prompt did not provide a required field.
- **Needs confirmation** means the tool may write or destructively change
  external state.
- **Auth required** means the server rejected the current auth settings.
- **Streaming not supported** means the requested streaming path is not
  available in the current MCP V1 flow.

Update the server settings from the MCP dialog when auth is wrong. Do not send
the secret value to support.

## Contact Support

Send:

- account email;
- MCP server name and service id;
- status, tool count, and last sync time;
- visible error copy;
- endpoint hostname/path with secrets redacted;
- auth mode, but not the secret value;
- whether the issue happens during save, test, sync, enable, or tool use;
- approximate time and timezone.

Do not send bearer tokens, API keys, passwords, OAuth tokens, or secret query
strings.

## Related Articles

- `connectors/manage-mcp-servers.md`
- `connectors/connectors-overview.md`
- `security/privacy-and-access.md`
