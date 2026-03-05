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

# Automatically move images from Lead record to Opportunity on Lead Conversion

This article demonstrates how to automatically move images from a converted lead record to its corresponding opportunity.

## Overview

SharinPix offers a feature to automatically rename albums during the lead conversion process in Salesforce. Renaming an album means associating all images from the converted lead to the newly created opportunity. This ensures that the associated images remain accessible after the conversion.

This feature can be enabled by configuring a custom metadata type in Salesforce.

## Steps to Enable the Feature

**Prerequisites**

* **System Administrator** access is required to modify metadata settings in Salesforce.
* The SharinPix package must be on the latest versions.

**Instructions**

1. Go to **Setup** in Salesforce
2. In the Quick Find box, type **Custom Metadata Types** and select it.
3. Click on **Manage Records** next to the **SharinPix Bypass**.
4. Edit the **LeadConversion** record, tick the **Active** field, and save the record.

Now that the Active field is checked, when a lead is converted, the lead's album contents will be moved to the opportunity's album.
