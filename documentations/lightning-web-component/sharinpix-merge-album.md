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

# SharinPix Merge Album

{% hint style="info" %}
The **SharinPix Merge Album** component permits merging images from a specific SharinPix Album to another album.

It could be used to pull images from an existing record (from a field pointing to this record) and copy those pictures into the current record.
{% endhint %}

<figure><img src="../.gitbook/assets/image (13) (6).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used on:

* Page Builder
* Desktop
* Mobile
* In your own Lightning Component development
{% endhint %}

## Getting Started

To use the **SharinPix Merge Album** component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/image (14) (5).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

<figure><img src="../.gitbook/assets/image (15) (5).png" alt=""><figcaption></figcaption></figure>

* **Button label:** Used to specify the button's label. The default value is **SharinPix Merge Albums**.
* **Source Record Id Field API Name:** API name of the field containing the record ID of the source album.
* **Duplicate Images:** Duplicate the images instead of permanently moving them. If this option is selected, the images in the source album will not be moved; instead, they will be duplicated.

## Demo

The picture below shows the **source album** on a Contact record:

![](<../.gitbook/assets/Screenshot_from_2022-01-20_16-28-03 (1) (1) (1).png>)

The picture below shows the target album on an Account record **before** using the **SharinPix Merge Album** component:

![](<../.gitbook/assets/Screenshot_from_2022-01-20_16-35-55 (1) (1) (1).png>)

To merge the images from the source album to the target album, click on the button **SharinPix Merge Album**.

The picture below shows the result in the target album **after** using the **SharinPix Merge Album** component:

![](<../.gitbook/assets/Screenshot_from_2022-01-20_16-42-00 (1) (1) (1).png>)
