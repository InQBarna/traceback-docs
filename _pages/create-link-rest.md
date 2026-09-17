---
layout: default
title: Create Dynamic Links with the REST API
permalink: /create-link-rest/
---
# Create Dynamic Links with the REST API

Traceback provides a REST API for programmatically creating dynamic links.

This method is intended for server-side usage and automated workflows.

---

## When to Use the REST API

Use the REST API when you need to:

- Generate links dynamically on your backend
- Create links as part of a campaign pipeline
- Integrate link creation into existing systems
- Avoid direct access to Firestore

This is functionally equivalent to Firebase Dynamic Links REST creation, with a Traceback-specific schema.

---

## How REST Link Creation Works

At a high level, the REST workflow is:

1. Your backend sends a request to the Traceback API.
2. The request defines:
   - The deep link destination
   - Platform routing behavior
   - Attribution and campaign metadata
3. Traceback stores the link configuration.
4. A short or long dynamic link URL is returned.
5. The link can be distributed immediately.

The API abstracts storage and routing logic; clients only consume the resulting URL.

---

## Authentication and Hosting Model

Traceback REST APIs are hosted as part of your Firebase project when using the Firebase Extension.

Authentication is handled using project-level credentials and access rules defined by api keys. The traceback extension installation installs a default api key in firebase document `_traceback - > apikeys`. Create new api keys for specific services as needed using firebase console and firestore access or firestore api. We recommend controlling firestore access rules appropriately.

This allows:

- Self-hosted infrastructure
- Full control over access
- No external dependency on third-party hosted services

---

## Request

The REST API endpoint:

```
POST https://${YOUR_DOMAIN}/v1_create_campaign
x-traceback-api-key: ${YOUR_API_KEY}
Content-Type: application/json

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
   "clipboardTrackingEnabled": true
 }  
 ```

### curl example

```bash
curl -X POST "https://${YOUR_DOMAIN}/v1_create_campaign" \
  -H "x-traceback-api-key: ${YOUR_API_KEY}" \
  -H "Content-Type: application/json" \
  -d '{
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
    "clipboardTrackingEnabled": true
  }'
```

`title`, `description`, and `image` are the social metadata parameters — see [Social metadata parameters](#social-metadata-parameters-all-optional) below.

---

## Response Behavior

The REST API returns:

```
{
   "id": "abc123def456",
   "path": "/summer-promo",
   "title": "Summer Promo",
   "description": "Summer promotional campaign",
   "image": "https://example.com/image.png",
   "followLink": "https://example.com/products/summer",
   "expires": "2025-12-31T23:59:59.000Z",
   "clipboardTrackingEnabled": true,
   "campaignUrl": "https://your-project.web.app/summer-promo",
   "createdAt": "2025-01-15T10:30:00.000Z",
   "updatedAt": "2025-01-15T10:30:00.000Z"
 } 
```

---

## Schema and Parameters

For a detailed description and contract look at `https://${YOUR_DOMAIN}//api-doc.yaml`.

### Social metadata parameters (all optional)

`title`, `description`, and `image` control the rich preview shown when the link is opened or shared on social platforms (WhatsApp, iMessage, Slack, etc.) — the same social metadata described in [Generate Link Previews with Social Metadata](/generate-links-with-social-metadata/). They map to that page's `st`/`sd`/`si` manual-URL parameters, just expressed as regular JSON fields here instead of query-string shorthand.

### `clipboardTrackingEnabled` (boolean, optional, default: `true`)

Controls whether the preview page copies a unique URL to the clipboard before redirecting the user to the App Store or Play Store.

- **`true`** (default): The preview page is shown with an "Open" button. On tap, a unique URL is copied to the clipboard and the user is redirected to the store. After install, the app reads the clipboard to match the install to this campaign (per-install attribution).
- **`false`**: No preview page interaction is shown. The user is redirected automatically after a short delay without any clipboard copy. Use this when per-install attribution via clipboard is not needed.

### Apple App Store campaign parameters (all optional)

When the preview page redirects an iOS visitor to the App Store, these values are appended to the App Store URL as Apple's own affiliate/campaign tracking parameters:

| Parameter | Maps to App Store param | Description | Example |
|-----------|--------------------------|--------------|---------|
| `appleAffiliateToken` | `at` | Your Apple affiliate token | `affiliate123` |
| `appleCampaignText` | `ct` | Freeform campaign identifier for attribution reporting | `summer_campaign` |
| `appleMediaType` | `mt` | Apple media type code | `8` |
| `appleProviderId` | `pt` | Apple affiliate provider ID | `provider456` |

These are only used for the App Store redirect on iOS; they have no effect on Android or desktop routing.

---

## Ensure deep link is valid

At minimum, the path value provided must be valid and non existing. Else, the creation API will fail with HTTP error code 400.

---

## Next Steps

- [Learn how to construct links manually using URL parameters](/create-link-manual/)
- [Create or inspect links directly via Firestore](/create-link-firestore/)
- Configure how links are handled in your [iOS](/receive-link-ios/) and [Android](/receive-link-android/) apps

