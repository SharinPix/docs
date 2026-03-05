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
  actions:
    visible: true
---

# Deeplink to SharinPix does not work in Rich Text field. What should I do?

SharinPix deeplinks do not work in Rich Text fields due to a Salesforce bug. One workaround is to use the SharinPix universal link instead.

The SharinPix universal link format is as follows:

<mark style="color:$danger;">`https://app.sharinpix.com/native_app/upload?token=`</mark>_<mark style="color:blue;">**`<Insert SharinPix Token>`**</mark>_

Where _<mark style="color:blue;">**\<Insert SharinPix Token>**</mark>_ refers to the SharinPix token.

{% hint style="success" %}
**Tips:**&#x20;

* The example below demonstrates how to embed SharinPix universal links in HTML links:\
  **\<a href="https://app.sharinpix.com/native\_app/upload?token=**_<mark style="color:blue;">**\<Insert SharinPix Token>**</mark>_**">Launch SharinPix app\</a>**



* The example below demonstrates how to embed SharinPix universal links in Salesforce formulae:\
  **HYPERLINK('https://app.sharinpix.com/native\_app/upload?token=**_<mark style="color:blue;">**\<Insert SharinPix Token>**</mark>_**', 'Launch SharinPix app')**
{% endhint %}

{% hint style="warning" %}
**Note:** SharnPix universal links do not work in offline mode.
{% endhint %}
