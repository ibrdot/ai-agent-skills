---
id: moclaw.concepts.session_thread_message
title: Session, Thread, And Message
type: concept
product_area: chat
audience: support
status: verified
last_reviewed_at: 2026-07-09
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Session, Thread, And Message

## Direct Answer

MoClaw chat is not a single text box. It has three layers:

- **Session**: a user-visible chat workspace listed in **Recents**. It can have
  a title, source, runtime binding, messages, files, schedules, and channel
  badges.
- **Thread**: a conversation branch inside a session.
- **Message**: a single user or AI message inside a thread.

The current `/chat` route can point at a specific Session with a `session`
query parameter. The left sidebar shows **Recents** for selecting, renaming, or
deleting sessions. A new Session is not the same as a browser login session or
Auth0 session.

## Why This Matters For Support

Many support issues are layer issues:

- "I cannot see previous messages" can be an active-thread hydration or message
  loading issue.
- "I cannot send a message" can be a session, runtime, workspace, or usage-gate
  readiness issue.
- "The file will not open" can be a workspace-file or artifact resolver issue,
  not a message issue.
- "I cannot find this schedule or channel conversation" can be a user looking
  at the wrong Session or expecting one Session to contain another channel's
  context.

## Boundaries

- Do not call a Session a browser session or login session.
- Do not say creating a new Session deletes old sessions, clears account
  memory, or guarantees a fresh cloud computer.
- Do not call a Thread a chat room.
- For normal users, usually say "current conversation"; explain Thread/Session
  only when troubleshooting requires it.

## Related Cards

- `moclaw.ui.chat_page`
- `moclaw.reference.chat_conversations_and_history`
- `moclaw.concepts.workspace_file_and_artifact`
