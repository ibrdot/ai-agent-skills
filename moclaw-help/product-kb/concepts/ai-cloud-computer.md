---
id: moclaw.concepts.ai_cloud_computer
title: AI Cloud Computer
type: concept
product_area: workspace
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-29
source_paths:
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/docs/system-reference.md
  - maxgent/client/webapp/src/modules/runtime/computers/components/cloud-computer-header-action.tsx
  - maxgent/client/webapp/src/modules/runtime/computers/hooks/use-cloud-computer-viewer-action.ts
  - maxgent/client/webapp/src/modules/runtime/desktop/components/desktop-viewer-layer.tsx
  - maxgent/client/webapp/src/modules/chat/message/lib/tool-display.ts
  - maxgent/libs/sandbox-mcp/src/mcp/tools/browser.ts
  - maxgent/libs/sandbox-mcp/src/mcp/tools/file.ts
  - maxgent/libs/sandbox-mcp/src/mcp/tools/bash.ts
applies_to:
  plans: [trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# AI Cloud Computer

## Direct Answer

The AI Cloud Computer is MoClaw's cloud work environment for the user. MoClaw
opens browsers, reads and writes files, runs commands, uses tools, saves
outputs, and shows progress in the web UI from this environment.

## What It Can Do

Users can understand it as the computer where the AI does its work:

- browse webpages, click, fill forms, take screenshots, and read pages;
- read, write, and search cloud workspace files;
- preview files such as PDF, Excel, Word, PowerPoint, Markdown, and images;
- run shell commands or code;
- generate and publish artifacts;
- execute scheduled tasks.

## Boundaries

- It is not the user's local computer.
- It does not access local files or the local browser by default.
- Local capabilities require Local Desktop and usually require user permission
  or an enabled local capability.
- If the workspace/sandbox is unavailable, files, the desktop viewer, and tool
  execution can all be affected.

## Related Cards

- `moclaw.concepts.workspace_file_and_artifact`
- `moclaw.reference.ai_cloud_computer_viewer`
- `moclaw.reference.cloud_and_local_tools`
- `moclaw.troubleshooting.local_desktop_disconnected`
- `moclaw.ui.chat_page`
