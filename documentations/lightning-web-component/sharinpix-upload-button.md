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

# SharinPix Upload Button

{% hint style="info" %}
The **SharinPix Upload Button** component is used to upload an image in a specific **SharinPix Album**.
{% endhint %}

![](<../.gitbook/assets/image (16) (4).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* Community Builder
* Page Builder
* Desktop
* Mobile
* In your own Lightning Component development
{% endhint %}

## Getting Started

To use the SharinPix Upload Button component, you simply need to drag and drop the component from the Lightning App Builder onto the page layout.

![](<../.gitbook/assets/image (1) (4) (1).png>)

## Lightning Component Parameters

![](<../.gitbook/assets/image (2) (4).png>)

* **Album Id:** Used to specify the album Id. If you want to use the record Id as the album Id, leave this field blank.
* **Label:** Used to specify the button's label.
* **Component Id:** Used to specify the component Id to be matched by add-on components on a page.
* **Enable Action: Used to enable/disable Tag Action. Note** : The Tag Action is enabled by default on the SharinPix Album component. For more information on this feature and how to complete the Tag Action setup, refer to this article: [_Tag Action_](../features/working-with-tags/tag-action.md)
* **Enable Image Sync:** Used to enable/disable Image Sync. **Note:** Image Sync is checked by default on the SharinPix Upload Button. Additional steps are required to get this feature fully working on your Salesforce object. Please refer to this article to complete the Image Sync setup: [_Setup SharinPix Image Sync_](../image-sync/setup-sharinpix-image-sync.md)
* **Enable Toast:** Used to enable/disable toast message upon successful image upload.
* **Auto Refresh View:** Used to enable/disable the option to reload the view.
* **Custom Permission Id or Name:** Used to specify the Id or Name of a custom permission.
* **Auto Tags:** Enter semi-colon delimited list of tag names to automatically apply on images after upload. Example: TagA;TagB;TagC

## Demo

The picture below shows the SharinPix Upload Button component on a record page:

![](<../.gitbook/assets/image (3) (4).png>)

To add an image to the album specified in the SharinPix Upload Button component's parameters, click on the **Add** button.

The picture below shows the uploaded image inside the specified album after clicking on the **Add** button:

![](<../.gitbook/assets/image (4) (3) (1).png>)

{% hint style="success" %}
**Tip:**

The SharinPix Upload Button component is only available in Lightning.

However, the component can be replicated for usage in Classic and in Visualforce implementations. To do so, refer to the following article:

[Implement a SharinPix upload button in a Visualforce page](../cookbook/implement-a-sharinpix-upload-button-in-a-visualforce-page.md)
{% endhint %}
