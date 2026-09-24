---
id: moclaw.playbooks.ask_for_screenshot_or_reference_id
title: Ask For Screenshot Or Reference Id
type: playbook
product_area: support
audience: support
status: verified
last_reviewed_at: 2026-06-08
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web, desktop, telegram, slack, mobile]
---

# Ask For Screenshot Or Reference Id

## When To Use

Use this playbook when the AI cannot resolve a user problem from the current
question and the issue needs reproducible context for support or engineering.

## Response Pattern

1. Ask for only the fields needed for this symptom.
2. Explain that secrets should be redacted.
3. Prefer visible product state over internal speculation.
4. Keep the request short enough for a frustrated user to complete.

## Safe Default Fields

- Account email.
- Approximate time and timezone.
- Screenshot of the visible MoClaw UI state.
- Exact visible error copy.
- Trace, reference, invoice, checkout-session, file, connector, or task id if
  the UI shows one.
- If a failed chat message copy includes `Diagnostic data:`, ask for that
  compact copied diagnostic section rather than full logs.
- Plan or model tier if the issue is billing, credits, or model access related.

If the user is using the in-app **Bug Report** form, ask for a short written
description and, if useful, one image screenshot up to 5 MB. Do not ask them to
attach logs or non-image files through that screenshot control.

## Symptom-Specific Fields

| Symptom | Ask For |
|---|---|
| Workspace unavailable | Account email, approximate time, screenshot, visible trace/reference id. |
| Sandbox capacity full | Approximate time, region if known, whether retry later works. |
| Model timeout | Model tier, short prompt description, approximate time. |
| Connector expired | Connector name, current connector status, whether reconnect was attempted. |
| GitHub repo missing | GitHub account/org, whether the GitHub App is installed for that repo. |
| Google Workspace setup | Whether Drive folder selection completed, visible connector status. |
| File preview/download failed | File name, workspace path if visible, file size, file type, approximate time. |
| Billing issue | Account email, charge amount/date, invoice or checkout reference if visible. |
| Local Desktop issue | Desktop app version, affected local capability, requested local path, visible error, and macOS permission status if relevant. |
| Failed chat message | Exact visible failure copy, copied `Diagnostic data:` section if available, approximate time, and whether Retry was shown. |

## Redaction Rule

Tell users to redact secrets before sending screenshots or logs. Secrets include
passwords, full card numbers, CVV, API keys, OAuth tokens, signed URLs, private
repo tokens, and personal data unrelated to the issue.

## Forbidden Claims

- Do not ask users for passwords, CVV, full card numbers, API keys, OAuth
  tokens, or private SSH keys.
- Do not request entire logs when a small visible error snippet is enough.
- Do not treat copied message diagnostic ids as secrets or as a full log dump.
- Do not ask for non-image files through the Bug Report screenshot attachment.
- Do not expose raw internal stack traces back to the user.
- Do not make the user repeat data already visible in the current conversation.

## Related Cards

- `moclaw.troubleshooting.workspace_unavailable`
- `moclaw.troubleshooting.sandbox_capacity_full`
- `moclaw.troubleshooting.model_provider_timeout`
- `moclaw.troubleshooting.connector_expired`
- `moclaw.troubleshooting.file_cannot_preview_or_download`
