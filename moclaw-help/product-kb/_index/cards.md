# Card Index

This index lists the current cards and their status.

## Foundation

| Card                                     | Status   | Purpose                                   |
| ---------------------------------------- | -------- | ----------------------------------------- |
| `moclaw.foundation.product_identity`     | verified | Defines MoClaw identity and boundaries.   |
| `moclaw.foundation.glossary`             | verified | Shared product terminology.               |
| `moclaw.foundation.support_answer_style` | verified | Support answer tone and forbidden claims. |

## Concepts

| Card                                          | Status   | Purpose                                                                                    |
| --------------------------------------------- | -------- | ------------------------------------------------------------------------------------------ |
| `moclaw.concepts.ai_cloud_computer`           | verified | Explains the cloud execution environment.                                                  |
| `moclaw.concepts.session_thread_message`      | verified | Explains Session/Recents, Thread, and Message layers.                                      |
| `moclaw.concepts.workspace_file_and_artifact` | verified | Distinguishes workspace files from artifacts.                                              |
| `moclaw.concepts.memory_and_personalization`  | verified | Distinguishes chat history, preferences, workspace memory files, and internal memory APIs. |
| `moclaw.concepts.connectors_channels_skills`  | verified | Distinguishes third-party access, chat channels, and skills.                               |
| `moclaw.concepts.credits_entitlement`         | verified | Explains credits and entitlement.                                                          |

## UI Map

| Card                                   | Status   | Purpose                                                                                                           |
| -------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| `moclaw.ui.chat_page`                  | verified | Describes the `/chat` surface.                                                                                    |
| `moclaw.ui.workspace_sidebar`          | verified | Describes left-sidebar workspace tools and Recents session list.                                                  |
| `moclaw.ui.settings`                   | verified | Describes current Settings tabs and connector-entry correction.                                                   |
| `moclaw.ui.dock_panel`                 | verified | Explains the Session Dock across wide and narrow layouts.                                                         |
| `moclaw.ui.mobile_layout`              | verified | Explains mobile/narrow layout behavior.                                                                           |
| `moclaw.ui.connectors_panel`           | verified | Explains left sidebar > Connectors rows, states, settings modal, GitHub account management, and MCP Manage.       |
| `moclaw.ui.billing_and_usage_surfaces` | verified | Maps usage badge, Settings Account/Usage/Billing/API Keys, pricing dialog, invoices, and credit-history surfaces. |

## Reference

| Card | Status | Purpose |
|---|---|---|
| `moclaw.reference.trials` | verified | Current no-public-30-day-trial support posture, Pro checkout trial boundaries, stale 7-day/daily-refill claims, and paywall expectations. |
| `moclaw.reference.pricing_and_credits` | verified | Pricing/credits rules and risks. |
| `moclaw.reference.connectors_status` | verified | Connector/channel availability map. |
| `moclaw.reference.model_tiers` | verified | User-facing model tier availability and support wording. |
| `moclaw.reference.feature_flags` | verified | Feature visibility gates by runtime config/environment. |
| `moclaw.reference.connector_cli_local_login` | verified | connector-cli local-dev login handoff, one-time code flow, environment gate, and secret boundaries. |
| `moclaw.reference.file_preview_limits` | verified | File upload/download transfer limits. |
| `moclaw.reference.file_preview_renderers` | verified | File viewer renderers, document/code/Mermaid/spreadsheet preview rules, export actions, and Copy link boundary. |
| `moclaw.reference.local_desktop_permissions` | verified | Electron Desktop capability, fixed Home file boundary, OS permission, and Bash risk rules. |
| `moclaw.reference.native_mobile_status` | verified | Native iOS/Android status and mobile-web distinction. |
| `moclaw.reference.google_workspace_scopes` | verified | Google OAuth scopes, service-specific readiness, `drive.file`, and Workspace Folder boundary. |
| `moclaw.reference.github_authorization_scope` | verified | GitHub identity, installation, and repository scope boundary. |
| `moclaw.reference.referrals` | verified | Referral link, review, reward, expiry, and rollout rules. |
| `moclaw.reference.refund_policy` | verified | Refund escalation boundary and forbidden billing claims. |
| `moclaw.reference.billing_plan_lifecycle` | verified | Plan entitlement, Stripe subscription state, credit wallets, and cancel/reactivate lifecycle rules. |
| `moclaw.reference.billing_invoices` | verified | Payment history, invoice links, and invoice-display boundaries. |
| `moclaw.reference.credit_expiry_and_consumption_order` | verified | Credit wallet types, expiry, usage order, and ledger boundaries. |
| `moclaw.reference.credit_pack_limits` | verified | Credit Pack purchase limits, checkout eligibility, fulfillment, expiry, and entitlement boundaries. |
| `moclaw.reference.user_preferences_and_settings` | verified | General, appearance, usage badge, and local preference persistence. |
| `moclaw.reference.account_profile_and_user_menu` | verified | User menu, account identity display, logout, and profile-edit boundaries. |
| `moclaw.reference.authentication_and_login` | verified | Login, Auth callback, protected-route return targets, logout, and account-switch state reset boundaries. |
| `moclaw.reference.account_identity_and_data_requests` | verified | Account identity edits, account deletion, data deletion/export, and legal privacy request routing. |
| `moclaw.reference.skills_and_slash_commands` | verified | Skills surface behavior, System/User labels, and slash command boundaries. |
| `moclaw.reference.ai_cloud_computer_viewer` | verified | Desktop Chat header entry, global viewer states, pop-out, and restart boundaries. |
| `moclaw.reference.cloud_and_local_tools` | verified | Cloud browser/files/terminal tool labels, Local Desktop tool boundaries, and Used tools support wording. |
| `moclaw.reference.scheduled_tasks` | verified | Scheduled task creation through chat, Schedules page, status mapping, cancellation, and timezone boundaries. |
| `moclaw.reference.run_history_status` | verified | Run History i18n/showcase traces vs current `/chat` UI alternatives. |
| `moclaw.reference.agent_email_and_phone` | verified | Agent-owned mailbox/SMS implementation traces, runtime disabled tools, and Gmail/channel/account-email boundaries. |
| `moclaw.reference.support_feedback_and_diagnostics` | verified | Bug Report availability, screenshot attachment limits, Reference ID, and safe diagnostic collection. |
| `moclaw.reference.first_task_and_starter_prompts` | verified | First-run quick start, starter links, Try yourself handoff, and safe first-prompt guidance. |
| `moclaw.reference.chat_channel_binding_flows` | verified | Telegram, Slack, Lark, and Discord channel binding, waiting, disconnect, and availability boundaries. |
| `moclaw.reference.openai_codex_device_auth` | verified | Connect Codex device-auth flow, states, and credential-safety boundaries. |
| `moclaw.reference.chat_conversations_and_history` | verified | Recents, Sessions, new conversation threads, history loading, and session failure wording. |
| `moclaw.reference.chat_composer_controls` | verified | Chat input controls, send/stop state, keyboard behavior, and voice rules. |
| `moclaw.reference.message_display_and_actions` | verified | Message content blocks, Thinking/Used tools, copy/retry, copied diagnostics, follow-ups, and media opening. |

## How-To

| Card | Status | Purpose |
|---|---|---|
| `moclaw.how_to.connect_github` | verified | Connect GitHub identity and repository/organization access. |
| `moclaw.how_to.connect_linear` | verified | Connect Linear OAuth, workspace/user access, actor attribution, and provider-ID rules. |
| `moclaw.how_to.connect_google_workspace` | verified | Connect Google Workspace, complete Drive folder setup, and handle Picker/folder fallback. |
| `moclaw.how_to.manage_mcp_servers` | verified | Manage remote MCP servers from the MCP connector dialog. |
| `moclaw.how_to.use_local_desktop` | verified | Download MoClaw Desktop from the Web App, then use local tools inside the desktop app. |
| `moclaw.how_to.buy_credits_or_upgrade` | verified | Upgrade, buy credits, or reactivate subscription from Usage/Pricing. |
| `moclaw.how_to.cancel_or_reactivate_pro` | verified | Cancel paid Pro, cancel trialing Pro, or reactivate a canceling subscription. |
| `moclaw.how_to.use_artifacts` | verified | Open, download, copy, and prompt with artifacts. |
| `moclaw.how_to.manage_schedules` | verified | View, refresh, and cancel scheduled tasks from the Schedules page. |
| `moclaw.how_to.upload_or_reference_file` | verified | Upload local files or reference existing workspace files in chat. |
| `moclaw.how_to.use_skills_and_slash_commands` | verified | View loaded skills and use `/new` or `/stop` commands. |

## Troubleshooting

| Card | Status | Purpose |
|---|---|---|
| `moclaw.troubleshooting.credits_locked` | verified | Balance visible but usage blocked. |
| `moclaw.troubleshooting.local_desktop_disconnected` | verified | Local capability unavailable in MoClaw Desktop or a local task started in the Web App. |
| `moclaw.troubleshooting.workspace_unavailable` | verified | Workspace/sandbox runtime unavailable or needs restart. |
| `moclaw.troubleshooting.sandbox_capacity_full` | verified | Temporary workspace capacity exhaustion. |
| `moclaw.troubleshooting.model_provider_timeout` | verified | Upstream model provider timed out. |
| `moclaw.troubleshooting.connector_expired` | verified | Connector expired, reconnect failed, disconnect failed, or provider revoke is unconfirmed. |
| `moclaw.troubleshooting.github_repo_not_visible` | verified | GitHub repo/organization missing after connection. |
| `moclaw.troubleshooting.google_workspace_needs_folder` | verified | Google Drive folder setup required. |
| `moclaw.troubleshooting.schedule_did_not_run` | verified | Scheduled task did not run or shows failed/paused/expired. |
| `moclaw.troubleshooting.local_folder_permission_denied` | verified | Local file access blocked by the Home boundary, OS permission, symbolic-link protection, or size limit. |
| `moclaw.troubleshooting.file_cannot_preview_or_download` | verified | File preview/download unavailable, failed, or too large. |
| `moclaw.troubleshooting.chat_file_upload_or_attachment_failed` | verified | Chat file upload, paste, drag/drop, failed attachment chips, large pasted text, and queued attachment messages. |
| `moclaw.troubleshooting.voice_recording_not_working` | verified | Voice button missing, microphone permission, unsupported browser, and transcription failures. |
| `moclaw.troubleshooting.checkout_payment_not_updated` | verified | Checkout success, missing credits, missing subscription state, payment-history lag, and safe escalation. |
| `moclaw.troubleshooting.model_tier_unavailable_or_switch_failed` | verified | Model tier rows locked/missing, switch failure, and server fallback behavior. |
| `moclaw.troubleshooting.mcp_server_connection_or_tools_missing` | verified | MCP row missing, remote MCP test/sync failure, missing tools, endpoint/auth errors, and safe escalation. |
| `moclaw.troubleshooting.referral_invite_link_not_working` | verified | Referral accept-page states, invalid/disabled links, browser storage errors, bind failures, and review boundaries. |

## Playbooks

| Card                                                  | Status   | Purpose                                                                                     |
| ----------------------------------------------------- | -------- | ------------------------------------------------------------------------------------------- |
| `moclaw.playbooks.billing_refund_escalation`          | verified | Safe handling for billing, refund, and charge escalation.                                   |
| `moclaw.playbooks.security_privacy_answering`         | verified | Safe handling for access, privacy, and compliance questions.                                |
| `moclaw.playbooks.feature_not_shipped_yet`            | verified | Safe answer for missing, gated, screenshot-only, roadmap, or coming-soon feature questions. |
| `moclaw.playbooks.ask_for_screenshot_or_reference_id` | verified | Minimal safe diagnostic information collection.                                             |

## Release Notes

| Card                                | Status   | Purpose                                                                               |
| ----------------------------------- | -------- | ------------------------------------------------------------------------------------- |
| `moclaw.release_notes.known_issues` | verified | Tracks unresolved product decisions, source cleanup items, and resolved KB decisions. |
