---
layout: default
title: Create a Traceback Dynamic Link
permalink: /create-link/
---
# Create a Traceback Dynamic Link

Traceback links can be created directly inside your Firebase project or using the Traceback campaign management tools.

This page describes the available creation methods.

---

## Create Links from Firebase Console (Firestore)

If Traceback is installed as a Firebase Extension, links are stored and managed inside your project's Firestore database.

Typical workflow:

1. Open your Firebase project.
2. Navigate to **Firestore**.
3. Create or edit a document inside the configured Traceback links collection.
4. Define the link destination and routing parameters.
5. The link becomes immediately active.

This method is recommended for:

- Development
- Automated workflows
- Direct infrastructure control

See [Create Dynamic Links via Firestore](/create-link-firestore/).

Includes the full Firestore document schema and a JSON example.
{: .doc-caption}

---

## Create Links with Traceback Manager

[Traceback Manager](https://tracebackapp.inqbarna.com) is a separate service that provides a user interface for creating and maintaining campaigns.

Using Traceback Manager you can:

- Create links without accessing Firestore
- Organize campaigns
- Edit metadata and routing behavior
- Manage attribution parameters

This method is recommended for:

- Marketing teams
- Campaign management
- Non-technical users

---

## Other Link Creation Methods

### REST API

You can programmatically create Traceback links using the REST API.

See [REST Dynamic Link Creation](/create-link-rest/).

This documentation describes the high-level workflow and request structure.
{: .doc-caption}

---

### Manual URL Construction

Traceback links can also be built manually by composing a URL with the appropriate parameters.

See [Manual URL Construction](/create-link-manual/).

A full parameter reference is provided in that section.
{: .doc-caption}

---

## Next Steps

- Configure link handling in your app:
  - [Receive Dynamic Links (iOS)](/receive-link-ios/)
  - [Receive Dynamic Links (Android)](/receive-link-android/)
- [Learn how to define routing parameters using manual URL construction](/create-link-manual/)

