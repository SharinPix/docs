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

# SharinPix To PDF

{% hint style="warning" %}
This component is only available in the Enterprise license plan of SharinPix. For more info, please contact [support@sharinpix.com](mailto:support@sharinpix.com)
{% endhint %}

The **SharinPix To PDF** component allows users to generate a PDF using preselected images from a SharinPix Album.

This is a great way for you to generate reports and send them as attachments in email. In addition, the PDF generated will be saved on the record as Content Document.

<figure><img src="../.gitbook/assets/image (4) (2) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used on:

* Page Builder
* Desktop
* Mobile
* Community: For more information about how to use the SharinPix to PDF component in Salesforce Community, click [here](../features/main-integration/using-sharinpix-to-pdf-component-in-salesforce-community.md).
{% endhint %}

## Getting Started

{% hint style="warning" %}
**Note:**

In order to use this component, you should ensure that:

* Image Sync is enabled for the **SharinPix Album** component. To do so, check the **Enable Image** **Sync** checkbox in the SharinPix Album's parameters. This step is required to enable the creation of **SharinPix Image Objects** upon image uploads. Click [here](../image-sync/setup-sharinpix-image-sync.md) for more information about how to setup the SharinPix Image Sync.
* The permission set **SharinPix Lightning Components** is assigned to all users attempting to use the SharinPix To PDF component.
{% endhint %}

To use the SharinPix To PDF component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/image (5) (2) (1).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

<figure><img src="../.gitbook/assets/image (6) (2) (1).png" alt=""><figcaption></figcaption></figure>

* **Generate PDF Button Label:** Used to set the custom button's label. The default value is **Generate PDF**.
* **Image URL field:** The image URL field from SharinPix Image object you want us to use. This refers to the type of image transformation.
* **Image Caption Text:** The text field from SharinPix Image object is used as the caption for each image.
* **Number Of Columns:** The number of columns you want for the table generated for the table of images.
* **First Page Content:** This is used to display the content of the given field as the first page of the PDF. The parameter can take a list of one or more Rich Text field API names delimited by a semi-colon.
* **Last Page Content:** This is used to display the content of the given field as the last page of the PDF. The parameter can take a list of one or more Rich Text field API names delimited by a semi-colon.
* **Images' Pre-description:** Optional Rich Text field used as pre-description of the images. The parameter can take a list of one or more Rich Text field API names delimited by a semi-colon.
* **Images' Post-description:** Optional Rich Text field used as post-description of the images. The parameter can take a list of one or more Rich Text field API names delimited by a semi-colon.
* **Page Orientation:** Orientation of the generated PDF. The default value is **portrait**.
* **Single Image Per Page:** Used to display only one image per page.
* **Footer format:** An HTML format to display in the footer section of each page. Merge fields such as {pagenumber} and {pagecount} can include the page number and the total number of pages in the PDF.
* **Filename Field:** The API name of the field that will contain the filename to be used for the generated PDF.
* **captionTextBelowImage:** Used to display one column with caption text below each image. Number of Columns should be taken as 1 and the option '**Single Image Per Page** ' should be **unchecked**.

{% hint style="success" %}
**Tip:**

* The SharinPix package includes the Apex class **SharinPixToPdfAutomation** which consists of an invocable method allowing automatic PDF generation using Flows. For more information on how to set up such automations, refer to the following article: [Generate SharinPix PDFs Automatically](../cookbook/generate-sharinpix-pdfs-automatically.md).
* You can also generate PDF files for multiple records using an Apex Batch. For more information on such implementation, refer to the following link: [Generate PDF files using an Apex Batch Implementation (Developer-Oriented)](../cookbook/generate-sharinpix-pdfs-automatically.md#apex-batch-implementation-developer-oriented)
{% endhint %}

## Demo

To generated the PDF, select some images from the SharinPix Album and click on **Generate PDF** button as shown below:

![](<../.gitbook/assets/7ffd4dac-b219-4254-9bd4-f26297157744 (1) (1) (1).png>)

Below is an instance of the PDF generated:

![Resorts | Salesforce - Google Chrome](<../.gitbook/assets/9afb1d3c-164a-4759-8cf6-ff125c9e5e34 (1) (1) (1).png>)

{% hint style="success" %}
**Tip:**

For best results, use the SharinPix Transformations to have custom image size.

More information on transformation can be found here: [SharinPix Transformation - get your images automatically resized!](../image-sync/sharinpix-transformation-get-your-images-automatically-resized.md)
{% endhint %}

Below are some references for optimal image transformations for you to have a visually appealing PDF:

| Layout                                 | Columns | Transformation type    | Value     |
| -------------------------------------- | ------- | ---------------------- | --------- |
| Portrait 4 images per page             | 2       | Pad to size            | 1000x1500 |
| <p>Portrait 6 images per page<br></p>  | 2       | <p>Pad to size<br></p> | 1000x1000 |
| <p>Portrait 8 images per page<br></p>  | 2       | <p>Pad to size<br></p> | 1000x650  |
| <p>Portrait 10 images per page<br></p> | 2       | <p>Pad to size<br></p> | 1000x580  |
| Landscape 3 images per page            | 1       | Pad to size            | 1000x1500 |

![](<../.gitbook/assets/Capture_d’écran_2020-07-17_à_10.30.14 (1) (1) (1).png>)

{% hint style="danger" %}
**Note:**

Salesforce has some limitations regarding PDF generation.

For the SharinPix to PDF component to work as expected, kindly ensure that the generated PDF file is less that file is 60 MB and that the maximum total size of all images included in a generated PDF is less than 30 MB.

For more information on Salesforce PDF generation limitations, kindly refer to this article:

[Visualforce PDF Rendering Considerations and Limitations](https://developer.salesforce.com/docs/atlas.en-us.pages.meta/pages/pages_output_pdf_considerations.htm)
{% endhint %}
