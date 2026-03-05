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

# Upload Max File SIze

## Overview

In this article, we will demonstrate how to restrict the maximum size of a file when uploading on a SharinPix Album or SharinPix Single Image. To do so, we will:

* [Create a SharinPix Permission to set Max File Size](upload-max-file-size.md#creation-of-sharinpix-permission)
* [Assign the Permission to a SharinPix Component](upload-max-file-size.md#assign-the-sharinpix-permission-to-the-album-component)

{% hint style="warning" %}
**Prerequisite:**

**Before using this feature, ensure:**

* The SharinPix Package Version 1.340 (or later) is installed; refer to the article below to upgrade your current package: [_How to upgrade SharinPix package_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)
{% endhint %}

## Creation of SharinPix Permission

* In [SharinPix Permissions](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md), create a new record or edit an existing permission.
* Open the Upload section and set the maximum file size in **Megabytes**.

![](<../../.gitbook/assets/DOC SF - 1920 x 600(1).png>)

## Assign the SharinPix Permission to the Album component

* On a [SharinPix Album](../../lightning-web-component/sharinpix-album-lwc.md), add the **ID** or **Name** of the SharinPix Permission record, which includes the maximum file size.
* In this example, the custom permission was named **Maximum File Size of 2MB**. It has been set in the **Custom Permissions Id or Name** parameter of a _SharinPix Album_ component.

![](<../../.gitbook/assets/DOC SF - 1920 x 360 (4).png>)

{% hint style="success" %}
**Tip:**

The above will also work for a [SharinPix Single Image](../../lightning-web-component/sharinpix-single-image.md). The custom permission created should then be defined as a Single Image Permission.
{% endhint %}

## Demo

Now, the file will not be uploaded, and an alert will appear during upload if it exceeds the maximum file size set for the permission.

![](<../../.gitbook/assets/DOC SF - 1920 x 1080(2) (1).png>)
