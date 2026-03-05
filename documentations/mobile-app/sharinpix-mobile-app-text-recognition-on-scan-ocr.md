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

# SharinPix Mobile App: Text Recognition on Scan (OCR)

It is possible to enable text recognition (OCR) during a scan using the SharinPix mobile app. This feature allows you to extract the text while scanning documents and images. The extracted text will be uploaded alongside the scanned document/image and will be accessible within your Salesforce organization.

This article demonstrates how to use the Text Recognition on Scan (OCR) feature.

{% hint style="warning" %}
**Note:**

The Text Recognition functionality is disabled by default.

For more information on how to enable this feature, refer to the following article: [SharinPix Mobile App: Deeplink syntax](sharinpix-mobile-app-deeplink-syntax.md#ocr)
{% endhint %}

After [enabling the text recognition](sharinpix-mobile-app-deeplink-syntax.md#ocr) feature, open the SharinPix mobile app and select the scan mode, as shown in the screenshot below:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Text Recognition on Scan (OCR) - 1.png" alt=""><figcaption></figcaption></figure>

The scan screen shows up:

* Scan a document or an image containing any text
* Once the scan is done, click on **Next** then **Done**

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Text Recognition on Scan (OCR) - 2.png" alt=""><figcaption></figcaption></figure>

Click on the submit button to upload the image

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Text Recognition on Scan (OCR) - 3.png" alt=""><figcaption></figcaption></figure>

## Access Scanned Text on SharinPix Image Object

The text extracted during the scan is stored in the [SharinPix Image Object](../image-sync/the-sharinpix-image-object.md) in Salesforce in the **OCRText\_\_c** custom field.

The following shows an example:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Text Recognition on Scan (OCR) - 4.jpg" alt=""><figcaption></figcaption></figure>
