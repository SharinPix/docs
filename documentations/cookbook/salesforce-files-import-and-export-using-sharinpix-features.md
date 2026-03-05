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

# Salesforce Files Import and Export using SharinPix Features

This article demonstrates how to use SharinPix features to import and export Salesforce files to SharinPix.

## Import Salesforce files onto a SharinPix Album

The SharinPix package included the **SharinPix Import Files** component which allows users to import Salesforce files onto a SharinPix album.

For more information on how to configure and use the **SharinPix Import Files** component, refer to the following article: **SharinPix Import Files** component

[SharinPix Import Files](../lightning-web-component/sharinpix-import-files.md)

{% hint style="warning" %}
**Note:**

* For non-admin users to be able to use the SharinPix Import Files component, the **SharinPix Lightning Components** permission set should be assigned to them.
* If you cannot find the **SharinPix Import Files** component or **SharinPix Lightning Components** permission set within your organization, kindly [upgrade your SharinPix package](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange).
{% endhint %}

## Export Images from SharinPix to Salesforce files (Developer-Oriented)

To export images from SharinPix to Salesforce files, you can make use of Salesforce automations such as Flows or Triggers to retrieve the image URLs and using the same to upload the images as Salesforce files.

To retrieve SharinPix image URLs, you can:

* Use one of our _Utils_ Apex methods. The SharinPix package includes Apex methods that you can easily use on your side to retrieve image URLs. These Apex methods are documented in the following documentation: [Utils methods](utils-methods.md)
* Use the [SharinPix Image Sync feature](../image-sync/setup-sharinpix-image-sync.md). When activated, this feature will automatically generate SharinPix Image records for each image uploaded on the configured object. The corresponding image URLs are generated and stored in the SharinPix Image records.
