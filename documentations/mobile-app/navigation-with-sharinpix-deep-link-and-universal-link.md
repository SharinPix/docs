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

# Navigation with SharinPix Deep Link and Universal Link

[Deep links](sharinpix-mobile-app-deeplink-syntax.md) are URLs with a custom scheme following the format: sharinpix://upload?token=.... Universal links are URLs with the standard HTTP scheme and follow the format: https://app.sharinpix.com/native\_app/upload?token=....

Both can be used to launch the SharinPix mobile app from other apps such as the Salesforce mobile app, the Salesforce Field Service app or any custom app or website.

## Deep Link and Universal Link Standard Behaviour

Open a deep link or universal link within your application. This action should prompt the SharinPix mobile app to launch, as illustrated in the diagram provided below:

<figure><img src="../.gitbook/assets/Navigation with SharinPix Deep Link and Universal Link - 1.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

Usually when using the links, the SharinPix mobile app is launched instantly as explained above. **You should not need to follow the below steps.** However, if you do encounter difficulties, kindly ensure that the SharinPix app on your device is up to date. Issues may arise from using an outdated version of the SharinPix app or accessing the link from a browser's address bar. In such cases, please follow the steps below to open SharinPix.
{% endhint %}

## Deep Link and Universal Link Quirks

### Deep Link Quirks

If you encounter the popup displayed in the diagram below when using a deep link, select "Open" to launch the SharinPix mobile app.

In case you choose "Cancel", you can click the deep link again to open the prompt and then proceed to select "Open".

<figure><img src="../.gitbook/assets/Navigation with SharinPix Deep Link and Universal Link - 2.png" alt=""><figcaption></figcaption></figure>

### Universal Link Quirks

If you come across one of the popups depicted in the diagrams below when using a universal link, choose "Open" or "Allow" to initiate the SharinPix mobile app.

If you opt for "Cancel" or "Don't allow", you can click the universal link to open the prompt again and then proceed to select "Open" or "Allow".

<figure><img src="../.gitbook/assets/Navigation with SharinPix Deep Link and Universal Link - 3 (1).png" alt=""><figcaption></figcaption></figure>

If you haven't received any popups or selected "Cancel" or "Don't allow", you can utilize one of the two buttons in the image below to launch the SharinPix mobile app. We recommend the OPEN button at the top.

<figure><img src="../.gitbook/assets/Navigation with SharinPix Deep Link and Universal Link - 4.png" alt=""><figcaption></figcaption></figure>

If you come across the popup shown in the diagram below when opening the universal link, it suggests that Sharinpix is not yet installed on your device.

<figure><img src="../.gitbook/assets/Navigation with SharinPix Deep Link and Universal Link - 5.png" alt=""><figcaption></figcaption></figure>

To install SharinPix on your device, choose one of the links either App Store for iOS or Google PlayStore for Android as indicated in the diagram below.

<figure><img src="../.gitbook/assets/Navigation with SharinPix Deep Link and Universal Link - 6 (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tips:**

For more information about where to find the SharinPix mobile app, refer to [this](where-to-find-the-sharinpix-mobile-app.md) article.
{% endhint %}
