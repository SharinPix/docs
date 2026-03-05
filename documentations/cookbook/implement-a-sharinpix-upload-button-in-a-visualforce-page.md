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

# Implement a SharinPix upload button in a Visualforce page

{% hint style="info" %}
This article demonstrates how to implement a SharinPix upload button in a Visualforce page by modifying the **SharinPix Visualforce component**.
{% endhint %}

<figure><img src="../.gitbook/assets/test.jpg" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

The SharinPix package includes the ready-made **SharinPix Upload Button** component which can also be used. This component is available in **Lightning** and can be directly added to your record page.

For more information about the SharinPix Upload Button component and how it is used, refer to the article below:

[SharinPix Upload Button](../lightning-web-component/sharinpix-upload-button.md)
{% endhint %}

To implement the above upload button, modify the SharinPix Visualforce component as follows:

```html
<sharinpix:SharinPix height="35px" parameters="{'abilities':{'album_id':{'Access':{'see':true,'image_list':true,'image_upload':true,'image_delete':true,'fullscreen':true,'image_caption':true,'trash':true,'image_tag':true}}},'Id':'album_id', 'path':'/upload'}"></sharinpix:SharinPix>
```

Here are some points to consider when using the above code snippet:

* The button's height is 35px
* The value, **album\_id** , should be replaced with your desired album ID (or record ID)

You can also modify the button's label using the **label** parameter as demonstrated below:

```html
<sharinpix:SharinPix height="35px" parameters="{'abilities':{'album_id':{'Access':{'see':true,'image_list':true,'image_upload':true,'image_delete':true,'fullscreen':true,'image_caption':true,'trash':true,'image_tag':true}}},'Id':'album_id', 'path':'/upload', 'label':'Upload Images'}"}"></sharinpix:SharinPix>
```

{% hint style="success" %}
**Tip:**

Different SharinPix album abilities and features can be applied to the SharinPix Visualforce component.

Such abilities and features can be tested using the **SharinPix Code Generator**. This feature can also be used to generate the corresponding code for the Visualforce component.

For more information about the SharinPix Code Generator, refer to the article below:

[SharinPix Code Generator](sharinpix-code-generator.md)
{% endhint %}

{% hint style="success" %}
**Resources:**

For more information about the SharinPix Visualforce component, refer to the links below:

* [SharinPix Visualforce Component (Admin-friendly version)](../features/main-integration/using-on-classic-with-a-visualforce-page-without-an-apex-controller-admin-friendly-version.md#sharinpix-visualforce-component)
* [SharinPix Visualforce Component (Developer-oriented)](../features/main-integration/using-on-classic-with-a-visualforce-page-with-an-apex-controller-developer-skills-required.md#id-1.-sharinpix-visualforce-component)
{% endhint %}
