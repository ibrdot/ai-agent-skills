---
id: help.product.feature_availability
title: Why A Feature May Not Appear
audience: user
status: verified
source_cards:
  - moclaw.playbooks.feature_not_shipped_yet
  - moclaw.reference.feature_flags
  - moclaw.reference.connectors_status
  - moclaw.reference.chat_channel_binding_flows
  - moclaw.reference.local_desktop_permissions
  - moclaw.reference.native_mobile_status
  - moclaw.reference.model_tiers
  - moclaw.reference.run_history_status
last_reviewed_at: 2026-07-29
---

# Why A Feature May Not Appear

Some MoClaw features depend on account, plan, environment, connector metadata,
or feature flags. If you do not see a button or entry point, it does not always
mean the product is broken.

Screenshots, demo pages, older docs, videos, non-public builds, or another
user's account can also show features that are not visible for your current
account.

## What To Check

- Your current plan and account state.
- The current workspace or chat where you expect the feature.
- The relevant product surface, such as the desktop-only Cloud Computer button
  in the top Chat header or the left-sidebar **Connectors**, **Channels**,
  **Artifacts**, and **Skills** entries.
- Whether the feature requires a connected service, active Pro, Local Desktop,
  provider setup, or account-level enablement.
- Whether you are looking at mobile web, desktop web, or a native mobile app.
- Whether the doc or screenshot you saw is current for your account.
- Whether the feature is actually visible in your current UI, not just mentioned
  in an old doc, demo, or non-public build.

## Common Examples

- Google Workspace is a current connector when it appears in **left sidebar >
  Connectors**. If you do not see it, support should check your current UI and
  account context rather than assume the connector is unlaunched.
- Lark, Discord, and some channel entries may be account or environment gated.
- Local development login flows, design pages, playground pages, and memory APIs
  are not normal customer-facing product entry points.
- Run History may appear in demo/showcase copy or old screenshots, but the
  current left sidebar source does not confirm a shipped **Run History**
  section. Use chat history, **Used tools**, **Schedules**, and **Artifacts** as
  current alternatives.
- Native mobile clients may exist in product work without being publicly
  available to every user.
- Exact model names can change; the UI shows user-facing model tiers.
- Future or roadmap connectors may appear in old planning material before they
  are visible in **left sidebar > Connectors**.

## If You Saw It In A Screenshot Or Doc

A screenshot, doc, demo, or non-public build is useful, but it is not proof that
the feature is available for every account. It may come from an internal
environment, beta account, demo, older build, feature-gated rollout, or
implementation work that is not exposed in your current UI.

When checking availability, use your current product UI first. If the feature is
missing, support can compare your current UI state with the source you saw.

## Current Alternatives

- For previous task context, use chat history or load earlier messages.
- For recent tool calls and errors, open **Used tools** in the message.
- For scheduled work, open **left sidebar > Schedules**.
- For generated outputs, open **left sidebar > Artifacts**.
- For channels, check **left sidebar > Channels**.
- For data connectors, check **left sidebar > Connectors**.
- For model choice, use the tier selector shown in the current chat UI.

## How To Ask Support

Send:

- Account email.
- The feature you expected.
- The page or section where you expected it.
- Current plan if relevant.
- Screenshot of the visible UI state.
- The screenshot, doc, or video where you saw the feature, if available.
- The task you are trying to complete, so support can suggest a current
  alternative.

## Do Not Assume

Do not assume a feature is available to all users just because it appears in a
doc, screenshot, or internal product plan. Also do not assume the feature is
permanently unavailable just because it is missing from your current UI. Use the
current UI and support confirmation for your account.
