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

# SharinPix Mobile PDF Form Launcher

The **SharinPix Mobile PDF Form Launcher** is used on the Salesforce mobile app to open the PDF form on the SharinPix mobile app.

<figure><img src="../.gitbook/assets/Image from Gradio (17).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
* On Mobile
* In Flows (but not in Field Service Mobile Flow)
* In your own Lightning Component development
{% endhint %}

<figure><img src="../.gitbook/assets/Image from Gradio (18).png" alt=""><figcaption></figcaption></figure>

## Getting Started

## Lightning Component Parameters

![](<../.gitbook/assets/pdf1 (1) (1) (1).png>)

* **Button Label:** This property supports using an expression to define its custom label. The correct format is {!$Label.customLabelName}.
* **Album ID:** Enter the Album ID or Record ID. Leave blank to use the current Record ID. This property supports using an expression to define its custom label. The correct format is {!$Label.customLabelName}.
* **Component Id:** Component ID to be matched by SharinPix components on the page. This is any text which will be common between this component and the SharinPix album component. It allows for matching components to communicate in case some components need to be repeated on the same record page. Example: Set 'sharinpix-1' as Target Component ID here and also on SharinPix Album component's Component ID field. This property supports using an expression to define its custom label. The correct format is {!$Label.customLabelName}.
* **New field API name:** Text field to be used as job name. If set to None, value will default to either the record's name (if available) or the record ID. This property supports using an expression to define its custom label. The correct format is {!$Label.customLabelName}.
* **Auto tags:** Add tags separated by the | character. These tags will be enforced on images taken by the user. This property supports using an expression to define its custom label. The correct format is {!$Label.customLabelName}.
* **Pdf Template Url:** URL of the pdf to be filled. This property supports using an expression to define its custom label. The correct format is {!$Label.customLabelName}. We use the URL on which is shared on the Pdf Template record.
* **Pre-Fill Fields' API Names:** Field API names of fields containing pre-filled values. The correct format is Field1|Field2|Field3. This property supports using an expression to define its custom label. The correct format is {!$Label.customLabelName}.
* **Universal link:** Generate a universal link when enabled instead of a deep link.

**Universal links** are exclusive to Apple devices running iOS, and have the ability to open a web page from an application. Instead of defining a custom URL scheme, a universal link matches a set of web pages to locations in-app.

**Deep links** are a type of link that send users directly to an app instead of a website or a store. They are used to send users straight to specific in-app locations. Deep linking does this by specifying a custom URL scheme (iOS Universal Links) or an intent URL (on Android devices) that opens your app if it’s already installed.

## Demo

* Add the SharinPix Mobile Pdf Form Launcher Component on the Lightning Component.

![](<../.gitbook/assets/image - 2026-02-06T163056.835.png>)

* Click on the Fill Form button onto the Lightning Web Component.

<figure><img src="../.gitbook/assets/Image from Gradio (17).png" alt=""><figcaption></figcaption></figure>

* The picture below depicts the Pdf Form with filled values on the text fields including the signature field and [photo fields](../mobile-app/sharinpix-pdf-photo-field.md).

![](<../.gitbook/assets/first (1) (1) (1).jpg>)

{% hint style="warning" %}
**Warning:**

Signing the PDF before capturing the photos using the photo fields will result in losing the signature.

We recommend that users sign the PDF after capturing the photos on the photo fields.
{% endhint %}

* To be able to sign, click on the button'Sign here'.
* The picture below shows the result.
* You can sign on the signature window.

![](<../.gitbook/assets/second (1) (1) (1).jpg>)

* The picture below depicts the signature on the Pdf Form after clicking the 'create' button on the signature window as shown above.
* Photo Field can be added as well on the pdf. You can refer to the article [SharinPix PDF Photo Field](../mobile-app/sharinpix-pdf-photo-field.md) for more info.

![](<../.gitbook/assets/phot and sig mobile (1) (1) (1).jpg>)

## Final Result

You can also save the PDF.

![](<../.gitbook/assets/1-1 (1) (1) (1).png>)
