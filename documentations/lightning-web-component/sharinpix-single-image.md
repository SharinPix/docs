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

# SharinPix Single Image

{% hint style="info" %}
The **SharinPix Single Image** component is used to display an image having a specific tag.

Using this component, users can also upload a photo on a record in only a few clicks. In this case, the uploaded image will be automatically tagged with the tag name specified by the SharinPix Single Image component.
{% endhint %}

![](<../.gitbook/assets/image (5) (3) (1).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Community Builder
* On Page Builder
* On Desktop
* On Mobile
* In Flows (but not in Field Service Mobile Flow)
* In your own Lightning Component development
{% endhint %}

## Getting Started

To use the SharinPix Single Image component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

![](<../.gitbook/assets/image (6) (4) (1).png>)

## Lightning Component Parameters

![](<../.gitbook/assets/image (7) (3) (1).png>)

* **Height:** Used to specify the component's height. The default value is **300** (px).
* **Tag name:** Used to specify the tag name of the image to be displayed. The default value is **main**.
* **Album Id:** Used to specify the album Id. If you want to use the record Id as the album Id, leave this field blank.
* **Placeholder URL:** Used to set the URL of the image to be used as the default placeholder.
* **Custom Permission ID or Name:** Used to specify the ID or name of the SharinPix Permission object to be applied on the component.
* **Enable Image Sync:** Used to enable/disable Image Sync. _Note: Image Sync is checked by default on the SharinPix Single Image component. Additional steps are required to get this feature fully working on your Salesforce object. Please refer to this article to complete the Image Sync setup:_ [_Setup SharinPix Image Sync_](../image-sync/setup-sharinpix-image-sync.md)
* **Enable Action:** Used to enable/disable Tag Action. _Note: The Tag Action is enabled by default on the SharinPix Album component. For more information on this feature and how to complete the Tag Action setup, refer to this article:_ [_Tag Action_](../features/working-with-tags/tag-action.md).
* **Enable Crop:** Used to enable/disable the cropping option on the uploaded image. Use a [SharinPix Permission](../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md) to activate the crop after upload. The SharinPix Permission in the **Custom Permission ID or Name** will override the value of the Enable Crop parameter.
* **Auto Refresh View:** Used to enable/disable the option to reload the view.
* **Component Id:** Used to specify an ID to identify the component when multiple components are being used.

{% hint style="warning" %}
**Note:**

For the tag to be properly applied to the image or for the image to be displayed on the Single Image component, you should make sure that the tag is marked as **LISTED** in the tag section of [SharinPix Global Settings](../getting-started-with-sharinpix/overview-of-the-sharinpix-administration-dashboard.md) as depicted below.

For more information on how to mark the tag as listed on the global settings, click [here](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/image-uploaded-to-single-image-component-is-not-displayed-what-should-i-do).
{% endhint %}

![](<../.gitbook/assets/image (8) (3) (1).png>)

{% hint style="success" %}
**Tips:**

To view and/or use all abilities available on the Single Image component, use the SharinPix Permission object. To do so, go to the SharinPix Permission object and switch to the Single Image tab. The available abilities are:

* See album
* Upload images (Setting this ability to false will make the component read-only.)
* Crop images
* Delete images
* Tag name
* Placeholder URL
{% endhint %}

## Demo: Crop After Upload

The example below shows how the SharinPix Single Image component (highlighted in red) can be used on a Contact record page to add a profile picture:

![](<../.gitbook/assets/SingleImagebuilderrecord (1) (1) (1).png>)

To enable the **Crop After Upload** ability, we need to create a SharinPix Permission object and set the **crop image after upload** to true as shown below:

![](<../.gitbook/assets/SingleImageBuilderPermission (1) (1) (1).png>)

Add the name or ID of the SharinPix Permission object we just created to the Single Image component:

![](<../.gitbook/assets/image (9) (3) (1).png>)

To upload a photo, simply click on the component and select the desired photo.

The example below depicts the uploaded photo when the **Crop After Upload** option is enabled in the component's parameters:

![](<../.gitbook/assets/image (10) (3) (1).png>)

Below is the uploaded photo after cropping has been applied and the result on a record

![](<../.gitbook/assets/SingleImagebuildercrop1 (1) (1) (1).png>)

## Demo: Delete Single Image

To enable the delete ability, we need to create a SharinPix Permission object and set **Delete images** to true as shown below:

![](<../.gitbook/assets/SingleImageBuilderDelete (1) (1) (1).png>)

Add the name or ID of the SharinPix Permission object we just created to the Single Image component:

![](<../.gitbook/assets/image (11) (2) (1).png>)

We can now delete images displayed in the Single Image component.

![](<../.gitbook/assets/image (12) (2) (1).png>)

## Demo: Add Image Caption

To enable the caption ability, we need to create a SharinPix Permission object and set **Image Caption** to true as shown below:

![](<../.gitbook/assets/SingleImageBuilderCaptionPermission (1) (1) (1).png>)

Add the name or ID of the SharinPix Permission object we just created to the Single Image component as depicted earlier.

We can now add caption for a Single Image component as depicted below.

![](<../.gitbook/assets/image (13) (2) (1).png>)

## Demo: Add Annotation on Image

To enable the caption ability, we need to create a SharinPix Permission object and set **Annotation Images** to true as shown below:

![](<../.gitbook/assets/SingleImageBuilderAnnotationPermission (1) (1) (1).png>)

If Annotate Images is set to true, you will be able to annotate your image in the SharinPix Single Image Component.

![](<../.gitbook/assets/image (14) (2) (1).png>)

![](<../.gitbook/assets/image (15) (2) (1).png>)

{% hint style="success" %}
**Tip:**

For more information on how to enable and add image captions, click [here](../getting-started-with-sharinpix/single-image-caption.md).
{% endhint %}
