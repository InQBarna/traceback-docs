---
layout: default
title: Set Up a Custom Domain
permalink: /setup-custom-domain/
---
# Set Up a Custom Domain

Traceback supports custom domains for dynamic links.

Custom domains allow you to use branded URLs while maintaining full deep linking, deferred routing, and attribution functionality.

---

## How Custom Domains Work in Traceback

Traceback dynamic links are served using **Firebase Hosting**.

When you configure a custom domain in Firebase Hosting, that domain becomes available for:

- Dynamic link URLs
- App previews
- Platform routing (iOS Universal Links, Android App Links)

Traceback does not require a separate domain configuration step beyond Firebase Hosting.

---

## High-Level Setup Steps

To use a custom domain with Traceback:

1. Open your Firebase project.
2. Navigate to **Hosting**.
3. Add a custom domain to your Hosting site.
4. Complete domain verification and DNS configuration.
5. Use the custom domain when creating Traceback links.

Once configured, all Traceback links generated with this domain will use the custom hostname.

---

## Firebase Hosting Documentation

Traceback relies on standard Firebase Hosting behavior for custom domains.

For detailed, step-by-step instructions, see:

**Firebase Hosting – Custom Domains**

https://firebase.google.com/docs/hosting/custom-domain

---

## Notes

- The same domain can be used for iOS and Android deep linking.
- Ensure the domain is correctly configured for:
  - Associated Domains (iOS)
  - App Links verification (Android)
- Domain changes do not require SDK updates.

---

## Next Steps

- Create dynamic links using your custom domain
- Configure link handling in your mobile apps
- Review analytics and attribution data

