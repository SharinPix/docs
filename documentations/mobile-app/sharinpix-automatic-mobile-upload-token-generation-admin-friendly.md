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

# SharinPix automatic mobile upload token generation (Admin Friendly)

This article demonstrates how to generate SharinPix tokens allowing _**image upload using the SharinPix mobile app only**_. Such token configuration is solely used for mobile uploads and not for album display.

## Overview

This article demonstrates how to create a Salesforce Flow that will generate and store SharinPix mobile app tokens to upload images onto an album upon the creation of records.

To do this, we will:

* [Create the SharinPix Token field(s) that will store the token generated](sharinpix-automatic-mobile-upload-token-generation-admin-friendly.md#creation-of-the-sharinpix-token-field-s)
* [Create the Flow](sharinpix-automatic-mobile-upload-token-generation-admin-friendly.md#creation-of-the-flow)

{% hint style="warning" %}
**Note:**

To access online features such as **viewing** SharinPix albums, specific SharinPix images, and SharinPix search within the SharinPix mobile app, the SharinPix app **online mode** can be used. For more information on how to make use of the online mode feature, refer to the following article:

[SharinPix Mobile App: Online mode](sharinpix-mobile-app-online-mode.md)
{% endhint %}

## Creation of the SharinPix Token field(s)

For this demo, we will use the **Work Order** object. Firstly, we need to create fields that will store the token generated. You have two ways of doing this:

1. By creating a single field of type **Long Text Area** that will store the token.
2. By creating multiple fields of type **Text Area (255)**. In this case, the token will be split into chunks of a maximum of 255 characters. Each chunk will be then stored in the fields.

### 1. Creation on a single field to store the SharinPix Token

Create a field named **SharinPix Token** of type **Long Text Area** on the Opportunity object.

### 2. Creation of multiple fields to store the SharinPix Token

{% hint style="success" %}
As Formula in Salesforce doesn't support Long Text Area field, we suggest creating 3 fields of type **Text Area(255)** to support the token also in Formula. However, those should not be needed if you are using the token in the Field Service mobile app.

_If you don't need the token to be part of a formula field_ , please ignore all the parts of this article including references to those fields, and only focus on the single SharinPix token field of type Long Text Area field.
{% endhint %}

Create three fields, of data type **Text(255)** and field labels:

1. SharinPix Token 1
2. SharinPix Token 2
3. SharinPix Token 3

## Creation of the Flow

{% hint style="info" %}
The SharinPix package includes the class **TokenGeneration** which contains a method that can be used to generate a token for an object. Using this method, the token generated can be automatically stored inside the user-defined field(s).
{% endhint %}

{% hint style="warning" %}
For the rest of the demo, we will use single field **SharinPix Token** , instead of **SharinPix Token 1**, **SharinPix Token 2** , and **SharinPix Token 3** to store the token.
{% endhint %}

This section demonstrates how to create a Flow that invokes the apex class **TokenGeneration** in order to generate a token for newly-created/updated Work Order records.

To do so, follow the steps below:

* Go to Setup. In the Quick Find Box, type **Flows**.
* Under **Process Automation** , select **Flows**.
* Click on the **New Flow** button.
* Select the option **Record-Triggered Flow** , and click on the **Create** button.

<figure><img src="../.gitbook/assets/SharinPix automatic mobile upload token generation (Admin Friendly) - 1.png" alt=""><figcaption></figcaption></figure>

* After clicking on _Create_ , the _Configure Start_ modal will be displayed. Fill in the modal as indicated below:
  * **Select Object** : Work Order
  * **Configure Trigger** : A record is created or updated
  * **Set Entry Conditions** : None
  * **Optimize the Flow for** : Actions and Related Records
* Click on **Done** to save the configurations.

<figure><img src="../.gitbook/assets/SharinPix automatic mobile upload token generation (Admin Friendly) - 2.png" alt=""><figcaption></figcaption></figure>

* Next, add an **Action** element.

{% hint style="warning" %}
**Warning:**\
Starting with the Salesforce **Winter’26 release** , Apex Actions can no longer be executed directly in the **Run Immediately** path of a record-triggered flow. Instead, they must be placed in an **asynchronous path** , as the synchronous execution option is no longer supported.

For more details, please refer to the documentation here:\
[_Unable to save a flow with an Apex Action after the Salesforce Winter ’26 release – What should I do?_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/i-am-unable-to-save-a-flow-with-an-apex-action-after-the-salesforce-winter-26-release-what-should-i)
{% endhint %}

<figure><img src="../.gitbook/assets/SharinPix automatic mobile upload token generation (Admin Friendly) - 3.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/SharinPix automatic mobile upload token generation (Admin Friendly) - 4.png" alt=""><figcaption></figcaption></figure>

* On the \_Action \_modal, use the search bar to find the **sharinpix\_\_TokenGeneration** Apex class.
* Click on **sharinpix\_\_TokenGeneration**.

<figure><img src="../.gitbook/assets/SharinPix automatic mobile upload token generation (Admin Friendly) - 5.png" alt=""><figcaption></figcaption></figure>

* On the \_Action \_modal for _sharinpix\_\_TokenGeneration_ , populate the fields as indicated below:
  * **Label:** Generate Mobile Upload Tokens
  * **Description:** Enter a description (optional)
  * **Field API Name(s)** : SharinPix\_Token\_\_c
    * _Note: This is a mandatory field and refers to the SharinPix token field API name._
  * **Record ID:**{!$Record.Id}
    * _Note: This is a mandatory field and refers to the current Work Order record Id._

{% hint style="warning" %}
If you are using multiple fields to store the token, please note that:

* The token generated is split and stored into the fields **SharinPix Token 1** , **SharinPix Token 2**, and **SharinPix Token 3**.
* The values **SharinPix\_Token\_1\_\_c** , **SharinPix\_Token\_2\_\_c,** and **SharinPix\_Token\_3\_\_c** refer to the field API names used to store the token generated.
* For the Flow to work as expected, you must ensure that:
  1. Each API name is typed correctly in the **Field API Name(s)** section.
  2. The API names should be separated by a semi-colon as shown below:

&#x20;         **SharinPix\_Token\_1\_\_c**;**SharinPix\_Token\_2\_\_c;SharinPix\_Token\_3\_\_c**
{% endhint %}

<figure><img src="../.gitbook/assets/SharinPix automatic mobile upload token generation (Admin Friendly) - 6.png" alt=""><figcaption></figcaption></figure>

There are other **optional** variables that are available in the \_Action \_modal, namely:

* **Custom Permission ID or Name:** ID or Name of the **SharinPix Permission** object (of type **Mobile Launcher**) to be used for opening the SharinPix Mobile App.
* **Hours Before Token Expires:** This can be used to set the number of hours before the token expires. This variable has a type **Number** and only takes **integers** as values. For example, if you want the token to expire in 3 hours, just enter 3 in the **Value** field.
* **Record Name**: This can be used to reference the record name (or number) inside the token.

{% hint style="warning" %}
**Note**:

* If you do not want the tokens to expire, do not fill in the **Hours Before Token Expires** parameter.
* If you want the token to expire after a specified number of hours, ensure that you provide enough time before the token expires as expired tokens are no more valid and cannot be used to upload photos.
{% endhint %}

<figure><img src="../.gitbook/assets/SharinPix automatic mobile upload token generation (Admin Friendly) - 7.png" alt=""><figcaption></figcaption></figure>

5\. Click **Done** to save the _Action_ configurations.

6\. Save the Flow and activate it.

## Find the SharinPix Token

Using the above Flow, tokens are generated/updated for all Work Order records created/updated.

The SharinPix Token can be found inside the **SharinPix Token** field of the newly-created/updated Work Order records.

<figure><img src="../.gitbook/assets/SharinPix automatic mobile upload token generation (Admin Friendly) - 8.png" alt=""><figcaption></figcaption></figure>
