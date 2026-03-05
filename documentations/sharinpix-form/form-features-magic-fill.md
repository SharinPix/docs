# Form Features - Magic Fill

## Overview

{% hint style="info" %}
SharinPix **Magic Fill** allows you to automatically populate a **text field** with dynamic content generated from an image.\
Using an AI model, Magic Fill analyzes the image and produces text based on a **user-defined prompt**.

This configuration is available directly in the [**SharinPix Form Template Editor**](sharinpix-form-template-editor.md).

This article covers the following:

* [How to configure Magic Fill on Text and Text Area Fields](form-features-magic-fill.md#configure-magic-fill-on-text-and-text-area)
* [Demo of the Magic Fill feature with an Address Extraction Example](form-features-magic-fill.md#demo-address-extraction-example)
{% endhint %}

## Getting Started

### Configure Magic Fill on Text and Text Area

Magic Fill can be enabled for any Text or Text Area component inside a SharinPix Form.

1. In the **SharinPix Form Template Editor**, open the **Magic Fill** tab of the element.
2. Check the option **“Magic Fill”**.
3. Provide a **prompt** that instructs the AI on what information to extract or how to interpret the image.

The prompt is essential: it tells the AI what kind of text you expect from the uploaded image.

![](<../.gitbook/assets/DOC SF - 1920 x 1080 (6) (2).png>)

#### Examples of What Magic Fill Can Do

You can use Magic Fill to:

* Ask the AI to **describe** the image
* Extract **specific details** , such as a serial number, condition, or text written on a label
* Read information from **documents, tags, labels, or packaging**
* Parse structured content such as addresses, dates, or reference numbers

Magic Fill can be configured on a question element of type **Text Area** the same way as shown in the image below

![](<../.gitbook/assets/DOC SF - 1920 x 480 (2).png>)

### Demo: Address Extraction Example

This example demonstrates the Magic Fill feature within an **Address Extraction** scenario. When a user uploads an image of an address label or document, the **Address** field is automatically filled with the extracted address information.

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (2) (2).png>)

The example below shows a **Proof of Address** photo which has been taken and is going to be used by the **Address** text field that is not yet populated.

![](<../.gitbook/assets/DOC SF - 1920 x 1080 (1) (4).png>)

The diagram below shows the form after the **Proof of Address** has been captured. The **Address** field is automatically filled with the AI-extracted address based on the image and the configured Magic Fill prompt.

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (1) (1) (2).png>)
