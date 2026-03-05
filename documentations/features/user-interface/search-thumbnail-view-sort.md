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

# Search Thumbnail View - Sort

This article demonstrates how to sort images in a Search component using custom sorting based on the

* image's **date\_taken**.
* Image's **date\_uploaded**.

{% hint style="warning" %}
**Warning:**

If the album contains more than 200 images, sorting cannot be performed.
{% endhint %}

## Enabling sorting images using a SharinPix Permission

To sort images on Search Components, follow the steps below:

1. Create a new [SharinPix Permission](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md) or edit an existing one (if applicable).
2. On the SharinPix Permission record, in the sort section, choose the sort field and Sort order.

![](<../../.gitbook/assets/image (32) (2).png>)

3. Click on the **Save** button when done.

{% hint style="success" %}
**Tip:**

* The default Sorting field is '_Date\_Uploaded_,' and Sorting Order is '_Descending_ '.
* For more information on how to assign the SharinPix Permission to the Search component, refer to this article: [SharinPix Permission object](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md)
{% endhint %}

