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

# SharinPix Rich Text To PDF

{% hint style="warning" %}
This component is only available in the Enterprise license plan of SharinPix. For more info, please contact [support@sharinpix.com](mailto:support@sharinpix.com)
{% endhint %}

{% hint style="info" %}
The **SharinPix Rich Text To PDF** component permits the conversion of images found inside a **Rich Text** field into a PDF.

This is a great way for you to generate report and send them as attachment in email. In addition, the PDF generated will be saved on the record as Content Document.
{% endhint %}

<figure><img src="../.gitbook/assets/image (12) (5).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used on:

* Page Builder
* Desktop
* Mobile
* In your own Lightning Component development
{% endhint %}

## Getting Started

{% hint style="warning" %}
**Note:**

In order to use the SharinPix Rich Text To PDF component you should ensure that:

* Your record page should have **at least one** field of type **Text Area (Rich)**.
* The permission set **SharinPix Lightning Components** is assigned to all users attempting to use the SharinPix Rich Text To PDF component.
{% endhint %}

To use the SharinPix Rich Text To PDF component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/image (1) (3) (1).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

<figure><img src="../.gitbook/assets/Image from Gradio (13).png" alt=""><figcaption></figcaption></figure>

* **Generate PDF Button Label:** Used to specify the button's label.
* **Rich Text field:** Used to specify the API name of the Rich Text field whose content will be converted to PDF.

## Demo

The example below shows a Rich Text field containing images:

![](<../.gitbook/assets/image (2) (3) (1).png>)

To generate the PDF click on the SharinPix Rich Text To PDF component's button. The picture below depicts a preview of the PDF generated:

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2020.05.18-16_15_34 (1) (1) (1).png>)
