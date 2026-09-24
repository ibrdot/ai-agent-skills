---
id: moclaw.ui.billing_and_usage_surfaces
title: Billing And Usage Surfaces
type: ui_map
product_area: billing
audience: user
status: verified
last_reviewed_at: 2026-07-23
applies_to:
  plans: [free, trial, pro]
  environments: [test, prod]
  platforms: [web]
---

# Billing And Usage Surfaces

## Direct Answer

MoClaw billing and usage UI is split across **Settings > Account**,
**Settings > Usage**, **Settings > Billing**, **Settings > API Keys**, the
New Chat usage badge, and the bottom-left user menu.

Use this card for "where do I find it?" questions. Use the billing reference
cards for policy claims about pricing, trials, credit expiry, refunds, or
entitlement.

## Main Surfaces

| Surface | Use For |
|---|---|
| New Chat usage badge | Compact available-credit balance in the New Chat header; hover card with credit buckets; opens Settings > Usage. |
| Bottom-left user menu | User identity, plan card, upgrade/buy/resubscribe action, and credits shortcut. |
| Settings > Account | Current plan, subscription status, validity period, upgrade, cancel, or keep subscription. |
| Settings > Usage | Total credits, credit buckets, usage action, Show on home toggle, and credit history. |
| Settings > Billing | Payment History for subscription and Credit Pack invoices/receipts. |
| Settings > API Keys | Codex identity when available; Connect Codex flow. |
| Pricing dialog | Subscription checkout for non-subscribers; Credit Pack checkout for paid users. |

## Settings Layout

Desktop Settings uses left-side tabs:

1. General
2. Appearance
3. Account
4. Usage
5. Billing
6. API Keys
7. About

Mobile Settings is a sheet with these sections stacked vertically. Do not tell
mobile users to use a left-side Settings tab.

## Usage Surface Details

**Settings > Usage** can show:

- total available credits;
- a tooltip explaining credit consumption order;
- credit buckets for bonus credits, monthly quota, and purchased credits;
- the primary action: **Upgrade**, **Buy Credits**, or **Keep subscription** /
  resubscribe depending on subscription state;
- a **Show on home** toggle that controls the New Chat usage badge;
- credit history with **All**, **Credit**, and **Debit** filters;
- retry or stale-data notices when a refresh fails.

The usage badge is shown only in the New Chat header for signed-in users outside
the mock adapter when **Show on home** is enabled. Session and feature pages do
not show it.

## Billing Surface Details

**Settings > Billing** currently focuses on **Payment History**. It can show:

- invoice rows for subscriptions and Credit Packs;
- filter tabs for **All**, **Subscription**, and **Credit Pack**;
- paid status;
- amount and date;
- PDF download links when available;
- hosted invoice or receipt links when available;
- retry and empty states.

Billing does not by itself promise refunds, prorations, charge-dispute outcomes,
or invoice corrections.

## Account Surface Details

**Settings > Account** shows the signed-in profile and current plan/subscription
identity. Depending on state, its action can be:

- upgrade to Pro;
- cancel subscription;
- keep subscription / reactivate.

Cancellation uses a confirmation dialog. Paid Pro cancellation and trialing Pro
cancellation have different mechanics, so route policy questions to the
subscription lifecycle cards.

## Pricing Dialog Details

The pricing dialog changes by account state:

- non-subscribers see the subscription view and a checkout/upgrade action;
- paid users see the Credit Pack view with a credit-pack slider and checkout
  action;
- checkout redirects externally through the billing provider.

The current UI source uses `$20 / month` for the Pro subscription and 100
credits per $1 in the Credit Pack slider. Treat these as current UI facts, and
load billing reference cards before making durable pricing promises.

Current public support posture is no public 30-day no-card MoClaw Trial. Do not
promise a **Start Trial** action unless the user's current account UI explicitly
shows one.

## Do Not Say

- Do not say **Settings > Billing** is where users cancel; cancellation is in
  Account/usage-driven subscription actions.
- Do not say Credit Packs extend Pro, Trial, or subscription entitlement.
- Do not promise every invoice has both PDF and hosted receipt links.
- Do not promise refunds, prorations, or charge-dispute outcomes from the UI.
- Do not tell mobile users to click a left Settings tab.
- Do not use this UI map alone as the source for pricing, trial, or expiry
  policy.

## Related Cards

- `moclaw.ui.settings`
- `moclaw.reference.billing_plan_lifecycle`
- `moclaw.reference.pricing_and_credits`
- `moclaw.reference.credit_pack_limits`
- `moclaw.reference.trials`
- `moclaw.reference.billing_invoices`
- `moclaw.reference.credit_expiry_and_consumption_order`
- `moclaw.how_to.buy_credits_or_upgrade`
- `moclaw.how_to.cancel_or_reactivate_pro`
- `moclaw.troubleshooting.credits_locked`
- `moclaw.troubleshooting.checkout_payment_not_updated`
