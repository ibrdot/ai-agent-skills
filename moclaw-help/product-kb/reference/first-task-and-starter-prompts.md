---
id: moclaw.reference.first_task_and_starter_prompts
title: First Task And Starter Prompts
type: reference
product_area: onboarding
audience: support
status: verified
last_reviewed_at: 2026-06-09
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web, mobile]
---

# First Task And Starter Prompts

## Direct Answer

Users can start a MoClaw task from `/chat` by typing the outcome they want in
the chat composer. On an empty first-run chat, MoClaw can show a **Start here**
quick-start surface with example tasks. Selecting an example pre-fills the
composer; it does not automatically send the task.

Quick start is conditional. It appears only when the chat is empty, initial
history has loaded as empty, the AI Cloud Computer environment is ready, there
is no environment error, usage is not blocked, no live response is running, and
no starter preset handoff is active.

## Quick Start Surface

The current quick-start tabs are:

- **Featured**;
- **Research**;
- **Create**;
- **Work**;
- **Automations**.

Examples include research, building apps or websites, image generation, email
work, PDF editing, data analysis, web data collection, competitor monitoring,
morning briefings, workflow automation, and cron-style jobs.

If the user clears a pre-filled quick-start draft while still on the first-run
surface, quick start can reappear. Slash commands are hidden on the first-run
quick-start composer.

## Starter Links

MoClaw also supports `/start/$slug` onboarding preview pages and a
`/start?config=<slug>` alias. The alias redirects only when `config` is a valid
kebab-case starter slug. Invalid slugs resolve to not found.

The `/start/$slug` page:

- fetches a public onboarding bundle by id;
- renders a read-only chat snapshot from the bundle;
- can show preset workspace files and skills in the snapshot panel;
- offers **Try yourself** / sign-in CTAs;
- uses browser session storage to hand the preset and optional first prompt to
  `/chat`;
- opens sign-in for anonymous users, then continues the handoff after sign-in;
- shows a storage error if the handoff cannot be saved, for example because the
  browser blocks storage;
- shows an onboarding fetch error if the bundle cannot be loaded.

An empty **Try yourself** handoff binds the preset without sending a first chat
message. A non-empty text handoff stores that text as the pending first message,
which `/chat` drains only after the environment is ready, a session exists, and
initial message history is no longer loading.

The frontend preview does not inject the preview transcript directly into the
live chat thread. The live chat environment is initialized or updated from the
same preset when the handoff succeeds.

## Safe User Wording

Use wording like:

> Open `/chat` and describe the outcome you want. If **Start here** examples
> are visible, click one to fill the composer, edit it, then send. If you came
> from a starter page, click **Try yourself** to bring the preset into your own
> chat; you may need to sign in first.

For better first prompts, ask for:

- the desired outcome;
- the relevant context;
- files, links, or connected services MoClaw should use;
- constraints such as audience, format, deadline, or style;
- where the output should go, such as an artifact, email draft, document, or
  scheduled task.

## Do Not Say

- Do not promise quick start is always visible.
- Do not say clicking a quick-start example immediately runs the task.
- Do not promise every quick-start example works without the needed plan,
  credits, files, connectors, permissions, or schedule availability.
- Do not promise every `/start` link remains valid forever.
- Do not treat a starter preview transcript as a live chat thread.
- Do not say starter handoff works when browser session storage is blocked.
- Do not expose browser-storage internals or preset/endpoint details in
  normal customer-facing answers.

## Related Cards

- `moclaw.foundation.product_identity`
- `moclaw.reference.chat_composer_controls`
- `moclaw.reference.chat_conversations_and_history`
- `moclaw.concepts.ai_cloud_computer`
- `moclaw.how_to.upload_or_reference_file`
- `moclaw.reference.connectors_status`
- `moclaw.reference.scheduled_tasks`
