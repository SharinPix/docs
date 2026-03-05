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

# SharinPix Chatter

The **SharinPix Chatter** component enables users to add Chatter posts for a specific image from an album or a specific image annotation.

![](<../.gitbook/assets/screenshot-spx-fsl-summer20-dev-ed.lightning.force.com-2020.08.12-16_51_20 (1) (1) (1).png>)

{% hint style="info" %}
**Information:**<br>

This feature is only available on Lightning. It can be used on:

* Community Builder
* Page Builder
* Desktop
* Mobile
* In your own Lightning Component development
{% endhint %}

## Getting Started

To use the SharinPix Chatter component, you simply need to drag and drop the component from the Lightning App Builder onto the page layout.

<figure><img src="../.gitbook/assets/image (9) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

<figure><img src="../.gitbook/assets/image (10) (1) (1).png" alt=""><figcaption></figcaption></figure>

* **Record ID or External ID:** Used to specify the Salesforce record ID or the external ID corresponding to the Salesforce record.
* **Record ID of parent object:** Used to specify the Salesforce record ID of the parent record.
* **Height:** Used to specify the component's height. The default height is **700 (px)**.
* **Component ID:** Used to specify the Component ID which can be any common text between the **SharinPix Chatter** component and the corresponding **SharinPix Album** component. The ID allows communication between matching components. **Please note that this field should be filled in order to use the SharinPix Chatter component.**
* **Chatter feeds for viewed images:** Used to enable/disable the option to show chatter publisher and feed for the viewed image.
* **Chatter feeds for selected annotations:** Used to enable/disable the option to show chatter publisher and feed for the selected annotation.

## Demo

The example below shows a Chatter post corresponding to the image selected from the album:

![](<../.gitbook/assets/screenshot-spx-fsl-summer20-dev-ed.lightning.force.com-2020.08.12-17_30_05_(1) (1) (1) (1).png>)

{% hint style="success" %}
**Tip:**<br>

Below are some useful links relating to the SharinPix Chatter component that you may refer to:

* [Using the Chatter](../chatter-feed/use-the-pre-build-sharinpix-album-with-chatter-feed.md#using-the-chatter)
* [Use SharinPix with Chatter component on specific images or annotations](../chatter-feed/sharinpix-chatter-feed-for-image-and-annotation-how-it-works-what-to-expect.md)
{% endhint %}
