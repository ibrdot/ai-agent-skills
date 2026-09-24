---
id: moclaw.foundation.product_identity
title: What Is MoClaw?
type: concept
product_area: foundation
audience: user
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/README.md
  - maxgent/client/webapp/src/i18n/locales/en.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# What Is MoClaw?

## Direct Answer

MoClaw is a personal AI agent that works inside the user's **AI Cloud
Computer**. The user gives tasks in chat, and MoClaw uses the cloud computer's
browser, files, terminal, skills, connectors, and scheduled tasks to complete
the work.

## What Users Usually Mean

When users ask what MoClaw is, they usually need three boundaries:

- whether it is just a normal chatbot;
- whether it is only a Claude wrapper;
- whether it directly operates on their local computer.

## Boundaries

- MoClaw is not only a question-answering chatbot; it uses tools to perform
  work.
- MoClaw is not only a Claude wrapper. Claude, DeepSeek, and other models are
  model choices; the MoClaw product layer includes the cloud computer, workspace,
  tools, connectors, schedules, and UI.
- By default, MoClaw works in the cloud environment and does not touch the
  user's local machine. Local browser or local file capabilities require Local
  Desktop plus user authorization.

## Support Answer

Use this answer shape:

> MoClaw is a personal AI agent that works inside its own AI Cloud Computer.
> You give it tasks in chat, and it can open webpages, read and write files,
> run commands, use connectors, or run scheduled work in that cloud computer.
> It is more than a chat reply, and it does not operate on your local computer
> by default.

## Related Cards

- `moclaw.concepts.ai_cloud_computer`
- `moclaw.ui.chat_page`
- `moclaw.concepts.credits_entitlement`
