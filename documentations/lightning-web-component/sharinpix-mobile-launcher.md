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

# SharinPix Mobile Launcher

{% hint style="info" %}
The **SharinPix Mobile Launcher component** permits to launch the SharinPix mobile app from the Salesforce mobile app.
{% endhint %}

![](<../.gitbook/assets/image (8) (3).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Community Builder
* On Page Builder
* On Desktop
* On Mobile
* In your own Lightning Component development
* In Flows (but not in Field Service Mobile Flow)

**Note:** The SharinPix Mobile Launcher component is not available in Salesforce Field Service (FSL). However, you can still launch the SharinPix mobile app from a Field Service Mobile Flow. To do so, refer to the following article:

[Integration of SharinPix App with SFS (FSL) App using Flows](../integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-flows.md)
{% endhint %}

{% hint style="warning" %}
**Prerequisites:**

The SharinPix Mobile Launcher works alongside the SharinPix mobile app.

**Kindly ensure that the SharinPix mobile app has been installed on your device before testing the component.**

For more information on how to install the SharinPix mobile app, click [here](../mobile-app/where-to-find-the-sharinpix-mobile-app.md).
{% endhint %}

## Getting Started

To use the SharinPix Mobile Launcher component, you simple need to drag and drop the component from the Lightning App Builder onto your page layout.

![](<../.gitbook/assets/image (1) (2) (1).png>)

## Lightning Component Parameters

![](<../.gitbook/assets/4 (4) (1) (2).png>)

* **Button Label:** Used to set the component's label. The default value is **Launch Mobile App**.
* **Album ID:** Used to specify the album Id. If you want to use the record Id as the album Id, leave this field blank.
* **Name field API name:** Text field to be used as job name. If set to None, value will default to either the record's name (if available) or the record ID.
* **Mode:** Used to specify whether to upload picture from the device's camera or roll. The values available are **camera** and **roll**, **scan**, **systemcam**, **snapsay**. Note that mode takes precedence on each of the listed options. Example: If mode is set to **systemcam** and parameter systemcam is set to false, the user will get access to System Camera.
* **Allow images from roll/gallery:** Used to enable/disable option to select images from the device's roll/gallery when **Mode** is set to **camera**. This option is set to **True** by default.
* **Tags:** Used to set up a tag list that will be made available when capturing photos.
* **Auto tags:** Used to specify auto tags which will be enforced on the picture taken.
* **Default tags:** Used to specify default tags that will be applied by default on the picture taken. The user has the option to remove the default tags after capturing the picture.
* **Checklist:** Used to fill a checklist with the tags specified.
* **Custom parameters:** Used to specify additional user-defined parameters to be appended to the SharinPix app launcher URL. Note that all duplicate parameters added in the mobile launcher will override the parameters values selected. Example: If you checked flash (equals true) and enter "flash=false" in Custom Parameters, the value of flash will be set to false. You can use the placeholder "**{userId}**" or "**{user\_id}**" to auto populate the current user Salesforce Id. Example "userId={userId}". For more information on the parameters that can be added, please follow [this article](../mobile-app/sharinpix-mobile-app-deeplink-syntax.md).
* **Custom Permission ID or Name:** ID or Name of SharinPix Permission for SharinPix Mobile Launcher
* **Component Id:** Component ID to be matched by SharinPix components on the page. This is any text which will be common between this component and the SharinPix album component. It allows for matching components to communicate in case some components need to be repeated on the same record page. Example: Set 'sharinpix-1' as Component Id here and also on SharinPix Album component's Component ID field.
* **Use Universal link format:** Used to generate a universal link when enabled. If disabled, a deeplink is generated instead. _Note: This feature can only be used to launch the SharinPix mobile app when online._
* **Show overlay:** Use selected image from a SharinPix Album component as overlay. The component will be disabled if no image is selected.
* **Camera flash:** Used to enable/disable the camera flash. This option is applicable when **camera mode** is on.
* **Confirm image taken:** Used to enable/disable option to preview and confirm each picture taken before the upload. This option is applicable when the **Mode** is set to **camera**.
* **Skip job association screen (deprecated):** This feature has been deprecated.

{% hint style="success" %}
**Tips:**

After submission from the SharinPix Mobile App, a return URL can be added to the Custom parameters to automatically return to the external app, such as the Salesforce mobile app or Salesforce Field Service app. For more information on the return URL, please refer to [this](../mobile-app/sharinpix-mobile-app-deeplink-syntax.md#ret_url) article.
{% endhint %}

## Demo

The image below shows the SharinPix Mobile Launcher component in the Salesforce mobile app:

![](<../.gitbook/assets/image (2) (2) (1).png>)

Select the button **Launch Mobile App** to launch the **SharinPix** mobile app.

The image below depicts the SharinPix mobile app when launched:

![](<../.gitbook/assets/image (3) (3).png>)

{% hint style="success" %}
**Tips:**

* You can refer to the link below for more details about the SharinPix Mobile Launcher component and how to add same on a Record Page\
  [Use the SharinPix Mobile Launcher component on a Record Page.](../features/main-integration/using-on-lightning-with-sharinpix-mobile-launcher-lightning-component-admin-friendly.md)
* The Mobile Launcher component uses tokens to capture and upload images which, when expired cannot be used to upload images anymore. Such tokens have a validity of 30 days by default. If you want to increase the token duration, you can do so by overriding the value of the custom label, **MobileTokenExpiryDays** , available in the SharinPix package to specify your desired number of days before the tokens expire for the Mobile Launcher component.

**Note:** This option is valid as from the package version **1.200**
{% endhint %}

{% hint style="warning" %}
**Note: Access Denied on Mobile Launcher**

User has no edit access to the record:

If the user has only view access to the record, a SharinPix Permission with **Upload Image** ability should be assigned to the Mobile launcher Component.
{% endhint %}
