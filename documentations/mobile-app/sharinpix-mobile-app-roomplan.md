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

# SharinPix Mobile App: Roomplan

The roomplan functionality allows users to scan and create detailed 3D models of rooms and buildings within the SharinPix mobile app. This feature utilizes the device's LiDAR sensors to measure and visualize real-world spaces accurately. It is only available on devices that run on iOS 14 and later and support LiDAR capabilities.

This article demonstrates how to use the RoomPlan feature.

## Supported Devices

The Roomplan feature is currently **only** available on devices with a LiDAR scanner, including:

* iPhone 12 Pro and later models
* iPad Pro (3rd generation) and later models

## Roomplan Configurations

The **roomplan** mode is available by default on [supported devices](sharinpix-mobile-app-roomplan.md#supported-devices), and it can be customized through SharinPix deeplinks. For more information on configuring **roomplan** through deeplinks, refer to the links below:

* [Using roomplan as the **default** mode](sharinpix-mobile-app-deeplink-syntax.md#mode)
* [RoomPlan mode visibility](sharinpix-mobile-app-deeplink-syntax.md#visibility-for-the-modes)

## Demo

To use the RoomPlan feature, first select the **ROOM PLAN** mode. The scan screen will open as shown in the screenshot below.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Roomplan - 1.png" alt=""><figcaption></figcaption></figure>

Once the scan is completed, click **Done**. A preview of the scanned space will be displayed as depicted below.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Roomplan - 2.png" alt=""><figcaption></figcaption></figure>

After completing the scanning process, the 3D model cannot be previewed on the SharinPix mobile app. However, once it is uploaded to Salesforce, the model can be viewed and used to take measurements using our 3D viewer, which is further detailed in the documentation.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Roomplan-3.png" alt=""><figcaption></figcaption></figure>

Once the model is uploaded, you can access it through the [SharinPix Album](../lightning-web-component/sharinpix-album.md) on Salesforce. In preview mode, a **3D Viewer** button will appear, allowing us to open the 3D Viewer. This viewer enables detailed exploration of the model and supports precise measurements directly within the interface.

To take a measurement, click to place points on the model—measurements are calculated between two points. Measurements can be removed from the model as needed, and the units of measurement can also be changed.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Roomplan - 4.png" alt=""><figcaption></figcaption></figure>
