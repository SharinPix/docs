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

# SharinPix Mobile App: Template Image

The SharinPix Template Image functionality allows mobile users to load and annotate a template image within the SharinPix mobile app. This is useful in cases where users are expected to annotate an existing template, such as a blueprint or map. Once the template image is downloaded the first time, this feature is also available offline.

This article demonstrates how to:

* [Configure the SharinPix Mobile Launcher Component to launch a template image in annotation mode on the SharinPix Mobile App from the Salesforce mobile app.](sharinpix-mobile-app-template-image.md#configure-the-sharinpix-mobile-launcher-component-to-launch-the-template-image)
* [Configure a SharinPix Deeplink to launch a template image in annotation mode on the SharinPix Mobile App from the Salesforce mobile app.](sharinpix-mobile-app-template-image.md#configure-a-sharinpix-deeplink-to-launch-the-template-image)

## Configure the SharinPix Mobile Launcher Component to launch the Template Image

We can use the mobile launcher component to open the template image in an annotation mode in the SharinPix mobile app. For this, the **template\_image** parameter should be configured in the custom parameters section as indicated in the picture below. The template\_image parameter takes as value **a template image public URL**.

Here is an example of the key and value to be added in the custom parameters with the template image URL '**https://p.sharinpix.com/image.test.com/smart\_solar.png**':

<mark style="color:red;">`template_image=https://p.sharinpix.com/image.test.com/smart_solar.png`</mark>

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Template Image  - 1.png" alt=""><figcaption></figcaption></figure>

## Configure a SharinPix Deeplink to launch the Template Image

{% hint style="warning" %}
**Pre-requirement:**

Prior to configuring the deeplink, you should ensure that a **SharinPix mobile upload token** is available for the record on which you intend to use the Template Image Viewer.

You can refer to the following article to set up an automation that will generate a SharinPix token upon the creation of records if required:

[SharinPix automatic mobile upload token generation (Admin Friendly)](sharinpix-automatic-mobile-upload-token-generation-admin-friendly.md)
{% endhint %}

We can use a deeplink to open the template image on an annotation mode in the SharinPix Mobile App. For this, the **template\_image** parameter should be configured in the SharinPix deeplink. Our deeplink URL starts with **sharinpix://** instead of https:// and opens our mobile app when installed on the device system.

The general syntax of such deeplink is as follows:

<mark style="color:red;">`"sharinpix://upload?token=<Your Token>&template_image=<Image URL>"`</mark>

As indicated above, the template\_image parameter takes an **encoded version of the template image public URL** as value. For example, if your image URL is **https://image.test.com/smart\_solar.png** , here is the encoded version to be used as the value for the **template\_image** parameter: <mark style="color:red;">`https%3A%2F%2Fimage.test.com%2Fsmart_solar.png`</mark>

Here is an example of the deeplink with the **template\_image** parameter configured with the **encoded version of the template image public URL** :

<mark style="color:red;">`sharinpix://upload?token=<Your Token>&template_image=https%3A%2F%2Fimage.test.com%2Fsmart_solar.png`</mark>

{% hint style="danger" %}
**IMPORTANT**:

URL encoding means converting special characters into a format that can be transmitted over the Internet.

There is a handy tool that can be used to perform this: [https://www.urlencoder.org/](https://www.urlencoder.org/).
{% endhint %}

{% hint style="success" %}
**Tip:**

The above deeplink can be embedded in custom implementations such as Screen Flow to open the template image within the SharinPix mobile app.
{% endhint %}

## Demo

Click the 'Sketch Plan' button as shown in the diagram below to open the template Image URL configured.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Template Image  - 2.png" alt=""><figcaption></figcaption></figure>

The image below shows the template image when opened on the annotation mode in the SharinPix mobile app.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Template Image  - 3.jpeg" alt=""><figcaption></figcaption></figure>

You can find various tool to annotate on the template image as shown in the diagram below.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Template Image  - 4.jpeg" alt=""><figcaption></figcaption></figure>

Once you click on the save button, the image with annotation will be uploaded to the target album as depicted in the diagram below.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Template Image  - 5.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Tips:

The template image can also be used on the PDF Photo Field. For more information, refer to the following article: [Link Documentation](sharinpix-pdf-photo-field.md#template_image).
{% endhint %}
