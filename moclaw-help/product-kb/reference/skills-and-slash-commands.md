---
id: moclaw.reference.skills_and_slash_commands
title: Skills And Slash Commands
type: reference
product_area: workspace
audience: support
status: verified
owner: product
last_reviewed_at: 2026-07-09
source_paths:
  - maxgent/client/webapp/src/modules/skills/components/skills-tab.tsx
  - maxgent/client/webapp/src/modules/skills/components/skills-tab-view.tsx
  - maxgent/client/webapp/src/modules/skills/components/skills-page.tsx
  - maxgent/client/webapp/src/modules/skills/components/skills-page-view.tsx
  - maxgent/client/webapp/src/routes/_authenticated/chat.skills.tsx
  - maxgent/client/webapp/src/modules/chat/composer/components/chat-input.tsx
  - maxgent/client/webapp/src/modules/chat/composer/hooks/use-chat-composer.ts
  - maxgent/client/webapp/src/hooks/slash-command-executor.ts
  - maxgent/client/webapp/src/hooks/chat-actions.ts
  - maxgent/client/webapp/src/api/maxclaw-adapter.ts
  - maxgent/client/webapp/src/api/types.ts
  - maxgent/server/app-server/app/routers/workspace.py
  - maxgent/server/app-server/app/routers/commands.py
  - maxgent/server/app-server/app/domains/agent_runtime/routes/runtime_v2.py
  - maxgent/server/app-server/app/schemas/workspace.py
  - maxgent/server/app-server/app/schemas/command.py
  - maxgent/server/app-server/app/services/skill.py
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/client/webapp/src/i18n/locales/zh.json
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Skills And Slash Commands

## Direct Answer

Skills and slash commands are different user-visible surfaces.

- **Skills** are available capability instructions discovered in the current
  AI Cloud Computer workspace. **left sidebar > Skills** opens the Skills
  surface.
- **Slash commands** are chat-composer shortcuts loaded from `/api/commands`.
  The current command registry includes `/new` and `/stop`.

Do not tell users that every Skill is invoked by typing `/<skill-name>`. Current
frontend code uses `/` for slash commands, not for directly running a Skill.

## Skills Surface

The left-sidebar **Skills** entry:

- loads only when the workspace/session is available;
- calls `GET /api/workspace/skills?agent_id=...`;
- lists kernel/system skills and user skills;
- shows each skill name, optional description, and source label;
- can show skill cards on the standalone `/chat/skills` page;
- shows **No skills** when no skills are returned.

Skill source mapping:

| Backend Origin | UI Source |
|---|---|
| `kernel` | System |
| `user` | User |

Backend origin can be returned by the sandbox, or inferred from the path for
older sandbox payloads:

- `/opt/moclaw/kernel/...` -> kernel/system skill;
- `/home/user/.workspace/...` -> user skill.

## Slash Commands

The chat composer:

- fetches commands with `GET /api/commands`;
- opens the command menu when the draft starts with `/` or the `/` button is
  clicked;
- filters commands by name or description;
- supports Escape to close, ArrowUp/ArrowDown to move, and Enter/click to run;
- treats exact command text such as `/new` as command execution on submit;
- sends slash-prefixed text as normal chat text when commands are disabled.

Current command registry:

| Command | Behavior |
|---|---|
| `/new` | Creates a new thread/current conversation inside the current Session. |
| `/stop` | Stops the current execution via frontend abort behavior. |

## Support Boundaries

- Do not describe the Skills surface as a public skill marketplace.
- Do not promise install/delete controls in the current visible Skills surface.
  User-installed skill storage and internal install/uninstall APIs exist, but
  the current visible surface is for inspection.
- Do not call slash commands "skills" in user answers. Say "Commands" for the
  `/` menu.
- If Skills is empty or fails to load, first check that the workspace/session is
  active and ready.

## Related Cards

- `moclaw.ui.workspace_sidebar`
- `moclaw.ui.chat_page`
- `moclaw.concepts.connectors_channels_skills`
- `moclaw.reference.chat_conversations_and_history`
- `moclaw.playbooks.feature_not_shipped_yet`
