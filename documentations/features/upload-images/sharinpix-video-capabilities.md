---
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: false
  tags:
    visible: true
  actions:
    visible: true
---

# SharinPix Video Capabilities

## Overview

SharinPix allows users to **record, upload, and view videos** directly within the SharinPix Mobile App and Salesforce. Whether you're capturing short clips in the field or uploading pre-recorded videos, SharinPix provides flexible video support for your organization.

This article covers :

1. [Recording Videos in the SharinPix Mobile App](sharinpix-video-capabilities.md#recording-videos-in-the-sharinpix-mobile-app)
2. [Uploading and Viewing Videos in Salesforce](sharinpix-video-capabilities.md#uploading-and-viewing-videos-in-salesforce)
3. [Supported Video Formats](sharinpix-video-capabilities.md#supported-video-formats)
4. [Playable Video Sizes in Salesforce](sharinpix-video-capabilities.md#playable-video-sizes-in-salesforce)

{% hint style="info" %}
**Prerequisite**

1. Video feature is available only on the **Enterprise** plan and must be **explicitly enabled**. Please contact [SharinPix Support](../../getting-started-with-sharinpix/how-to-contact-support.md) to activate this feature.
2. If you are on another plan, you can also try this feature in a **sandbox** first using the **SharinPix Mobile App**.
{% endhint %}

## Recording Videos in the SharinPix Mobile App

The SharinPix mobile app includes a built-in video recording feature.

**How to Record:**

1. Open the SharinPix mobile app.
2. Select the **Video** mode from the scrollable mode list at the bottom.
3. Tap the **Record** button to begin recording. Tap again to stop.
4. Tap the thumbnail to **view the video**, with an option for **full-screen playback**.
5. While recording, you can tap the **Snap** button (to the right of the record button) to capture still photos.

<figure><img src="../../.gitbook/assets/Video Recording Doc (3) (1).gif" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
App configuration options, such as choosing which camera opens, are available [here](../../mobile-app/sharinpix-mobile-app-deeplink-syntax.md).
{% endhint %}

### Video Duration Limits

Users on the **Enterprise Plan** can record videos up to **30 seconds** long.

{% hint style="info" %}
**Info**

* **To record videos longer than 30 seconds**, customers must:
  1. Be on the **Enterprise** plan.
  2. Use their **own AWS S3 storage**.
  3. Explicitly [request support](../../getting-started-with-sharinpix/how-to-contact-support.md) to activate extended playback.
* Videos captured using the SharinPix Mobile App are automatically saved in **MP4** format.
{% endhint %}

## Uploading and Viewing Videos in Salesforce

Videos recorded on the mobile app, or uploaded through other SharinPix-supported interfaces, can be viewed directly in Salesforce:

1. From the **gallery view**, click on any video to open it in the image viewer.

![](<../../.gitbook/assets/Click on the (8).png>)

2\. If your video has been uploaded successfully, **a play button** will appear on the video, allowing you to preview it.

![](<../../.gitbook/assets/Click on the (9).png>)

## Supported Video Formats

SharinPix supports the following **common web formats** :

* **MP4**
* **WEBM**
* **MOV**

{% hint style="success" %}
**Tip**

Need another format? [Contact SharinPix Support](../../getting-started-with-sharinpix/how-to-contact-support.md) to discuss additional format support.
{% endhint %}

## Playable Video Sizes in Salesforce

| Plan Type                   | Playable Video Size |
| --------------------------- | ------------------- |
| Enterprise                  | Up to 25 MB         |
| Pro / Lite / Basic / Legacy | Not Avalaible       |

{% hint style="success" %}
**Tip**

For assistance with playing larger videos, please [contact SharinPix support](../../getting-started-with-sharinpix/how-to-contact-support.md).
{% endhint %}
