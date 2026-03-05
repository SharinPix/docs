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

# SharinPix Copy To Clipboard

The **SharinPix Copy To Clipboard** component permits the user to select and copy images from the **SharinPix Album** component and paste the same images in a field of type **Rich Text Area**.

![](<../.gitbook/assets/image (1) (8).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used on:

* Page Builder
* Desktop
* In your own Lightning Component development
{% endhint %}

## Getting Started

{% hint style="warning" %}
**Note:**

In order to use the SharinPix Copy To Clipboard component, you must ensure that Image Sync is enabled for the **SharinPix Album** component. To do so, check the **Enable Image Sync** checkbox in the SharinPix Album's parameters.

This step is required to enable the creation of SharinPix Image Objects upon image uploads.

You can click [here](../image-sync/setup-sharinpix-image-sync.md) for more information about how to setup the SharinPix Image Sync.
{% endhint %}

To use the SharinPix Copy To Clipboard component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

![](<../.gitbook/assets/image (126).png>)

## Lightning Component Parameters

![](<../.gitbook/assets/image (2) (3).png>)

* **Button label:** Used to specify the copy button's label. The default value is **Copy to Clipboard**.
* **Image URL field:** Used to specify the image size by selecting an **Image URL field** from the dropdown menu. The default value is **sharinpix\_\_ImageURLFull\_\_c** which will display the image in full size.
* **Image Caption Text:** Used to specify the caption text to be displayed alongside the image. The default value is **sharinpix\_\_Title\_\_c** which refers to the image's title.
* **Number of Columns:** Used to specify the maximum number of images to be displayed per row. The values available range from 1 to 10 rows.
* **Prefix Images with Rich Text Area:** Used to specify the field for which the value/content will be added **before** all selected images. The default value is **None**.
* **Suffix Images with Rich Text Area:** Used to specify the field for which the value/content will be added **after** all selected images. The default value is **None**.
* **Open Preview in New Tab:** Used to enable/disable option to open the preview in a new tab. This parameter should be enabled if your browser blocks certain modal contents..

{% hint style="warning" %}
**Note:**

Some browsers, such as Safari, block certain modal contents. In such cases, the parameter **Open Preview in New Tab** should be checked so as to preview the images properly.
{% endhint %}

## Demo

Select images from the **SharinPix Album** component:

![](<../.gitbook/assets/image (3) (2).png>)

Click on the button **Copy to Clipboard**. This will open a modal previewing the selected images as shown below:

![](<../.gitbook/assets/screenshot-enterprise-computing-8320-dev-ed.lightning.force.com-2020.05.13-15_49_09 (1) (1) (1).png>)

Click on the button **Copy to Clipboard** inside the modal to copy the images. Once done, you can paste them inside a field of type **Rich Text Area** :

![](<../.gitbook/assets/image (4) (3).png>)

{% hint style="warning" %}
**Note:**

When using the **Copy to Clipboard** , the content copied is in HTML format. Therefore it's essential to note that not all platforms support the handling of HTML content. This means that pasting such content may not work as expected on every platform. Only platforms that explicitly allow the use of HTML content will be able to correctly render and handle the pasted HTML.

For example, Gmail is a platform that supports HTML content. When you paste HTML content into a Gmail email composition window, it retains the formatting and renders the content as intended.

Moreover, if you want to test out the capability of the receiver to hold HTML, you can copy a part of this page including an image, and paste it in that place. If the images are not rendered that means that the container may not be able to hold HTML so it will not be compatible with Copy To Clipboard from SharinPix as well.
{% endhint %}
