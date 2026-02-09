---
layout: default
title: View Analytics Data
permalink: /view-analytics-data/
---
# View Analytics Data

Traceback collects interaction and attribution data for each dynamic link.

This data can be used to understand link performance, campaign effectiveness, and user acquisition flows.

---

## Overview

Each Traceback link interaction may generate events such as:

- Link opens
- Redirect decisions
- App launches
- Deferred deep link resolutions

These events are associated with the link configuration and any campaign metadata defined at creation time.

---

## Available Data

Traceback records information including:

- Link identifiers
- Campaign parameters
- Platform and device context
- Routing outcomes
- Attribution metadata

The exact dataset depends on your deployment configuration and enabled features.

---

## Accessing Analytics Data

Traceback is designed as a **self-hosted attribution platform**.

Depending on your setup, analytics data may be accessed through:

- Firestore collections within your Firebase project
- Exported event pipelines
- Internal dashboards or reporting tools
- Traceback Manager (when enabled)

---

## View analytics data using traceback manager

[Traceback Manager](https://tracebackapp.inqbarna.com) is a separate service that provides a user interface for creating and maintaining campaigns. It also offers powerful analytics tracking visualization

This includes:

- Aggregated performance views
- Campaign reporting
- Attribution analysis

---

## Analytics API

### Request

The REST API endpoint:

```json
POST https://${YOUR_DOMAIN}/v1_campaign_analytics/%20summer-promo?durationDays=7&endDate=2026-01-10
x-traceback-api-key: ${YOUR_API_KEY}
```

### Response Behavior

The REST API returns:

```json
{
  "campaignPath": "/summer-promo",
  "durationDays": 7,
  "startDate": "2025-01-08",
  "endDate": "2025-01-14",
  "analytics": {
    "2025-01-08": {
      "open_link_preview": { "desktop": 5, "android": 3, "ios": 2 },
      "redirects": { "desktop": 1, "android": 2, "ios": 0 },
      "first_opens_intent": { "desktop": 0, "android": 0, "ios": 0 },
      "first_opens_install": { "desktop": 0, "android": 0, "ios": 0 },
      "reopens": { "desktop": 0, "android": 0, "ios": 0 }
    },
    "2025-01-10": {
      "open_link_preview": { "desktop": 10, "android": 7, "ios": 4 },
      "redirects": { "desktop": 0, "android": 1, "ios": 3 },
      "first_opens_intent": { "desktop": 0, "android": 1, "ios": 2 },
      "first_opens_install": { "desktop": 0, "android": 0, "ios": 1 },
      "reopens": { "desktop": 0, "android": 3, "ios": 5 }
    }
  }
}
```

### Schema and Parameters

For a detailed description and contract look at `https://${YOUR_DOMAIN}//api-doc.yaml`.

---

## Next Steps

- Create and distribute dynamic links
- Verify link routing behavior
- Use your existing analytics infrastructure to inspect recorded events

