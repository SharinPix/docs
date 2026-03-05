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

# SharinPix Album (LWC)

The **SharinPix Album (LWC)** component permits the user to manage images. Using this component one can upload, delete, display, download, edit or even tag an image.

There are many more features provided by SharinPix Album (LWC). You will find links to some useful articles detailing these features at the end of this article.

{% hint style="warning" %}
This component is the Lightning Web Component version of the SharinPix Album.

Refer to [this](sharinpix-album.md) article for the aura version.
{% endhint %}

{% hint style="info" %}
**Information:**<br>

This feature is only available on Lightning. It can be used:

* On Community Builder
* On Page Builder
* On Desktop
* On Mobile
* In Flows (but not in Field Service Mobile Flow)
* In your own Lightning Component development
{% endhint %}

## Getting Started

To use the SharinPix Album (LWC) component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/image (6) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Lightning Web Component Parameters

<figure><img src="../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>

* **AlbumId:** Used to specify the album Id. If you want to use the record Id as the album Id, leave this field blank.
* **Height:** Used to specify the album's height. The default album height is **500** (px).
* **Use Fullscreen Image Viewer:** Used to enable/disable the option to view image in full screen.
* **Enable Action:** Used to enable/disable Tag Actio&#x6E;**. Note**: The Tag Action is enabled by default on the SharinPix Album (LWC). For more information on this feature and how to complete the Tag Action setup, refer to this article: [_Tag Action_](../features/working-with-tags/tag-action.md)
* **Enable Image Sync:** Used to enable/disable Image Sync. **Note:** Image Sync is checked by default on the SharinPix Album (LWC). Additional steps are required to get this feature fully working on your Salesforce object. Please refer to this article to complete the Image Sync setup: [_Setup SharinPix Image Sync_](../image-sync/setup-sharinpix-image-sync.md)
* **Enable Toast:** Used to enable/disable toast message upon successful image upload.
* **Custom Permission Id or Name:** Used to specify the Id or Name of a custom permission.
* **Available Tags:** Used to specify a list of tag names delimited by a semi-colon. Example: TagA;TagB;TagC;
* **Auto Tags:** Used to specify a list of tags delimited by a semi-colon to apply to every image uploaded. Example: TagA;TagB;TagC;
* **Component ID:** Used to specify the component Id's to be matched by add-on components on a page.

{% hint style="warning" %}
**Note**\
\
Due to a Salesforce platform limitation, previously configured default parameter values may not be applied correctly, especially when used in **Salesforce Flow**. To ensure your configuration is properly recognized, remove the existing default values and reconfigure them with your desired settings.
{% endhint %}

## Demo

The picture below depicts a SharinPix Album (LWC) component with uploaded images:

![](<../.gitbook/assets/AlbumLWCRec (1) (1) (1).png>)

The picture below shows the fullscreen view upon clicking on an image in the SharinPix album (LWC) :

![](<../.gitbook/assets/AlbumLWCRecFull (1) (1) (1).png>)

{% hint style="success" %}
**Tips:**\
\
Below are some useful links about the SharinPix Album component's feature that you may refer to:

* [Use the SharinPix Album component on a Record Page.](../features/main-integration/using-on-a-lightning-record-page.md)
* [Use SharinPix Album component on the Lightning Home Page.](../features/main-integration/using-on-the-lightning-home-page.md)
* [Use SharinPix Album component in Salesforce Community.](../features/main-integration/using-sharinpix-in-salesforce-community.md)
* [The SharinPix Album's menu commands.](../features/menu-commands/)
* [The SharinPix Album's user interface.](../features/user-interface/)

_**Note:**_ Those articles are demos with the Aura version of the SharinPix Album, but the functionalities are also the same on the Lightning web component version.
{% endhint %}
