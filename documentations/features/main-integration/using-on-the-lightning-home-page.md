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

# Using on the Lightning Home Page

In this section, we will learn about the different steps for adding the **SharinPix Album** Component onto the Home page, as shown in the screenshot below.

![](<../../.gitbook/assets/image (65) (1).png>)

**Information:**

The **SharinPix Album** component was previously named **SharinPix**.

* [Difference between the Record page and the Home Page](using-on-the-lightning-home-page.md#difference-between-the-record-page-and-the-home-page)
* [Choosing an album Id](using-on-the-lightning-home-page.md#choosing-an-album-id)
* [Finding the Album Id](using-on-the-lightning-home-page.md#finding-the-album-id)
* [Drag and drop the SharinPix Album onto the Home Page](using-on-the-lightning-home-page.md#drag-and-drop-the-sharinpix-album-onto-the-home-page)
* [Configure the SharinPix Album's parameters](using-on-the-lightning-home-page.md#configure-sharinpix-albums-parameters)

## Difference between the Record Page and the Home Page

{% hint style="success" %}
In the chapter [Using SharinPix on Lightning From a Record Page](using-on-a-lightning-record-page.md), we've seen that it is possible to add the SharinPix Album component to a record page without specifying the album Id. This is because the component's default album id corresponds to the id of the current record.

However when adding the SharinPix Album component to the **Home Page** , it is mandatory to specify an album id, as the **Home Page** does not possess a default record Id.

Each album needs to be associated with a Record Page.
{% endhint %}

## Choosing an album Id

In order to determine which album Id to use, you need to choose which images you want to display on the **Home Page**. If these images are already present on a record page, you can use its corresponding record id as the album Id. (see the next section, _Finding the Album Id_, to learn how to retrieve a record page's record id).

However, if you don't have a ready-made record page that uses the SharinPix Album component in a ready-made object, you'll need to create a custom object to house the records and images for your home page.

Here's how this can be done:

* Create a new custom object, named for example, Photo Files.
* Create at least one record for your object. (Say, Home Page Photos.)
* Add a SharinPix Album component to the new record ([Using SharinPix on Lightning From a Record Page](using-on-a-lightning-record-page.md) for more info.)
* Upload your home page images into the SharinPix Album component.

Next, we'll get the Album Id to use on our Home Page's SharinPix Album.

## Finding the Album Id

Here's how to find the **record Id (album Id)** of a record of your choice:

* Navigate to the desired record containing the images you wish to display on the **Home Page.**
* Copy the highlighted value as shown below from the address bar of the browser. ( 18 numbers after the "object name/")
* Paste the copied value inside the **album id** field (see [Configure SharinPix Parameters](using-on-the-lightning-home-page.md#configure-sharinpix-albums-parameters)).

![](<../../.gitbook/assets/image (66) (1).png>)

## Drag and drop the SharinPix Album onto the Home Page

To add SharinPix Album component on the Home Page:

1. Click on the **Setup Icon**.
2. Select **Edit Page**.
3. From the **Lightning Components** list under the **Custom - Managed** section, select the **SharinPix Album** component.
4. Drag and drop the component into the page.

![](<../../.gitbook/assets/image (67) (1).png>)

## Configure SharinPix Album's parameters

After dropping the **SharinPix Album** component on the desired region, you will be able to configure its parameters from the right side panel.

The parameters are:

* **Album Id** - Specify an album id from which to display the images. **IMPORTANT:** The value for the album is **required** in the **Home Page** layout context. (see [Extracting the album Id](using-on-the-lightning-home-page.md#finding-the-album-id))
* **Height** - Specify the height of the SharinPix component. The Minimum size allowed is 300.
* **Use Fullscreen Image Viewer** - Enable/disable option to view image in full screen.
* **Fullscreen Viewer Padding** - To add padding.
* **Enable Action** - Enable/disable Tag Action.
* **Enable Image Sync** - Enable/disable Image Sync.
* **Enable Toast** - Enable/disable toast on successful image upload.
* **Auto Refresh View** - Enable/disable option to reload view.
* **Custom Permission Id or Name** - Specify the id for a custom permission.
* **Component ID** - Used to specify the component Id's to be matched by add-on components on a page.

![](<../../.gitbook/assets/image (68) (1).png>)

5\. Click on **Save** when done.
