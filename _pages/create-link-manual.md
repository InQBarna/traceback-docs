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

---

## Parameter Encoding

All parameter values must be URL-encoded.

In particular:

- The `link` parameter must be encoded if it contains its own query parameters.
- Social metadata URLs should be publicly accessible.

---

## Behavior Notes

- If platform-specific parameters are missing, Traceback attempts best-effort routing.
- Attribution parameters are stored and passed to the application on open.
- Manual links behave identically to links created via Firestore, REST API, or Traceback Manager.

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
| `ofl` | No | TODO\*\* Web fallback URL | `https://example.com/web` |
| `utm_source` | No | Attribution source | `newsletter` |
| `utm_medium` | No | Attribution medium | `email` |
| `utm_campaign` | No | Campaign name | `spring_launch` |
| `st` | No | TODO\*\* Social share title | `My Campaign` |
| `sd` | No | TODO\*\* Social share description | `Open this content in the app` |
| `si` | No | TODO\*\* Social share image URL | `https://example.com/image.png` |

\* Traceback only supports one iOS app and android app per extension installation
\** Features that will be supported in the future versions of traceback to enable a higher feature mapping between old fireabase dynamic links and traceback

---

## Next Steps

- Create links programmatically using the REST API
- Configure how links are received in your iOS and Android applications
- Set up a custom domain for production use

