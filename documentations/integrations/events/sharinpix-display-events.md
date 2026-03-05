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

# SharinPix Display Events

The present article shows the types of SharinPix Display Events and the type of behavior that emit them. Those events are namely:

* [viewer-image-viewed](sharinpix-display-events.md#viewer-image-viewed)
* [viewer-closed](sharinpix-display-events.md#viewer-closed)

{% hint style="success" %}
**Note:**

To capture the different events listed below, please refer to the following article: [Capturing Client-side events](capturing-client-side-events.md)
{% endhint %}

## viewer-image-viewed

This event is emitted after an image is clicked upon and hence the Large View Mode is activated.

* Before clicking.

<figure><img src="../../.gitbook/assets/image (61).png" alt=""><figcaption></figcaption></figure>

* After clicking on image.

<figure><img src="../../.gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>

## viewer-closed

This event is emitted when the current viewer is closed and hence the Large View is deactivated.

* Large View activated.

<figure><img src="../../.gitbook/assets/image (62).png" alt=""><figcaption></figcaption></figure>

* Large View deactivated.

<figure><img src="../../.gitbook/assets/image (1) (3).png" alt=""><figcaption></figcaption></figure>
