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
  actions:
    visible: true
---

# View a SharinPix album from the SFS (FSL) app

This article demonstrates how to make use of the SharinPix app's online mode to view a SharinPix album from the SFS app.

To do so, you will need to:

* [Generate a SharinPix token to access the SharinPix album](view-a-sharinpix-album-from-the-sfs-fsl-app.md#generation-of-the-sharinpix-token-developer-oriented)
* [Construct the SharinPix deeplink that will launch the SharinPix mobile app to view the album](view-a-sharinpix-album-from-the-sfs-fsl-app.md#construction-of-the-sharinpix-deeplink)
* [Create an App Extension that will make use of the URL](view-a-sharinpix-album-from-the-sfs-fsl-app.md#creation-of-the-app-extension)

{% hint style="warning" %}
**Note:**

* This feature works only when online
* Ensure that the latest version of the SharinPix mobile app has been downloaded on your device before implementing this feature
{% endhint %}

## Generation of the SharinPix token (Developer-Oriented)

The SharinPix token will allow users to view a SharinPix album associated with a Salesforce record in the SharinPix mobile app.

To generate such tokens automatically and store them in Salesforce fields, a Salesforce Trigger can be implemented. For more information on how to implement a trigger that will automatically generate a token on Salesforce records, refer to the following SharinPix article:

[SharinPix automatic token generation (Developer-oriented)](../../access-and-security/sharinpix-automatic-token-generation-developer-oriented.md)

## Construction of the SharinPix deeplink

Once your token has been generated and stored in a Salesforce field, go ahead and construct the SharinPix  deeplink as follows:

<mark style="color:$danger;">`sharinpix://online?token={!`</mark>_<mark style="color:$danger;">**`<FieldApiName>`**</mark>_<mark style="color:$danger;">`}&host=app.sharinpix.com`</mark>

**Note:** The section _<mark style="color:$danger;">**`<FieldApiName>`**</mark>_&#x73;hould be replaced by the field API Name of the field storing the SharinPix token. For example:

**sharinpix://native\_app/online?token={!SharinPix\_Token\_\_c}\&host=app.sharinpix.com**

{% hint style="success" %}
**Tip:**

* The above deeplink uses the SharinPix mobile app's **online mode** feature. This feature provides access to online features such as SharinPix images, albums, and search within the SharinPix mobile app. For more information about the **online mode,** refer to the following article:\
  [SharinPix Mobile App: Online mode](https://docs.sharinpix.com/m/documentation/l/1530458-sharinpix-mobile-app-online-mode)
* The above configuration is also compatible with SharinPix universal links. The SharinPix online mode format for universal links is as follows:\
  https://app.sharinpix.com/native\_app/online?token={!_**\<FieldApiName>**_}\&host=app.sharinpix.com
{% endhint %}

## Creation of the App Extension

Once your SharinPix deeplink is ready, create a new App Extension. To do so, follow the steps below:

* Go to Setup, then type _Field Service Mobile Settings_ in the Quick Find box. Click on **Field Service Mobile Settings**.
* Click on the **Show Details** button next to the **Field Service Mobile Settings** item

<figure><img src="../../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

* Scroll down to the App Extensions Section
* Click on **New** to create a new App Extension
* Next, fill in the App Extension details as follows:
  * For the **Type**, select **Android** if you intend to use the App Extension on Android platforms or select **iOS** if you intend to use it on iOS platforms
  * For the **Launch Value**, enter the SharinPix deeplink constructed in the previous section, that is, **sharinpix://online?token={!SharinPix\_Token\_\_c}\&host=app.sharinpix.com** in our case&#x20;
  * To complete, fill in the other required fields

<figure><img src="../../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>

To test the implementation:

* Log onto the SFS app
* Access the object on which the App Extension has been made available
* From the **Actions** menu, select the newly created App Extension. This action will launch the SharinPix mobile app to display the album
