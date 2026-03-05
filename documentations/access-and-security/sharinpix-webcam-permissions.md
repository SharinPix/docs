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

# SharinPix Webcam Permissions

This feature can be configured using a [SharinPix Permission](sharinpix-permission-object-how-to-create-and-assign-custom-permission.md) record.

## Setting up the upload from webcam feature using a SharinPix Permission record

The upload from the webcam feature can be configured using a [SharinPix Permission record](sharinpix-permission-object-how-to-create-and-assign-custom-permission.md) as follows:

* From App Launcher, type **SharinPix Permission**
* Click on the button **New** to create a new SharinPix Permission record
* Next, under the **Upload** section, enter **'webcam'** in the field labeled as **Uploader**

![](../.gitbook/assets/screenshot-sharinpix.atlassian.net-2023.07.18-18_00_25.png)

* Select the other desired abilities if needed and click **Save** when done
* Next, assign the created SharinPix Permission record to the desired SharinPix standard album or your custom album

{% hint style="success" %}
**Tip:**

* For more information about the SharinPix Permission object and how it is configured, refer to the following article: [SharinPix Permission object](sharinpix-permission-object-how-to-create-and-assign-custom-permission.md)
* Setting the **Uploader** ability to **webcam** also allows access to the front and rear cameras as Webcams on tablets (such as the Microsoft Surface tablets).
{% endhint %}
