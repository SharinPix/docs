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

# Share Link

This article demonstrates how to use the **Share** feature to share pre-selected images outside of Salesforce using a public URL.

{% hint style="warning" %}
**Note:**

The richer [SharinPix Share](../../lightning-web-component/sharinpix-share.md) feature is recommended, as the Share Link is limited and may no longer be maintained.
{% endhint %}

{% hint style="info" %}
On the SharinPix dashboard's Organization page, there's a configuration that should only be modified as necessary.

**Enable public access to shared images**: Tick the checkbox before using the Share Link feature. This ensures proper image rendering on shared links for external users without Salesforce or SharinPix authentication. It does not apply to the SharinPix Share Lightning Web Component.
{% endhint %}

![](<../../.gitbook/assets/Screenshot from 2024-03-29 14-55-05.png>)

Follow the steps below to generate a public URL for the images using the Share feature.

* On the SharinPix Album, select the desired images.
* Click on the thumbnail menu.

![](../../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2023.02.10-15_07_39.png)

* Click on **Share**.

![](../../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2023.02.10-15_05_36.png)

* On the modal, click **Copy Link** to copy the generated public URL containing the selected images.

![](../../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2023.02.10-15_14_58.png)

* Check the **Allow download** option to allow users to download images when accessing the public URL.

![](<../../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2023.02.10-15_14_58 (1).png>)

{% hint style="warning" %}
**Note:**

If you see the following error on the modal: **Contact your Salesforce administrator to enable the share feature on your organization**. Kindly tick **Enable public access to shared images** on the [SharinPix dashboard's Organization page](../../getting-started-with-sharinpix/overview-of-the-sharinpix-administration-dashboard.md).
{% endhint %}

![](<../../.gitbook/assets/Screenshot from 2024-03-29 15-45-06.png>)
