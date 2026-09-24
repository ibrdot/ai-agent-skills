---
id: help.workspace.cloud_and_local_tools
title: Cloud And Local Tools
audience: user
status: verified
source_cards:
  - moclaw.reference.cloud_and_local_tools
  - moclaw.concepts.ai_cloud_computer
  - moclaw.reference.message_display_and_actions
  - moclaw.reference.local_desktop_permissions
last_reviewed_at: 2026-07-28
---

# Cloud And Local Tools

MoClaw can use tools while working on your task. In chat, these may appear under
**Used tools**.

## Cloud Tools

Labels such as **Open page in cloud browser**, **Run cloud command**, **Read
cloud file**, or **Write cloud file** mean MoClaw worked inside the AI Cloud
Computer.

That is MoClaw's cloud workspace, not your personal laptop or desktop.

Cloud tools can include browser work, workspace file work, terminal commands,
web search/fetch, artifact publishing, schedules, and other task tools
depending on your setup.

Some older or generic tool rows may say **Read file**, **Write file**, or
**Run command** without saying **cloud** or **local**. Treat those as visible
activity labels, not as proof that your personal computer was used.

## Local Tools

Labels such as **Open page in local browser**, **Read local file**, **Read local
clipboard**, or **Run local command** mean the task is using Local Desktop.

Local capabilities are available only inside MoClaw Desktop; the browser Web
App does not provide them. Local file tools are currently fixed to the desktop
user's Home directory, with runtime path checks and the operating system's own
permissions. There is no per-directory approval prompt or approved-folder list.

Local Bash commands use a separate permission model. On supported platforms,
Bash is enabled in the current default config and runs commands directly while
enabled. The command runs with your desktop app user's local permissions; the
Home-limited initial working directory is not a file system sandbox.

Local Desktop capabilities are separate from each other. A task may need local
browser state without needing local files, or local files without needing Bash.
Use the visible tool label to identify which local surface is involved, then
check **Settings > Local Tools** in MoClaw Desktop when troubleshooting.

## Login State

The cloud browser does not automatically reuse the login state from your
personal browser. If a cloud task needs a personal account, you may need to sign
in again there.

Local browser access is available only inside the running desktop app. Isolated
Browser is the current default. Local Chrome is an explicit experimental mode
that may require Chrome remote debugging and controls a dedicated MoClaw
automation tab rather than arbitrary existing tabs.

## Tool Details

Open a **Used tools** row to see details such as a command, output, error, or
running status. Do not send passwords, API keys, OAuth tokens, signed URLs, or
other secrets when asking support about a tool row.

## Related Articles

- `getting-started/ai-cloud-computer.md`
- `desktop/local-desktop.md`
- `chat/read-chat-messages-and-open-files.md`
- `troubleshooting/common-errors.md`
