---
id: moclaw.playbooks.security_privacy_answering
title: Security And Privacy Answering
type: playbook
product_area: security
audience: support
status: verified
owner: product
last_reviewed_at: 2026-07-28
source_paths:
  - product-kb/00-foundation/product-identity.md
  - product-kb/00-foundation/support-answer-style.md
  - product-kb/concepts/ai-cloud-computer.md
  - product-kb/concepts/connectors-channels-skills.md
  - product-kb/concepts/workspace-file-and-artifact.md
  - product-kb/reference/local-desktop-permissions.md
  - product-kb/reference/google-workspace-scopes.md
  - product-kb/reference/account-identity-and-data-requests.md
  - maxgent/server/app-server/app/domains/connector/README.md
  - maxgent/docs/google-workspace-scopes.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web, desktop, telegram, slack, mobile]
---

# Security And Privacy Answering

## When To Use

Use this playbook when the user asks what MoClaw can access, whether a connector
can read their data, whether Local Desktop can access local files, where files
live, asks whether customer data is used for model training, asks for
account/data deletion, or asks for compliance/legal guarantees.

## Response Pattern

1. Answer the specific access boundary first.
2. Name the relevant product surface: AI Cloud Computer, workspace file,
   artifact, upload, connector, channel, Local Desktop, or account request.
3. Say what the product can confirm from current sources.
4. Ask for the user's specific concern if the question is broad.
5. Escalate compliance, legal, deletion, DPA, audit, or certification questions.
6. Do not convert implementation facts into legal/security-policy guarantees.

## Boundary Decision Table

Use this table when the user asks "can MoClaw see X?" or "is X local/private?"

| User scenario                                                               | Answer boundary                                                                                                                                        | Good next step                                                                                                                            |
| --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| User uploaded a local file in chat                                          | The file becomes available to the MoClaw workspace for that task; it is no longer local-only.                                                          | Explain preview/download/upload limits if the file will not open.                                                                         |
| User referenced a workspace file with `@`, **Quote in chat**, or **Prompt** | This is an existing workspace file reference, not a fresh local upload.                                                                                | Use workspace file and artifact cards; do not ask for raw signed URLs.                                                                    |
| User connected Google Workspace                                             | Google access is service-specific. Drive/Docs/Sheets/Slides are scoped through the selected Workspace Folder under `drive.file`.                       | If Drive fails, check Workspace Folder setup before OAuth expiry.                                                                         |
| User connected GitHub/Linear/MCP                                            | Access depends on the provider authorization and connector configuration.                                                                              | Ask for provider/resource name and visible status/error, not tokens.                                                                      |
| User connected a chat channel                                               | A channel is a chat entry point, not proof of data-connector access.                                                                                   | Route service-data questions to connector cards instead.                                                                                  |
| User installed Local Desktop                                                | Installation alone does not grant whole-computer access. Local file tools are currently fixed to the desktop user's Home root.                         | Confirm the task runs in MoClaw Desktop, then check capability, canonical path, and OS permissions. There is no product-level directory prompt. |
| User uses Bash Commands                                                     | Bash has a separate and broader local risk model. On supported platforms it is enabled in the default config and runs commands directly while enabled. | Explain that the Home-limited initial working directory is not a file system sandbox. Do not suggest Bash as an OS-permission workaround. |
| User asks for deletion/export/retention/model training/compliance           | Current KB does not confirm self-serve legal/privacy controls, retention timelines, model-training policy, or compliance guarantees.                   | Route to support/owner-reviewed policy and ask only for minimal account/request context.                                                  |

## Access Surface Matrix

| Surface                    | What To Say                                                                                                                                                                                                                      | Do Not Say                                                                                                           |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| AI Cloud Computer          | MoClaw normally works in a cloud workspace for tasks and generated files.                                                                                                                                                        | Do not say cloud work happens only on the user's local machine.                                                      |
| Uploaded files             | Uploading a file gives MoClaw a workspace copy/reference for the task.                                                                                                                                                           | Do not call uploaded files local-only after upload.                                                                  |
| Workspace files            | Workspace files belong to the AI Cloud Computer; Artifacts are published outputs. The current Artifacts page does not expose the broader file tree.                                                                              | Do not expose raw sandbox paths, signed URLs, auth headers, or internal IDs.                                         |
| Connectors                 | Connectors are third-party access paths authorized through service-specific flows.                                                                                                                                               | Do not say connectors have zero data access or that one connector grants access to all services.                     |
| Google Workspace           | Current Drive/Docs/Sheets/Slides design is folder-scoped through `drive.file` and a selected Workspace Folder; Gmail, Calendar, and Tasks are separate service scopes.                                                           | Do not say MoClaw can read the user's entire Google Drive or that all Google services share one readiness state.     |
| Channels                   | Channels let users chat with MoClaw from apps like Telegram or Slack.                                                                                                                                                            | Do not say a chat channel grants third-party data connector access.                                                  |
| Local Desktop              | Local Desktop is a separate local connector. File tools are currently fixed to the desktop user's Home root and remain subject to runtime path checks and OS permissions.                                                        | Do not say installing Local Desktop grants full-machine access or describe a product-level folder approval flow.     |
| Bash Commands              | Bash is separate from file tools. On supported platforms it is enabled in the default config and runs commands directly while enabled. The starting directory must be inside Home, but the command is not file-system-sandboxed. | Do not suggest Bash as a workaround for an OS-denied file.                                                           |
| Account/data requests      | Current UI does not confirm self-serve account deletion/export controls; route account/data, legal, and privacy requests to owner-reviewed support.                                                                              | Do not promise deletion/export/retention timelines, legal outcomes, automatic subscription cancellation, or refunds. |
| Compliance/training policy | Link the current Privacy Policy/Terms surfaces when useful, but route specific SOC 2, ISO, HIPAA, DPA, GDPR, retention, or model-training questions to owner-reviewed policy.                                                    | Do not invent security certifications, subprocessors, retention periods, training-data rules, or legal commitments.  |

## Confirmed Boundaries

- MoClaw is primarily an AI Cloud Computer that runs tasks in a cloud workspace.
- Uploaded files and workspace references become available inside the MoClaw
  workspace for the task; they should not be described as local-only after
  upload.
- Workspace file references from `@`, **Quote in chat**, or **Prompt** point to
  existing workspace resources; they should not be described as a second local
  upload.
- Workspace files and artifacts are product workspace resources; they are not
  the same as arbitrary local files on the user's computer.
- Connectors are third-party access paths. Availability and scopes depend on the
  connector and current account configuration.
- Connector implementation includes encrypted credential storage and brokered
  action execution, but support should not make broader token-storage,
  retention, audit, or compliance guarantees without owner-reviewed policy.
- Google Workspace Drive/Docs/Sheets/Slides access is intentionally
  folder-scoped through `drive.file` and a selected Workspace Folder; Gmail,
  Calendar, and Tasks use their own scopes.
- Google Picker receives a downscoped `drive.file` access token; the Google
  refresh token remains server-side.
- A Google Workspace OAuth connection can be valid while Drive still needs
  Workspace Folder setup.
- Channels are chat entry points, not proof of third-party data access.
- Local Desktop is a local connector and is not granted full-machine file access
  just because it is installed.
- Local Desktop file tools are currently fixed to the desktop user's Home root.
  Requested paths are normalized before the runtime boundary check, file reads have a
  size limit, and OS permissions still apply.
- Local Desktop no longer has a per-directory approval prompt, permanent
  approved-folder list, or in-app system-file-settings shortcut.
- Local Desktop Bash Commands use a different risk model from file tools. On
  supported platforms Bash is enabled in the default config and runs commands
  directly while enabled. The Home-limited starting directory is not a file
  system sandbox.
- Current source-backed UI does not show self-serve account deletion, data
  deletion, data export, or profile-edit controls inside Settings.
- Account/data deletion, subscription cancellation, refund review, and legal
  privacy requests are separate workflows that may need separate owners.
- Public Privacy Policy and Terms links are exposed from the user menu and
  Settings/About surfaces, but this KB does not replace those policies.

## Escalate When

- The user asks for SOC 2, ISO, HIPAA, GDPR, DPA, retention, deletion, or legal
  terms.
- The user asks whether deleting an account cancels Pro, refunds charges, or
  removes billing records.
- The user asks whether MoClaw trains models on customer data and no
  owner-reviewed policy card exists.
- The user asks for exact OAuth scopes or token storage guarantees beyond the
  connector source docs.
- The user reports a suspected data exposure, unauthorized access, or token leak.
- The user wants to send secrets, raw logs, signed URLs, OAuth codes, provider
  tokens, cookies, card details, or full browser storage.

## Safe Information To Request

- Account email.
- Product surface involved: cloud workspace, connector, channel, Local Desktop,
  upload, artifact, account/data request, or billing.
- Visible page/section and exact visible error copy.
- Approximate time and timezone.
- Screenshot with secrets redacted.
- Provider name and high-level resource name when relevant, such as GitHub
  organization or Google Workspace Folder name. Do not ask for provider tokens.
- For account/data requests: account email, request type, whether they can still
  sign in, whether the question is about model-training policy, and whether
  there is an active subscription or recent checkout.

## Forbidden Claims

- Do not claim a certification or compliance status without an owner-reviewed
  policy source.
- Do not say connectors have no access to user data.
- Do not say connecting a chat channel grants access to all data in that
  third-party workspace.
- Do not say Google Workspace can read the user's entire Drive.
- Do not say Gmail or Calendar working proves Drive/Docs/Sheets/Slides are
  ready.
- Do not say Local Desktop can access the whole computer.
- Do not say uploaded files are local-only after they are uploaded to a cloud
  workspace.
- Do not expose OAuth tokens, signed URLs, secret values, internal hostnames, or
  raw stack traces in user-facing answers.
- Do not promise account/data deletion, export, or retention timelines without
  an owner-reviewed policy.
- Do not promise whether customer data is or is not used for model training
  without an owner-reviewed policy.
- Do not promise that account deletion automatically cancels subscriptions,
  refunds charges, removes invoices, or erases billing records.
- Do not ask users to paste passwords, full card numbers, CVV, API keys, OAuth
  tokens, device codes, cookies, provider secrets, raw email/file contents,
  browser storage, government IDs, or full raw logs.

## Example

> MoClaw separates cloud workspace access, connector access, and Local Desktop
> access. For Local Desktop specifically, installing the app does not give full
> machine access: local file tools are currently fixed to the desktop user's
> Home directory and still follow OS permissions. There is no
> product-level folder approval prompt. Shell commands run directly while Bash
> is enabled and are not contained by a file system sandbox. For legal or
> compliance guarantees, I need to route this to the product/security owner.

## Example: Google Workspace

> Google Workspace access depends on the connector permissions you approved.
> For Drive/Docs/Sheets/Slides, current MoClaw knowledge says access is scoped
> to the selected Workspace Folder through Google `drive.file`; it should not
> be described as full Google Drive access. Gmail, Calendar, and Tasks have
> separate permissions for the tasks you ask MoClaw to do, so Gmail working
> does not automatically mean Drive setup is complete.

## Related Cards

- `moclaw.concepts.ai_cloud_computer`
- `moclaw.concepts.connectors_channels_skills`
- `moclaw.concepts.workspace_file_and_artifact`
- `moclaw.reference.local_desktop_permissions`
- `moclaw.reference.google_workspace_scopes`
- `moclaw.reference.account_identity_and_data_requests`
- `moclaw.troubleshooting.local_folder_permission_denied`
