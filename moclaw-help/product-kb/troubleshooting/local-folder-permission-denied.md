---
id: moclaw.troubleshooting.local_folder_permission_denied
title: Local File Access Denied
type: troubleshooting
product_area: local_desktop
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-28
source_paths:
  - maxgent/client/desktop/docs/moclaw-desktop.md
  - maxgent/client/desktop/electron/main/capabilities/config-store.ts
  - maxgent/client/desktop/electron/main/capabilities/local-capability-service.ts
  - maxgent/client/desktop/runtime/src/capabilities/fs.rs
applies_to:
  plans: [trial, pro]
  environments: [local, test, prod]
  platforms: [desktop]
---

# Local File Access Denied

## Symptom

MoClaw cannot read, list, search, write, move, delete, or inspect a local file or
folder through Local Desktop.

## Likely Causes

- The task is not running inside MoClaw Desktop, or its local runtime is
  unavailable.
- The requested path resolves outside the current user's Home directory, which
  is the default local file root.
- The operating system denied access. On macOS this can happen for protected
  folders even when they are inside Home.
- The file does not exist or the desktop app user does not have the needed OS
  read/write permission.
- A write targets an existing symbolic link, which the runtime rejects.
- A file read exceeds the current 50 MB limit.

There is no longer a MoClaw per-directory approval prompt, permanent approved
folder list, or in-app shortcut to system file access settings.

## Recovery Steps

1. Confirm the task is open in the running MoClaw Desktop app, not in the
   browser Web App.
2. Confirm that the requested file or folder is inside the current desktop app
   user's Home directory. A path outside Home is outside the current supported
   file-tool scope.
3. Retry the exact local file task and note the visible error.
4. If the OS denied a protected path, review the operating system's own app/file
   permissions. On macOS, use **System Settings > Privacy & Security** directly.
5. For a rejected symbolic-link write target, use the real destination path or
   a normal file path inside Home.
6. For a file larger than 50 MB, narrow, split, or reduce the file before
   retrying.

Do not wait for a MoClaw folder prompt; the product-level directory prompt has
been removed.

## Runtime Boundary Checks

| Operation                        | Current check                                                                                                        |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Read, list, search, info | The requested existing path is canonicalized and must remain inside the fixed Home root. |
| Write | The parent directory must resolve inside the fixed Home root, and an existing symbolic-link destination is rejected. |
| Delete | The parent directory must resolve inside the fixed Home root. The final symbolic link is deleted as a link, and deleting the Home root itself is rejected. |
| Move | The source and destination parents must resolve inside the fixed Home root. A final source symbolic link is moved as a link. |

The Home root and 50 MB read limit are derived in memory at startup rather than
persisted as user settings. Operating-system permission checks still apply after
the runtime boundary check. Intermediate symbolic links are still fully resolved,
so they cannot be used to escape the Home boundary.

## Escalate When

- The desktop app is running and the canonical path is inside Home, but the same
  operation still fails after the user checks the relevant OS permission.
- The error suggests a path escaped the Home boundary unexpectedly.
- The error includes connector/runtime details that the user cannot act on.

## Do Not Say

- Do not tell the user to approve or permanently authorize a folder, manage an
  approved-folder list, or open system file settings from MoClaw Desktop.
- Do not say restarting the AI Cloud Computer changes local OS file
  permissions.
- Do not suggest enabling or using Bash as a workaround. A shell command is a
  separate, broader permission surface and is not a file-tool sandbox.
- Do not ask the user to paste private file contents, local secrets, tokens,
  cookies, signed URLs, or full raw logs into chat.

## Related Cards

- `moclaw.reference.local_desktop_permissions`
- `moclaw.troubleshooting.local_desktop_disconnected`
- `moclaw.how_to.use_local_desktop`
