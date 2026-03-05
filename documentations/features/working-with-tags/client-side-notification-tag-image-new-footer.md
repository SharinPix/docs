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

# Client Side notification – tag-image-new (Footer)

In the present article, an example case study will be shown on the use of the **tag-image-new** event. This example will demonstrate how a footer is displayed whenever a new tag is added to an image.

{% hint style="success" %}
* The current example only serves as a showcase of what can be done by capturing the event emitted whenever a new tag is added to a specific image.
{% endhint %}

The SharinPix Album below contains photos of model parts that contain a product information tag.

![](<../../.gitbook/assets/image (19) (4).png>)

* Upon clicking on an image's thumbnail, the large view mode is activated.

![](<../../.gitbook/assets/image (20) (4).png>)

Whenever a tag **reference** is applied to the image, model, id and serial number fields are displayed to allow the user to enter the corresponding model, ID and serial number represented on the product tag found in the image. The screenshot below illustrates this feature.

![](<../../.gitbook/assets/image (21) (3).png>)

{% hint style="info" %}
The event **tag-image-new** is one of many SharinPix events. To learn more about these SharinPix Events, refer to the following chapter: [SharinPix integration - events](../../integrations/events/) .
{% endhint %}
