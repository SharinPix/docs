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

# Personalized image download - footer integration

The present article will show how it is possible to create a custom download hyperlink that can be added at the footer of a SharinPix Album.

{% hint style="info" %}
**Info:**&#x20;

The **Visualforce Page** and **Apex Class** used in the present article can be found on GitHub by following this link: [https://github.com/SharinPix/demo-apex/tree/custom-footer-download](https://github.com/SharinPix/demo-apex/tree/custom-footer-download)
{% endhint %}

* In the present context, the Visualforce Page is launched from a **custom Lightning action** found on the record page of the Contact Object. The screenshot below shows the custom action being executed.

![](../../.gitbook/assets/custom_footer_action.png)

* Upon clicking on an image's thumbnail, the **Download Image** hyperlink appears.

![](../../.gitbook/assets/image_viewed.png)

* When clicking on the **Download Image** hyperlink, the image that is currently being viewed is downloaded.
