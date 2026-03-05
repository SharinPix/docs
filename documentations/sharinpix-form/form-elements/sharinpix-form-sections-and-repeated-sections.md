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

# Form Features - IFrame

## Overview

The **IFrame** element embeds a web page inside a SharinPix Form. Use it for procedures, maps, or dashboards. You can also embed content exposed through [**SharinPix Share**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-share). Set the URL with a formula. This makes it dynamic per record.

This article covers:

* [How to configure the IFrame (URL and aspect ratio)](sharinpix-form-sections-and-repeated-sections.md#iframe-element-configuration-in-the-form-template-editor)
* [Fire Inspection Demo: Configure a dynamic IFrame using a prefilled URL](sharinpix-form-sections-and-repeated-sections.md#fire-inspection-demo-configure-a-dynamic-iframe-using-a-prefilled-url)

{% hint style="warning" %}
**Prerequisites:**

Before using the IFrame element:

* Ensure the [**SharinPix Forms Admin**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/sharinpix-permission-sets) permission set is assigned.
* The **latest version of the SharinPix Package** must be installed. Refer to [_this documentation_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to update your package.
* Ensure end users can access the embedded URL (network access and authentication).
{% endhint %}

{% hint style="info" %}
**Use Case Example: Show SharinPix Albums in a form**

The iFrame element can be used to embed a [SharinPix Album component](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-album-lwc) in a form. To generate shareable SharinPix album URLs, you can either:

1. Use the [SharinPix Share component](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-share) to manually generate a URL
2. Or automatically generate URLs as documented [here](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/cookbook/generate-sharinpix-shareable-album-links-automatically).
{% endhint %}

## IFrame element configuration in the Form Template Editor

Configure IFrames in the [SharinPix Form Template Editor](sharinpix-form-template-editor.md).

### Configure IFrame element with a static URL

#### Add the IFrame element

Open your form template in the Form Template Editor. Find **IFrame** in the element palette. Drag it into your form.

#### Configure the IFrame settings

Select the IFrame element. Configure these parameters:

* **URL**: a [formula](sharinpix-form-formula-functions-and-operators.md) that resolves to a URL string
* **Aspect Ratio**: controls the IFrame height relative to its width

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (23) (1).png" alt=""><figcaption></figcaption></figure>

#### Set the URL (example)

Use a quoted string as a static URL:

* URL: `"https://example.com"`
* URL: `"<your-sharinpix-share-url>"`

{% hint style="info" %}
**Dynamic URLs**

You can build the URL dynamically per record. Jump to [Dynamic IFrame element with a dynamic URL](sharinpix-form-sections-and-repeated-sections.md#fire-inspection-demo-configure-a-dynamic-iframe-using-a-prefilled-url).
{% endhint %}

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (24) (1).png" alt=""><figcaption></figcaption></figure>

### Fire Inspection Demo: Configure a dynamic IFrame using a prefilled URL

#### Step 1: Generate URL

Generate a [dynamic Share URL](../salesforce-integration/generate-sharinpix-shareable-form-links-automatically.md) for the record where the form is launched.

#### Step 2: Prefill URL

* Add a **Text** question.
* Set an API name for the question (example: `album_share_url`).
* [Prefill](form-features-default-or-prefill-values.md) it with the field name storing the Share URL (example: `Share_URL__c`).
* Hide or disable the question.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (30).png" alt=""><figcaption></figcaption></figure>

Make sure to set the api name of the text question to use it in a formula.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (29).png" alt=""><figcaption></figcaption></figure>

#### Step 3: Use the dynamic share URL

* Set the IFrame **URL** to your prefilled Text value.
* Use `<PrefilledTextApiName>.value` to reference the field value.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (28).png" alt=""><figcaption></figcaption></figure>

#### Step 4: Test in preview

Preview the form to test the embedded content. Share access follows the Share settings.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (20).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

* If you embed a SharinPix Share link, review its access level. Avoid edit access in read-only use cases.
* The IFrame element does not render in the PDF output.
* The IFrame is not limited to SharinPix Share: you can use any SalesForce public links
{% endhint %}
