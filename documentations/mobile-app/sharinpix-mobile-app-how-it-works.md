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

# SharinPix Mobile App: How it works

The present article gives an overview of how the SharinPix Offline Mobile application works and what makes it an ideal companion when taking pictures on the field.

## Connected to Salesforce

* Every picture you take with the SharinPix Mobile App is uploaded to the corresponding album/record in Salesforce.
* You just need to navigate to the Salesforce record of your choice and open the SharinPix mobile app from there using any [integration listed below](sharinpix-mobile-app-how-it-works.md#how-to-integrate-sharinpix-mobile-app-and-salesforce)

![](../.gitbook/assets/salesforce_connect_\(2\).png)

## Offline mode

* Pictures can be taken while the device is offline.

![](../.gitbook/assets/Webp.net-resizeimage_\(1\).jpg)

* The images are then uploaded to Salesforce when a connection is re-established in background without any user interaction.

![](../.gitbook/assets/Webp.net-resizeimage_\(3\).jpg)

## How to integrate SharinPix mobile App and Salesforce?

SharinPix mobile App needs to be integrated with any Salesforce or 3rd Party app to works.

This could be done using :

\- [SharinPix Mobile Launcher](../lightning-web-component/sharinpix-mobile-launcher.md) Lightning Component (or [Launcher as VF Component](../features/main-integration/using-the-mobile-launcher-visualforce-component.md)) when integrating with Salesforce mobile App

\- [App Extension on Salesforce Field Service mobile App](../integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-app-extension.md)

\- [Flow on Field Service mobile App](../integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-flows.md)

\- [Deeplink URL integration](sharinpix-mobile-app-deeplink-syntax.md) in any App
