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

# Known limitation on iOS – Download a PDF

There exists a known limitation when opening a PDF URL within the **IOS Salesforce Mobile Application**.

{% hint style="warning" %}
**Note:**&#x20;

The current limitation has been observed at the publication time of this article; subsequent IOS and Salesforce Mobile Application versions may present a dissimilar behavior from that presented here.
{% endhint %}

For example, the screenshot below illustrates a Visualforce Page that is displaying:

* A **SharinPix Album**
* A hyperlink containing a URL (towards a PDF file) in the form `http://www.pdf995.com/samples/pdf.pdf`. Upon clicking on the hyperlink, you will be directed to a view as shown below.

<figure><img src="../../.gitbook/assets/image (13) (1).png" alt=""><figcaption></figcaption></figure>

## Limitation

**LIMITATION**: The above view does not offer an option to save the current PDF file into a storage medium.
