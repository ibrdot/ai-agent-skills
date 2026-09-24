# Product Map

This map is the compact product-area inventory for MoClaw support AI. It is not
a customer-facing article. Use it to decide which cards to load before answering
questions about the product.

## How To Use

1. Identify the user's product area from the question.
2. Load the primary cards for that area, then the matching help-center article.
3. Check `status` before making promises.
4. If the question crosses areas, answer by naming each surface separately.

Example: "Can MoClaw read my files?" must separate uploaded files, workspace
files, Google Drive connector files, and Local Desktop files.

## Product Areas

| Area | User-facing scope | Primary cards | Common traps |
|---|---|---|---|
| Foundation | What MoClaw is, support answer tone, product terms. | `moclaw.foundation.product_identity`, `moclaw.foundation.glossary`, `moclaw.foundation.support_answer_style` | Do not answer from marketing copy alone. |
| First task and onboarding | Quick start examples, starter links, `/start`, first prompt guidance. | `moclaw.reference.first_task_and_starter_prompts`, `moclaw.reference.chat_composer_controls` | Quick start pre-fills the composer; it does not automatically run the task. |
| Chat | Sessions/Recents, composer, send/stop, voice, conversations, history, message display, copy/retry, model tier UI. | `moclaw.reference.chat_conversations_and_history`, `moclaw.concepts.session_thread_message`, `moclaw.reference.chat_composer_controls`, `moclaw.reference.message_display_and_actions`, `moclaw.reference.model_tiers` | Keep Session, Thread, browser login session, and account history separate. |
| Workspace | AI Cloud Computer, workspace files, Artifacts, file preview/download, skills, left sidebar. | `moclaw.concepts.ai_cloud_computer`, `moclaw.concepts.workspace_file_and_artifact`, `moclaw.reference.ai_cloud_computer_viewer`, `moclaw.reference.file_preview_renderers` | File preview failure is not data loss; Run History is not confirmed as a current visible panel. |
| Cloud and local tools | Cloud browser/files/terminal labels, Local Desktop labels, Used tools wording. | `moclaw.reference.cloud_and_local_tools`, `moclaw.reference.local_desktop_permissions`, `moclaw.how_to.use_local_desktop` | Cloud tools run in the AI Cloud Computer, not on the user's machine. Local tools require Electron Desktop and the relevant capability boundary. |
| Files and attachments | Attach/paste/drag-drop uploads, workspace references, `@` references, queued attachment sends. | `moclaw.how_to.upload_or_reference_file`, `moclaw.troubleshooting.chat_file_upload_or_attachment_failed`, `moclaw.reference.file_preview_limits` | Workspace references are not re-uploaded; queued attachment sends wait for the active response to finish. |
| Connectors | GitHub, Google Workspace, Linear, MCP server management, connector status and reconnect/disconnect. | `moclaw.reference.connectors_status`, `moclaw.ui.connectors_panel`, `moclaw.how_to.connect_github`, `moclaw.how_to.connect_google_workspace`, `moclaw.how_to.connect_linear`, `moclaw.how_to.manage_mcp_servers` | OAuth success is not the same as provider resource access. Do not ask for OAuth tokens or provider secrets. |
| Channels and communications | Telegram/Slack/Lark/Discord chat channels, agent-owned email/SMS boundaries. | `moclaw.reference.chat_channel_binding_flows`, `moclaw.reference.agent_email_and_phone`, `moclaw.concepts.connectors_channels_skills` | Keep chat channels separate from data connectors. Agent-owned email/SMS implementation traces do not prove public availability. |
| Local Desktop | Electron-only local browser/files/clipboard/commands, the fixed Home file boundary, OS permissions, and the Bash enable switch. | `moclaw.reference.local_desktop_permissions`, `moclaw.how_to.use_local_desktop`, `moclaw.troubleshooting.local_folder_permission_denied` | The Web App offers Desktop installers but does not run or connect local tools. File tools are fixed to Home; Bash is not a file-system sandbox. |
| Automation | Scheduled tasks, schedule list, cancellation, failed/paused/expired states. | `moclaw.reference.scheduled_tasks`, `moclaw.how_to.manage_schedules`, `moclaw.troubleshooting.schedule_did_not_run` | Do not promise a visible New Schedule button unless current UI confirms it. |
| Billing and entitlement | Pricing, credits, trials, usage gate, Credit Packs, invoices, referrals, refunds. | `moclaw.reference.pricing_and_credits`, `moclaw.concepts.credits_entitlement`, `moclaw.reference.trials`, `moclaw.reference.billing_plan_lifecycle`, `moclaw.reference.billing_invoices` | Current support posture is no public 30-day no-card Trial; refund outcomes need escalation. |
| Account and settings | Login/logout, account menu, profile/account data requests, settings, language/theme/timezone/notifications. | `moclaw.reference.authentication_and_login`, `moclaw.reference.account_profile_and_user_menu`, `moclaw.reference.account_identity_and_data_requests`, `moclaw.reference.user_preferences_and_settings`, `moclaw.ui.settings` | Most preferences are browser-local; do not promise account-wide sync. |
| Support diagnostics | Bug Report, Reference ID, copied diagnostic ids, safe screenshot/error collection. | `moclaw.reference.support_feedback_and_diagnostics`, `moclaw.playbooks.ask_for_screenshot_or_reference_id`, `moclaw.reference.message_display_and_actions` | Ask for compact visible/copyable diagnostics, not passwords, tokens, signed URLs, private file contents, or full raw logs. |
| Security and privacy | Access boundaries, uploaded files, connectors, Google Drive scope, Local Desktop, compliance/data requests. | `moclaw.playbooks.security_privacy_answering`, `moclaw.reference.google_workspace_scopes`, `moclaw.reference.local_desktop_permissions`, `moclaw.reference.account_identity_and_data_requests` | Do not claim SOC 2/GDPR/DPA timelines or retention rules without owner-reviewed policy. |
| Mobile and availability | Mobile web, native mobile status, missing/gated/beta features, roadmap wording. | `moclaw.reference.native_mobile_status`, `moclaw.ui.mobile_layout`, `moclaw.playbooks.feature_not_shipped_yet`, `moclaw.reference.feature_flags` | Engineering traces or screenshots are not proof of current public availability. |

## Status Snapshot

| Status               | Treat as                                                                                                                                          |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| `verified`           | Current product code/UI confirms the card. Answer directly within card scope.                                                                     |
| `needs_verification` | Useful product guidance exists, but at least one availability, policy, or rollout detail needs confirmation. Use "currently" or "when available". |
| `conflicted`         | Sources disagree. Name the distinction and avoid a one-rule answer.                                                                               |
| `draft`              | Use only as internal context unless another verified card supports the answer.                                                                    |

## High-Risk Boundaries

- Do not answer billing refunds, prorations, chargebacks, or legal policy as a
  product guarantee.
- Do not promise public availability for native mobile, Local Desktop, chat
  channels, OpenAI Codex device auth, or roadmap/future connectors from internal
  traces alone.
- Do not equate source code, routes, APIs, tests, i18n strings, or demo/showcase
  surfaces with launched customer-facing capabilities.
- Do not collapse chat history, settings preferences, workspace memory files,
  and account/data requests into one "memory" concept.
- Do not collapse uploaded files, workspace files, Google Drive files, and local
  files into one access model.
- Do not ask users to paste secrets, full raw logs, signed URLs, private file
  contents, API keys, OAuth tokens, cookies, device codes, or card details.
