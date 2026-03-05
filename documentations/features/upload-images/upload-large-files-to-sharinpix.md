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

# Upload Large Files To SharinPix

## Overview

In this article, we will demonstrate how to use a multipart image upload on a SharinPix Album or SharinPix Single Image. To do so, we will:

* [Create a SharinPix Permission to set Multipart Upload](upload-large-files-to-sharinpix.md#creation-of-sharinpix-permission)
* [Assign the Permission to a SharinPix Component](upload-large-files-to-sharinpix.md#assign-the-sharinpix-permission-to-the-album-component)

SharinPix uses a feature called **Multipart Upload** for large file transfers: breaking a large file into smaller parts, uploading them in parallel for speed, and reassembling them in Amazon S3.

The key benefits include:

* Improved Throughput/Speed when uploading large files
* Enhanced Reliability and Fault Tolerance
* Efficient Memory Usage

{% hint style="warning" %}
**Note:**&#x20;

* If you do not frequently upload files larger than **100 MB**, do not activate this, as it will affect performance
* **Before using this feature, ensure you have the latest SharinPix package installed.** [_How to upgrade SharinPix package_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)
{% endhint %}

## Creation of SharinPix Permission

* In [SharinPix Permissions](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md), create a new record or edit an existing permission.
* Open the Upload section and check Multipart Upload.

![](<../../.gitbook/assets/Upload Multipart Doc.png>)

## Assign the SharinPix Permission to the Album component

* On a [SharinPix Album](../../lightning-web-component/sharinpix-album-lwc.md), add the **ID** or **Name** of the SharinPix Permission record, which includes the maximum file size.
* In this example, the custom permission was named **Upload Multipart**. It has been set in the **Custom Permissions ID or Name** parameter of a _SharinPix Album_ component.

![](<../../.gitbook/assets/Upload Multipart Doc (1).png>)

{% hint style="success" %}
**Tip:**\
\
The above will also work for a [SharinPix Single Image](../../lightning-web-component/sharinpix-single-image.md). The custom permission created should then be defined as a Single Image Permission.
{% endhint %}
