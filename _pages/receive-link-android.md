---
layout: default
title: Receive Dynamic Links on Android
permalink: /receive-link-android/
---
# Receive Dynamic Links on Android

Traceback provides an Android SDK that resolves incoming dynamic links and delivers routing and attribution data to your application.

This page describes the high-level integration flow. Detailed setup and implementation steps are maintained in the SDK repository.

---

## Overview

When a user opens a Traceback link on Android:

1. The system attempts to open your app using Android App Links.
2. The Traceback SDK processes the incoming intent.
3. Any deferred deep link information is resolved.
4. Your application receives the final destination and associated metadata.

This behavior mirrors the deep link lifecycle previously supported by Firebase Dynamic Links.

---

## Requirements

Before receiving dynamic links:

- Your app must support **Android App Links**.
- The Traceback domain must be configured for link verification.
- The Traceback Android SDK must be added to your project.

---

## Integration Guide

Full installation, configuration, and usage examples are available in the SDK repository:

**Traceback Android SDK Documentation**

https://github.com/InQBarna/traceback-android

The SDK documentation includes:

- Dependency installation
- Manifest configuration
- Intent handling
- Deferred deep link resolution
- Accessing attribution metadata

---

## Typical Handling Flow

At runtime:

1. The app receives an incoming intent associated with a Traceback link.
2. The Traceback SDK extracts routing and attribution parameters.
3. The SDK provides the resolved deep link to the application.
4. Your navigation logic routes the user to the appropriate screen.

---

## Next Steps

- Configure a custom domain for production links
- Create and test dynamic links
- Review available attribution and analytics features

