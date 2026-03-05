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

# Using SharinPix deeplink to launch a PDF from Salesforce mobile

This article demonstrates how to:

* [Configure a SharinPix deeplink to launch a PDF from the Salesforce mobile](using-sharinpix-deeplink-to-launch-a-pdf-from-salesforce-mobile.md#configure-the-sharinpix-deeplink-to-launch-the-pdf)
* [Enable and display the PDF values on the SharinPix Image record relating to the submitted PDF](using-sharinpix-deeplink-to-launch-a-pdf-from-salesforce-mobile.md#enable-and-display-the-pdf-values)

{% hint style="warning" %}
**Requirements**

For such implementation, please ensure that you have a **PDF** document which:

* Does not consist of features that require being online
* Utilizes either embedded fonts or the following standard fonts: Courier, Courier-Bold, Courier-BoldOblique, Courier-Oblique, Helvetica, Helvetica-Bold, Helvetica-BoldOblique, Helvetica-Oblique, Times-Roman, Times-Bold, Times-Italic, Times-BoldItalic, Symbol, ZapfDingbats.
{% endhint %}

## Configure the SharinPix deeplink to launch the PDF

{% hint style="warning" %}
**Pre-requirement:**

Prior to configuring the deeplink, you should ensure that a **SharinPix token** is available for the record on which you intend to upload the PDF.

You can refer to the following article to set up an automation that will generate a SharinPix token upon creation of records if required:

[SharinPix automatic token generation (Admin Friendly)](../../mobile-app/sharinpix-automatic-mobile-upload-token-generation-admin-friendly.md)
{% endhint %}

To launch a PDF from the Salesforce mobile app using SharinPix, the **pdf** parameter should be configured in the SharinPix deeplink.

The general form of such deeplink is as follows:

<mark style="color:$danger;">`sharinpix://upload?token=<Your Token>&pdf=<Your Encoded PDF URL>`</mark>

As indicated above, the pdf parameter takes as value **an encoded version of the PDF URL**. For example, if your PDF URL is **https://pdf.test.com/smart\_solar.pdf** , here is the encoded version to be used as the value for the **pdf** parameter: <mark style="color:$danger;">`https%3A%2F%2Fpdf.test.com%2Fsmart_solar.pdf`</mark>

Here is an example of the full deeplink:

<mark style="color:$danger;">`sharinpix://upload?token=<Your Token>&pdf=https%3A%2F%2Fpdf.test.com%2Fsmart_solar.pdf`</mark>

### The Prefill Option

The prefill option is used to prefill the PDF text boxes. To enable this option, the parameter **pv** should be added, followed by **the text box name**. This parameter should store the encoded prefill value as shown below:

<mark style="color:$danger;">`pvTextboxName=<Your Encoded Prefill Value>`</mark>

The example below demonstrates a deeplink using the **pdf** parameter **along with the prefill option** :

<mark style="color:$danger;">`sharinpix://upload?token=<Your Token>&pdf=<Your Encoded PDF URL>&pvSurname=John%20Doe`</mark>

## Enable and display the PDF values

The PDF values can be displayed on the **SharinPix Image** record corresponding to the submitted PDF as demonstrated below:

![](<../../.gitbook/assets/image (70).png>)

{% hint style="warning" %}
**Note:**

* For the time being, values are only saved in fields containing text values (<mark style="color:$danger;">`'STRING', 'TEXTAREA', 'PICKLIST', 'MULTIPICKLIST', 'PHONE', 'URL'`</mark>)
* For the above configuration:
  * The **SharinPix Image Sync feature should be enabled for the object on which you are uploading the PDF**. For more information on how to enable the Image Sync on an object, refer to this article: [Setup SharinPix Image Sync](../../image-sync/setup-sharinpix-image-sync.md)
  * A Webhook of type **Upload Done** or **New Image** should be configured for your organization. For more information on how to configure SharinPix Webhooks, refer to this [link](../../image-sync/image-sync-for-pictures-uploaded-via-sharinpix-mobile-app.md#how-to-configure-the-webhook).
{% endhint %}

To enable and display the PDF values, follow the steps below:

* From **Setup**, search for **Custom Metadata Types**
* Click on **Manage Records** next to **SharinPix Bypass**

<figure><img src="../../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

* Then, click on the Edit button corresponding to the **PdfValuesEnabled** entry
* On the **SharinPix Bypass Edit** page, check the **Active** checkbox

![](<../../.gitbook/assets/image (71).png>)

* Next, go to the **Object Manager** tab and search for the **SharinPix Image** object
* Go to the **Page Layouts** section and click on **SharinPix Image Layout**
* Add the **PDF Values** field to the page layout:

![](<../../.gitbook/assets/image (72) (1).png>)

Now that the **PdfValuesEnabled** option has been enabled, and the **PDF values** field added to the SharinPix Image object's page layout, after submitting PDF from the SharinPix mobile app, all the PDF values will be synced on the related SharinPix Image record. These values will be stored in a JSON format in the **PdfValues\_\_c** field:

![](<../../.gitbook/assets/image (73) (1).png>)

If the PDF contains field names corresponding to the SharinPix Image object's field API names within Salesforce, the fields are automatically filled with the value entered on the PDF as demonstrated below:

_On PDF_:

![](<../../.gitbook/assets/image (74) (1).png>)

_Corresponding field on Salesforce, (FieldName\_\_c in our case) is automatically populated with the value entered on the PDF_:

![](<../../.gitbook/assets/image (75) (1).png>)

{% hint style="success" %}
**Tips:**

* You can make use of this handy tool to encode the PDF URL: [https://www.urlencoder.org/](https://www.urlencoder.org/)
* The SharinPix to PDF deeplink can also be used in [Field Service App Extensions](../../integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-app-extension.md) and [Field Service Mobile Flows](../../integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-flows.md).
{% endhint %}
