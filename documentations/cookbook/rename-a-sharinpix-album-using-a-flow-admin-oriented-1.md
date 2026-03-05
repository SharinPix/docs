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

# Automatic Album Token Generation using a Flow (Admin-Oriented)

## Overview

This article explains how the invocable Apex `GenerateAlbumTokenAutomation` generates an online token to access a SharinPix Album through a Salesforce Flow.

It covers the following:

1. [Input Parameters](rename-a-sharinpix-album-using-a-flow-admin-oriented-1.md#input-parameters)
2. Flow Configuration Guide

* Step 1: [Prepare Custom Field To Store Token](rename-a-sharinpix-album-using-a-flow-admin-oriented-1.md#step-1-prepare-custom-field-to-store-token)
* Step 2: [Configure a Record-Triggered Flow](rename-a-sharinpix-album-using-a-flow-admin-oriented-1.md#step-2-configure-a-record-triggered-flow)
* Step 3: [Add the Action to Generate the Album Token](rename-a-sharinpix-album-using-a-flow-admin-oriented-1.md#step-3-add-the-action-to-generate-the-form-token)
* Step 4: [Add Update Element](rename-a-sharinpix-album-using-a-flow-admin-oriented-1.md#step-4-add-update-element)
* Step 5: [Save and Activate the Flow](rename-a-sharinpix-album-using-a-flow-admin-oriented-1.md#step-5-save-and-activate-the-flow)

3. [Demo](rename-a-sharinpix-album-using-a-flow-admin-oriented-1.md#demo)

{% hint style="warning" %}
**Prerequisites**

Before configuring this automation, ensure the following:

* You have the latest **SharinPix Package** installed. This feature requires version **1.346** or higher. You can follow [this guide](https://docs.sharinpix.com/faqs/how-to-update-sharinpix-package-from-the-appexchange) to upgrade your SharinPix Managed Package to the newest version.
{% endhint %}

## Input Parameters

Below are the inputs required when using the `GenerateAlbumTokenAutomation` invocable method in a Salesforce Flow. These parameters must be provided to successfully generate an album token.

<table><thead><tr><th width="155.9921875">Parameter</th><th width="399.9921875">Description</th><th>Required/Optional</th></tr></thead><tbody><tr><td>recordId</td><td>The Salesforce Record ID (e.g. Work Order ID) to generate Album token for.</td><td>Required</td></tr><tr><td>permissionId</td><td>Name or ID of the SharinPix Permission object (of type <em>Album</em>) to be used for token generation. If no SharinPix Permission is specified, the user will receive an album token with basic abilities.</td><td>Optional</td></tr><tr><td>expiry</td><td>Number of days after which the token will expire. </td><td>Optional</td></tr></tbody></table>

## Flow Configuration Guide

The following flow setup uses a **Record-Triggered Flow** to automatically generate a SharinPix token when a record is created or updated. The **Work Order** object is used here as an example, but you can apply the same automation to any Salesforce standard or custom object, depending on where you want to generate the token.

### Step 1: **Prepare Custom Field To Store Token**

A field is needed on the Work Order object to store the generated token. To do so, create a **Text Area (Long)** field to store the entire token.

1. Go to **Setup** > **Object Manager** > **Work Order**.
2. Click on **Fields & Relationships** > **New**.
3. Select **Text Area (Long)** as the field type.
4. Name the field (e.g., `SharinPix Album Token`) and set the **length** to the maximum value (`131,072` characters).
5. **Save** the field.

This field will store the full token returned by the flow.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (1) (6).png" alt=""><figcaption></figcaption></figure>

### **Step 2: Configure a Record-Triggered Flow** <a href="#step-2-configure-a-record-triggered-flow" id="step-2-configure-a-record-triggered-flow"></a>

1. Go to **Setup** > **Flows** > Click **New Flow**
2. Choose **Start From Scratch** and click **Next**
3. Choose **Record-Triggered Flow** and click **Create**
4. Set the following values:

| Setting               | Value                                    |
| --------------------- | ---------------------------------------- |
| Object                | Work Order\*                             |
| Trigger               | A record is created or updated           |
| Set Entry Conditions  | _Status_ Field _Equals_ to _In Progress_ |
| Optimize the Flow for | Actions and Related Records              |
| Add Asynchronous Path | On                                       |

\*Please note that the _Object_ Setting can be configured as desired.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (1) (5).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (5) (3).png" alt=""><figcaption></figcaption></figure>

### **Step 3: Add the Action to Generate the Album Token** <a href="#step-3-add-the-action-to-generate-the-form-token" id="step-3-add-the-action-to-generate-the-form-token"></a>

1. For this example, we will create a [SharinPix Permission](../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md) of type &#x41;_&#x6C;bum_ with the following abilities:

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (3) (2).png" alt=""><figcaption></figcaption></figure>

2. On your flow, add an **Action** element
3. Search for `Sharinpix__GenerateAlbumTokenAutomation`
4. On the **Action** modal for `Sharinpix__GenerateAlbumTokenAutomation`, populate the fields as indicated below:

| Field                           | Example Value                        |
| ------------------------------- | ------------------------------------ |
| Record ID                       | Triggering WorkOrder > Work Order ID |
| Expiry in Days                  | 10                                   |
| SharinPix Permission Name or ID | Album Permission\*                   |

\*Note that if no **SharinPix Permission** is specified, the user will receive an album token with basic abilities.

{% hint style="warning" %}
**Warning**

* If the expiry value is not specified, the token will default to 30 days. If the token should not expire, the expiry value should be set to zero (`0`). This field only accepts whole numbers; decimal values are not supported and will result in an error.
{% endhint %}

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (3) (3).png" alt=""><figcaption></figcaption></figure>

### **Step 4: Add Update Element** <a href="#step-4-add-update-element" id="step-4-add-update-element"></a>

This step is used to store the token generated by the Apex action into the custom field `SharinPix_Album_Token__c` you created on the Work Order.

1. Add an **Update** element
2. Select **Use the Work Order record that triggered the flow**
3. For this example, we will not add any filter conditions.
4. In the **Set Field Values for the Work Order Record** section, populate it as indicated below:

<table><thead><tr><th width="248.38671875">Field</th><th>Value</th></tr></thead><tbody><tr><td>SharinPix_Album_Token__c</td><td>Outputs from sharinpix__GenerateAlbumTokenAutomation.SharinPix_Album_Token__c</td></tr></tbody></table>

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (2) (2).png" alt=""><figcaption></figcaption></figure>

### Step 5: Save and Activate the Flow <a href="#step-5-save-and-activate-the-flow" id="step-5-save-and-activate-the-flow"></a>

**Save** the Flow and click **Activate**.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (4) (2).png" alt=""><figcaption></figcaption></figure>

## Demo

To test the Flow, create or go to a Work Order record and set the _Status_ field to _In Progress_.

After the flow runs, the generated token will be stored in the `SharinPix_Album_Token__c` field of the Work Order. You can view it directly from the record detail page to confirm that the token was generated successfully.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (5) (4).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
To use the generated token to open a SharinPix Album in online mode, you can refer to this article: [SharinPix Mobile App: Online Mode](../mobile-app/sharinpix-mobile-app-online-mode.md).
{% endhint %}

The image below illustrates the SharinPix Album configured with the permissions outlined in the [Album Permission](rename-a-sharinpix-album-using-a-flow-admin-oriented-1.md#step-3-add-the-action-to-generate-the-form-token) above.       &#x20;

<figure><img src="../.gitbook/assets/Copy of DOC Mobile - 1920 x 1080 (2).png" alt=""><figcaption></figcaption></figure>
