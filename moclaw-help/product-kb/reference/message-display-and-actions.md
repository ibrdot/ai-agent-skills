---
id: moclaw.reference.message_display_and_actions
title: Message Display And Actions
type: reference
product_area: chat
audience: user
status: verified
last_reviewed_at: 2026-07-28
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Message Display And Actions

## Direct Answer

The chat message list renders user messages, assistant messages, streaming
output, file/image/voice blocks, visible activity such as **Thinking** and
**Used tools**, failure notices, copy/retry actions, older-message loading, and
suggested follow-ups.

## Message Content Types

| Content           | User-facing behavior                                                                                                                                     |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Text              | Renders as Markdown for assistant messages and as a user bubble for user messages. User metadata tags are stripped from visible user bubbles.            |
| File              | Renders as a file card. Click opens file preview when possible. Assistant file cards can also expose download.                                           |
| Image             | Renders inline. If the original URL is missing or expired, the renderer can resolve a fresh URL from `file_id`; otherwise it shows a failed image state. |
| Voice             | Renders as a voice player with play/pause, waveform progress, duration, and an unavailable state when the audio cannot be resolved.                      |
| Link preview      | Renders as a link preview card when a link preview block is present.                                                                                     |
| Image placeholder | Renders an image placeholder when the original image context is not available.                                                                           |

## Activity Display

- **Thinking** renders as a collapsible line. It may auto-expand while active.
- The Thinking row is visible product output/status, not a promise to expose
  complete private model reasoning.
- Tool calls render as tool pills.
- Consecutive tool pills can group into **Used N tool(s)**.
- Tool pills open a popover with command, output, error, or running status.
- Long text tool output is truncated after 30 lines with a **Show more lines**
  action.
- Binary tool output displays **Binary file — cannot preview**.
- Tools that create workspace files can surface a file card after the tool
  activity.

## Message Actions

- User and assistant messages can show a copy action on hover/focus when there
  is copyable text and the message is not pending.
- Normal completed messages do not append diagnostic data just because internal
  ids exist.
- User message copy strips hidden metadata tags such as file or image reference
  tags from the copied text.
- Assistant message copy includes text and inline user text, but not Thinking
  blocks, tool output, file cards, images, or voice blocks.
- Failed, aborted, interrupted, or otherwise failure-marked messages may append
  a `Diagnostic data:` section to the copied payload.
- Assistant diagnostics can include **Assistant Message ID** and **Run ID**.
- User diagnostics can include **User Message ID** and **Client Message ID**.
- If a failed assistant message has no visible text, copy may contain only the
  `Diagnostic data:` section.
- Diagnostic data is compact support identity/correlation text, not full raw
  logs, secrets, file contents, or signed URLs.
- Pending user messages show **Sending** after a short delay.
- Failed user messages can show reason-specific notices such as usage limit,
  rate limit, prompt too long, workspace issue, provider timeout, or unsupported
  image context.
- Retry can appear for failed text-only user messages when the failure UI marks
  the failure retryable, such as model provider timeout, or when the failure has
  no more specific banner. Usage limit, rate limit, prompt-too-long, workspace
  issue, and current-session issue notices may show guidance without Retry.
- Retry resends the failed text in the current conversation. It does not start a
  new conversation.
- Uploaded attachments cannot be reconstructed for retry from the message
  bubble. Workspace `@` references in the text may be rebuilt from the current
  mention/reference store; if a referenced file is stale or gone, retry falls
  back to the text semantics.
- Assistant failed messages show a response-failed style notice. Aborted
  assistant messages show a canceled divider.
- **Load earlier messages** appears when older history exists and is not already
  loading.

## Failure Notices

| Failure source                                                         | Visible behavior                                                                                   |
| ---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| User `payment_required` or assistant insufficient-credits/payment text | Shows usage-limit / get-credits style copy. Route to billing and credits guidance.                 |
| User `rate_limit_error`                                                | Shows **Too many active sessions — please wait a moment and try again.**                           |
| User `prompt_too_long`                                                 | Shows **Conversation too long — please start a new conversation.**                                 |
| User `sandbox_unavailable`                                             | Shows workspace recovery copy. Do not treat it as a billing problem.                               |
| User `upstream_timeout`                                                | Shows **The model provider timed out. Please retry.** and can expose Retry for text-only messages. |
| User `unsupported_image_context`                                       | Shows current-session issue / start-new-chat guidance.                                             |
| Assistant non-payment failure                                          | Usually shows **Response failed**. Copy may still include diagnostic ids.                          |

## Suggested Follow-Ups

- Suggested follow-ups render under the message list only when the latest
  current-thread message is an assistant reply with suggestions.
- Suggested follow-ups are hidden while streaming or while the chat area is
  disabled.
- Selecting a suggested follow-up sends that text as a new message.
- Suggestions disappear after the next user message because the latest message
  is no longer an assistant reply.

## File And Media Opening

- File and image clicks route through the message-list file preview path.
- File downloads use file id attachment download first when possible, then URL,
  content, or workspace/sandbox fallback.
- Preview/download availability still follows the file preview/download rules;
  a file card does not guarantee that preview or download will succeed.
- Voice playback can resolve a fresh playable URL from `file_id`. If the file
  cannot resolve or play, the voice player shows **unavailable**.
- Only one voice player should play at a time; starting another voice playback
  claims the shared audio slot.

## Do Not Say

- Do not promise every file card can preview or download.
- Do not promise a failed image or unavailable voice message is data loss.
- Do not say retry works for failed messages with uploaded files.
- Do not say Retry starts a new conversation.
- Do not say every failed message shows Retry; some failures show a specific
  banner without Retry.
- Do not say `Diagnostic data:` is a secret, full log dump, or proof that normal
  completed messages leak internal ids.
- Do not present **Thinking** as complete hidden chain-of-thought.
- Do not tell users that suggested follow-ups are permanent.
- Do not expose raw signed URLs or internal metadata tags in support answers.

## Related Cards

- `moclaw.reference.chat_composer_controls`
- `moclaw.reference.cloud_and_local_tools`
- `moclaw.reference.file_preview_limits`
- `moclaw.troubleshooting.file_cannot_preview_or_download`
- `moclaw.troubleshooting.voice_recording_not_working`
- `moclaw.concepts.workspace_file_and_artifact`
