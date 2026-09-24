---
id: moclaw.concepts.memory_and_personalization
title: Memory And Personalization
type: concept
product_area: workspace
audience: support
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/server/app-server/app/domains/sandbox/domain/workspace_policy.py
  - maxgent/client/webapp/src/modules/artifacts/list/components/artifacts-page.tsx
  - maxgent/server/app-server/app/domains/memory/README.md
  - maxgent/docs/api-contracts/server-memory-internal-api.md
  - maxgent/client/webapp/docs/reference/system-reference.md
  - product-kb/concepts/session-thread-message.md
  - product-kb/concepts/workspace-file-and-artifact.md
  - product-kb/reference/account-identity-and-data-requests.md
  - product-kb/playbooks/security-privacy-answering.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Memory And Personalization

## Direct Answer

MoClaw can use user context across work, but support answers must distinguish
four different things:

- chat history inside the current Session/Thread;
- browser-local UI preferences such as theme, language, and send-key behavior;
- workspace memory files such as `MEMORY.md` and the `memory/` directory inside
  the AI Cloud Computer workspace;
- internal server-owned memory/search APIs.

Do not promise a separate self-serve **Memory** settings page, per-memory
delete controls, account-wide memory export, or guaranteed "forget this" UI
unless current product UI confirms it.

Marketing/pricing copy may mention memory, but support answers should stay
grounded in the currently verified product surfaces below.

## User-Visible Memory Files

The workspace root has product metadata for:

- `MEMORY.md`, labeled as **memories**;
- `memory/`, labeled as **memory files**.

The current web app has no whole-workspace file browser. Users can open memory
files after MoClaw surfaces them in Chat or as an Artifact; this is not a
dedicated Memory settings panel.

Memory files are workspace files. They can be opened, referenced, or prompted
with when the same workspace file rules allow it. They are not automatically the
same thing as a published Artifact.

The default workspace template includes `MEMORY.md` as a long-term memory file
that starts empty. A fresh workspace can also say there is no memory yet.

## Internal Memory Boundary

The server has internal memory APIs for write/get/list/search/reindex/status.
Those routes are disabled by default unless `MEMORY_ROUTES_ENABLED=true`, use
sandbox authentication, and are not a customer-facing self-serve path.

Internal memory routes and tool names such as `memory_search` or `memory_get`
may help calibrate product capability, but normal support answers should not
send users raw endpoint paths or tell them to call internal APIs.

Implementation detail: root memory files such as `MEMORY.md` / `memory.md` are
stored as documents, while files under `memory/` are the indexed memory files
eligible for chunking/search and embeddings. This distinction is useful for
support accuracy, but users should usually hear the simpler workspace-file
explanation unless they ask about search behavior.

## What A User Can Ask For

Users can ask MoClaw to update future behavior or workspace context, but support
should describe that as an agent task/request, not as a guaranteed account-wide
memory deletion control.

If the user wants legal/account-level deletion, export, retention, or model
training policy answers, route to the account/data request path and the privacy
playbook.

## Safe Support Wording

Use wording like:

> MoClaw may use context from your conversation and workspace files. If you see
> `MEMORY.md` or a `memory/` folder, treat those as workspace files in the AI
> Cloud Computer. I do not see a confirmed separate Memory settings page for
> editing or deleting individual memories, so for account/data deletion or
> export requests use the account/data request path.

For user preferences, route to Settings. For account deletion, data deletion,
data export, retention, or legal privacy requests, route to the account/data
request article and privacy playbook.

## Do Not Say

- Do not say MoClaw has a confirmed standalone **Memory** settings page.
- Do not promise users can self-serve delete, edit, export, or disable each
  memory item.
- Do not say `/new` clears all memory or workspace files.
- Do not say "forget this" is a guaranteed full data deletion command.
- Do not say memory files are always published Artifacts.
- Do not expose internal memory route paths as customer-facing instructions.
- Do not ask users to paste private memory files, secrets, API keys, OAuth
  tokens, cookies, or signed URLs.

## Related Cards

- `moclaw.concepts.session_thread_message`
- `moclaw.concepts.workspace_file_and_artifact`
- `moclaw.reference.user_preferences_and_settings`
- `moclaw.reference.account_identity_and_data_requests`
- `moclaw.playbooks.security_privacy_answering`
