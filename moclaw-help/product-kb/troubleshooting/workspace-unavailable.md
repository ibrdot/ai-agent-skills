---
id: moclaw.troubleshooting.workspace_unavailable
title: Workspace Unavailable
type: troubleshooting
product_area: workspace
audience: user
status: verified
owner: product
last_reviewed_at: 2026-06-08
source_paths:
  - maxgent/client/webapp/src/lib/sandbox-error.ts
  - maxgent/client/webapp/src/lib/environment-retry.ts
  - maxgent/client/webapp/src/lib/environment-error-display.ts
  - maxgent/client/webapp/src/stores/environment-store.ts
  - maxgent/client/webapp/src/lib/message-failure.ts
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Workspace Unavailable

## Symptom

The user sees a workspace issue, workspace restart guidance, waiting for
sandbox, sandbox unavailable, or a failed message whose reason resolves to
`sandbox_unavailable`.

## Likely Causes

- The AI Cloud Computer failed to start or attach.
- The sandbox runtime is recovering or failed to recover.
- A workspace tool is unavailable.
- The workspace could not access a workspace file.
- The browser received raw transport details, such as 502, but the UI should
  surface safe workspace copy.

## Recovery Steps

1. Ask the user to retry the message if the UI offers a retry action.
2. If the UI offers restart workspace, use that action.
3. If the state says recovering, wait briefly and retry.
4. If the issue began after opening a stale file or artifact, retry from the
   current Artifacts list or the file card in Chat.
5. If the same workspace error repeats after restart, ask the user for account
   email, approximate time, and any visible trace/reference id.

## Escalate When

- Restart workspace fails.
- The same workspace error repeats across a new chat.
- The user sees repeated workspace permission errors for files that should be in
  the workspace.
- Raw transport details such as 502/Bad Gateway leak into the user-visible UI.

## Do Not Say

- Do not expose raw 502/Bad Gateway/RPC details in user-facing answers.
- Do not tell the user to fix Local Desktop for cloud workspace errors.
- Do not use the capacity-full recovery path unless the error is specifically
  capacity exhausted.

## Related Cards

- `moclaw.troubleshooting.sandbox_capacity_full`
- `moclaw.concepts.ai_cloud_computer`
- `moclaw.reference.ai_cloud_computer_viewer`
- `moclaw.concepts.workspace_file_and_artifact`
