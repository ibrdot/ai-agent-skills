---
id: moclaw.playbooks.feature_not_shipped_yet
title: How To Answer When A Feature Is Missing Or Uncertain
type: playbook
product_area: support
audience: support
status: verified
owner: product
last_reviewed_at: 2026-06-15
source_paths:
  - product-kb/_index/conflicts-and-decisions.md
  - product-kb/reference/feature-flags.md
  - product-kb/reference/connectors-status.md
  - product-kb/reference/chat-channel-binding-flows.md
  - product-kb/reference/connector-cli-local-login.md
  - product-kb/reference/local-desktop-permissions.md
  - product-kb/reference/native-mobile-status.md
  - product-kb/reference/model-tiers.md
  - product-kb/reference/run-history-status.md
  - product-kb/reference/agent-email-and-phone.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web, desktop, telegram, slack, mobile]
---

# How To Answer When A Feature Is Missing Or Uncertain

## When To Use

Use this when users ask about Discord, Lark, Notion, native mobile, Run History,
roadmap items, exact model lists, or any
feature whose availability is uncertain.

Also use it when the user says they saw a feature in a screenshot, old doc,
demo, marketing image, coworker account, or video, but do not see it in their
own account.

Use it when the only evidence is a private engineering trace, route, API,
translation string, test, demo/showcase surface, or old doc. Those are
non-public product traces, not public availability guarantees.

## Evidence Classifier

| Strongest evidence | Answer posture |
|---|---|
| Current UI shows the entry for this user | Give the exact path and normal next step. |
| Verified KB confirms it with conditions | Include the conditions before the action. |
| Availability setting, environment rule, provider metadata, plan gate, or account gate | Say availability may depend on the current account/environment; ask for current UI state if needed. |
| Private engineering trace/API/translation/test/demo/old doc only | Say the KB does not confirm public availability; do not expose implementation details in a normal user answer. |
| Sources conflict | Name the safe distinction and offer the confirmed alternative. |

## Decision Ladder

1. Load the direct feature card if one exists.
2. Classify the strongest evidence with the table above.
3. Check the current user-facing UI path in the loaded card or help article.
4. Check whether availability depends on account, plan, environment, feature
   flag, connector metadata, provider setup, Electron host, or local capability
   availability.
5. If the only evidence is an old doc, demo/showcase copy, translation string,
   old screenshot, non-user-facing API, test, route, or private engineering
   trace, say the current KB does not confirm that the feature is publicly
   available for every account.
6. Give the nearest confirmed alternative for the user's real task.
7. If the user needs account-specific confirmation, ask for minimal diagnostic
   context and avoid roadmap promises.

## Common Cases

| User asks about | Safe answer |
|---|---|
| Run History missing | Current real left sidebar does not confirm a shipped Run History section. Use chat history, **Used tools**, **Schedules**, and **Artifacts** as current alternatives. |
| Native mobile app | Native iOS/Android work is documented, but public App Store/Google Play availability is not confirmed by this KB. Separate mobile web layout from native app release. |
| Lark or Discord channel | Check **left sidebar > Channels**. Lark is gated/hidden in prod by current frontend visibility; Discord has UI traces but still needs account/environment/provider setup confirmation. |
| Exact model names | Answer by visible tiers: Fast, Standard, Ultra. Exact provider/model mapping can drift and should not be presented as a permanent exhaustive list. |
| Notion or future connector | If only roadmap/seed docs mention it, say it is not confirmed as a current connector. Offer currently visible connector options. |
| Google Workspace missing | Google Workspace is a current connector when visible. If the row is missing, ask for current UI/account context instead of treating it as unlaunched. |
| Referrals missing or disabled | Treat it as feature-gated and account/environment dependent. Do not promise the invite program is live for every account. |
| Screenshot or doc shows a button | A screenshot/doc can be stale, demo-only, or account-specific. Ask for the current page and visible UI state. |
| Private engineering trace, route, API, or translation mentions a feature | Treat it as a non-public trace only. Do not say it is live unless the current UI or verified KB confirms it. |
| Connector CLI local login | Hidden local-dev handoff, not normal production connector management. |
| Internal memory APIs | Do not present internal memory/search tool names as a customer Memory settings page or self-serve delete/export controls. |
| Agent email/SMS | Implementation traces exist, but current runtime hides raw agent email/SMS tools from model visibility. Do not promise every user has an agent mailbox or phone number. |
| Design/playground routes | Development or design-gated surfaces. Do not treat them as customer product capabilities. |

## Response Pattern

1. Answer what is currently confirmed.
2. Say that account availability depends on current settings/environment when
   that is true.
3. Give the user a concrete place to check.
4. Distinguish "there are product traces" from "this is visible in the current
   account."
5. Do not promise release dates, beta access, waitlists, or roadmap timing.
6. Do not expose source paths, internal endpoints, feature flag names, seed
   files, or implementation details in customer-facing answers.
7. If the user needs a workaround, give the nearest confirmed alternative.

## Example

> I can confirm that the product has traces of this entry point or capability,
> but whether it is enabled for your account depends on the current `/chat` UI.
> Check the relevant Channels or Connectors section in the left sidebar. If it
> is not there, it may not be enabled for your current account or environment.

## Customer-Facing Template

> This feature is not necessarily broken. Some MoClaw entries depend on account,
> plan, environment, feature flag, connector setup, or provider configuration.
> Screenshots or old docs can also come from demos, internal environments, or
> earlier versions.
>
> First check the relevant left-sidebar section in your current account. If the
> entry is not there, I can help with a currently available alternative for the
> task you are trying to complete. For account-specific confirmation, send the
> account email, current page screenshot, plan, source of the screenshot/doc you
> saw, and the task you wanted to complete.

## Ask For

- Current environment if the user knows it: prod, test, or local.
- Screenshot or current left-sidebar entry points.
- Account plan.
- Service they want to connect.
- Actual task they want to complete, so you can offer an alternative.
- Where they saw the feature: current UI, old docs, screenshot, video, demo, or
  coworker account.
- Minimal account diagnostics: account email, page path, visible error text,
  approximate time, and timezone.

## Forbidden Claims

- Do not say it is launching soon.
- Do not say it is available to every user.
- Do not equate internal engineering traces with public release.
- Do not equate demo/showcase copy, translation keys, or internal APIs with
  user-visible UI.
- Do not invent ETA, waitlist, beta eligibility, or roadmap promises.
- Do not say a screenshot proves this is a bug.
- Do not say the feature will never exist because the user's account lacks it.
- Do not expose source paths, internal endpoints, feature-flag names, seed
  files, or implementation details in normal user-facing answers.
