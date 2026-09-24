---
id: moclaw.reference.feature_flags
title: Feature Flags
type: reference
product_area: platform
audience: support
status: verified
owner: product
last_reviewed_at: 2026-07-15
source_paths:
  - maxgent/client/webapp/src/lib/config.ts
  - maxgent/client/webapp/src/lib/config.test.ts
  - maxgent/client/webapp/src/lib/connector-visibility.ts
  - maxgent/client/webapp/src/routes/connector.local.login.tsx
  - maxgent/client/webapp/src/routes/referral.accept.tsx
  - maxgent/client/webapp/src/routes/playground.tsx
  - maxgent/docs/referral-program-mvp.md
  - maxgent/server/app-server/app/core/config.py
  - maxgent/server/app-server/app/domains/memory/routes/internal.py
  - maxgent/server/app-server/deployment/values/test.yaml
  - maxgent/server/app-server/deployment/values/prod.yaml
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Feature Flags

## Direct Answer

Some MoClaw features are gated by runtime config, environment, or account state.
If a user cannot see a button or entry point, support should check feature
availability before saying the feature does not exist.

A feature can be present in private engineering traces, routes, translations,
tests, old docs, or service APIs without being a launched customer-facing
feature. For support answers, current visible UI and verified KB scope outrank
non-public product traces.

## Evidence Classes

| Evidence | How to treat it |
|---|---|
| Visible in the user's current UI | Give the exact visible path and normal troubleshooting steps. |
| Verified KB card says available, with conditions | Answer with the documented account, plan, environment, provider, or permission conditions. |
| Availability setting, environment rule, provider metadata, or account gate controls visibility | Say it may not be enabled for the current account/environment; do not promise universal availability. |
| Private engineering trace, route, API, translation string, test, demo/showcase, or old doc only | Treat as a non-public trace, not proof of public launch. Offer a confirmed alternative. |

## Current Web Feature Flags

| Feature | Config rule | Support meaning |
|---|---|---|
| Voice Message | `FEATURE_VOICE_MESSAGE !== false` | Voice UI is default-on, but still needs backend voice setup. |
| Google Workspace | Runtime availability setting | Google Workspace is a current connector when visible in the product UI; runtime config can still affect whether a given account/environment sees it. |
| Direct Session Events | `FEATURE_DIRECT_SESSION_EVENTS === true` | Streaming/event behavior can differ by environment. |
| Referrals | `FEATURE_REFERRALS === true` | Referral CTA/accept flow is hidden or disabled when off. |

## Code-Backed But Hidden Or Limited Surfaces

| Surface | Current evidence | Support handling |
|---|---|---|
| Connector CLI local login | `/connector/local/login` is gated outside prod. | Treat as a local-dev terminal handoff, not normal production connector management. |
| Lark channel | Channel registry includes Lark, but frontend visibility hides it in `prod`. | If missing, say it may not be enabled; do not promise production Lark availability. |
| Discord channel | Current frontend visibility shows Discord, but binding still needs provider/account setup. | Guide only when the row is visible; otherwise use the missing-feature playbook. |
| Referrals | Web and backend have referral flows, but production deployment keeps referrals disabled until enabled. | If invite UI says unavailable or the CTA is missing, do not promise live referral rewards. |
| Playground route | The route is gated to development or design-enabled builds. | Treat it as an internal demo surface, not a customer product capability. |
| Internal memory routes | Server memory routes are disabled by default unless explicitly enabled. | Do not present `memory_search`/`memory_get` or memory APIs as a customer Memory settings page. |
| Agent email/SMS | Implementation traces exist, but current runtime hides raw agent email/SMS tools from model visibility. | Do not promise every user has an agent mailbox or phone number. |
| Run History | Showcase/i18n/internal runtime traces exist, but current real left sidebar does not confirm a Run History section. | Offer chat history, **Used tools**, **Schedules**, and **Artifacts** as current alternatives. |

## Environment Notes

- Runtime `config.js` can override build-time Vite variables.
- Test deployment values enable referrals; production values currently disable
  referrals.

## Support Implications

- First classify the evidence. If the evidence is only a non-public trace or is
  hidden behind a gate, answer conditionally and route to confirmed
  alternatives.
- If Google Workspace is missing, do not call it unlaunched. Treat it as a
  current connector whose visibility may depend on the user's current UI,
  account, or environment.
- If a referral link shows disabled/unavailable, do not promise the invite
  program is live.
- If voice is hidden, check the feature flag and backend provisioning before
  describing it as a browser issue.

## Do Not Say

- Do not tell users to change environment variables.
- Do not promise feature availability across all accounts and environments.
- Do not describe a hidden feature as fully launched.
- Do not say a non-public trace means "the feature is live."
- Do not use feature flags as a substitute for product decisions in public
  answers.

## Related Cards

- `moclaw.reference.connectors_status`
- `moclaw.reference.local_desktop_permissions`
- `moclaw.reference.chat_composer_controls`
- `moclaw.playbooks.feature_not_shipped_yet`
