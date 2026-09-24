---
id: moclaw.reference.native_mobile_status
title: Native Mobile Status
type: reference
product_area: mobile
audience: support
status: verified
last_reviewed_at: 2026-06-09
applies_to:
  plans: [free, trial, pro]
  environments: [local, test, prod]
  platforms: [mobile]
---

# Native Mobile Status

## Direct Answer

MoClaw has native iOS and Android client work documented in the repository, but
public App Store / Google Play availability is not confirmed by the current KB.
Support should distinguish mobile web layout from native mobile app release
status.

## Confirmed From Current Sources

- Native mobile clients live under `client/ios` and `client/android`.
- They are intended as pure native chat apps, not WebView shells.
- They use the same Session, Thread, Message, and Streaming Message protocol as
  the web app.
- Native authentication and network integration were documented as deferred
  until the first signed-in product flow.
- Release-channel docs mention dev, internal, beta, and prod tracks, but this is
  not the same as public availability confirmation.

## Answering Rule

When a user asks "Is there a mobile app?":

1. If they mean using MoClaw from a phone browser, load
   `moclaw.ui.mobile_layout`.
2. If they mean a native iOS/Android app, say native clients are documented in
   product work but public release status should be checked in the current
   product UI or with support.
3. Do not claim App Store or Google Play availability unless a current release
   source confirms it.

## Do Not Say

- Do not say the native app is publicly launched for all users.
- Do not say MoClaw has no mobile work.
- Do not confuse mobile web responsive layout with native app distribution.
- Do not promise beta, TestFlight, Play closed testing, or production access
  without product confirmation.

## Related Cards

- `moclaw.ui.mobile_layout`
- `moclaw.playbooks.feature_not_shipped_yet`
