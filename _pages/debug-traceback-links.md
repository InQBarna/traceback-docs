---
layout: default
title: Debug Traceback Links
permalink: /debug-traceback-links/
---
# Debug Traceback Links

Traceback provides multiple ways to verify that dynamic links are correctly configured and resolved.

Because Traceback is self-hosted within your Firebase project, most debugging can be performed by inspecting your own infrastructure and application logs.

---

## Overview

When a dynamic link does not behave as expected, the issue is typically related to one of the following:

- Link configuration
- Domain setup
- Platform deep link configuration
- Application handling logic

Debugging usually involves validating each stage of the routing process.

---

## Basic Verification Steps

1. Open the dynamic link in a browser.
2. Confirm the link resolves to the expected preview or redirect.
3. Verify that the configured deep link destination is correct.
4. Test the link on both iOS and Android devices.
5. Reinstall the app when testing deferred deep linking.

---

## Inspect Link Configuration

Traceback link definitions are stored inside your Firebase project.

You can:

- Open **Firestore**
- Locate the configured Traceback links collection
- Verify routing parameters and campaign metadata

If the stored configuration is incorrect, update the document and test again.

---

## Check Event and Routing Data

Depending on your deployment, Traceback may record:

- Link open events
- Routing decisions
- Attribution metadata

These records can be inspected through:

- Firestore collections
- Backend logs
- Internal monitoring tools

---

## SDK-Level Debugging

If the link reaches the device but does not route correctly:

- Confirm Associated Domains (iOS) or App Links (Android) are properly configured.
- Verify your application receives the incoming URL or intent.
- Add temporary logging in your navigation or deep link handling logic.

Detailed SDK troubleshooting guidance is available in:

- https://github.com/InQBarna/traceback-iOS
- https://github.com/InQBarna/traceback-android

---

## Future Debugging Tooling

Additional tools for inspecting link resolution and attribution flows will be documented as they become available.

---

## Next Steps

- Verify your custom domain configuration
- Review link parameters and routing rules
- Inspect recorded analytics and event data

