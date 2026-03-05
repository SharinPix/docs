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

# Using on Lightning with "SharinPix Search" Lightning Component (Dev Skills Required)

The present article will show how to use the SharinPix Search Lightning Component in Salesforce.

The Lightning Component **SharinPix Search** is already installed with the SharinPix package. In the present context, we will use this component on the record page of the Account object.

* Access the **Lightning App Builder:**
  * The attribute **Report ID** corresponds to the **Report** record that references one or more records from which to display the relevant images.
  * The attribute **Tag Operator** possesses two values: **OR** and **AND.** Those values are logical operators that ensure that the tags are either both present or one of them is at-least present on the image search result.
  * The attribute **Tag Names** correspond to the set of tags in JSON format that will be used as a search filter by the attribute **Tag Operator**. Example: \["Paris", "London"]
  * The attribute **Affixes** are prefixes and suffixes to add to the object IDs returned by the report. Value should be an array in JSON format. Leave blank for none. Example: \["london\_+", "+\_paris"]
  * The **Height** attribute defines the search result area measured in pixels(px).

![](<../../.gitbook/assets/image (63).png>)

* The screenshot demonstrates how the SharinPix Search Lightning Component appears on a record Page of an Account Object.

![](../../.gitbook/assets/sharinpix_search.png)
