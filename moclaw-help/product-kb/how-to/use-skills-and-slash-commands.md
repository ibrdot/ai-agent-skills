---
id: moclaw.how_to.use_skills_and_slash_commands
title: Use Skills And Slash Commands
type: how_to
product_area: workspace
audience: user
status: verified
owner: product
last_reviewed_at: 2026-07-09
source_paths:
  - maxgent/client/webapp/src/modules/skills/components/skills-tab.tsx
  - maxgent/client/webapp/src/modules/skills/components/skills-page.tsx
  - maxgent/client/webapp/src/modules/skills/components/skills-page-view.tsx
  - maxgent/client/webapp/src/modules/chat/composer/components/chat-input.tsx
  - maxgent/client/webapp/src/modules/chat/composer/hooks/use-chat-composer.ts
  - maxgent/server/app-server/app/routers/workspace.py
  - maxgent/server/app-server/app/routers/commands.py
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Use Skills And Slash Commands

## Direct Answer

Use **left sidebar > Skills** to inspect loaded skills. Use the `/` button or type
`/` in the chat composer to open the command menu.

## View Skills

1. Open `/chat`.
2. Open the left sidebar.
3. Click **Skills**.
4. Review the skill cards. Hover description text when the page truncates a
   longer description.

Skill rows can be marked **System** or **User**. System skills come from the
kernel workspace; user skills come from the user's workspace skill location.

## Use Slash Commands

1. Click the `/` button in the composer, or start a message with `/`.
2. Type to filter commands.
3. Use ArrowUp/ArrowDown or click a row.
4. Press Enter or click the command to run it.

Current commands include:

- `/new` to start a new conversation thread;
- `/stop` to stop the current execution.

## If You Cannot See It

- If **Skills** is empty, the current workspace may not have skills loaded.
- If **Skills** is loading or fails, check whether the AI Cloud Computer/session
  is active and ready.
- If the `/` command menu is hidden, the current surface may have commands
  disabled. In that case `/text` is sent as a normal message.
- Do not assume a specific skill is available in every workspace.
- Do not promise install/delete controls or direct skill-file opening unless the
  current UI shows those actions.

## Related Cards

- `moclaw.reference.skills_and_slash_commands`
- `moclaw.ui.workspace_sidebar`
- `moclaw.ui.chat_page`
