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

# SharinPix Generate Form Response PDF

## Overview

The **Generate Form Response PDF** component is a button that allows users to instantly generate a PDF version of the latest SharinPix form they have submitted. Users can configure it, choosing to either open the generated Form Response PDF in a new tab for immediate viewing or import it directly into a [SharinPix Album](sharinpix-album-lwc.md).

![](<../.gitbook/assets/DOC SF - 1920 x 360 (1) (1) (1) (1) (2).png>)

{% hint style="info" %}
**Info:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
* On Mobile
* On Community Builder
* In your own Lightning Component development
* In Flows
{% endhint %}

{% hint style="warning" %}
**Prerequisites**

* **Permissions:** Users must have the **SharinPix Forms** **Admin** or **SharinPix Forms User** permission set assigned. For more information on these two permission sets, check [_SharinPix Permission sets_](../access-and-security/sharinpix-permission-sets.md).
* **Package Version:** Ensure that the SharinPix Package Version **1.355 (or later)** is installed. Refer to the article below to upgrade your current package: [_How to upgrade SharinPix package_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)
* A [**SharinPix Form Template**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-template-editor) should be configured beforehand.
{% endhint %}

## Getting Started

To use the SharinPix Generate Form Response PDF component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

![](<../.gitbook/assets/DOC SF - 1920 x 360 (1) (1) (1) (1) (1) (2).png>)

## Lightning Component Parameters

![](../.gitbook/assets/SFSDFSDGFDS.png)

| Parameter                          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Default/Notes                                        |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| Button Label                       | The text displayed on the button that users will click to generate the SharinPix form response PDF.                                                                                                                                                                                                                                                                                                                                                                                                         | Default value: Generate Form Response PDF            |
| SharinPix Form Template Name or ID | Specifies which SharinPix Form Template to use to generate the PDF. Provide the template’s Name, ID, or a Salesforce field containing the template's Name or ID in the format: `{Inspection_Template__c}`. The PDF will be generated from the **latest Form Response** of the specified template submitted on the current record. The template must have been created in the [SharinPix Form Template Editor](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-template-editor). | Must match an existing template in your system.      |
| Select Action                      | This dropdown lets you choose what to do with the generated PDF. You can either open it in a new browser tab, or import it directly into a SharinPix album linked to the same record..                                                                                                                                                                                                                                                                                                                      | Default value: _Open Pdf in a New Tab_               |
| **Record ID** \*                   | (**Required in Flow Screens and Community Pages**) The Salesforce record ID of the record page.                                                                                                                                                                                                                                                                                                                                                                                                             | Auto-populated in some contexts; required otherwise. |

## Demo: Fire Safety Inspection Example

This example demonstrates importing the **fire safety inspection PDF** into the related site’s SharinPix album when a form is submitted.

The image below shows the **SharinPix Generate Form Response PDF** component configured in the Salesforce App Builder, with properties filled:

* **SharinPix Form Template Name** set to _Fire Safety Inspection_
* **Select Action** set to _Import to SharinPix album_

![](<../.gitbook/assets/VVVVV (1).png>)

Assuming at least one form response exists for the _Fire Safety Inspection_ form template, clicking the **SharinPix Generate Form Response PDF** button will generate a PDF of the latest form response and automatically import it into the SharinPix album linked to the same record. You may need to **refresh the page** to see the PDF appear in the album.

The image below displays the generated PDF stored within the SharinPix album:

![](<../.gitbook/assets/DOC SF - 1920 x 360 (2) (1) (1) (1).png>)

![](<../.gitbook/assets/DOC SF - 1920 x 360 (3) (1) (1) (1).png>)

{% hint style="danger" %}
**Alert**

The import to the SharinPix album will **only** occur once the **PDF URL** for the form response is **available**. For example, if the SharinPix Form response includes images that are still uploading, the PDF may not be immediately generated.
{% endhint %}
