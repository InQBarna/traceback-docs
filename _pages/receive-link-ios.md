---
layout: default
title: Receive Dynamic Links on iOS
permalink: /receive-link-ios/
---
# Receive Dynamic Links on iOS

Traceback provides an iOS SDK that resolves incoming dynamic links and delivers the associated routing and attribution data to your application.

This page describes the high-level integration flow. Detailed implementation steps are maintained in the SDK repository.

---

## Overview

When a user opens a Traceback link on iOS:

1. The system attempts to open your app using Universal Links.
2. The Traceback SDK processes the incoming URL.
3. The SDK resolves any deferred deep link data.
4. Your app receives the final destination and associated metadata.

This behavior matches the standard deep link lifecycle used by Firebase Dynamic Links.

---

## Requirements

Before receiving dynamic links:

- Your app must support **Associated Domains**.
- Universal Links must be configured for your Traceback domain.
- The Traceback iOS SDK must be added to your project.

---

## Integration Guide

Full installation, configuration, and code examples are available in the SDK repository:

**Traceback iOS SDK Documentation**

https://github.com/InQBarna/traceback-iOS/tree/main

The SDK documentation includes:

- Swift Package installation
- App lifecycle integration
- Handling Universal Links
- Receiving deferred deep link payloads
- Accessing attribution metadata

---

## Typical Handling Flow

At runtime:

1. The app receives a Universal Link.
2. The Traceback SDK extracts routing parameters.
3. The SDK notifies your application with the resolved deep link.
4. Your navigation logic routes the user to the correct screen.

---

## Next Steps

- Configure Android link handling
- Set up a custom domain
- Create and test dynamic links

