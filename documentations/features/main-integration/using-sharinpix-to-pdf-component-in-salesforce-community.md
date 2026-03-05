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

# Using SharinPix to PDF Component in Salesforce Community

{% hint style="warning" %}
This component is only available in the Enterprise license plan of SharinPix. For more info, please contact [support@sharinpix.com](mailto:support@sharinpix.com)
{% endhint %}

The **SharinPix To PDF** component allows users to generate a PDF using preselected images from a SharinPix Album.

This is a great way for you to generate reports and send them as attachments in email. In addition, the PDF generated will be saved on the record as Content Document.

This article demonstrates how to use this component in **Salesforce Communities**.

## Getting Started

{% hint style="warning" %}
**Note:**

In order to use this component, you should ensure:

*   That Image Sync is enabled for the **SharinPix Album** component. To do so, check the **Enable Image Sync** checkbox in the SharinPix Album's parameters. This step is required to enable the creation of **SharinPix Image Objects** upon image uploads.

    You can click [here](../../image-sync/setup-sharinpix-image-sync.md) for more information about how to set up the SharinPix Image Sync.
*   Enabled the usage of SharinPix in Salesforce Community

    You can click [here](using-sharinpix-in-salesforce-community.md) for more information on how to enable the usage of SharinPix in Communities.
{% endhint %}

To use the SharinPix To PDF component, you simply need to drag and drop the component from the **Components** section onto your community page layout.

![](<../../.gitbook/assets/image (88).png>)

## Lightning Component Parameters

![](<../../.gitbook/assets/image (89).png>)

{% hint style="danger" %}
**Note:**

* All Salesforce fields used as parameters in the SharinPix to PDF component are available on the SharinPix Image object.
* All custom fields used on the component should be added to the SharinPix Image object.
{% endhint %}

* **Generate PDF Button Label:** Used to set the custom button's label. The default value is **Generate PDF**.
* **Image URL field:** The API name of the Image URL field to be used for the type of image. Image sizes will depend on the field chosen. The default value is **sharinpix\_\_ImageURLFull\_\_c**
  * Some values already included in the SharinPix Package are:
    * sharinpix\_\_ImageURLFull\_\_c
    * sharinpix\_\_ImageURLOriginal\_\_c
    * sharinpix\_\_ImageURLThumbnail\_\_c
    * sharinpix\_\_ImageURLMini\_\_c
* **Image Caption Text:** The API name of the field storing the text to be displayed alongside the image. The default value is **None**.
* **Number Of Columns:** The maximum number of images to be displayed per row.
* **First Page Content:** The API name of the rich-text field to be used as first page content. The default value is **None**.
* **Last Page Content:** The API name of the rich-text field to be used as last page content. The default value is **None**.
* **Images' Pre-description:** The API name of the rich-text field to be used for the pre-description of images. The default value is **None**.
* **Images' Post-description:** The API name of the rich-text field to be used for the post-description of images. The default value is **None**.
* **Page Orientation:** Orientation of the generated PDF. The default value is **portrait**.
* **Single Image Per Page:** Used to display only one image per page.
* **Footer format:** An HTML format to display in the footer section of each page. Merge fields such as {pagenumber} and {pagecount} can be used to include page number and total pages of the PDF.

## Demo

To generated the PDF, select some images from the SharinPix Album and click on **Generate PDF** button as shown below:

![](<../../.gitbook/assets/image (90).png>)

The PDF generated can be found under the **Notes & Attachments** section in the **Related** tab:

![](<../../.gitbook/assets/image (91).png>)

Below is an instance of the PDF generated:

![](<../../.gitbook/assets/image (92) (1).png>)

{% hint style="success" %}
**Tip:**

For best results, use the SharinPix Transformations to have custom image size.

More information on transformation can be found here: [SharinPix Transformation - get your images automatically resized!](../../image-sync/sharinpix-transformation-get-your-images-automatically-resized.md)
{% endhint %}

Below are some references for optimal image transformations for you to have a visually appealing PDF:

| Layout                                 | Columns | Transformation type    | Value     |
| -------------------------------------- | ------- | ---------------------- | --------- |
| Portrait 4 images per page             | 2       | Pad to size            | 1000x1500 |
| <p>Portrait 6 images per page<br></p>  | 2       | <p>Pad to size<br></p> | 1000x1000 |
| <p>Portrait 8 images per page<br></p>  | 2       | <p>Pad to size<br></p> | 1000x650  |
| <p>Portrait 10 images per page<br></p> | 2       | <p>Pad to size<br></p> | 1000x580  |
| Landscape 3 images per page            | 1       | Pad to size            | 1000x1500 |

{% hint style="info" %}
The SharinPix to PDF component is also available in Salesforce Lightning. For more information about how to use this component in Lightning, refer to the following article:

[SharinPix To PDF](../../lightning-web-component/sharinpix-to-pdf.md)
{% endhint %}
