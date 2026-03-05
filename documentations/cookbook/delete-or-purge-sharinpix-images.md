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

# Delete or Purge SharinPix Images

The SharinPix Invocable methods provide data privacy and security control over SharinPix Album and Images, ensuring compliance with GDPR.

GDPR also known as General Data Protection Regulation is a legal framework that sets guidelines for the collection and processing of personal information from individuals who live in and outside of the European Union (EU).

These methods offer two options:

1. Permanently purge the album and its images, completely removing all data,
2. Or perform a soft delete, which removes the content from active use while allowing for potential recovery.

The SharinPix Apex methods are as follows:

* [DeleteSharinPixImageAutomation](delete-or-purge-sharinpix-images.md#deletesharinpiximageautomation)
* [DeleteSharinPixAlbumAutomation](delete-or-purge-sharinpix-images.md#deletesharinpixalbumautomation)

{% hint style="warning" %}
**Note:**

The GDPR methods are decorated as @InvocableMethod, meaning that they can be used in Salesforce automation like Flows.

Both Invocable methods should run asynchronously because both callouts (to SharinPix) and DML operations (deletion of SharinPix Image records) are being done.
{% endhint %}

## DeleteSharinPixImageAutomation

The **DeleteSharinPixImageAutomation** allows Salesforce Admin to delete a list of images with the option to purge. Deletion of images can also be performed in bulk, which prevents exceeding Salesforce governor limits.

The Invocable class takes two parameters:

* **Image Id(s)** - List of SharinPix Image Public Ids to be deleted. Tip: You can leverage the [SharinPix Image Sync feature](../image-sync/setup-sharinpix-image-sync.md) to retrieve the image IDs.
* **Purge (Optional)** - If set to _true_ , SharinPix Image(s) will be **PERMANENTLY** deleted. If set to _false_ , SharinPix images will be kept in the trash for a period of 30 days before being **PERMANENTLY** deleted. Default value is _false_

![](<../.gitbook/assets/1_1 (3) (1).png>)

The above flow is an example of a flow used to delete all images on all Accounts having the status (a custom field) set to "_Close"_. This will trigger the Flow to delete all images tagged as "_delete"_ on the Account, as shown below.

![](<../.gitbook/assets/2_2 (2) (1).png>)

After retrieving the list of SharinPix images to be deleted, the record collection is looped through to assign the Image Public ID to a new collection.

![](<../.gitbook/assets/3_3 (1) (1).png>)

After building a list of SharinPix Image Public IDs, it can be provided to the invocable action **DeleteSharinPixImagesAutomation**. Below the purge parameter value is taken from a field named "Purge Images" on the triggering Account. This Flow will trigger and delete images on all triggering Account tagged as "_delete_".

![](<../.gitbook/assets/4_4 (1) (1).png>)

{% hint style="warning" %}
**Note:**

Please be aware that when the **DeleteSharinPixImageAutomation** is invoked within a Salesforce Flow, and the flow is triggered in bulk (e.g., multiple Account records are updated simultaneously), the list of SharinPix Image IDs provided as parameters can contain a maximum of 100 images with the <mark style="color:$danger;">`purge = true`</mark> setting and an additional 100 images with the <mark style="color:$danger;">`purge = false`</mark> setting. This limitation arises because the list of image IDs is processed in two separate batches—one for images marked for permanent deletion (purge) and another for those marked for soft deletion. If either batch exceeds 100 images, the deletion process will not proceed for that batch, though it will not impact the processing of the other batch.
{% endhint %}

## DeleteSharinPixAlbumAutomation

The **DeleteSharinPixImageAutomation** allows Salesforce Admin to delete a SharinPix Album with the option to purge.

The Invocable class takes two parameters:

* **Album Id** - Album ID of which all SharinPix Images will be deleted.
* **Purge (Optional)** - If set to _true_ , SharinPix Image(s) will be **PERMANENTLY** deleted. If set to _false_ , SharinPix images will be kept in the trash for a period of 30 days before being **PERMANENTLY** deleted. Default value is _false_

![](<../.gitbook/assets/5_5 (2).png>)

The above flow will be triggered automatically whenever the Account Status is set to "Expire". Once this status change occurs, the Flow is triggered to delete the entire SharinPix Album, including all associated files contained within it, ensuring that the album is fully removed from the Salesforce organization without any residual content remaining (if <mark style="color:$danger;">`purge = true`</mark>), else all images on the SharinPix Album will be moved to trash for a period of 30 days.

![](<../.gitbook/assets/image (64) (2).png>)

The Invocable class takes as parameters the triggering SharinPix Album's ID which in this case is the Account's ID and purge parameter value is taken from a field named "Purge Album"

## Need help to build your flow to delete SharinPix Images and Album?

The visual experts are here to help. Just send an email to [support@sharinpix.com](mailto:info@sharinpix.com) to get some help so we can explain you how we can deliver services through our experts to assist you on that duty!
