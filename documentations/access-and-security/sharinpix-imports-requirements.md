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

# SharinPix Imports Requirements

This article outlines the requirements for the following SharinPix operations:

* [Image import](sharinpix-imports-requirements.md#image-import)
* [Tag migration](sharinpix-imports-requirements.md#tag-migration)
* [Tag bulk deletion](sharinpix-imports-requirements.md#tag-bulk-deletion)

## Required Import Information

Mass image imports and tag migrations are recommended to be performed by the SharinPix team.

For such imports, kindly contact the SharinPix support team first at [**support@sharinpix.com**](mailto:support@sharinpix.com) with:

1. A description of the import you want to achieve.
2. The number of records/ images/tags included.
3. The average image size, if applicable.

Once the import is validated by our team, you will need to provide the following additional information:

* Your organization ID.
* A CSV file including all your import data. Please refer to the [Image Import](sharinpix-imports-requirements.md#image-import), [Tag Migration](sharinpix-imports-requirements.md#tag-migration), [Tag Bulk](sharinpix-imports-requirements.md#tag-bulk-deletion) Deletion sections for more information on the CSV file format in each case.
* Your organization's API limit.
* Kindly also state if [tag action](../features/working-with-tags/tag-action.md) or [image sync](../image-sync/setup-sharinpix-image-sync.md) should be launched after the import.

{% hint style="info" %}
Failed imports requiring manual intervention are **Import Errors**. Choose their recipients in [Notification settings](notification-settings.md).
{% endhint %}

{% hint style="warning" %}
**Note:**

For small-volume imports, the SharinPix package already includes Apex methods you can easily run on your end. Some of these methods are:

* **uploadAttachment**: Uploads Salesforce attachments to SharinPix albums.
* **uploadContentDocument**: Uploads Salesforce ContentDocuments to SharinPix albums.
* **uploadFromUrl**: Uploads an image to SharinPix using a URL.

For more information on how to call the above methods and other SharinPix import Apex methods, please refer to the following article: [Utils methods](../cookbook/utils-methods.md).

⚠️ Large import volumes can trigger internal safety limits, resulting in a temporary block for your organization. Please follow our volume guidelines to ensure uninterrupted service.
{% endhint %}

## Image Import

### Image Import from Storage to SharinPix

For image imports from your storage (for example, Amazon S3) to SharinPix, the CSV file should include the following columns:

* **album\_id**: The _album\_id_ column should contain the 18-digit record ID on which you want the image to be uploaded.
* **url**: The _url_ column should contain the public image URLs as they appear in your storage.
* **tags**: The _tags_ column should contain the tag or tags to be applied to each image. If two or more tags should be applied, please ensure that all tags are added in a single cell and separated by commas as follows: <mark style="color:$danger;">`tag1,tag2,tag3`</mark>

### Image Import from Salesforce Content Document to SharinPix

For image imports from Salesforce files to SharinPix, the CSV file should include the following columns:

* **album\_id**: The _album\_id_ column should contain the 18-digit record IDs on which you want the image to be uploaded.
* **content\_document\_id**: The _content\_document\_id_ column should contain the 18-digit Content Document record IDs
* **tags**: The _tags_ column should contain the tag or tags to be applied to each image. If two or more tags should be applied, please ensure that all tags are added in a single cell and separated by commas as follows: <mark style="color:$danger;">`tag1,tag2,tag3`</mark>

## Tag Migration

For tag migrations from one organization to another, the CSV file should include the following columns:

* **Id**: Should contain the IDs of the tags to be migrated.
* **Name**: Should contain the tags' technical name.
* **Label**: Should contain the tags' labels.
* **Listed**: Should indicate whether the tags should be available for use in your organization.\
  _&#x4E;ote_: This column can only contain true or false (boolean).
* **Visible**: Should indicate whether the tags should be visible to everyone in your organization.\
  _&#x4E;ote_: This column can only contain true or false (boolean).
* **Color**: Should contain the tags' label color in Hex format.
* **Public**: Should indicate whether the tag should be public (shared externally). This is only used for tags used to share images externally. It is excluded in most cases.\
  _&#x4E;ote:_ _This column can only contain true or false (boolean)._
* **Allow download**: Should indicate whether file downloading is permitted when the tag is public.\
  _&#x4E;ote:_ _This column can only contain true or false (boolean)._

{% hint style="success" %}
**Tip:**

On the [Tags](https://app.sharinpix.com/admin/tags) page of the admin dashboard, a CSV download option is available at the bottom of the page that contains all the tags in your organization, with all the required columns for tag migrations.
{% endhint %}

## Tag Bulk Deletion

For tag bulk deletions, only **Id** column is required, containing the IDs of all tags to be deleted.

{% hint style="success" %}
**Tip:**

Tag IDs can be retrieved by viewing tags from the [Tags page](https://app.sharinpix.com/admin/tags) on the admin dashboard. A CSV download option is available at the bottom of the page that contains all the tags in your organization.
{% endhint %}
