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
  actions:
    visible: true
---

# SharinPix Media Import Feature

## Overview

The SharinPix Media Import feature allows users to easily transfer any media content, including images, documents, and other files, from Salesforce into SharinPix. Media sources can be Content Documents, Attachments, or even external sources with a public URL.

After the import is completed, you will see the files in the [SharinPix Album](../lightning-web-component/sharinpix-album.md) component on the Salesforce records.

## Key Components

* **SharinPix Media Import Object**: This custom Salesforce object stores details of media files to be imported into SharinPix.
* **Automated Sync**: Once a SharinPix Media Import record is inserted, an automated batch process begins synchronizing the media files with SharinPix.

{% hint style="danger" %}
<mark style="color:red;">**Warning:**</mark>

This feature is designed for single or small-volume imports.

Large import volumes can trigger internal safety limits, resulting in a temporary block for your organization. Please follow our volume guidelines to ensure uninterrupted service.

* High-Volume Imports: If you need to process large batches, please follow the guidance in [this documentation](https://docs.sharinpix.com/documentation/access-and-security/sharinpix-imports-requirements#required-import-information) for the correct workflow.
* Need guidance? [Contact SharinPix Support](../getting-started-with-sharinpix/how-to-contact-support.md) before proceeding.
{% endhint %}

## Prerequisites

* The permission set **SharinPix Media Import** must be assigned to users who will use this feature.
* To use this feature, you will need to grant API access to SharinPix. Link: [Basic Setup - Step 2 - Register your Salesforce organization to SharinPix](../getting-started-with-sharinpix/basic-setup/basic-setup-step-2-register-your-salesforce-organization-to-sharinpix.md)
* SharinPix Package Version **1.310 or later** is required to access this feature. Refer to [this documentation](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to update your package.

## Steps to Use the SharinPix Media Import Feature

**1. Creating SharinPix Media Import Records**

You can create records in the SharinPix Media Imports object manually or through various automated tools and methods, such as:

**Manual Creation**

1. Navigate to the **SharinPix Media Imports** tab in Salesforce.
2. Click on **New**.
3. Fill in the required details, including the file to be imported or the media URL.
4. Click **Save**.

**Using Data Loader**

1. Open **Data Loader** and log in with your Salesforce credentials.
2. Select the **Insert** operation.
3. Choose the **SharinPix Media Imports** object.
4. Upload a CSV file containing the details of the media records.
5. Map the CSV fields to Salesforce fields.
6. Click **Next** and then **Finish** to start the import process.

**Using Salesforce Inspector Extension**

1. Install the Salesforce Inspector extension for Chrome.
2. Open Salesforce and navigate to the **SharinPix Media Imports** object.
3. Use the extension to import data by pasting CSV data or JSON format.

**2. Automating the Import Process with Custom Flows**

Salesforce Flows can be used to automate the creation of SharinPix Media Import records:

1. Go to **Setup** and navigate to **Flows**.
2. Create a new **Flow** and select the type (e.g., Record-Triggered Flow).
3. Define the criteria for when the Flow should trigger (e.g., upon creation or update of a record).
4. Add an **Action** to create a record in the SharinPix Media Imports object.
5. Map the necessary fields from the triggering record to the SharinPix Media Imports object, including the file URL if applicable.
6. Save and activate the Flow.

## Field Mapping

* **sharinpix\_\_AlbumId\_\_c**: he Salesforce record ID on which the media will be added to in SharinPix
* **sharinpix\_\_AttachmentId\_\_c**: Id of Attachment record
* **sharinpix\_\_ContentDocumentId\_\_c**: Id of the Content Document record
* **sharinpix\_\_Url\_\_c**: Public Url of media to be imported
* **sharinpix\_\_Tags\_\_c**: Auto tag the medias. If more than one tag is applied, a semi-colon (;) is used as a delimiter.
* **sharinpix\_\_CallbackRequired\_\_c**: Check this if you want SharinPix to update the Media Import record with the ImageId.

{% hint style="danger" %}
**Note** :

* Only one of the fields **sharinpix\_\_AttachmentId\_\_c**, **sharinpix\_\_ContentDocumentId\_\_c**, or **sharinpix\_\_Url\_\_c** can be filled at a time.
* Additionally, **sharinpix\_\_AlbumId\_\_c** is required.
{% endhint %}

![media\_import\_sample](<../.gitbook/assets/image (59).png>)

## Automated Synchronization

Once SharinPix Media Import records are inserted, a batch job automatically starts syncing them with SharinPix. The batch job handles the transfer of media files, ensuring they are uploaded to SharinPix without manual intervention.

You can monitor the progress and status of the batch jobs by navigating to the **Apex Jobs** page in Salesforce Setup.

If the field **sharinpix\_\_CallbackRequired\_\_c** is checked, the **sharinpix\_\_ImageId\_\_c** will be populated with the SharinPix Image Public Id.

{% hint style="info" %}
Failed imports requiring manual intervention are **Import Errors**. Choose their recipients in [Notification settings](../access-and-security/notification-settings.md).
{% endhint %}

{% hint style="warning" %}
This feature only works when creating a SharinPix Media Import record. Editing the record afterwards won't trigger the sync.
{% endhint %}

## Image Sync functionality

You can activate the Image Sync functionality if you would like any media transferred to have their corresponding SharinPix Image records. You can follow the documentation here on how to set up a Webhook: [Image Sync for pictures uploaded via SharinPix Mobile App](../image-sync/image-sync-for-pictures-uploaded-via-sharinpix-mobile-app.md)

{% hint style="info" %}
For further assistance or queries, please contact the [SharinPix support team](mailto:support@sharinpix.com).
{% endhint %}
