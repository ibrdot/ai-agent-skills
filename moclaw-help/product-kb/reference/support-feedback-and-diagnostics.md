---
id: moclaw.reference.support_feedback_and_diagnostics
title: Support Feedback And Diagnostics
type: reference
product_area: support
audience: support
status: verified
last_reviewed_at: 2026-06-09
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web, mobile]
---

# Support Feedback And Diagnostics

## Direct Answer

MoClaw can show an in-app **Bug Report** / **Report a Bug** entry in the top
right controls when the feedback path is available. The feedback entry is
hidden when observability/Sentry feedback is not configured, such as local dev,
no DSN, or self-hosted builds without the feedback path.

The feedback dialog supports:

- a required text description;
- one optional screenshot attachment;
- pasted screenshots from the clipboard;
- PNG, JPEG/JPG, or WebP image input through the file picker;
- one screenshot staged at a time; choosing or pasting another screenshot
  replaces the previous staged screenshot;
- image attachments up to 5 MB.

The submit action is disabled while the message is empty, while a screenshot is
being read, or while a previous submit is in progress. If the user pastes a
non-image file, the UI shows the unsupported-screenshot error instead of
silently attaching it. If a screenshot is over the size cap, the UI shows the
5 MB limit error.

If submission fails, the UI shows the feedback submit error and keeps the form
state so the user can retry.

## Diagnostic Context Sent With Feedback

When available, the feedback event can include sanitized chat-attempt
correlation data so support/engineering can join the report to the current chat
failure. Current fields can include:

- `attempt_id`;
- `query_id`;
- `trace_id`;
- `thread_id`;
- `last_event_id`;
- `last_event_type`;
- `status`;
- `updated_at`.

When no latest attempt diagnostics are available but an active thread exists,
the feedback path can still include `thread_id` with `available: false`. This is
correlation metadata, not a request for the user to paste secrets or raw logs.

## Reference ID

Some failed local session terminal notices show **Reference ID** and a **Copy
reference** action. The copied diagnostic text is limited to fields such as:

- `sessionId`;
- `eventId`;
- `threadId`;
- `code`, when present.

The visible Reference ID is the terminal event id. The **Copy reference** action
copies compact key-value diagnostics such as
`sessionId=... eventId=... threadId=... code=...`; optional unavailable fields
are omitted.

If the UI shows a Reference ID or copy-reference action, it is useful support
context. Users should still redact anything else visible in a screenshot or log
snippet.

## What Support Should Ask For

Ask only for the minimum context needed to reproduce or locate the issue:

- account email;
- approximate time and timezone;
- short description of what happened and what the user expected;
- screenshot of the visible MoClaw UI state, if helpful;
- exact visible error copy;
- Reference ID or copied reference diagnostic text, if the UI shows one;
- affected file name, connector name, task/schedule name, invoice/checkout
  reference, or model tier when relevant.

## Redaction Rules

Tell users to redact secrets before sending screenshots, snippets, or
diagnostics. Secrets include:

- passwords;
- full card numbers and CVV;
- API keys;
- OAuth tokens and authorization codes;
- cookies;
- signed URLs;
- private repository tokens;
- unrelated personal data.

Do not ask for full terminal logs when a small visible snippet, Reference ID,
and timestamp are enough.

## Do Not Say

- Do not promise the Bug Report button is always visible.
- Do not promise a specific support SLA or immediate fix.
- Do not say a missing Bug Report button means the user's account is broken.
- Do not ask for passwords, CVV, full card numbers, API keys, OAuth tokens,
  cookies, signed URLs, private SSH keys, or verification codes.
- Do not tell users to paste full raw logs when scoped visible context is
  enough.
- Do not ask users to attach non-image files through the Bug Report screenshot
  control.
- Do not expose internal stack traces or Sentry implementation details in
  normal user-facing answers.

## Related Cards

- `moclaw.playbooks.ask_for_screenshot_or_reference_id`
- `moclaw.foundation.support_answer_style`
- `moclaw.reference.message_display_and_actions`
