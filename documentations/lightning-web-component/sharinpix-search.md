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

# SharinPix Search

The **SharinPix Search** component permits to search for all images corresponding to records available in a report.

![](<../.gitbook/assets/SearchBuilderrecord (1) (1) (1).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used on:

* Community Builder
* Page Builder
* Desktop
* Mobile
* In Flows (but not in Field Service Mobile Flow)
* In your own Lightning Component development
{% endhint %}

{% hint style="warning" %}
**Note:**

If you encounter the error: **Error: Malformed JSON: Expected '\[' at the beginning of List/Set** when configuring the component within **Salesforce Community** , please see the article below:

[I got the error 'Error: Malformed JSON: Expected '\[' at the beginning of List/Set' when configuring the SharinPix Search on COmmunity. What should I do?](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/i-got-the-error-error-malformed-json-expected-at-the-beginning-of-list-set-when-configuring-the-shar)
{% endhint %}

## Getting Started

To use the SharinPix Search component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/image (3) (2) (1).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

![](<../.gitbook/assets/Screenshot from 2024-06-18 14-52-51 (1) (1) (1).png>)

* **Report ID:** Used to specify the report ID containing required the record IDs.
* **Report Parameters:** Used to specify the parameters to be passed to the report. The value entered should be an array in JSON format. To filter the current record, use the parameter {recordId} as the filter value. The example that follows demonstrates report parameters that query all images uploaded to the current Account record based on a report on Account: **\[{"column":"ACCOUNT\_ID","operator":"equals","value":"{recordId}"}].** Another example demonstrates report parameters that query all images uploaded to a custom object '**Candidate' record** based on a report on Object Candidate: **\[{"column":"CUST\_ID","operator":"equals","value":"{recordId}"}]**.

{% hint style="warning" %}
**Note:**

For more information on how to write report parameters, click on the following link: \
[How to open the Image Search page with a Report Id and Filters dynamically](../features/search-images/how-to-open-the-image-search-page-with-a-report-id-and-filters-dynamically.md)

If you still have problems getting the report parameters, please get in touch with [SharinPix Support](https://docs.sharinpix.com/m/documentation/l/1637081-how-to-contact-support).
{% endhint %}

* **Tag Operator:** Used to specify the operator to be used when applying multiple tags to filter the search. The values available for this field are **OR** and **AND**. When using **OR** , the search will return the images having any of the tags specified whereas using **AND** in the search will return images having all of the tags specified.
* **Tag Names (JSON):** Used to specify the tags to be applied to filter the search with only SharinPix Images containing the provided tag names. The value entered in this field should be an array in JSON format, for example, \["Paris","London"]. **Note**: If you are not using this parameter within **Salesforce Community**, add an empty square bracket, that is, **\[]**, instead.
* **Excluded Tags (JSON):** Used to specify the tags to be applied to filter the search with tags to be excluded (Any SharinPix Image containing the provided tag names will be excluded even if the tag is specified in the _Tag Names (JSON_) parameter). The value entered in this field should be an array in JSON format, for example, \["Paris","London"]. **Note:** If you are not using this parameter within **Salesforce Community**, add an empty square bracket, that is, \[], instead.
* **Affixes (JSON):** Used to specify affixes or suffixes to be added to the object IDs found in the report. The value entered in this field should be an array in JSON format, for example, \["Paris","London"]. Here, LONDON is used as the prefix and PARIS as the suffix. **Note**: If you are not using this parameter within **Salesforce Community,** add an empty square bracket, that is, **\[],** instead.
* **Height**: Used to specify the height of the component. The default value is **500** (px).
* **Custom Permission ID or Name:** Used to specify the Id or Name of custom permission.
* **Use Fullscreen Image Viewer:** Used to enable/disable the option to view images in full screen.
* **Component ID:** Used to specify the component IDs to be matched by add-on components on a page.
* **Enable Image Sync:** Used to enable/disable Image Sync. **Note:** Image Sync is checked by default on the SharinPix Album component. Additional steps are required to get this feature fully working on your Salesforce object. Please refer to this article to complete the Image Sync setup: [_Setup SharinPix Image Sync_](../image-sync/setup-sharinpix-image-sync.md). **Note**: The SharinPix Search component supports the [_SharinPix Collage feature_](../features/search-images/using-collage-on-search-component.md) _. To trigger an_[ _Image Sync_](../image-sync/what-are-the-uses-of-image-sync.md) _for a collage, the **Enable Image Sync** checkbox should be checked._
* **Auto Refresh View:** Used to enable/disable the option to reload the view. **Note:** This option is not supported in Salesforce Community. When configured within a Community, it is advised to disable this option on the component.

## Demo

{% hint style="success" %}
**Tip:**

* The SharinPix package includes the report **SharinPix Sample Account Report** (see picture below) which contains all Account records.
* To use the Sharinpix Search, it does not require [Image Sync](../image-sync/what-is-sharinpix-image-sync.md).
{% endhint %}

![](<../.gitbook/assets/screenshot-enterprise-computing-8320-dev-ed.lightning.force.com-2020.05.15-15_49_48 (1) (1) (1).png>)

The picture below depicts the SharinPix Search component's results when using the report **SharinPix Sample Account Report**.

![](<../.gitbook/assets/Searchbuilderrecord2 (1) (1) (1).png>)

{% hint style="success" %}
**Tips:**

Below are some useful links about the SharinPix Search component's feature that you may refer to:

* [Using the SharinPix Search component on a record page.](../features/main-integration/using-on-lightning-with-sharinpix-search-lightning-component-dev-skills-required.md)
* [Creating a report to be used in the SharinPix Search component.](../features/search-images/how-to-create-a-report-for-image-search.md)
* [Using your personalized Search in a Salesforce Flow (Admin-Oriented)](../features/search-images/using-your-personalized-search.md)
{% endhint %}
