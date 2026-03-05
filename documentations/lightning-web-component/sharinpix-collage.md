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

# SharinPix Collage (before/after photo layout)

{% hint style="info" %}
The **SharinPix Collage** component permits users to combine **two** images from a SharinPix Album into a single image. This component also allows users to save the collage to a SharinPix Album.
{% endhint %}

<figure><img src="../.gitbook/assets/sharinpix_share (5).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Community Builder
* On Page Builder
* On Desktop
* On Mobile
* In Flows (but not in Field Service Mobile Flow)
{% endhint %}

## Getting Started

To use the SharinPix Collage component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/sharinpix_share (6).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

<figure><img src="../.gitbook/assets/sharinpix_share (7).png" alt=""><figcaption></figcaption></figure>

* **Component ID:** Used to specify the common ID with the targeted SharinPix component. _**Note:** This parameter should be populated for the SharinPix Collage component to work. The value entered here should match the value in the component ID parameter of the corresponding SharinPix Album component found on the page._
* **Button Label:** Used to specify the label to be shown on the button to create a collage.

## Demo

The picture below depicts a SharinPix Collage component and a SharinPix Album component with uploaded images.

{% hint style="warning" %}
**Note:**

* Both components are related using the same **Component ID** value.
* The SharinPix Collage's button in disabled as no image selection has been performed yet.
{% endhint %}

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (3).png" alt=""><figcaption></figcaption></figure>

Start by selecting two images. The SharinPix Collage's button should be enabled after the selection as depicted below:

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (4).png" alt=""><figcaption></figcaption></figure>

Click on the button to start the collage:

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (8).png" alt=""><figcaption></figcaption></figure>

Click the Save button to save the collage to the SharinPix Album. At this point, users can adjust, zoom in, or out of the images in the collage:

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (6).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (7).png" alt=""><figcaption></figcaption></figure>
