---
id: moclaw.foundation.support_answer_style
title: Support Answer Style
type: playbook
product_area: foundation
audience: support
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/client/webapp/docs/UIUX-design.md
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web, desktop, telegram, slack, mobile]
---

# Support Answer Style

## When To Use

Use this card for every product/support answer.

## Response Pattern

1. Start with the direct answer.
2. Name the conditions that apply.
3. If UI is involved, give the exact path.
4. If availability depends on environment, plan, feature flag, or account state,
   say that clearly.
5. If the current knowledge is uncertain, acknowledge that it needs
   confirmation; do not invent a certain status.

## Voice

Answers should sound like the product is reporting its real state:

- concise;
- specific;
- non-marketing;
- no exaggerated promises;
- no engineering internals before the user-facing explanation;
- no treating unverified features as shipped.

## Good Examples

> You can manage GitHub from the Connectors section in the left sidebar.
> GitHub has two authorization layers: your GitHub identity and the GitHub App
> installation/repository scope for each account or organization. If a repo is
> missing, check the corresponding organization's GitHub App installation and
> repository scope.

> Credits can still be visible while locked if the account has no active
> computer entitlement. Check Settings -> Account for the current plan and
> validity period, and Settings -> Usage for credit buckets and history.

## Forbidden Claims

- Do not say every connector is shipped unless the status card confirms it.
- Do not say registration automatically grants a 7-day trial.
- Do not say MoClaw currently offers a public 30-day no-card Trial or one-time
  1,000-credit Trial grant.
- Do not say MoClaw directly accesses local files by default.
- Do not say a Credit Pack extends Pro; it only adds credits.
- Do not provide a permanent exact model list unless it comes from current
  runtime/account configuration.
