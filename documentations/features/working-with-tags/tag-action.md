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

# Tag Action

The Tag Action is a SharinPix feature used to update fields whenever a specific tag is applied to an image. It can be used both on **standard** and **custom** objects and is available both in **Salesforce Classic** and **Lightning**.

This article demonstrates how:

* [To enable the Tag action in Salesforce Classic Experience](tag-action.md#enabling-tag-action-in-salesforce-classic-experience)
* [To enable the Tag action in Salesforce Lightning Experience](tag-action.md#enabling-tag-action-in-salesforce-lightning-experience)
* [To configure a Tag action](tag-action.md#configuring-tag-action)
* [The Tag action works in action](tag-action.md#the-tag-action-in-action)
* [To enable Tag actions for SharinPix Mobile App uploads](tag-action.md#enable-tag-actions-for-sharinpix-mobile-app-uploads)

{% hint style="warning" %}
**Note**:

Configuring the Tag Action requires access to the Administration Dashboard. For more information about how to access and use the Administration Dashboard, refer to the following article: [Overview of the SharinPix Administration Dashboard](../../getting-started-with-sharinpix/overview-of-the-sharinpix-administration-dashboard.md)
{% endhint %}

## Enabling Tag action in Salesforce Classic Experience

To activate **Tag Action** in the Salesforce Classic Experience, simply add the code snippet below within a Visualforce Page.

It is to be noted that the **recordId** attribute takes as value the Album Id (or the record Id) of the corresponding SharinPix Album.

```html
<sharinpix:TagAction recordId="{!$CurrentPage.Parameters.Id}" />
```

## Enabling Tag action in Salesforce Lightning Experience

To activate the Tag Action on the Salesforce Lightning Experience, proceed as follows:

* Drag and drop the [SharinPix Album](../../lightning-web-component/sharinpix-album.md) component from the Lightning App Builder onto your page layout.
* Ensure that the **Enable Action** checkbox is set to true in the component's lightning parameters.
* Save the page when you are done.&#x20;

![](<../../.gitbook/assets/Copy of Template (9).png>)

## Configuring Tag Action

To configure the Tag Action on a tag, proceed as follows:

* Open the [SharinPix Admin Dashboard](../../getting-started-with-sharinpix/overview-of-the-sharinpix-administration-dashboard.md).
* From the top menu, select **Tags**.
* Create or edit the tag on which you want to activate the Tag Action.
* Enter the tag details if needed, then click on the **New Tag Action** button in the Tag Actions section located at the bottom of the page.

![](<../../.gitbook/assets/Copy of Template (12).png>)

* Configure the new **Tag** **Action** as indicated below.
  1. **Field name:** Insert the Salesforce API name of the field you want to update
  2. **Value:** Select between a predefined value or a custom one
  3. Click on **Update Tag** to save the action.
  4. Optional: Click on the button **New Tag Action** to create more **Tag Actions** for the current tag.

![](<../../.gitbook/assets/Copy of Template (13).png>)

{% hint style="warning" %}
**Note:**

For the Tag Action to work properly, you should ensure that the users have access to the field applied to the Tag Action's configuration.
{% endhint %}

Below is the detailed list of Tag Action values. The field specified in the \_Field Name \_parameter will be populated with the selected Tag Action value.

| Name          | Description                                                                                                                                                             |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Width         | The original width of the image.                                                                                                                                        |
| Height        | The original height of the image.                                                                                                                                       |
| Full url      | The URL of the image with a maximum width and height of 1920px.                                                                                                         |
| Large url     | The URL of the image with a maximum width and height of 200px.                                                                                                          |
| Mini url      | The URL of the image with a maximum width and height of 100px.                                                                                                          |
| Original  url | The URL of the original image                                                                                                                                           |
| Id            | The SharinPix ID of the image as stored in the database of SharinPix.                                                                                                   |
| Geolocation   | Geolocation value found in the image metadata.                                                                                                                          |
| Fit to size   | <p>A URL to the image fitted to the specified size.<br>Click <a href="tag-action.md#transformation">here</a> for more details about <strong>Fit to size</strong>.</p>   |
| Fill to size  | <p>A URL to the image filled to the specified size.<br>Click <a href="tag-action.md#transformation">here</a> for more details about <strong>Fill to size</strong>.</p>  |
| Scale to size | <p>A URL to the image filled to the specified size.<br>Click <a href="tag-action.md#transformation">here</a> for more details about <strong>Scale to size</strong>.</p> |
| Pad to size   | <p>A URL to the image padded to the specified size.<br>Click <a href="tag-action.md#transformation">here</a> for more details about <strong>Pad to size</strong>.</p>   |
| Custom value  | Add a custom value to the field (can be a text, true or false, a numeric)                                                                                               |
| Watermark     | <p>Adds a watermark on the image.<br>Click <a href="tag-action.md#watermark">here</a> for more details about how to add a Watermark.</p>                                |
| Limit to size | <p>Sets a size limit.<br>Click <a href="tag-action.md#transformation">here</a> for more details about <strong>Limit to size</strong>.</p>                               |

### Transformation

The difference between **Fit**, **Fill**, **Scale,** and **Pad** is as follows:

* **Fit to sIze**: The image is resized so that it takes up as much space as possible within a bounding box defined by the given width and height parameters. The original aspect ratio is retained and all of the original image is visible.
* **Fill to size**: An image is created with the exact given width and height while retaining the original aspect ratio, using only part of the image that fills the given dimensions if necessary (only part of the original image might be visible if the requested aspect ratio is different from the original aspect ratio).
* **Scale to size**: Changes the size of the image exactly to the given width and height without necessarily retaining the original aspect ratio: all original image parts are visible but might be stretched or shrunk.
* **Pad to size**: Resizes the image to fill the given width and height while retaining the original aspect ratio and with all of the original image visible. If the proportions of the original image do not match the given width and height, padding is added to the image to reach the required size.
* **Limit to size**: Sets a size limit. If an image's dimensions exceed the limit value entered, the image is scaled down to that specified value.

The image below shows an example of how to configure a Tag Action with a **Fit to size** of value 500x500 px.

![](<../../.gitbook/assets/Copy of Template (14).png>)

{% hint style="warning" %}
**Note:**&#x20;

* When applying a transformation, the original image is not affected.&#x20;
* The size can be specified by using **\<width>x\<height>** or **\<width and height>**.&#x20;

Examples are:

* **500x500** for a width and height of 500px. This can also be only written as "500".
* **600x400** for a width of 600px and height of 400px.
* **750** for a width and height of both 750px.
{% endhint %}

{% hint style="success" %}
**Tip:**

For more information about fit, fill, scale, and pad, refer to the following article:

[SharinPix Transformations Examples](../../image-sync/sharinpix-transformations-examples.md)
{% endhint %}

### Watermark

When choosing the option **Watermark**, the following is displayed in the **Tag Actions** section:

![](<../../.gitbook/assets/Copy of Template (15).png>)

You can now set:

1. The Image ID of the watermark image to be used in the **Image** field.
2. The width of the watermark in the **Width** field.
3. The height of the watermark in the **Height** field.
4. Choose the watermark format in the field labeled **Format**. It can either be in pixels or in percentage.
5. The opacity in the field labeled as **Opacity**.

![](<../../.gitbook/assets/Copy of Template (16).png>)

{% hint style="success" %}
**Tip:**

For more information about **Watermark** , refer to the following article:

[SharinPix Transformation watermark entry](../../image-sync/sharinpix-transformation-get-your-images-watermarked.md#specify-the-image-to-use-as-watermark-image-id-parameter)
{% endhint %}

## The Tag action in action

Assuming a Tag Action is properly configured, each time the tag is applied to an image, the tag action is executed and the selected value is inserted into the specified field.

## Enable Tag actions for SharinPix Mobile App uploads

<mark style="color:$primary;">By default, the SharinPix Tag Action is not triggered when uploading tagged images using the SharinPix mobile app to prevent unintended Salesforce API usage.</mark>

To enable this setting, perform the following steps:

1. Open the administration dashboard
2. Click on the settings tab

![](<../../.gitbook/assets/Untitled design (3) (1).png>)

3. Next, click on the **Edit Organization** button.

![](<../../.gitbook/assets/Untitled design (4).png>)

4. On the settings edit page, tick the checkbox labelled **“Run tag actions for uploads from the Sharinpix Mobile App".**

![](<../../.gitbook/assets/Untitled design (5).png>)

5. Click on the **Update Organization** button located at the bottom of the page to save the changes.

![](<../../.gitbook/assets/Untitled design (6) (1).png>)

{% hint style="warning" %}
Note:

Enabling this setting will increase your Salesforce API Usage.
{% endhint %}

Once the above setting has been enabled and assuming you configured a Tag action on a particular tag, images that are tagged with the later in the SharinPix Mobile App will run the associated Tag action when they are uploaded.
