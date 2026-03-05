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

# Using Collage on Search Component

The Collage ability enables combining **two** images from a SharinPix Search component into a new image, uploaded to the SharinPix Album. The album to which the new collage will be uploaded will be the album for the record page on which the Search component is being used.

To be able to use this feature, we will need to:

* [Create a SharinPix Permission to enable the Collage ability.](using-collage-on-search-component.md#create-permission-to-enable-collage-ability)
* [Add the SharinPix Permission to the Search Component.](using-collage-on-search-component.md#add-permission-to-search-component)

## Create Permission to enable Collage ability

Go to SharinPix Permission from the App Launcher, create new permission, select **Search** , and enable the collage ability as shown below:

<figure><img src="../../.gitbook/assets/Gradio Image (5).png" alt=""><figcaption></figcaption></figure>

## Add Permission to Search Component

Add the SharinPix Permission Name or Id you created in the component search parameters as shown below:

<figure><img src="../../.gitbook/assets/Gradio Image (6).png" alt=""><figcaption></figcaption></figure>

## Demo

The picture below depicts a SharinPix Search component.

<figure><img src="../../.gitbook/assets/Gradio Image (7).png" alt=""><figcaption></figcaption></figure>

Start by selecting two images. The Collage feature should be enabled after the selection as depicted below:

<figure><img src="../../.gitbook/assets/Gradio Image (8).png" alt=""><figcaption></figcaption></figure>

Click on the button 'Create collage' to start the collage:

<figure><img src="../../.gitbook/assets/Gradio Image (9).png" alt=""><figcaption></figcaption></figure>

Click on the save button to save the collage on the SharinPix Album. At this point, users can adjust, zoom in or out the images in the collage:

<figure><img src="../../.gitbook/assets/Gradio Image (11).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/Gradio Image (12).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

This feature also saves the collage in a SharinPix Album component. Therefore, to synchronize your images, you must enable image sync on [SharinPix Search component.](../../lightning-web-component/sharinpix-search.md#lightning-component-parameters)
{% endhint %}
