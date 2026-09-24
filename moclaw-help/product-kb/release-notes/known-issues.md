---
id: moclaw.release_notes.known_issues
title: Current Knowledge Base Known Issues
type: release_note
product_area: support
audience: internal
status: verified
owner: product
last_reviewed_at: 2026-07-28
source_paths:
  - product-kb/_index/conflicts-and-decisions.md
  - product-kb/reference/trials.md
  - product-kb/reference/credit-pack-limits.md
  - product-kb/reference/openai-codex-device-auth.md
  - product-kb/reference/account-identity-and-data-requests.md
applies_to:
  plans: [unknown]
  environments: [unknown]
  platforms: [unknown]
---

# Current Knowledge Base Known Issues

## Open Product Decisions And Source Cleanup

These items either need product/owner confirmation before support copy can make
a hard public promise, or need source cleanup so old code/seed traces stop
contradicting the verified support posture.

| Area | Tracker state | Safe support posture | Required decision or cleanup |
|---|---|---|---|
| Trial source cleanup | Verified support posture; stale sources remain | Say MoClaw does not currently offer a public 30-day no-card Trial with a one-time 1,000-credit grant. If a free/no-entitlement user sees a paywall or **Upgrade to Pro**, that is expected. Treat **Start 3-day free trial**, when visible, as Pro checkout, not the old no-card MoClaw Trial. | Remove/update stale 30-day Trial UI copy, the old 7-day automatic trial seed, and the `subscription_checkout.py` "1k credits/day" comment if the no-card Trial remains unavailable. |
| Connectors entry point | Source disagreement remains; safe route verified | Use **left sidebar > Connectors** as the canonical user path. Mention `/settings/connectors` only as a recovery/settings route. | Confirm final canonical connector-management entry point for public support copy. |
| Credit Pack expiry | Product/billing policy confirmation remains | Say current implementation shows Credit Pack/addon credits expiring after 1 year, and ask users to check **Settings > Usage** for account-specific dates. Do not say Credit Packs never expire. | Confirm the intended public expiry policy; update the stale "never expire" backend comment or implementation/copy. |
| OpenAI Codex OAuth wording | Product wording confirmation remains | Treat **Connect Codex** as an experimental identity path only when visible in **Settings > API Keys**. Do not promise plan, environment, account, or model availability. | Confirm public availability, supported account types, and final name/positioning for Codex/ChatGPT identity. |
| Account/data/legal policy | Safe support route verified; policy still owner-owned | Say Settings does not currently expose self-serve email/name/avatar edit, account deletion, data export, or data deletion controls. Route deletion/export/retention/model-training/compliance questions to support or owner-reviewed policy. | Publish or confirm the owner-reviewed account/data/legal support process, timelines, and policy language. |

## Resolved KB Decisions

These areas no longer need to stay in the open-issues list, but support answers
should still avoid over-promising beyond the verified source-backed posture.

| Area | Verified support posture |
|---|---|
| Local Desktop | The desktop-sized browser Web App exposes a Desktop installer entry but does not run or connect local tools. Local capabilities run only inside Electron Desktop. File tools use the fixed Home boundary and OS permissions; the old directory prompt and approved-folder list no longer exist. |
| Native mobile | Native iOS and Android clients exist in the codebase and are not just WebView shells, but public App Store / Google Play availability is not confirmed by the verified sources. |
| Chat channels | Telegram, Slack, Lark, and Discord flows are documented in code. Lark is gated out of prod UI; Discord visibility still depends on provider setup. Channel binding is not connector/data authorization. |
| Model tiers | Answer from user-visible tiers and current account/settings when possible. Do not maintain or promise a static exhaustive model list. |
| Run History | Current left-sidebar source does not confirm a real Run History panel. Route users to chat history, **Used tools**, **left sidebar > Schedules**, and **Artifacts** instead. |
| Trial public posture | Current support posture is no public 30-day no-card MoClaw Trial and no public one-time 1,000-credit Trial grant. |

## Operational Rule

For unresolved policy or source-cleanup items, use the safe support posture
above and the linked product cards. Do not turn old seed knowledge, demo UI,
i18n strings, stale comments, or internal endpoints into public product
promises.
