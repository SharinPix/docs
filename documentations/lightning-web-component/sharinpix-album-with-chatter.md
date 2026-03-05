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

# SharinPix Album with Chatter

The **SharinPix Album with Chatter** component permits the use of the SharinPix Album component alongside Salesforce Chatter. Using this component, one can start a Chatter discussion on a specific image.

The picture below shows the SharinPix with Chatter component. As you can see, this component consists of two elements:

* The SharinPix Album component (on the left)
* The preview pane (on the right)

![](<../.gitbook/assets/screenshot-app-java-2138-dev-ed.lightning.force.com-2020.05.12-16_28_08 (1) (1) (1).png>)

**Information:**

{% hint style="info" %}
**Info:**<br>

This feature is only available on Lightning. It can be used on:

* Community Builder
* Page Builder
* Desktop
* Mobile
* In your own Lightning Component development
{% endhint %}

## Getting Started

To use the SharinPix Album with Chatter component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

![](<../.gitbook/assets/image - 2026-02-06T151859.211.png>)

## Lightning Component Parameters

<figure><img src="../.gitbook/assets/image (8) (1) (1).png" alt=""><figcaption></figcaption></figure>

* **Album ID:** Used to specify the album ID. If you want to use the record ID as the album ID, leave this field blank.
* **Height:** Used to specify the height of both components. The default album height is **700** (px).
* **Enable Action:** Used to enable/disable Tag Action for the SharinPix Album component. **Note**: The Tag Action is enabled by default on the SharinPix Album component. For more information on this feature and how to complete the Tag Action setup, refer to this article: [_Tag Action_](../features/working-with-tags/tag-action.md)
* **Enable Image Sync:** Used to enable/disable Image Sync. **Note:** Image Sync is checked by default on the SharinPix Album component. Additional steps are required to get this feature fully working on your Salesforce object. Please refer to this article to complete the Image Sync setup: [_Setup SharinPix Image Sync_](../image-sync/setup-sharinpix-image-sync.md)
* **Custom Permission ID:** Used to specify the ID of a custom permission to be used on the SharinPix Album component.
* **Record ID of parent object (for SharinPix Chatter):** Used to specify the Salesforce record ID of the parent record for the SharinPix Chatter component.
* **Chatter feeds for viewed images:** Used to enable/disable the option to show Chatter publisher and feed for the image viewed.
* **Chatter feeds for selected annotations:** Used to enable/disable the option to show Chatter publisher and feed for the selected annotation.

## Demo

The picture below depicts the SharinPix Album with Chatter component with some uploaded images:

![](<../.gitbook/assets/screenshot-enterprise-computing-8320-dev-ed.lightning.force.com-2020.05.13-11_45_26 (1) (1) (1).png>)

The example below shows a Chatter Post corresponding to an image:

![](<../.gitbook/assets/screenshot-app-java-2138-dev-ed.lightning.force.com-2020.05.12-16_40_04 (1) (1) (1).png>)

{% hint style="info" %}
To start a Chatter discussion on a specific image, simply click on the image. The Chatter preview pane will then be available on the right-hand-side of the component.
{% endhint %}

{% hint style="success" %}
**Tip:**<br>

Below are some useful links about the SharinPix Album with Chatter component's feature that you may refer to:

* [Use the pre-build SharinPix Album with Chatter Feed.](../chatter-feed/use-the-pre-build-sharinpix-album-with-chatter-feed.md)
* [Comment on Chatter using the SharinPix Album with Chatter component.](../features/user-interface/large-view-annotation-comment-with-chatter.md)
* [Use SharinPix with Chatter component on specific images or annotations.](../chatter-feed/sharinpix-chatter-feed-for-image-and-annotation-how-it-works-what-to-expect.md)
{% endhint %}
