---
id: moclaw.reference.cloud_and_local_tools
title: Cloud And Local Tools
type: reference
product_area: workspace
audience: support
status: verified
last_reviewed_at: 2026-07-28
applies_to:
  plans: [trial, pro]
  environments: [local, test, prod]
  platforms: [web, desktop]
---

# Cloud And Local Tools

## Direct Answer

MoClaw can use tools in the AI Cloud Computer and, inside MoClaw Desktop, local
tools. The safest support distinction is:

- **cloud** tool labels mean the AI Cloud Computer/workspace;
- **local** tool labels mean MoClaw Desktop/local machine capabilities;
- generic **Used tools** rows show activity, not complete hidden reasoning.

Tool availability depends on plan, account, connector setup, workspace
readiness, whether the task is running in MoClaw Desktop, and the capabilities
its local runtime advertises.

Some legacy or built-in labels are generic, such as **Read file**, **Write
file**, or **Run command**. Do not infer local-machine access from those labels
alone. Use explicit **cloud** labels, explicit **local** labels, the source
kind, and the surrounding task context.

## Cloud Tool Families

Current visible cloud tool labels include:

| Family                 | Example Labels                                                                                                                                        | Meaning                                                                      |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| Cloud browser          | **Open page in cloud browser**, **Click in cloud browser**, **Fill in cloud browser**, **Take cloud browser screenshot**, **Read cloud browser page** | Browser work inside the AI Cloud Computer.                                   |
| Cloud files            | **Browse cloud files**, **Read cloud file**, **Write cloud file**, **Edit cloud file**, **Search cloud file content**                                 | File work inside the cloud workspace.                                        |
| Cloud terminal         | **Start cloud terminal**, **Run cloud command**, **List cloud terminals**                                                                             | Command or script execution inside the AI Cloud Computer.                    |
| Built-in web/search    | **Search web**, **Open web page**                                                                                                                     | Web search/fetch style actions surfaced as built-in tool activity.           |
| Task/artifact/schedule | **Subtask**, **Update todo**, **Publish file**, **Create schedule**, **Cancel schedule**                                                              | Task management, artifact publishing, or schedule operations when available. |
| External MCP           | `{{source}}: {{action}}` fallback labels                                                                                                              | A configured remote MCP server or external tool source.                      |

Cloud browser and cloud terminal are not the user's personal laptop. If the
user's task needs personal login state, the cloud browser may require signing in
again. Local browser tools are available only inside MoClaw Desktop. Isolated
browser mode is the default, and experimental Local Chrome mode controls only a
dedicated Moclaw automation tab.

## Local Tool Families

Local labels are reserved for Local Desktop behavior, such as:

- **Open page in local browser**
- **Read local browser page**
- **Read local file**
- **Write local file**
- **Read local clipboard**
- **Write local clipboard**
- **Inspect local system**
- **Run local command**

MoClaw Desktop is different from the AI Cloud Computer. The browser Web App does
offers a Desktop installer entry but does not run local tools or connect to the
desktop runtime. Local file tools are fixed to the desktop user's Home directory
and remain subject to runtime path checks and OS permissions. There is no
product-level directory prompt or approved-folder list. On supported platforms
Bash is enabled in the current default config, runs commands directly while
enabled, and starts only in an allowed working directory; that
working-directory check is not a file system sandbox.

Do not treat all local labels as the same permission surface:

| Local Surface   | Boundary                                                                                                                                                                                                                   |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Local browser   | Uses Local Desktop browser capability; isolated mode is the default and experimental Local Chrome controls only a dedicated Moclaw automation tab.                                                                         |
| Local files     | Requires Local Desktop file capability. File tools are currently fixed to the desktop user's Home root; runtime and OS permission checks still apply.                                                                      |
| Local clipboard | Uses a separate clipboard capability; never ask users to share clipboard secrets.                                                                                                                                          |
| Local command   | On supported platforms Bash is enabled in the default config and runs commands directly while enabled with the desktop app user's OS permissions. Its Home-limited initial working directory is not a file system sandbox. |

## Support Wording

When users ask about a tool row:

1. Use the visible label first.
2. If it says **cloud**, explain that the action happened in MoClaw's cloud
   workspace.
3. If it says **local**, confirm the task ran in MoClaw Desktop and explain the
   relevant capability boundary or setting.
4. If it is a generic built-in label without **cloud** or **local**, avoid
   guessing the machine. Explain the visible action and route to the relevant
   surface if the task context is clear.
5. If it is an MCP/source fallback label, load MCP/server-specific connector
   cards before promising behavior.
6. If the tool row shows command, output, error, or running status, explain that
   the user can open the row for details, but do not expose secrets or raw
   signed URLs.

## Do Not Say

- Do not say cloud browser or cloud terminal actions happened on the user's
  local computer.
- Do not say MoClaw can access local files, clipboard, browser login state, or
  local shell commands without Local Desktop and required permissions.
- Do not suggest local Bash commands to bypass an operating-system file
  denial.
- Do not say local browser actions always use the user's already-open Chrome;
  isolated browser mode is the default.
- Do not describe a Local Desktop connection card in the browser Web App.
- Do not say Local Desktop grants unrestricted machine access.
- Do not describe a per-directory approval prompt, approved-folder list, or
  in-app system-file-settings shortcut; those flows no longer exist.
- Do not say a generic **Run command** or **Read file** label proves the action
  happened on the user's local computer.
- Do not expose raw internal tool names as the main customer-facing answer.
- Do not describe **Thinking** or **Used tools** as complete private
  chain-of-thought.

## Related Cards

- `moclaw.concepts.ai_cloud_computer`
- `moclaw.reference.message_display_and_actions`
- `moclaw.reference.local_desktop_permissions`
- `moclaw.reference.scheduled_tasks`
- `moclaw.how_to.use_local_desktop`
- `moclaw.troubleshooting.workspace_unavailable`
- `moclaw.troubleshooting.local_desktop_disconnected`
- `moclaw.how_to.manage_mcp_servers`
