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

# SharinPix PDF Merge

{% hint style="info" %}
The **SharinPix PDF Merge** component permits users to combine two or more PDFs from a SharinPix Album into a single PDF. It also allows the user to save the merged PDF in the SharinPix Album.
{% endhint %}

<figure><img src="../.gitbook/assets/image (20) (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
* On Mobile
{% endhint %}

## Getting Started

To use the SharinPix PDF Merge component, simply drag and drop the component from the Lightning App Builder onto the page layout.

<figure><img src="../.gitbook/assets/image (21) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

<figure><img src="../.gitbook/assets/image (22) (3).png" alt=""><figcaption></figcaption></figure>

* **Button Label:** Used to specify the label to be shown on the button to merge PDFs.
* **Filename Field API Name:** The Field API name of the field containing the filename for the merged PDF from the album record.
* **All pages:** All pages of the PDF documents will be merged if at least one of them is selected.
* **Component ID:** Used to specify the common ID with the targeted SharinPix component. **Note:** _This parameter should be populated for the SharinPix PDF Merge component to work. The value entered here should match the value in the component ID parameter of the corresponding SharinPix Album component found on the page._

{% hint style="warning" %}
**Note:**

Specific pages can also be merged. If your multi-page PDFs show as one page or image only, you can [contact SharinPix Support](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/how-to-contact-support) to increase the number of pages rendered for PDF documents.
{% endhint %}

### Demo

The picture below depicts a SharinPix PDF Merge and a SharinPix Album component with uploaded PDFs.

![](<../.gitbook/assets/pdfMergeRec (1) (1) (1).png>)

{% hint style="warning" %}
**Note:**

* Both components are related using the same **Component ID** value.
* The SharinPix PDF Merge button is disabled as no PDF selection has been performed yet.
{% endhint %}

Start by selecting the PDFs to be merged. The SharinPix PDF Merge button should be enabled after the selection, as shown below.

To select the PDF, you have to click on the image.

![](<../.gitbook/assets/pdfMerge0 (1) (1) (1).png>)

First PDF is open and the images are selected.

![](<../.gitbook/assets/pdfMerge1 (1) (1) (1).png>)

Second PDF is open and the images are selected.

![](<../.gitbook/assets/pdfMerge2 (1) (1) (1).png>)

Click on the button to start the merge.

The merged PDF is uploaded to the related SharinPix Album component as shown in the picture below.

![](<../.gitbook/assets/pdfMerge3 (1) (1) (1).png>)

In the screenshot below, you can see that the whole PDF has been merged in the order it has been selected.

![](<../.gitbook/assets/pdfMerge4 (1) (1) (1).png>)
