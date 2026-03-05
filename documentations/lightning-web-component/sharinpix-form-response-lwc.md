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

# SharinPix Form Response LWC

## Overview

The **SharinPix Form Response** Lightning Web Component (LWC) is designed to display and process form responses stored in Salesforce. It embeds the SharinPix Form Response viewer inside Salesforce record pages and Communities, enabling users to view submitted forms directly within the platform.

The component also checks whether the form response has been processed and provides contextual toast messages to guide users.

{% hint style="info" %}
**Info**

This feature is only available on **Lightning Experience**.\
It can only be used on the **Form Response record page** , including:

* On Page Builder
* On Desktop
* On Mobile
* On Community Builder.
* In your own Lightning Component development

⚠️ This component cannot be used in Flows.
{% endhint %}

{% hint style="warning" %}
**Prerequisites**

* **Permissions:**\
  Users must have the **SharinPix Forms** **Admin** or **SharinPix Forms User** permission set assigned. For more information on these two permission sets, check [_SharinPix Permission sets_](../access-and-security/sharinpix-permission-sets.md).
* **Package Version:**\
  Ensure that the latest SharinPix Package Version is installed.
* **Setup Requirements:**\
  A SharinPix Form Template must exist, and responses must be linked to Salesforce records via the `FormResponse__c` object.
{% endhint %}

## Getting Started

To use the **SharinPix Form Response** component:

1. Open the **Lightning App Builder**.
2. Drag and drop the **SharinPix Form Response** component onto the **Form Response record page**.
3. Configure the component parameters as described below.
4. Save and activate the page.

![](<../.gitbook/assets/DOC SF - 1920 x 1080 (1) (1) (1) (2).png>)

## Lightning Component Parameters

| Parameter | Description                                   | Default/Notes                       |
| --------- | --------------------------------------------- | ----------------------------------- |
| height    | The height of the component in pixels.        | Default: `500px`                    |
| recordId  | The Salesforce record Id of the form response | For Salesforce Community usage only |

## Demo: Fire Safety Inspection Example

The image below shows the **SharinPix Form Response** component configured on the **Form Response record page** for the **Fire Safety Inspection Form Template** , with the **Height** property set to `500px`.

![](<../.gitbook/assets/DOC SF - 1920 x 1080 (2) (1) (1) (2).png>)
