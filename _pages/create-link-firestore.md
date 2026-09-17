---
layout: default
title: Create Dynamic Links via Firestore
permalink: /create-link-firestore/
---
# Create Dynamic Links via Firestore

Traceback stores every link as a document in your own Firebase project's Firestore database. When Traceback is installed as a Firebase Extension, you can create or edit links directly from the Firebase Console without going through the REST API or Traceback Manager.

This method is intended for development, automated infrastructure workflows, or teams that want direct control over their data.

---

## When to Use Firestore Directly

Use direct Firestore access when you need to:

- Create or inspect links during local development
- Script link creation as part of infrastructure-as-code or CI/CD
- Bulk-import or migrate links from another system
- Avoid depending on the REST API or an external UI

---

## Where Links Are Stored

Traceback links live at the following Firestore path:

```
_traceback_/dynamiclinks/records/{linkId}
```

- `_traceback_` — the top-level collection used by the extension
- `dynamiclinks` — a fixed document under that collection
- `records` — the subcollection containing one document per link
- `{linkId}` — an auto-generated document ID (or one you choose)

---

## Document Schema

Each document in `records` supports the following fields:

```json
{
  "path": "/summer-promo",
  "title": "Summer Promo",
  "description": "Summer promotional campaign",
  "image": "https://example.com/image.png",
  "followLink": "https://example.com/products/summer",
  "expires": "2025-12-31T23:59:59Z",
  "appleAffiliateToken": "affiliate123",
  "appleCampaignText": "summer_campaign",
  "appleMediaType": "8",
  "appleProviderId": "provider456",
  "otherFallbackLink": "https://example.com/fallback",
  "clipboardTrackingEnabled": true
}
```

Notes on specific fields:

- `path` (required): must start with `/` and be unique across all links.
- `title`, `description`, `image`: optional social metadata shown when the link is opened or shared on social platforms. See [Generate Link Previews with Social Metadata](/generate-links-with-social-metadata/).
- `expires`: stored as a Firestore `Timestamp`, not a string. When creating the document from the Console UI, use the Console's timestamp field type.
- `appleAffiliateToken`, `appleCampaignText`, `appleMediaType`, `appleProviderId`: optional Apple App Store campaign parameters, described in [REST Dynamic Link Creation](/create-link-rest/).
- `otherFallbackLink`: optional URL, used as the final fallback destination on **desktop only** when no `link` parameter was supplied. Not used on iOS/Android. See [REST Dynamic Link Creation](/create-link-rest/) for the full behavior description.
- `clipboardTrackingEnabled`: optional boolean, defaults to `true` when omitted. See [REST Dynamic Link Creation](/create-link-rest/) for the full behavior description.

---

## Typical Workflow (Firebase Console)

1. Open your Firebase project in the [Firebase Console](https://console.firebase.google.com).
2. Navigate to **Firestore Database**.
3. Go to `_traceback_` → `dynamiclinks` → `records`.
4. Click **Add document** and let Firestore auto-generate the document ID (or set your own).
5. Add the fields listed above, with `path` at minimum.
6. Save. The link becomes active immediately — no deploy or cache invalidation needed.

---

## Ensure the Path Is Valid and Unique

`path` must start with `/` and must not already be used by another document in `records`. Unlike the REST API, Firestore itself will not reject a duplicate path — Traceback simply resolves the first match it finds, so avoid creating conflicting documents.

---

## Next Steps

- [Create links programmatically using the REST API](/create-link-rest/)
- [Build links manually using URL parameters](/create-link-manual/)
- Configure how links are handled in your [iOS](/receive-link-ios/) and [Android](/receive-link-android/) apps

