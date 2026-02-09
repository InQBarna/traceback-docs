---
layout: default
title: Generate Link Previews with Social Metadata
permalink: /generate-links-with-social-metadata/
---
# Generate Link Previews with Social Metadata

Traceback allows you to add **social metadata** to your dynamic links, enabling rich link previews when your link is shared on social platforms such as iMessage, WhatsApp, Slack, or social media feeds.

---

## Overview

Social metadata enhances the way your dynamic links appear when shared:

- **Title**: The main text shown in the preview.
- **Description**: A short description or snippet of the linked content.
- **Image**: A thumbnail or featured image that represents the content.

These elements improve user engagement by giving context to the shared link.

---

## Create Links with Traceback Manager

[Traceback Manager](https://tracebackapp.inqbarna.com) is a separate service that provides a user interface for creating and maintaining campaigns.

Using Traceback Manager you can:

- Create links without accessing Firestore
- Organize campaigns
- Edit social metadata
- Manage attribution parameters
- Generate QR codes

---

## Create links manually using supported Social Metadata Parameters

TODO\* The following parameters can be added to a Traceback link:

| Parameter | Required | Description | Example |
|-----------|----------|-------------|---------|
| `st` | No | TODO\* Social title | `Check out this article` |
| `sd` | No | TODO\* Social description | `Learn how to build dynamic links with Traceback` |
| `si` | No | TODO\* Social image URL | `https://example.com/thumbnail.png` |

### TODO\* Example Link with Social Metadata

```
https://${YOUR_DOMAIN}.com/?link=https://example.com/article/123&st=Check+this+out&sd=Learn+how+to+use+Traceback&si=https://example.com/image.png
```

When shared on supported platforms, the link will display a preview using the provided title, description, and image.

---

## Best Practices

- Ensure the image is publicly accessible and optimized for social previews.
- Expected image aspect ratio is 300x200. Minimum size shuold be 300x200.
- Keep the title and description concise (ideally under 100 characters for title, 200 for description).
- Test the link on multiple platforms to confirm preview appearance.
- Encode all URL parameters properly to avoid parsing issues.

---

## Next Steps

- Use Traceback Manager or manual URL construction to create links with social metadata.
- Share links in test environments to verify previews.
- Combine with analytics to measure engagement from shared links.

