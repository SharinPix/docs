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

# SharinPix To Rich Text Area

The **SharinPix To Rich Text Area** component permits to send and display a list of images selected from **SharinPix Album** component to a **Rich Text Field** in the form of a table of images.

![](<../.gitbook/assets/screenshot-flow-efficiency-7456-dev-ed.lightning.force.com-2019.12.13-16_37_59 (1) (1) (1).png>)

**Information:**

This feature is only available on Lightning. It can be used on:

* Community Builder
* Page Builder
* Desktop
* Mobile

## Getting Started

{% hint style="warning" %}
**Note:**

In order to use this component, you should ensure that:

1. Image Sync is enabled for the **SharinPix Album** component. To do so, check the **Enable Image Sync** checkbox in the SharinPix Album's parameters. This step is required to enable the creation of **SharinPix Image Objects** upon image uploads. You can click [here](../image-sync/setup-sharinpix-image-sync.md) for more information about how to setup the SharinPix Image Sync.
2. Your Record Page has **at least one** field of type **Text Area (Rich)** to append the images to.
3. The Text Area (Rich) field should be set at maximum length, that is, at 131,072 characters.
{% endhint %}

To use the SharinPix To Rich Text Area component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

![](<../.gitbook/assets/14 (1) (1) (2).png>)

## Lightning Component Parameters

![](<../.gitbook/assets/Screenshot_from_2022-05-18_10-50-52 (1) (1) (1).png>)

* **Rich Text Area to append to:** The field in which the table of images will be appended.
* **Append Button Label:** The personalized label if needed (By default it’s Append to + the label of the field)
* **Replace Rich Text Area content**: If checked, the targeted Rich Text Area's contents will be replaced. Previous content will be lost and cannot be recovered.
* **Image URL field:** The image URL field from SharinPix Image object you want us to use (Type of image transformation). The default value is **sharinpix\_\_ImageURLFull\_\_c** which displays the images in full size.
* **Image Caption text:** The text field from SharinPix Image object used as caption for each image.
* **Number of columns:** The number of columns you want for the table generated for the table of images.
* **Group by:** Group images in date sections according to date field chosen. Leave **None** if no section is needed.

**Tip:**

The SharinPix package includes the Apex class **SharinPixToRichTextAutomation** consisting of an invocable method which can be used to automatically append images to a Rich Text using Process Builders and Flows. For more information on how to set up such automations, refer to the following article: [Append images to a Rich Text field using a Process Builder or Flow (Admin-Oriented)](../cookbook/append-images-to-a-rich-text-field-using-a-flow-admin-oriented.md)

## Demo

Upload and select SharinPix images:

![](<../.gitbook/assets/Screenshot_from_2022-05-19_09-48-59 (1) (1) (1).png>)

Click on the button **Append to My Images** to generate the table and to display the images inside the targeted Rich Text field as shown below:

![](<../.gitbook/assets/Screenshot_from_2022-05-19_09-57-52 (1) (1) (1).png>)

Below is an example of a table with sections of images date taken.

![](<../.gitbook/assets/Screenshot_from_2022-05-19_10-07-54 (1) (1) (1).png>)

{% hint style="warning" %}
**Note:**

If no images have been selected, all images found in the album will be selected by default to generate the table of images.
{% endhint %}
