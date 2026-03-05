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

# SharinPix To Album

The **SharinPix To Album** component permits to load images from a specific SharinPix Album to another album.

<figure><img src="../.gitbook/assets/Image from Gradio (15).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used on:

* Community Builder
* Page Builder
* Desktop
* Mobile
* In Flows (but not in Field Service Mobile Flow)
* In your own Lightning Component development
{% endhint %}

## Getting Started

To use the SharinPix To Album component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/Image from Gradio (14).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

<figure><img src="../.gitbook/assets/Image from Gradio (16).png" alt=""><figcaption></figcaption></figure>

* **Button label:** Used to specify the button's label. The default value is **Load Predefined Images**.
* **Source Album ID:** Used to specify the record ID or album ID from which images will be fetched. Please note that the value entered will be overwritten if the field **Source Album ID Field** is filled.
* **Source Album ID Field:** Used to specify the API name of the field from which the source album ID can be retrieved.
* **Tags Filter (JSON):** Used to specify the tag names to filter the images. The value entered should be in a JSON array format, for example, \["Paris","London"]. Please note that the value entered will be overwritten if the field **Tags Filter Field** is filled.
* **Tags Filter Field:** Used to specify the API name of the field from which the tag filters can be retrieved. The value entered inside the related field should be in a JSON array format.
* **Tag Operator:** Used to specify the operator to be used when multiple tags are being used. The values available are **OR** and **AND**. When using **OR** , the returned the images will have any of the tags specified whereas using **AND** will return images having all of the tags specified
* **Post-upload Action:** Choose which action to perform after uploading image(s) to the target album. There are 4 actions available - **Do nothing** , **Open first image** , **Start annotating first image**, **Start annotating first image with sticker**.
* **Action Value:** Enter an Action Value for the post-upload action. If the **Start annotating first image with sticker** action is selected, enter the tag name to filter the stickers by.
* **Action Value Field:** Used to specify the API name of the field from which the Action Value can be retrieved.
* **Auto Tags:** Enter comma-separated list of tag names to automatically apply on images after upload.
* **Auto Tags Field:** Used to specify the API name of the field from which the Auto Tags can be retrieved.
* **Target Component ID:** Used to specify the component ID which can be any common text between the **SharinPix To Album** component and the targeted **SharinPix Album** component. This ID allows communication between the matching components. _Please note that this field should be filled in order to use the SharinPix To Album component._

## Demo

The picture below shows the **source album** on a Contact record:

![](<../.gitbook/assets/screenshot-enterprise-computing-8320-dev-ed.lightning.force.com-2020.05.18-13_03_25 (1) (1) (1).png>)

The picture below shows the target album on an Account record **before** using the SharinPix To Album component:

![](<../.gitbook/assets/screenshot-velocity-site-4953-dev-ed.lightning.force.com-2020.05.18-14_30_15 (1) (1) (1).png>)

To load the images from the source album to the target album, click on the button **Load Predefined Images**.

The picture below shows the result in the target album **after** using the SharinPix To Album component:

![](<../.gitbook/assets/screenshot-velocity-site-4953-dev-ed.lightning.force.com-2020.05.18-14_31_15 (1) (1) (1).png>)
