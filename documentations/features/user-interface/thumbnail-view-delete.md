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

# Thumbnail View – Delete

This article demomstrates how to:

* [Delete an image](thumbnail-view-delete.md#image-deletion)
* [Delete multiple images](thumbnail-view-delete.md#multiple-image-deletion)
* [Add a delete confirmation alert](thumbnail-view-delete.md#delete-confirmation-setup)

## Image Deletion

To delete an image, use the red trash icon located on the top right corner of the image thumbnail as indicated below:

![](<../../.gitbook/assets/image (42).png>)

{% hint style="warning" %}
**Note:**

If the trash icon is not visible on the thumbnail, this means that the SharinPix delete image ability has not been enabled for the album. To enable the delete image ability:

* Either enable it in a SharinPix Permission record and add the permission to the required album
* Or enable it at an organisation level using the SharinPix Global Settings
{% endhint %}

![](<../../.gitbook/assets/image (43).png>)

{% hint style="success" %}
**Tips:**

* For more information about the SharinPix Permission object, refer to the following article:
  * [SharinPix Permission object](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md)
* For more information about how to access the SharinPix Global Settings, refer to the following article:
  * [Extended Setup - Customizing your SharinPix Global Settings](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/advanced-configuration-customizing-your-sharinpix-components-with-sharinpix-permissions)
{% endhint %}

## Multiple Image Deletion

To delete multiple images at once, follow the steps below:

* Select the desired images by clicking on the check icon on the top left of the thumbnail as shown below:

![](<../../.gitbook/assets/image (44).png>)

* Next, open the thumbnail view menu by clicking on the dropdown. Then click on **Delete**

![](<../../.gitbook/assets/image (45).png>)

## Delete Confirmation Setup

You can also add a delete confirmation alert that will popup whenever you delete one or more images.

![](<../../.gitbook/assets/image (46).png>)

The delete confimation alert can be added to a SharinPix album using the following methods:

* By enabling the **Confirm delete** feature in a SharinPix Permission record, then assign the permission to the desired album. More information about the SharinPix Permission object [here](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md).

![](<../../.gitbook/assets/image (47).png>)

* By enabling the **Delete confimation popup** ability at an organisation level using the SharinPix Global Settings. This configuration will enable the delete confirmation alert for all SharinPix albums on your by default. More information about the SharinPix Global Settings [here](../../getting-started-with-sharinpix/advanced-setup/advanced-configuration-customizing-your-sharinpix-components-with-sharinpix-permissions.md).

![](<../../.gitbook/assets/image (48).png>)

{% hint style="warning" %}
**Note:**

The delete confirmation alert is not enabled by default for image deletion when using the **red trash icon** on the thumbnail. However, it is enabled by default for deletion perfomed using the delete option from the **thumbnail dropdown menu**.
{% endhint %}

{% hint style="success" %}
**Tip:**

Deleted images can be restored from the **Trash bin** within 30 days after deletion.

For more information about the Trash bin ability and how it is used, please refer to the following article:

[Thumbnail view – Trash bin](thumbnail-view-trash-bin.md)
{% endhint %}
