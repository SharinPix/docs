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

# Using the Mobile Launcher Visualforce Component

## What is it used for?

The **Mobile Launcher** helps you to automatically generate a **Deeplink URL** which can then be used to launch the SharinPix Mobile App.

{% hint style="info" %}
For more information about Deeplink and its syntax, refer to the following article:

[SharinPix mobile App : Deeplink syntax](../../mobile-app/sharinpix-mobile-app-deeplink-syntax.md)
{% endhint %}

## How to use it:

Since it is a Visualforce Component, it can be easily inserted into a Visualforce Page. The code snippet below shows a sample implementation of the component within a Visualforce Page on the Account object.

```html
<apex:page standardController="Account">
	<sharinpix:MobileLauncher albumId="{! Account.Id }"></sharinpix:MobileLauncher>
</apex:page>
```

## How does it look ?

The screenshot below shows how the component looks when it is inserted into a page layout in the SalesforceApp, inside a Visualforce Page within the Salesforce App.

![](<../../.gitbook/assets/screenshot-docs.google.com-2022.08.25-18_06_24-removebg-preview (1).png>)

When you click on the **Take Pictures** button, the component will automatically launch the SharinPix mobile App.

However, if the latter is not already installed, the component will display the corresponding links to the SharinPix mobile App on the Google Play as well as on the App Store.

On an Android device:

![](<../../.gitbook/assets/screenshot-docs.google.com-2022.08.25-18_22_13-removebg-preview (1).png>)

On an IOS device:

![](<../../.gitbook/assets/screenshot-docs.google.com-2022.08.25-18_24_26-removebg-preview (1).png>)

## What parameters does the Mobile Launcher take ?

The Mobile Launcher can take several parameters. Each parameter applied affects the behavior inside the SharinPix mobile App when launched.

### albumId

The **albumId** attribute takes the ID of a record to which the photos taken by the SharinPix Mobile app will be uploaded.

```html
<sharinpix:MobileLauncher albumId="<<id of record>>"></sharinpix:MobileLauncher>
```

### urlParameters

The **urlParameters** attribute takes a set of parameters that will affect how the SharinPix Mobile App will behave when its launched.

```html
<sharinpix:MobileLauncher albumId="{! Account.Id }" urlParameters="confirmation=true&mode=camera"></sharinpix:MobileLauncher>
```

In the code snippet above, the urlParameters applied are:

* confirmation=true
* mode=camera

The **confimation** and **mode** parameters are used in the Deeplink URL. In this case, they will cause the SharinPix mobile App to open directly on camera mode and will preview each photo captured before uploading them.

The image depicts how the photo captured is previewed before being uploaded:

![](<../../.gitbook/assets/screenshot-docs.google.com-2022.08.23-17_48_40-removebg-preview_(1) (1) (2).png>)

Let's use two more urlParameters example to get you acquainted:

1\. Using the parameter **tags** :

```
urlParameters="tags=Red;Blue"
```

The results obtained when launching the SharinPix mobile App is as follows:

![](<../../.gitbook/assets/screenshot-docs.google.com-2022.08.23-18_09_12-removebg-preview (1).png>)

2\. Using the **checklist** parameter.

```
urlParameters="checklist=North;South;East;West"
```

The results obtained when launching the SharinPix mobile App is as follows:

![](<../../.gitbook/assets/screenshot-docs.google.com-2022.08.23-18_06_27-removebg-preview (1).png>)

{% hint style="success" %}
You can find more information about the **confirmation**, **mode**, **tags** and **checklist** parameters and many more in the following article:

[SharinPix mobile App : Deeplink syntax](../../mobile-app/sharinpix-mobile-app-deeplink-syntax.md)
{% endhint %}

### label

The **label** parameter takes the value of the text that will appear on the component button.

```html
<sharinpix:MobileLauncher albumId="{! Account.Id }" urlParameters="confirmation&mode=camera" label="Shoot Pictures"></sharinpix:MobileLauncher>
```

![](<../../.gitbook/assets/screenshot-docs.google.com-2022.08.25-18_27_47 (1).png>)

{% hint style="success" %}
How to use the Mobile Launcher in the Salesforce mobile App:

* Create a Visualforce Page containing the Mobile Launcher component.
* Add the VF Page created on a page layout in the Salesforce App.

You can also add the **SharinPix Mobile Launcher** component on a Lightning page. To do so, refer to the following article:

[Using on Lightning with "SharinPix Mobile Launcher" Lightning Component (Admin Friendly)](using-on-lightning-with-sharinpix-mobile-launcher-lightning-component-admin-friendly.md)
{% endhint %}
