---
layout: default
title: Traceback Dynamic Links
permalink: /traceback/
---

# Traceback Dynamic Links

**Traceback** is a **drop-in replacement for Firebase Dynamic Links** and a **self-hosted attribution platform**.

Traceback allows you to create smart links that route users to the correct destination across platforms, whether or not your app is installed.

---

## What Traceback Does

Traceback links provide a consistent user experience across iOS, Android, and the web:

- If the app is installed → opens the linked content inside the app
- If the app is not installed → redirects to the store
- After installation → restores the original destination (deferred deep linking)
- Desktop users → routed to your web content or landing page

This enables:

- User acquisition campaigns
- Content sharing
- Install attribution
- Contextual onboarding

Traceback links behave like traditional deep links but preserve context across installation.

---

## Why Traceback

Firebase Dynamic Links has been deprecated and shut down by Google, requiring teams to migrate to alternative solutions. :contentReference[oaicite:0]{index=0}

Traceback provides:

- A **Firebase-native workflow**
- Self-hosted infrastructure
- Full control over link data and attribution
- Compatibility with existing Dynamic Link mental models

Traceback can be deployed:

- As a Firebase Extension inside your project
- With optional campaign management through **Traceback Manager**

---

## How Traceback Works

Traceback uses a hosted redirect service and SDK integration to resolve a link into the best destination for the user’s platform.

High-level flow:

1. A Traceback link is opened.
2. The platform and install state are detected.
3. The user is routed:

   - App installed → Open app via Universal Links / App Links
   - App not installed → Redirect to store
   - After install → App retrieves deferred link + payload

4. The app receives metadata and attribution data.

---

## Creating Traceback Links

Traceback links can be created using:

- Firebase Console (via Firestore access)
- Traceback Manager (campaign UI)
- REST API
- Manual URL construction

See:

- **Create Dynamic Link**
- **REST Link Creation**
- **Manual URL Construction**

---

## Core Capabilities

Traceback provides:

- Cross-platform deep linking
- Deferred deep linking
- Install attribution
- Campaign metadata
- Custom domains
- Social link previews
- Self-hosted data ownership

---

## Next Steps

- [Create your first dynamic link](/create-link/)
- [Configure your custom domain](/setup-custom-domain/)
- [Integrate the iOS or Android SDK](/receive-link-ios/)

