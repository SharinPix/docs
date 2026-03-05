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

# SharinPix PDF Photo Field

The SharinPix PDF Photo Field allows mobile users to add images to a PDF on the SharinPix mobile app. This helps make the PDF more communicative.

This article:

* [Demonstrates adding an image in a PDF using the SharinPix PDF Photo Field](sharinpix-pdf-photo-field.md#demo)
* [Explain the Photo Field Parameters](sharinpix-pdf-photo-field.md#photo-field-parameters)
* [Explain prefill value for Photo Field](sharinpix-pdf-photo-field.md#prefill-photo-fields-with-template-images-using-url)

{% hint style="warning" %}
**Warning:**

Signing the PDF before capturing the photos using the photo fields will result in losing the signature.

We recommend that users sign the PDF after capturing the photos on the photo fields.
{% endhint %}

## Demo

The screenshot below shows the first screen when you have uploaded a PDF.

Photo fields should be of type **Text** and the name should start with "**sp\_photo\_**".

<figure><img src="../.gitbook/assets/SharinPix PDF Photo Field -1.png" alt=""><figcaption></figcaption></figure>

For this example, we have clicked on "**top view**". Once you click on one of the text fields, the app redirects you to the camera screen. Once you have taken the image, an upload icon will appear.

<figure><img src="../.gitbook/assets/SharinPix PDF Photo Field -2.png" alt=""><figcaption></figcaption></figure>

Once the image is uploaded you will be redirected to the PDF. The photo taken appears on the photo field previously selected.

{% hint style="warning" %}
**Note:**

You can replace the photo field thumbnail by selecting the field and capturing a new photo.
{% endhint %}

<figure><img src="../.gitbook/assets/SharinPix PDF Photo Field -3.png" alt=""><figcaption></figcaption></figure>

You can also click on the save icon, to save the work progress. Then, if you close the page and open it again, your image will still be on the PDF.

<figure><img src="../.gitbook/assets/SharinPix PDF Photo Field -4.png" alt=""><figcaption></figcaption></figure>

You can also delete the progress by clicking on the back arrow. A popup will appear, allowing you to choose to **continue working**, **delete,** or **save** and **exit**.

<figure><img src="../.gitbook/assets/SharinPix PDF Photo Field -5.png" alt=""><figcaption></figcaption></figure>

## Photo Field Parameters

This section lists the different parameters that can be used in the Photo Field:

* [mode](sharinpix-mobile-app-deeplink-syntax.md#mode)
* [roll](sharinpix-mobile-app-deeplink-syntax.md)
* [compass](sharinpix-mobile-app-deeplink-syntax.md#compass)
* [flash](sharinpix-mobile-app-deeplink-syntax.md#flash)
* [tags](sharinpix-mobile-app-deeplink-syntax.md#tags)
* [auto\_tags](sharinpix-mobile-app-deeplink-syntax.md#auto_tags)
* [default\_tags](sharinpix-mobile-app-deeplink-syntax.md#default_tags)
* [template\_image](sharinpix-pdf-photo-field.md#template_image)

The parameters should be configured in the default value section as indicated in the picture below:

<figure><img src="../.gitbook/assets/SharinPix PDF Photo Field -6.png" alt=""><figcaption></figcaption></figure>

### template\_image

We can use the Photo Field to open a [template image](sharinpix-mobile-app-template-image.md) in annotation mode in the SharinPix mobile app. The _template\_image_ parameter takes as value **an encoded version of the template image public URL.**

Here is an example of the key and value to be added in the _Default Value_ field with the template image URL '**https://p.sharinpix.com/image.test.com/smart\_solar.png**':

<mark style="color:red;">`template_image=https%3A%2F%2Fimage.test.com%2Fsmart_solar.png`</mark>

<figure><img src="../.gitbook/assets/SharinPix PDF Photo Field -7.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
This parameter can also be passed via the URL to have dynamic images tailored to specific Salesforce records that launch the SharinPix mobile app. In the above example, where the _Photo Field_ 's name is **sp\_photo\_templateImage**, the URL launching SharinPix can override its value with a URL parameter as provided below:

**...\&pvsp\_photo\_templateImage=template\_image%3Dhttps%253A%252F%252Fimage.test.com%252Fsmart\_solar.png**

For more information on pre-filling PDFs, see [Using SharinPix deeplink to launch a PDF from Salesforce mobile](../features/main-integration/using-sharinpix-deeplink-to-launch-a-pdf-from-salesforce-mobile.md).
{% endhint %}

SharinPix also includes an additional parameter **pf\_fill,** that can be used along with the **template\_image.** The **pf\_fill** parameter controls the behavior of displaying the template image on the photo field when initially opening a PDF document.

This parameter accepts two values:

* **true:** When set to **true** , the template image associated with the photo field will be automatically filled into the field when the PDF is first opened.

&#x20;    <mark style="color:red;">`"pf_fill": true`</mark>

* **false:** When set to **false** , the photo field will be blank when the PDF is first opened. (If no value is specified, the flag defaults to false.)

<mark style="color:red;">`"pf_fill": false`</mark>

Here is an example of the key and value to be added in the _Default Value_ field with the template image URL **https://p.sharinpix.com/image.test.com/smart\_solar.png** and the **pf\_fill** parameter.\
<mark style="color:red;">`template_image=https%3A%2F%2Fimage.test.com%2Fsmart_solar.png&pf_fill=true`</mark>

The picture below shows a PDF form with 2 photo fields, one with **template\_image** as default value and the other with both **template\_image** and **pf\_fill** as default value.

<figure><img src="../.gitbook/assets/SharinPix PDF Photo Field -8.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/SharinPix PDF Photo Field -9.png" alt=""><figcaption></figcaption></figure>

## Prefill Photo Fields with Template Images Using URL

{% hint style="warning" %}
Note:

To work around App Extension size limitations on Salesforce Field Service (SFS), check out the article [Integration of SharinPix App with SFS (FSL) App using App Extension](../integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-app-extension.md#creation-of-the-app-extension).
{% endhint %}

In addition to setting the <mark style="color:red;">`template_image`</mark> and <mark style="color:red;">`pf_fill`</mark> parameters directly in the **Default Value** of the PDF form field, SharinPix also supports **pre filling photo fields via URL parameters** when launching the PDF from a deep link.

**Syntax:**\
To pass a template image as a **prefill value** , use the <mark style="color:red;">`pv`</mark> prefix followed by the photo field name. The value should include the <mark style="color:red;">`template_image`</mark> URL and the optional <mark style="color:red;">`pf_fill`</mark> parameter, both **URL-encoded**.

**Example:**

<mark style="color:red;">`sharinpix://upload?token=...&pdf=https%3A%2F%2Fpdf-mobile-templates.com%2Ftemplate_image_test.pdf&pvsp_photo_field=template_image%3Dhttps%3A%2F%2Fpdf-template-image.jpg%26pf_fill%3Dtrue`</mark>

In the above example:

* <mark style="color:red;">`sp_photo_field`</mark> is the name of the photo field you want to prefill.
* The <mark style="color:red;">`pv`</mark> prefix indicates that it's a **prefill** value.
* The value of <mark style="color:red;">`pvsp_photo_field`</mark> includes:
  * <mark style="color:red;">`template_image=https://pdf-template-image.jpg`</mark> (image URL)
  * <mark style="color:red;">`pf_fill=true`</mark>

Both the key and value should be properly **URL-encoded**.

Notes

* If <mark style="color:red;">`pf_fill=true`</mark> is provided, the image will appear directly in the photo field when the PDF is opened.
* If <mark style="color:red;">`pf_fill`</mark> is not specified or set to <mark style="color:red;">`false`</mark>, the field will display the template image only when the user opens the photo field manually.
* This method is useful when launching PDFs from external apps or workflows where field values need to be set dynamically.
