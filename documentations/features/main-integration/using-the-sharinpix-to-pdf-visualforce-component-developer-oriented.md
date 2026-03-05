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

# Using the SharinPix to PDF Visualforce Component (Developer-Oriented)

The SharinPix to PDF Visualforce Component is used to generate a PDF rendering all images uploaded to a SharinPix album or pre-selected images from the album.

In this article, you will learn how to make use of the SharinPix to PDF Visualforce Component in your implementation.

![](<../../.gitbook/assets/image (93) (1).png>)

{% hint style="warning" %}
**Note:**

* To use the SharinPix to PDF Visualforce Component, a SharinPix package version of **1.170** or higher is required. If you have a version an older version, you can update the package from the **AppExchange**
* You should also ensure that the permission set **SharinPix Lightning Components** is assigned to all users attempting to use the SharinPix to PDF Visualforce Component
* This Visualforce Component can be used in Salesforce Classic as well as Lightning
* The SharinPix package also consists of the **SharinPix To PDF Lightning Component**. For more information about the same, please refer to the following article:\
  [SharinPix To PDF](../../lightning-web-component/sharinpix-to-pdf.md)
{% endhint %}

## Getting Started

To use the SharinPix to PDF Visualforce Component, you will first need to implement a Visualforce page embedding the **SharinPix to PDF Visualforce Component** as well as the **SharinPix Visualforce Component**. The SharinPix Visualforce Component is used to display a SharinPix album.

### Visualforce Page Implementation

The following code snippet demonstrates the Visualforce page:

```html
<apex:page standardController="Account">
    <sharinpix:SharinPixToPDF recordId="{!Account.Id}" generatePdfLabel="Generate PDF" imageUrlFieldApiName="sharinpix__ImageURLThumbnail__c" imageCaptionText="Name" 
                      columns="2" preDescriptionFieldApiName="none" postDescriptionFieldApiName="none" orientation="portrait" footer="Page {pagenumber} of {pagecount}"/>

    <sharinpix:SharinPix height="400px" parameters="{'abilities':{'{!CASESAFEID($CurrentPage.parameters.Id)}':{'Access':{'image_list':true,'image_upload':true,'image_delete':true,'see':true,'image_tag':true}},'tags':{'read':true}},'Id':'{!CASESAFEID($CurrentPage.parameters.Id)}'}"/>
</apex:page>
```

#### Component's Parameters

The SharinPix to PDF Visualforce Component's parameters are as follows:

* **recordId:** Used to specify the record ID.
* **generatePdfLabelInput:** Used to set the button's label.
* **imageUrlFieldApiName:** To specify the image URL field to be used to set the image size in the generated PDF. This parameter takes as value an image URL field API name available on corresponding SharinPix Image records. Some pre-defined SharinPix Image's Image URLs available in the package are:
  * **sharinpix\_\_ImageURLOriginal\_\_c**
  * &#x20;**sharinpix\_\_ImageURLFull\_\_c**
  * **sharinpix\_\_ImageURLThumbnail\_\_c**
  * **sharinpix\_\_ImageURLMini\_\_c**

{% hint style="success" %}
**Tip:**

You can also define custom image size by using **SharinPix Transformations**.

More information on transformations can be found here:

[SharinPix Transformation - get your images automatically resized!](../../image-sync/sharinpix-transformation-get-your-images-automatically-resized.md)
{% endhint %}

Below are some references for optimal image transformations for you to have a visually appealing PDF:

| <p>Layout<br></p>                      | <p>Columns<br></p> | <p>Transformation type<br></p> | <p>Value<br></p>     |
| -------------------------------------- | ------------------ | ------------------------------ | -------------------- |
| <p>Portrait 4 images per page<br></p>  | <p>2<br></p>       | <p>Pad to size<br></p>         | <p>1000x1500<br></p> |
| <p>Portrait 6 images per page<br></p>  | 2                  | <p>Pad to size<br></p>         | <p>1000x1000<br></p> |
| <p>Portrait 8 images per page<br></p>  | 2                  | <p>Pad to size<br></p>         | <p>1000x650<br></p>  |
| <p>Portrait 10 images per page<br></p> | 2                  | <p>Pad to size<br></p>         | <p>1000x580<br></p>  |
| <p>Landscape 3 images per page<br></p> | 1                  | <p>Pad to size<br></p>         | 1000x1500            |

* **imageCaptionText:** To specify the PDF image's caption. This parameter takes as value a corresponding field API name from the corresponding SharinPix Image records. Some pre-defined values available from the SharinPix package are:
  * **Name**
  * **sharinpix\_\_ImageID\_\_c**
  * **sharinpix\_\_AlbumID\_\_c**
  * **sharinpix\_\_FileName\_\_c**
  * **sharinpix\_\_Tags\_\_c**
* **columns:** To specify the number of image columns in the PDF generated. This parameter only takes values ranging from 1 to 10.
* **firstPageFieldApiName:** To specify the field API name to be used as first page content. This parameter only accepts **Rich Text** fields.
* **lastPageFieldApiName:**  To specify the field API name to be used as last page content. This parameter only accepts **Rich Text** fields.
* **preDescriptionFieldApiName:** To specify the **Rich Text** field API name to be used as the images' pre-description.
* **postDescriptionFieldApiName:** To specify the **Rich Text** field API name to be used as the images' post-description.
* **orientation:** To specify the image orientation in the PDF. This parameter only takes two values, **portrait** or **landscape**.
* **singleImagePerPage:** To enable/disable option to display only one image per page in the PDF. This parameter is of **Boolean** type and therefore accepts only **true** or **false** as value.
*   **captionTextBelowImage:** To enable/disable the option to display one or more images in a single column with a caption text to be placed below each image, instead of to the right.                                                                         **Note:** The **captionTextBelowImage** only works when:

    * The number of columns is set to 1
    * The option **singleImagePerPage** is unchecked
    * The **orientation** is set to **portrait**

    Here's an example of the PDF generated when the option **captionTextBelowImage** is set to true:

![](<../../.gitbook/assets/image (94) (1).png>)

* **footer:** To specify the PDF's page numbering. This parameter accepts the following format:&#x20;

**Page {pagenumber} of {pagecount}** where **{pagenumber}** refers to the current page number and **{pagecount}** refers to the total number of pages.

#### Parameters' Data Type

| Parameter Name                         | Data Type          |
| -------------------------------------- | ------------------ |
| <p>recordId<br></p>                    | Id                 |
| <p>generatePdfLabelInput<br></p>       | <p>String<br></p>  |
| <p>imageUrlFieldApiName<br></p>        | <p>String<br></p>  |
| <p>imageCaptionText<br></p>            | <p>String<br></p>  |
| <p>columns<br></p>                     | <p>String<br></p>  |
| <p>firstPageFieldApiName<br></p>       | <p>String<br></p>  |
| <p>lastPageFieldApiName<br></p>        | <p>String<br></p>  |
| <p>preDescriptionFieldApiName<br></p>  | <p>String<br></p>  |
| <p>postDescriptionFieldApiName<br></p> | <p>String<br></p>  |
| orientation                            | <p>String<br></p>  |
| <p>singleImagePerPage<br></p>          | <p>Boolean<br></p> |
| <p>captionTextBelowImage<br></p>       | <p>Boolean<br></p> |
| <p>footer<br></p>                      | String             |

### Demo

Once your Visualforce page is ready, go ahead and add the same on your page layout.

To generate a PDF, select some images from the SharinPix album and click on the button **Generate PDF** as shown below:

![](<../../.gitbook/assets/image (95) (1).png>)

{% hint style="success" %}
**Tip:**

Clicking on the **Generate PDF** button without selecting any image will generate a PDF including all images present in the album by default.
{% endhint %}

Below is an instance of the PDF generated:

![](<../../.gitbook/assets/image (96) (1).png>)

{% hint style="danger" %}
**Note:**

Salesforce has some limitations regarding PDF generation.

For the SharinPix to PDF component to work as expected, kindly ensure that the generated PDF file is less that file is 60 MB and that the maximum total size of all images included in a generated PDF is less than 30 MB.

For more information on Salesforce PDF generation limitations, kindly refer to this article:

[Visualforce PDF Rendering Considerations and Limitations](https://developer.salesforce.com/docs/atlas.en-us.pages.meta/pages/pages_output_pdf_considerations.htm)
{% endhint %}
