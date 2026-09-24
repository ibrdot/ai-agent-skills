---
id: help.billing.pricing_credits_trials
title: Pricing, Credits, And Trials
audience: user
status: verified
source_cards:
  - moclaw.reference.pricing_and_credits
  - moclaw.reference.credit_pack_limits
  - moclaw.reference.trials
  - moclaw.concepts.credits_entitlement
  - moclaw.troubleshooting.credits_locked
last_reviewed_at: 2026-08-06
---

# Pricing, Credits, And Trials

MoClaw billing has two separate ideas:

- **Entitlement**: whether your account can use the AI Cloud Computer.
- **Credits**: usage balance consumed by model, media, or tool activity.

Credits are not the same as product access. If your entitlement expires, your
credit balance may still be visible but locked.

## Pro And Credits

Current product sources show Pro as the main paid plan for AI Cloud Computer
access. Current checkout and UI sources show Pro at $20/month with 1,000
credits/month.

Credits are usage balance. A Credit Pack can add credits, but it does not
extend Pro or Trial access by itself. Current Credit Pack UI sources show
100 credits per $1 and a maximum of $200 / 20,000 credits. Current billing
implementation creates purchased Credit Pack wallets with a 1-year expiry; use
**Settings > Usage** for account-specific expiry dates instead of assuming a
missing visible date means "never expires."

## Trial Concepts

MoClaw does not currently offer a public 30-day no-card Trial with a one-time
1,000-credit grant. If you reach `/chat` without active access and see a
paywall or **Upgrade to Pro**, that is expected.

If the current checkout UI shows **Start 3-day free trial**, that is a Pro
subscription checkout state. It is not the same thing as a 30-day no-card
MoClaw Trial, and it can later become the monthly Pro subscription unless
canceled through the billing flow.

If you see old copy such as **Try MoClaw for 30 days**, **Start Free Trial**, or
**1,000 credits, valid for 30 days**, do not rely on it as the current public
offer. Use the action shown by your current account UI.

MoClaw Trial credits do not refill every day, and current support guidance
should not promise any public MoClaw Trial credit grant.

## Why Credits Can Be Locked

Credits can be visible but unusable when:

- Pro or Trial access expired.
- You bought credits but do not have active product access.
- Billing state is still refreshing after checkout.
- A selected model or feature requires Pro.

Check **Settings > Usage** for credits, **Settings > Account** for plan state,
and **Settings > Billing** for payment history.

If `/chat` shows **No active subscription**, restore access first. Buying more
credits alone may not unlock MoClaw if Pro or Trial access is inactive.

If `/chat` shows **Credits exhausted**, check **Settings > Usage** and use the
visible action to upgrade, buy credits, or restore the relevant plan state.

If `/chat` shows **Billing status is temporarily unavailable**, MoClaw is
retrying the billing/subscription check. Refresh **Settings > Usage** and
**Settings > Account** after a short wait. This message alone does not prove
that your payment failed or that your credits were removed.

## Refunds

Cancellation and refund are different operations. Refund outcomes require
billing review; do not assume the product can automatically promise a refund or
proration.

## Related Articles

- `billing/buy-credit-packs.md`
- `billing/cancel-reactivate-refunds.md`
- `troubleshooting/common-errors.md`
