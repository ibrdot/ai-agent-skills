---
id: moclaw.reference.account_identity_and_data_requests
title: Account Identity And Data Requests
type: reference
product_area: account
audience: support
status: verified
last_reviewed_at: 2026-06-09
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [web]
---

# Account Identity And Data Requests

## Direct Answer

MoClaw currently shows account identity in the bottom-left user menu and
**Settings > Account**, but current source-backed UI does not show self-serve
controls for editing email, display name, avatar, deleting an account, exporting
data, or deleting account data.

For profile changes, data deletion, data export, retention, DPA, model-training
policy, or legal privacy requests, use a support escalation path and avoid
making policy or timeline promises without an owner-reviewed policy.

Treat account identity, account/data requests, subscription cancellation, and
refund review as related but separate workflows. A user may need more than one
route.

## Current In-App Account Surfaces

| Surface | Current Behavior |
|---|---|
| Bottom-left user menu | Shows display name/email, plan card, Settings, Privacy Policy, Terms, and Logout. |
| Settings > Account | Shows signed-in profile, current plan/subscription state, and plan actions. |
| Settings > About | Links Privacy Policy and Terms. |
| Signed-in profile data | Includes the user id, email, and email verification state. |

## Profile Identity Rules

- The displayed profile is fetched from current auth/profile data.
- The profile shows an email only when the stored user email is verified.
- Display name can fall back to auth profile data or a verified email-derived
  name.
- Current Account UI does not expose profile edit controls.
- Profile changes may need to happen through the user's sign-in provider or via
  support, depending on the identity source.
- If the user cannot sign in, still collect the account email and visible login
  error, then route through sign-in troubleshooting plus the account/data request
  path.

## Data And Account Request Routing

Use this card when the user asks to:

- change email, display name, or avatar;
- delete or close their MoClaw account;
- delete workspace/account data;
- export data;
- ask about data retention, model training on customer data, legal privacy
  rights, DPA, GDPR, CCPA, or similar legal/compliance topics.

## Safe Escalation Fields

Ask only for:

- account email used to sign in;
- request type: profile change, account deletion, data deletion, data export,
  retention question, model-training-policy question, or legal/privacy request;
- brief description of the requested action;
- whether there is an active Pro subscription, open billing issue, or recent
  checkout that support should consider;
- whether the user can still sign in to the account;
- preferred contact email if different from the account email.

Do not request identity documents, passwords, OAuth tokens, API keys, full raw
logs, browser storage, or payment card details in the first response. If a later
owner-approved verification process is required, that should happen outside the
general support answer.

## Billing Interaction

Account deletion, data deletion, subscription cancellation, and refund review are
different operations. If the user has paid Pro, route cancellation/reactivation
questions to the billing lifecycle cards and refund questions to billing
escalation. Do not imply that deleting an account automatically cancels,
refunds, or resolves charges unless product/billing policy confirms it.

If the user asks whether deletion removes invoices, payment history, or Stripe
records, escalate to billing/privacy owners instead of guessing. Do not promise
removal of legally retained billing records without an owner-reviewed policy.

## Do Not Say

- Do not tell users they can delete an account from Settings.
- Do not promise a deletion/export/retention timeline.
- Do not promise GDPR, CCPA, SOC 2, ISO, HIPAA, DPA, or similar legal outcomes.
- Do not promise whether customer data is or is not used for model training
  without an owner-reviewed policy.
- Do not claim MoClaw can edit the user's email, avatar, or display name inside
  Settings.
- Do not ask for passwords, full card numbers, CVV, API keys, OAuth tokens,
  device codes, government IDs, browser storage, full raw logs, or unrelated
  personal data in the first support response.
- Do not expose internal auth subject IDs in customer-facing replies unless an
  owner-approved support process calls for it.

## Related Cards

- `moclaw.reference.account_profile_and_user_menu`
- `moclaw.reference.user_preferences_and_settings`
- `moclaw.playbooks.security_privacy_answering`
- `moclaw.reference.billing_plan_lifecycle`
- `moclaw.playbooks.billing_refund_escalation`
