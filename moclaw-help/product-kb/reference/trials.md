---
id: moclaw.reference.trials
title: Trial Availability And Pro Checkout Trial
type: reference
product_area: billing
audience: user
status: verified
owner: product
last_reviewed_at: 2026-06-09
source_paths:
  - maxgent/server/app-server/app/services/trial.py
  - maxgent/server/app-server/app/routers/public_subscription.py
  - maxgent/client/webapp/src/components/settings/trial-section-view.tsx
  - maxgent/client/webapp/src/components/subscription/trial-dialog.tsx
  - maxgent/client/webapp/src/components/settings/account-section.tsx
  - maxgent/client/webapp/src/routes/_authenticated/chat.tsx
  - maxgent/server/app-server/app/routers/subscription_checkout.py
  - maxgent/client/webapp/src/components/subscription/pricing-table.tsx
  - maxgent/client/webapp/src/i18n/locales/en.json
  - maxgent/client/webapp/src/i18n/locales/zh.json
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Trial Availability And Pro Checkout Trial

## Direct Answer

Product decision as of 2026-06-09: MoClaw does **not** currently offer a public
30-day no-card MoClaw Trial with a one-time 1,000-credit grant. New or free
users should expect the product-access paywall / upgrade flow when they do not
have active paid entitlement.

If a user asks whether Trial is 30 days or 3 days:

- Do **not** tell them there is a current 30-day no-card MoClaw Trial.
- If the current checkout UI shows a 3-day Pro trial, treat it as a Stripe Pro
  checkout state, not as a separate no-card MoClaw Trial.
- If the user sees a paywall or **Upgrade to Pro**, that is expected under the
  current product posture.

## Rules

### Current Public Support Posture

- No current public 30-day no-card MoClaw Trial.
- No current one-time 1,000-credit MoClaw Trial grant.
- No automatic 7-day registration trial.
- No daily trial-credit refill.
- Free/no-entitlement users should be routed to the visible paywall or
  **Upgrade to Pro** action.
- Do not promise any trial eligibility unless the current account UI explicitly
  shows a trial checkout action.

### Legacy / Hidden MoClaw Trial Sources

Several code and seed sources still mention a self-serve MoClaw Trial:

- `server/app-server/app/services/trial.py` contains a 30-day, one-shot
  trial-service implementation guarded by `subscription.allow_free_trial`.
- `trial-section-view.tsx`, `trial-dialog.tsx`, and i18n still contain copy such
  as **Try MoClaw for 30 days**, **Start Free Trial**, and
  **1,000 credits, valid for 30 days**.
- `subscription_checkout.py` has a stale endpoint comment saying
  "1k credits/day" for MoClaw Trial.
- E2E seed knowledge mentions a 7-day automatic registration trial.

Treat these as stale, hidden, disabled, or non-current for public support
answers unless product re-enables a trial program and updates the support
posture.

### Pro Checkout Trial

Source: `server/app-server/app/routers/subscription_checkout.py`

- Pro price is $20/month.
- Code can set `trial_period_days = 3` for first-time Pro checkout eligibility.
- Pro normally grants 1,000 credits/month.
- Pricing dialog user-visible copy includes **Start 3-day free trial**,
  **3-Day Free**, and **then $20 / month** when `trialEligible` is true.
- `trialEligible` in pricing/checkout means Stripe Pro trial eligibility. Do not
  confuse it with the old self-serve MoClaw Trial code path.
- Canceling Stripe Pro `trialing` is immediate in current server code and
  revokes remaining trial credits.

## Edge Cases

- If a user sees **Try MoClaw for 30 days** or **Start Free Trial**, treat that
  as stale, hidden, or account/environment-specific until the current UI proves
  otherwise. Do not present it as the normal current onboarding path.
- If a user sees **Start 3-day free trial** in Pro checkout, answer it as a Pro
  subscription checkout state that can become paid Pro unless canceled through
  the billing flow.
- Public marketing surfaces can still read `/api/public/subscription/gating`
  for a global trial flag, and authenticated surfaces can still call
  `/api/subscription/trial/eligibility`. These endpoints are implementation
  traces, not proof of current public trial availability.
- Legacy or already-existing trial accounts may still appear as account-specific
  states. Answer from the user's visible **Settings > Account** and
  **Settings > Usage** state.

## User-Facing Answer Pattern

Use this wording shape:

> MoClaw does not currently offer a public 30-day no-card Trial with a one-time
> 1,000-credit grant. If your account shows the paywall or **Upgrade to Pro**,
> that is expected. If checkout shows a 3-day Pro trial, treat that as part of
> the Pro subscription checkout flow, not as the old no-card MoClaw Trial.

## Do Not Say

- Do not say registration automatically grants a 7-day trial.
- Do not say there is a current public 30-day MoClaw Trial.
- Do not say there is a current one-time 1,000-credit MoClaw Trial grant.
- Do not promise eligibility for every account; answer from the current visible
  account UI.
- Do not say MoClaw Trial credits refill daily.
- Do not say a 3-day Pro trial always remains active until trial end after
  cancellation.

## Related Cards

- `moclaw.reference.pricing_and_credits`
- `moclaw.reference.billing_plan_lifecycle`
- `moclaw.troubleshooting.credits_locked`
