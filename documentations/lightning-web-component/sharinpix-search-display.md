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
---

# SharinPix Search Display

## Overview

The **SharinPix Search Display** Lightning Web Component (LWC) provides a visual interface for searching and selecting images stored in SharinPix albums linked to Salesforce records. It is designed to be easily embedded in wrapper components or Salesforce Flows, offering flexibility and configuration options.

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* In Flows (but not in Field Service Mobile Flow)
* In your own Lightning Component development
* In third third-party app Lightning [Avonni Dynamic Components](https://appexchange.salesforce.com/appxListingDetail?listingId=e855ec28-bf2c-47fa-aa38-30b43948ab4f\&tab=r)
{% endhint %}

## Getting Started

Below is a sample flow that is designed to show all images from all accounts in the Salesforce org.

![](<../.gitbook/assets/DOC SF - 1920 x 1080(1) (1) (1) (1).png>)

Configuring the Search Display component is fairly simple. You just need to pass the list of record IDs you built earlier in the component metadata using the flow builder.

![](<../.gitbook/assets/DOC SF - 1920 x 1080 (14) (1) (2).png>)

## Lightning Component Parameters

* **recordIds** - a list of Salesforce record Ids representing either an album record or SharinPix Image records Id
* **permissionId** - Name or Id of the SharinPix Permission of type Search
* **height** - Height in pixels of the component. Default is 500
* **selectedImageIds** - If images are selected, it will store the image public id (of type uuid)

## Demo

The result should looks like below.

![](<../.gitbook/assets/DOC SF - 1920 x 1080(2) (1) (1) (2).png>)
