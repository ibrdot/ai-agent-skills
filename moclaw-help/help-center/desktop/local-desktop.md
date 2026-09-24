---
id: help.desktop.local_desktop
title: Use Local Desktop
audience: user
status: verified
source_cards:
  - moclaw.reference.local_desktop_permissions
  - moclaw.how_to.use_local_desktop
last_reviewed_at: 2026-07-29
---

# Use Local Desktop

MoClaw Desktop is the desktop app for tasks that need your local browser, local
files, clipboard, or local shell commands. It is different from the AI Cloud
Computer opened from the Cloud Computer button in the top Chat header.

The browser Web App can download MoClaw Desktop, but it cannot run local tools
itself. Use those tools from the installed desktop app.

## Install and Open MoClaw Desktop

1. Open `/chat`.
2. On a desktop-sized browser, expand the left sidebar, then click the desktop
   download icon beside your account at the bottom.
3. Choose one of the installers currently shown for your computer.
4. Install and open MoClaw Desktop.
5. Sign in, then continue the local task inside the desktop app.

The download icon is shown only while the desktop-sized browser sidebar is
expanded. It is not shown on mobile or inside MoClaw Desktop. If you are already
in the desktop app, no browser connection is needed to use local tools.
The Cloud Computer button opens the cloud workspace viewer; it does not enable
Local Desktop capabilities.

To change local capability settings in MoClaw Desktop, open your account menu,
choose **Settings**, then open **Local Tools**.

## Capability Boundaries

| Capability | What It Means | Current Boundary |
|---|---|---|
| Chrome / browser | MoClaw can use a local browser mode through MoClaw Desktop. | Isolated Browser is the current default. Local Chrome is an explicit experimental mode that may require Chrome remote debugging and controls only a dedicated MoClaw automation tab. |
| Files | MoClaw can read, list, search, write, move, delete, or inspect local files through MoClaw Desktop. | File tools are currently fixed to the desktop user's Home directory, and operating-system permissions still apply. |
| Clipboard | MoClaw can use local clipboard capability when the desktop app advertises it. | Do not use it to share passwords, tokens, or other secrets. |
| Bash | MoClaw can run local shell commands on supported platforms. | Bash is enabled in the current default config and commands run directly while it is enabled. |

## Local File Access

MoClaw does not get full access to your machine just because the desktop app is
installed.

The current file-tool boundary is simple:

- The file root is fixed to the current desktop app user's Home directory.
- Paths are normalized and must stay inside that root.
- Existing symbolic-link write destinations are rejected.
- The Home root itself cannot be deleted.
- Deleting or moving a final symbolic link affects the link, not its target;
  intermediate symbolic links still cannot escape the Home boundary.
- File reads have a 50 MB default limit.
- The operating system can still deny access to protected locations.

MoClaw Desktop does not show a per-directory approval prompt, keep a permanently
approved-folder list, or provide a button that opens system file access settings.
If macOS blocks a protected folder, open **System Settings > Privacy & Security >
Files & Folders** directly and review MoClaw there.

## Bash Commands

Bash uses a separate permission model from local file tools. On supported
platforms it is enabled in the current default config, and commands run directly
without a per-command product prompt.

The initial working directory must be inside the allowed Home root. The command
runs with your desktop app user's OS permissions and can refer to paths outside
that working directory. This is not a file system sandbox. Use **Settings >
Local Tools** to turn Bash off when you do not want local command execution, and
do not use Bash as a workaround for an OS-denied local file.

## Related Articles

- `workspace/cloud-and-local-tools.md`
- `getting-started/ai-cloud-computer.md`
- `troubleshooting/common-errors.md`
