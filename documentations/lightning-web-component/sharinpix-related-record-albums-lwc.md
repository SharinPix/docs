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

# SharinPix Related Record Albums (LWC)

The **SharinPix Related Record Albums (LWC)** can be used to display a list of related records along with their corresponding SharinPix Albums on the parent record.

This article will cover:

1. [Lightning Component Parameters](sharinpix-related-record-albums-lwc.md#lightning-component-parameters)
2. [Demo](sharinpix-related-record-albums-lwc.md#demo)

![](<../.gitbook/assets/DOC SF - 1920 x 480 (1) (1) (2).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
* On Mobile
* In your own Lightning Component development
* On Community Builder
{% endhint %}

{% hint style="warning" %}
**Note:**

1. An additional configuration is required in the Community Builder to use the **SharinPix Related Record Albums** component in **Salesforce Community (Experience Cloud)**. Check the **Related Object** parameter's description in the **Lightning Component Parameters** section for more details.
2. This component is the Lightning Web Component version of the SharinPix Album. For the Aura version, refer to [this article](sharinpix-related-record-albums.md).
{% endhint %}

## Getting Started

To use the SharinPix Related Record Albums (LWC) component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/Image from Gradio (9).png" alt=""><figcaption></figcaption></figure>

### Lightning Component Parameters

![](<../.gitbook/assets/Click on the (12) (2) (1) (2).png>)

<table><thead><tr><th width="189.53125">Parameter</th><th>Description</th><th>Notes / Examples</th></tr></thead><tbody><tr><td>Related Object</td><td>Specifies the related or child object type to display.</td><td><strong>Salesforce Community usage:</strong> Enter manually in the format: <mark style="color:red;"><code>RelatedObjectApiName#LookupFieldApiName</code></mark><strong>Examples:</strong><br>- Display related Contacts on an Account page: <mark style="color:red;"><code>Contact#AccountId</code></mark><br>- Display a child Account on a parent Account page: <mark style="color:red;"><code>Account#ParentId</code></mark></td></tr><tr><td>Related Object(s)</td><td>Specifies multiple related objects to display in a single component.</td><td>Format: <mark style="color:red;"><code>RelatedObjectApiName#LookupFieldApiName</code></mark> or <mark style="color:red;"><code>RelatedObjectApiName#LookupFieldApiName#RelatedObjectFieldAPIName</code></mark>. Separate multiple objects with a semicolon <mark style="color:red;"><code>;</code></mark>.<br><strong>Examples:</strong><br>- Display related Contacts and Cases on an Account page: <mark style="color:red;"><code>Contact#AccountId;Case#AccountId</code></mark><br>- Display Opportunity and Contract records related to an Account, showing a specific field: <mark style="color:red;"><code>Opportunity#AccountId#Name;Contract#AccountId#ContractNumber</code></mark></td></tr><tr><td>Related Object Field API Name</td><td>Specifies the related record field to display.</td><td>Supports custom label expression: <mark style="color:red;"><code>{!$Label.customLabelName}</code></mark></td></tr><tr><td>Maximum Number of Records</td><td>Sets the maximum number of related records to display.</td><td>- Example: <mark style="color:red;"><code>5</code></mark> → Displays only the first 5 related records.<br>- Use when you want to limit visible results for performance or UI clarity.</td></tr><tr><td>Sort By Field</td><td>Specifies the related object's field API name used for sorting records.</td><td>- Example: <mark style="color:red;"><code>CreatedDate</code></mark> → Sorts by creation date.<br>- Example: <mark style="color:red;"><code>Name</code></mark> → Sorts alphabetically by record name.</td></tr><tr><td>Sort Order</td><td>Specifies sorting order.</td><td>Available values: <strong>Ascending</strong>, <strong>Descending</strong></td></tr><tr><td>Height</td><td>Sets the component’s height.</td><td>- Example: <mark style="color:red;"><code>500px</code></mark> → Component will be 500 pixels high.<br>- Use when you want to control the visible scroll area.</td></tr><tr><td>Use Fullscreen Image Viewer</td><td>Enables/disables fullscreen image viewing.</td><td>- Example: Enabled → Clicking an image opens it in fullscreen.<br>- Disable if fullscreen mode is not desired.</td></tr><tr><td>Fullscreen Viewer Padding</td><td>Adds padding for fullscreen view.</td><td>Default: <mark style="color:red;"><code>90px 0 0 0</code></mark></td></tr><tr><td>Enable Action</td><td>Enables/disables Tag Action.</td><td>Enabled by default on SharinPix Album.<br>More info: <a href="../features/working-with-tags/tag-action.md"><em>Tag Action</em></a> article</td></tr><tr><td>Enable Image Sync</td><td>Enables/disables Image Sync.</td><td>Enabled by default on SharinPix Album.<br>Additional setup required — see <a href="../image-sync/setup-sharinpix-image-sync.md"><em>Setup SharinPix Image Sync</em></a> article</td></tr><tr><td>Enable Toast</td><td>Enables/disables toast message on successful image upload.</td><td>- Example: Enabled → Shows “Image uploaded successfully” after upload.<br>- Disable if you want no success pop-up.</td></tr><tr><td>Auto Refresh View</td><td>Enables/disables automatic view reload.</td><td>- Example: Enabled → List refreshes automatically after an upload.<br>- Disable for manual refresh control.</td></tr><tr><td>Custom Permission ID or Name</td><td>Specifies a custom Sharinpix permission’s ID or Name.</td><td>- Use to restrict certain features to specific user groups using SharinPix Permissions.</td></tr></tbody></table>

## Demo

The example below demonstrates the SharinPix Related Record Albums (LWC) component showing the related Contact's Name and Case's Number on an Account page:

The Related Object(s) field has the following value: <mark style="color:red;">`Contact#AccountId#Name;Case#AccountId#CaseNumber`</mark>

![](<../.gitbook/assets/Click on the (23) (1) (1) (2).png>)

![](<../.gitbook/assets/Click on the (13) (1) (1) (2).png>)
