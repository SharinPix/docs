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

# How to bypass the 'Validation of Cookie Usage' error when using a SharinPix component in an Iframe?

## Description of the error

Traditionally, the Iframe syntax used to embed a SharinPix component was as follows:

```html
<apex:page standardController="Account" extensions="GetToken">    
    <iframe id="iframeId" class="sharinpix-iframe" src="https://app.sharinpix.com/?token={! SharinPixToken }"></iframe>    
</apex:page>
```

However, some devices encountered a cookie-based error as depicted in the image below:

![](<.gitbook/assets/image (1).png>)

## Solution: Use of the postMessage method

To overcome this issue, SharinPix adopted the use of the **postMesssage** method. For more detailed information about how to use the postMessage method to bypass the error, click on the link that follows:

[Using a SharinPix component in an Iframe (Developer-oriented)](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/main-integration/using-a-sharinpix-component-in-an-iframe-developer-oriented)
