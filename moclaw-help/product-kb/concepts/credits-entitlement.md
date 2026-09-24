---
id: moclaw.concepts.credits_entitlement
title: Credits And Computer Entitlement
type: concept
product_area: billing
audience: user
status: verified
owner: product
last_reviewed_at: 2026-08-06
source_paths:
  - maxgent/client/webapp/src/routes/_authenticated/chat.tsx
  - maxgent/client/webapp/src/lib/chat-usage-gate.ts
  - maxgent/client/webapp/src/stores/credits-store.ts
  - maxgent/server/app-server/app/routers/subscription_checkout.py
  - maxgent/server/app-server/app/services/trial.py
  - maxgent/client/webapp/src/i18n/locales/en.json
  - product-kb/reference/credit-pack-limits.md
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Credits And Computer Entitlement

## Direct Answer

MoClaw billing and access should be explained in two layers:

- **Computer Entitlement**: whether the account can use the AI Cloud Computer.
- **Credits**: usage balance consumed by model, media, or tool activity.

## Key Rule

Credits are not product access. Without active computer entitlement, a credit
balance can still be visible but cannot be spent.

## Common Confusion

- Buying only a Credit Pack does not extend Pro or Trial access.
- Cancellation is not a refund.
- Credits can expire, and they can also be locked because entitlement expired.

## Related Cards

- `moclaw.reference.pricing_and_credits`
- `moclaw.reference.credit_pack_limits`
- `moclaw.reference.trials`
- `moclaw.troubleshooting.credits_locked`
