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

# Duplicate SharinPix Images Using a Flow (Admin-Oriented)

## Overview

The <mark style="color:$danger;">`DuplicateImagesAutomation`</mark> Invocable Apex method allows users to duplicate **specific images** from one SharinPix album to another, with the option to include associated **tags**. This is ideal for use cases where only a subset of images (e.g., those flagged or selected in a custom UI) needs to be copied across records.

This invocable method is designed for use in **Salesforce Flows** and supports image transfer between any two records with linked SharinPix albums (e.g., from Case to another Case, Site to Project, etc.).

This article covers the following:

* [Input Parameters for DuplicateImagesAutomation](duplicate-sharinpix-images-using-a-flow-admin-oriented.md#input-parameters)
* [Flow Setup](duplicate-sharinpix-images-using-a-flow-admin-oriented.md#flow-setup)
  * [Step 1: Select Images from Source Album](duplicate-sharinpix-images-using-a-flow-admin-oriented.md#step-1-select-images-from-source-album)
  * [Step 2: Fetch Related Work Order Line Items](duplicate-sharinpix-images-using-a-flow-admin-oriented.md#step-2-fetch-related-work-order-line-items)
  * [Step 3: Choose Destination WOLIs](duplicate-sharinpix-images-using-a-flow-admin-oriented.md#step-3-choose-destination-wolis)
  * [Step 4: Execute Duplication](duplicate-sharinpix-images-using-a-flow-admin-oriented.md#step-4-execute-duplication)
  * [Step 5: Test and Deploy](duplicate-sharinpix-images-using-a-flow-admin-oriented.md#step-5-test-and-deploy)
* [Demo: Work Order to Work Order Line Item Example](duplicate-sharinpix-images-using-a-flow-admin-oriented.md#demo-work-order-to-woli-flow-example)

{% hint style="warning" %}
**Prerequisites**

Before configuring this automation, ensure the following:

* You have the latest **SharinPix Managed Package** installed.
{% endhint %}

## Input Parameters

Below are the inputs required when using the `DuplicateImagesAutomation` invocable method in a Salesforce Flow. These must be populated for the image duplication to succeed.

| Parameter          | Description                                                                                                                                        |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| imageIds           | A list of SharinPix **Image Public IDs** that should be duplicated. Example: <mark style="color:$danger;">`["id1", "id2"]`</mark>. _(Required)_    |
| destinationAlbumId | The **ID of the destination record** , where the duplicated images should be stored. This record must be linked to a SharinPix album. _(Required)_ |
| tags               | Boolean indicating whether to duplicate **tags** along with the images. _(Optional)_                                                               |

## Flow Setup

This example is based on a **Work Order to Work Order Line Item** scenario, where specific images from a Work Order’s SharinPix album are duplicated into the album of a related Work Order Line Item.

### Step 1: Select Images from Source Album

Use a **Screen Element** with the <mark style="color:$danger;">`SharinPix Album (LWC)`</mark> component.

* **Label** : <mark style="color:$danger;">`Select Images to copy`</mark>
* Users select images from the Work Order's SharinPix album
* In the <mark style="color:$danger;">`AlbumId`</mark> field, create a new resource of type **Variable** and Data Type **Text.** For the**API Name,** please type in "**recordId**"

![](<../.gitbook/assets/Click on the (18) (1) (1) (1).png>)

### Step 2: Fetch Related Work Order Line Items

Add a **Get Records** element to retrieve WOLIs related to the current Work Order.

* **Object** : Work Order Line Item
* **Filter** : <mark style="color:$danger;">`WorkOrderId`</mark> equals <mark style="color:$danger;">`Source_Album.RecordId`</mark> (or Work Order ID contextually)
* Store **All Records** , with **All Fields**

![](<../.gitbook/assets/Click on the (12) (1) (1) (1).png>)

### Step 3: Choose Destination WOLIs

Add another **Screen Element** using the **Data Table** component.

* **Label** : <mark style="color:$danger;">`Choose Work Order Line Item on which to paste duplicated images`</mark>
* Source Collection: The WOLIs from Step 2
* Allow selection of one or multiple WOLIs (as needed)
* Configure the rows and columns of the data table as per your use case. In this case, we will show <mark style="color:$danger;">`Work Order Line Item Number`</mark> as the column.

![](<../.gitbook/assets/Click on the (21) (1) (1).png>)

### Step 4: Execute Duplication

Add an **Apex Action** calling <mark style="color:$danger;">`sharinpix__DuplicateImagesAutomation`</mark>.

* **Label** : <mark style="color:$danger;">`Duplicate Selected Images`</mark>
* **List of Image Ids** : Value from Screen 1 (selected image IDs - <mark style="color:$danger;">`{!Source_Album.selectedImageIds}`</mark> )
* **Destination Album ID** : Selected WOLI(s) from the Data Table
* **Duplicate Tags** : <mark style="color:$danger;">`True`</mark> (optional)

![](<../.gitbook/assets/Click on the (22) (1) (1) (1).png>)

### Step 5: Test and Deploy

* Save and activate the Screen Flow.
* Add it to a **Lightning Page** and on the configuration page of the flow, tick the "**Pass record ID into this variable** " checkbox.
* Validate that selected images are duplicated to the chosen WOLIs, with tags preserved if configured.

![](<../.gitbook/assets/Click on the (23) (1) (2) (1).png>)

![](<../.gitbook/assets/Template (5) (1) (1) (1).png>)

## Demo: Work Order to WOLI Flow Example

On the Word Order record <mark style="color:$danger;">**`00000001`**</mark>, we have two related Work Order Line Item. Images are selected, and the 'next' button is pressed.

![](<../.gitbook/assets/Click on the (24) (1) (1).png>)

The next screen shows the data table displaying all the related WOLIs by their WOLI Number. Choose the WOLI record(s) on which the previously selected images will be duplicated and click next. The images have been successfully duplicated.

![](<../.gitbook/assets/Click on the (25) (1) (1).png>)

The images and tags appear on the previously selected WOLI record's album.

![](<../.gitbook/assets/Click on the (26) (1) (1).png>)
