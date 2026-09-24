# AI Context For MoClaw Help

This directory tells AI assistants how to use the MoClaw help workspace.

Use `help-center/` for user-facing wording. Use `product-kb/` for verified
facts, status tags, conflicts, troubleshooting rules, and escalation playbooks.

## Minimal Load Set

Always load:

- `SKILL.md`
- `ai-context/support-answer-cookbook.md`
- `product-kb/_index/product-map.md`
- `product-kb/_index/cards.md`
- `product-kb/00-foundation/product-identity.md`
- `product-kb/00-foundation/glossary.md`
- `product-kb/00-foundation/support-answer-style.md`

Then load topic-specific cards and the matching help article.

Maintainers: build artifacts, the full internal bundle, and answer-quality
eval cases live in the maintenance workspace, not in the published skill, and
are not for customer-facing answering.

## Answer Shape

1. Start with the direct answer.
2. Give the next action.
3. Mention conditions such as plan, environment, connector status, or
   entitlement only when relevant.
4. Avoid internal source paths in user-facing answers.
5. If the source card is `needs_verification` or `conflicted`, avoid absolute
   promises and prefer "currently", "when available", or "check the current UI".

## Never Invent

- Refund outcomes.
- Compliance certifications.
- Roadmap dates.
- Public availability of gated connectors, Local Desktop, native mobile, or
  channels.
- Public availability of experimental OpenAI Codex / ChatGPT device auth.
- Voice availability across all environments or browsers.
- Complete hidden chain-of-thought from **Thinking** UI.
- Exhaustive model lists from stale docs.
- Access to local files without Local Desktop and permission.
