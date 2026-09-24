# Support Answer Cookbook

Use this cookbook after routing a question with `answer-router.md` and loading
the relevant product cards. It provides short answer shapes, not new product
facts. If a source card disagrees with a cookbook line, the source card wins.

## General Shape

1. Give the direct answer in one or two sentences.
2. Name the product surface: chat, AI Cloud Computer, workspace file,
   connector, channel, Local Desktop, Settings, Billing, or support.
3. Give the next action or UI path.
4. Add the most important boundary or safety warning.
5. Link or route to the matching help article.

## Short Answer Templates

| User asks | Good first answer | Load |
|---|---|---|
| "What is MoClaw?" | MoClaw is a personal AI agent that works in an AI Cloud Computer for tasks, files, connectors, and generated outputs. | `help-center/getting-started/what-is-moclaw.md` |
| "Where is my generated file?" | Check **Artifacts** first. The current web app does not expose an **All files** browser for the whole workspace tree. | `help-center/workspace/files-and-artifacts.md` |
| "How do I send a file?" | Upload it in chat, paste/drag it when supported, or reference an existing workspace file with `@`. | `help-center/workspace/upload-or-reference-files.md` |
| "What does MoClaw remember?" | Separate current chat history, browser-local settings preferences, workspace memory files like `MEMORY.md`/`memory/`, and internal memory APIs; do not promise a Memory settings page or full deletion from `/new`. | `help-center/account/memory-and-personalization.md` |
| "Can it read my computer?" | Not without MoClaw Desktop. Local file tools are currently fixed to the desktop user's Home directory, have runtime path checks, and still follow OS permissions; they do not grant whole-computer access. | `help-center/security/privacy-and-access.md` |
| "Did Run cloud command use my laptop?" | No. Explicit **cloud** labels refer to the AI Cloud Computer; generic **Run command** labels alone are not proof of local-machine access. | `help-center/workspace/cloud-and-local-tools.md` |
| "A local capability is unavailable." | Confirm the task is open in MoClaw Desktop, reopen the app, and retry once. The browser Web App has no Local Desktop status card; if it still fails, check **Settings > Local Tools**. | `help-center/desktop/local-desktop.md` |
| "Why can't MoClaw Desktop read this folder?" | Confirm the task is running in MoClaw Desktop and the path is inside the current user's Home directory. MoClaw has no per-directory product prompt; the OS may still deny protected folders. | `help-center/desktop/local-desktop.md` |
| "Can I use Bash to read a blocked file?" | Do not use Bash as a workaround. On supported platforms it is enabled in the default config, runs commands directly while enabled with the desktop user's OS permissions, and is not a file system sandbox. Users can disable it in **Settings > Local Tools**. | `help-center/desktop/local-desktop.md` |
| "Can I delete/export my account data or change my email?" | Current Settings shows identity and plan state but not self-serve profile edit, account deletion, data export, or data deletion controls; collect safe request context and route to support. | `help-center/account/account-and-data-requests.md` |
| "Can it read all Google Drive?" | No current support wording should say full Drive access. Drive/Docs/Sheets/Slides are scoped to the selected Workspace Folder under `drive.file`. | `help-center/connectors/google-workspace-permissions.md` |
| "Do you train on my data or have SOC 2/GDPR/DPA?" | Do not improvise policy. Explain access boundaries from current docs, then route training-data, compliance, retention, and legal commitments to owner-reviewed policy/support. | `help-center/security/privacy-and-access.md` |
| "Why did copy include Diagnostic data?" | Failed or interrupted messages can copy compact diagnostic ids for support; normal completed messages do not append ids just because ids exist. | `help-center/chat/read-chat-messages-and-open-files.md` |
| "Why is Retry missing?" | Retry appears only for failed text-only user messages when the UI exposes it; uploaded-file failures cannot be reconstructed from the bubble. | `help-center/chat/read-chat-messages-and-open-files.md` |
| "Credits show but chat is blocked." | Credits and product access are separate; current public access is paid Pro/paywall-driven, so check active Pro entitlement and the visible usage gate before assuming the credits are gone. | `help-center/billing/pricing-credits-trials.md` |
| "Is the trial 30 days or 3 days?" | MoClaw does not currently offer a public 30-day no-card Trial or one-time 1,000-credit Trial grant; if a 3-day trial appears, treat it as Pro checkout state. | `help-center/billing/pricing-credits-trials.md` |
| "Can I buy credits without Pro?" | Credit Packs add usage credits; they do not unlock, reactivate, or extend Pro/Trial access, and current UI routes paid Pro users to the top-up path. | `help-center/billing/buy-credit-packs.md` |
| "Why is a model tier locked or switching back?" | Check active Pro entitlement and the tier selector; app-server may return Fast or Standard when the stored/requested tier is not authorized. | `help-center/chat/model-tier-locked-or-switch-failed.md` |
| "What is Connect Codex / Connected with ChatGPT?" | It is a Codex/ChatGPT device-auth credential, not a normal pasted OpenAI API key and not the user's MoClaw login identity. | `help-center/billing/connect-openai-codex.md` |
| "Where are usage, billing, invoices, and API keys?" | Use **Settings > Usage** for credits/history, **Account** for plan state, **Billing** for Payment History, and **API Keys** for Codex OAuth identity when visible. | `help-center/billing/find-usage-billing-and-invoices.md` |
| "Which credits are used first?" | MoClaw uses bonus credits, then subscription/trial credits, then Credit Pack credits; within a type it uses the earliest-expiring source first. | `help-center/billing/credit-expiry-and-usage-order.md` |
| "Why didn't referral credits arrive?" | Referral rewards are feature-gated, eligibility-checked, reviewed, and not instant; promo credits do not extend Pro or Trial. | `help-center/billing/referral-invite-link-not-working.md` |
| "I paid but Pro/credits did not update." | Refresh `/chat`, then check **Settings > Usage**, **Account**, and **Billing**; collect checkout time and safe references if still wrong. | `help-center/billing/checkout-payment-not-updated.md` |
| "Can I get a refund?" | Refund/proration outcomes need the support/billing process; current reviewed UI sources do not show a self-serve refund or Stripe Billing Portal path. | `help-center/billing/cancel-reactivate-refunds.md` |
| "Which integrations exist?" | Current confirmed connector rows are Google Workspace, GitHub, and Linear when visible; Telegram, Slack, Lark, and Discord are Channels, not data connectors. Treat MCP as available only if the current UI shows an MCP row or a newer verified source confirms it. | `help-center/connectors/connectors-overview.md` |
| "GitHub repo is missing." | GitHub identity, App installation, account/org enablement, and repository selection are separate. Check **Accessible Accounts & Organizations**, **Accounts & Organizations to Enable**, and GitHub-side **Configure in GitHub** scope. | `help-center/connectors/github-repository-access.md` |
| "Google Workspace connected but Drive fails." | Gmail/Calendar/Tasks can be ready while Drive still needs the Workspace Folder setup. | `help-center/connectors/google-workspace-permissions.md` |
| "Linear cannot see or update something." | Linear is OAuth2 for a connected user/workspace; writes default to the authorized user actor, and `teamId`/`stateId`/`projectId`/`assigneeId` need provider UUIDs. | `help-center/connectors/connect-linear.md` |
| "MCP tool is missing." | First check whether **left sidebar > Connectors** shows **MCP**. If it does, open **MCP > Manage**, then Test/Refresh/Sync and check server status/tool count. | `help-center/connectors/mcp-server-connection-errors.md` |
| "How do I schedule a task?" | Ask MoClaw in chat with the task, timing, and timezone if timing matters, then confirm it appears in **left sidebar > Schedules**; do not assume a sidebar New schedule button. | `help-center/automation/manage-schedules.md` |
| "My schedule did not run." | Open **left sidebar > Schedules**, check the row status and hover details, then collect schedule name, visible status, last/next run, expected time/timezone, and redacted screenshot if escalation is needed. | `help-center/automation/manage-schedules.md` |
| "Feature is missing." | Check current visible UI/account state; screenshots, demos, source code, routes, APIs, tests, and internal traces are not proof of current public availability. | `help-center/product/feature-availability.md` |
| "I saw it in code/API." | Treat code-backed hidden features as implementation traces unless the current UI or verified KB confirms availability; offer the nearest confirmed alternative. | `help-center/product/feature-availability.md` |
| "What should I send support?" | Use **Bug Report** if visible; otherwise use the normal support path. Send account email, approximate time/timezone, visible error copy, redacted screenshot, and Reference ID/copy diagnostics if shown. | `help-center/troubleshooting/contact-support-and-send-diagnostics.md` |

## Escalation Questions

Ask for minimal, safe context:

- account email;
- approximate time and timezone;
- product surface and UI path;
- exact visible error copy;
- screenshot with secrets redacted;
- connector/provider/resource name when relevant;
- Reference ID, copied diagnostic section, invoice id, file name, connector
  name, or task id if the UI shows one.

Never ask for passwords, full card numbers, CVV, API keys, OAuth tokens, device
codes, cookies, signed URLs, private file contents, browser storage, provider
secrets, or full raw logs.

## High-Risk One-Liners To Avoid

- "MoClaw can access your whole computer."
- "Google Workspace gives full Drive access."
- "A Slack/Telegram channel means MoClaw can read that workspace's data."
- "Retry works for uploaded files."
- "Thinking shows the complete hidden reasoning."
- "Credit Packs extend Pro."
- "Refunds are guaranteed."
- "Run History is a visible left-sidebar section."
- "This feature is definitely available because it appears in a screenshot."
- "This feature is live because it appears in code, a route, an API, or a
  translation string."
