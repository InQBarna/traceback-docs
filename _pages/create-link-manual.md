---
layout: default
title: Create Dynamic Links Manually
permalink: /create-link-manual/
---

# Create Dynamic Link manually

When opened, Traceback resolves the parameters and routes the user to the correct destination based on platform and install state.

---

## Parameter Reference

The following table lists the supported parameters.

| Parameter | Required | Description | Example |
|-----------|----------|-------------|---------|
| `link` | Yes | Deep link destination inside your app or website | `https://example.com/product/123` |
| `utm_source` | No | Attribution source | `newsletter` |
| `utm_medium` | No | Attribution medium | `email` |
| `utm_campaign` | No | Campaign name | `spring_launch` |
| `utm_term` | No | Attribution term (e.g. paid search keyword) | `running+shoes` |
| `utm_content` | No | Attribution content, used to differentiate similar content or links within the same ad | `banner_ad` |
| `st` | No | Social share title, overrides the Firestore-stored title for this URL only | `My Campaign` |
| `sd` | No | Social share description, overrides the Firestore-stored description for this URL only | `Open this content in the app` |
| `si` | No | Social share image URL, overrides the Firestore-stored image for this URL only | `https://example.com/image.png` |
| `cte` | No | Disables clipboard tracking on the preview page (`cte=false`) for links with no matching Firestore campaign | `false` |
| `ofl` | No | Desktop-only fallback destination when no `link` param is supplied, for links with no matching Firestore campaign | `https://example.com/fallback` |

---

## Parameter Encoding

All parameter values must be URL-encoded. In particular the `link` parameter must be encoded if it contains its own query parameters.

---

## Considerations

Social metadata URLs should be publicly accessible.

---

## Behavior Notes

- If platform-specific parameters are missing, Traceback attempts best-effort routing.
- Attribution parameters are stored and passed to the application on open.
- Manual links behave identically to links created via Firestore, REST API, or Traceback Manager.
- If a link is opened without a `utm_source` but the browser sends a `Referer` header, Traceback automatically fills `utm_source` with the referrer's domain and sets `utm_medium=referral_traceback`, so referral traffic is still attributed even without explicit UTM parameters.
- `st`/`sd`/`si` are resolved server-side when the preview page is rendered, so they affect both the `<meta>` tags used by social-media crawlers (WhatsApp, iMessage, Slack, etc.) and what's shown in the browser — they never change the underlying Firestore document, only the response for this specific request. This is why they're safe to accept directly from the URL, unlike the Apple campaign parameters below.
- `cte=false` only takes effect when the path has no matching Firestore campaign (clipboard tracking then defaults to enabled). For an existing campaign, `clipboardTrackingEnabled` is a value the link's creator chose deliberately via the REST API, Firestore, or Traceback Manager — the URL can never override it, for the same reason `at`/`ct`/`mt`/`pt` can't: it would let anyone who forwards the link silently flip a setting they don't own.
- `ofl` only takes effect when the path has no matching Firestore campaign, for the same reason as `cte`: for an existing campaign, `otherFallbackLink` is a destination the creator chose deliberately, and the URL can never redirect visitors somewhere else instead.
- `otherFallbackLink`/`ofl` is **desktop-only**. On iOS or Android, when this Traceback install has no app configured for that platform (a "dead end"), the `link` parameter is used as a browser fallback instead — the button is enabled and relabeled "Open in browser" — alongside the existing "app not available yet" message. If there's no `link` parameter either, the button is disabled and only the message is shown. Fallback order on desktop is `link` → the campaign's `followLink` → `otherFallbackLink`/`ofl` → no redirect; on iOS/Android it's `link` → app/store route → "app not available" message.

---

## Old firebase dynamic links mapping

The following table lists the old legacy firebase dynamic links

| Parameter | Required | Description | Example |
|-----------|----------|-------------|---------|
| `link` | Yes | Deep link destination inside your app or website | `https://example.com/product/123` |
| `ibi` | No | UNSUPPORTED* iOS bundle identifier | `com.example.app` |
| `isi` | No | UNSUPPORTED* iOS App Store ID | `123456789` |
| `apn` | No | UNSUPPORTED* Android package name | `com.example.app` |
| `afl` | No | UNSUPPORTED* Android fallback URL | `https://example.com/android` |
| `ifl` | No | TODO\*\* iOS fallback URL | `https://example.com/ios` |
| `ofl` | No | Web/desktop fallback URL | `https://example.com/web` |
| `utm_source` | No | Attribution source | `newsletter` |
| `utm_medium` | No | Attribution medium | `email` |
| `utm_campaign` | No | Campaign name | `spring_launch` |
| `at` | No | UNSUPPORTED\*\*\* Apple affiliate token | `affiliate123` |
| `ct` | No | UNSUPPORTED\*\*\* Apple campaign text | `summer_campaign` |
| `mt` | No | UNSUPPORTED\*\*\* Apple media type | `8` |
| `pt` | No | UNSUPPORTED\*\*\* Apple provider ID | `provider456` |
| `st` | No | Social share title | `My Campaign` |
| `sd` | No | Social share description | `Open this content in the app` |
| `si` | No | Social share image URL | `https://example.com/image.png` |

\* Traceback only supports one iOS app and android app per extension installation

\** Features that will be supported in the future versions of traceback to enable a higher feature mapping between old fireabase dynamic links and traceback

\*** Not accepted as manual URL parameters by design. Allowing `at`/`ct`/`mt`/`pt` to be set directly in the URL would let anyone append their own affiliate/campaign values to an existing link and hijack its Apple affiliate attribution. These are only settable server-side via the [REST API](/create-link-rest/) or [Firestore](/create-link-firestore/), where the value is controlled by whoever creates the link rather than whoever opens it. Support for overriding them through manual URL construction is under consideration but not yet decided.

The Apple campaign parameters (`at`, `ct`, `mt`, `pt`) are already supported by Traceback today as `appleAffiliateToken`, `appleCampaignText`, `appleMediaType`, and `appleProviderId` — but only when creating a link via the [REST API](/create-link-rest/) or [Firestore](/create-link-firestore/).

---

## Next Steps

- [Create links programmatically using the REST API](/create-link-rest/)
- [Create or inspect links directly via Firestore](/create-link-firestore/)
- Configure how links are received in your [iOS](/receive-link-ios/) and [Android](/receive-link-android/) applications
- [Set up a custom domain for production use](/setup-custom-domain/)

