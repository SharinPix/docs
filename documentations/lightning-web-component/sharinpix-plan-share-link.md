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

# SharinPix Plan Share Link

{% hint style="info" %}
The **SharinPix Plan Share Link** component permits the user to generate and share a SharinPix Plan URL.
{% endhint %}

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (10).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

The SharinPix Plan Share Link component is dependent on the [SharinPix Plan component](https://docs.sharinpix.com/m/documentation/l/1352879-sharinpix-plan).
{% endhint %}

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
* On Mobile
{% endhint %}

## Getting Started

To use the SharinPix Plan Share Link component, simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (11).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (12).png" alt=""><figcaption></figcaption></figure>

* **Generate Plan Share Link Button Label:** Used to specify the button's label. The default value is **Plan Share Link to target field.**
* **Target Field API Name:** API Name of the field where the URL will be stored.
* **Plan Data Source Record Id:** Id of Record containing the field specified by Plan Data filed API Name from which the plan data is to be retrieved.
* **Plan Data Field API Name:** API name of the field containing plan-related information.
* **SharinPix Plan Setting Name:** SharinPix Plan Setting Name configured for the related plan component.
* **Component Id:** Component ID to be matched by the SharinPix component on the page.

## Demo

The picture below depicts a SharinPix Plan component:

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (13).png" alt=""><figcaption></figcaption></figure>

To store the URL on the target field, click on the button **Plan Share Link to target field**.

The picture below shows the result in the target field after using the SharinPix Plan Share Link component.

{% hint style="warning" %}
**Note:**

Reload the page after clicking on the button **Plan Share Link to target field** to see the URL on the target field.
{% endhint %}

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (14).png" alt=""><figcaption></figcaption></figure>

The picture below shows the SharinPix Plan accessed outside Salesforce using the URL.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (15).png" alt=""><figcaption></figcaption></figure>
