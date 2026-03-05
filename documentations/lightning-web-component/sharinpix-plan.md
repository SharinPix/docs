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

# SharinPix Plan

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
* In Flows (but not in Field Service Mobile Flow)
* In Salesforce Community
* In your own Lightning Component development
{% endhint %}

To use the SharinPix Plan component, simply drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/image (16) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Configurations

<figure><img src="../.gitbook/assets/image (17) (3).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th>Field</th><th width="200.27734375">API Name</th><th width="77.88671875">Type</th><th>Description</th></tr></thead><tbody><tr><td>Plan Data Source Id<br></td><td>planDataSourceId<br></td><td>String</td><td>Id of Record containing the field specified by Plan Data Field API Name from where the plan data is to be retrieved. Leave blank to use data from Background Image Album record.<br></td></tr><tr><td>Plan Data Field API Name</td><td>planDataFieldApiName<br></td><td>String</td><td><mark style="color:red;">(Mandatory field)</mark><br>API name of the field containing plan-related information. Current Record Id will be used if Plan Data Source Id is not specified. This field needs to be a Long Text Area.<br></td></tr><tr><td>Background Image Album Field API Name<br></td><td>recordIdFieldApiName<br></td><td>String</td><td>API name of the field containing the record ID for the image to be displayed, with respect to the Background Image Tag set. Defaults to Record Id.<br></td></tr><tr><td>Background Image Tag<br></td><td>tag<br></td><td>String</td><td>Tag name to be used to identify an image from the album set by Background Image Album Field API Name or otherwise, the current record’s album.<br></td></tr><tr><td>Height</td><td>height</td><td>Integer</td><td>The height of the component (in px). Default: 500<br></td></tr><tr><td>Mode</td><td>mode</td><td>Picklist</td><td>Mode of the plan. Possible values are: <strong>readonly</strong>, <strong>geocode</strong>, and <strong>edit</strong><br></td></tr><tr><td>SharinPix Plan Setting Name</td><td>settingName</td><td>String</td><td>SharinPix Plan Setting Name configured for this plan component. More information on how to configure the SharinPix Plan Setting below.<br></td></tr><tr><td>Display Lookup Field<br></td><td>relatedItemsFieldApiName<br></td><td>String</td><td>Field API Name of the Lookup relationship to filter SharinPix Plan Items to be displayed based on record Id.<br></td></tr><tr><td>Field Set Name</td><td>fieldSet</td><td>String</td><td>Field Set Name which will decide the fields to be displayed on the plan item record. The default field set will be used if left blank. Only available in <strong>edit</strong> mode.<br></td></tr><tr><td>Marker label field API Name</td><td>markerlabelFieldApiName</td><td>String</td><td>Field API Name of the marker title to be displayed on the Plan.<br></td></tr><tr><td>Enable Toast</td><td>enableToast</td><td>Boolean</td><td>Show toast when a plan is successfully updated<br></td></tr><tr><td>Custom Permission ID or Name</td><td>permissionId</td><td>String<br></td><td>Name or ID of a SharinPix Permission object.<br></td></tr><tr><td>Component Id</td><td>componentId<br></td><td>String</td><td>(Optional)<br>Component Id to identify the SharinPix Plan component (useful when more than 1 component is present on the same page)<br></td></tr><tr><td>Parent Plan Data Field API Name</td><td>parentPlanDataFieldApiName</td><td>String<br></td><td><mark style="color:red;">(Deprecated)</mark><br>This field is deprecated and should be ignored.</td></tr></tbody></table>

## SharinPix Plan Setting

SharinPix Plan Setting will be used to determine the relationship between the object and the SharinPix Plan Item. The SharinPix Plan Item is the object that will save the annotations, such as Marker, CircleMarker, Polygon, Line, and Rectangle.

Before you create the SharinPix Plan Setting, you need to create the relationship between your main object and the SharinPix Plan Item. Create a field of type lookup on the SharinPix Plan Item object. Save the field API name as it will be used for the configuration later.

Steps to configure the SharinPix Plan Item:

1. Go to Salesforce Setup
2. Open Custom Metadata Types
3. Click on Manage Records for **SharinPix Plan Setting** Custom metadata type
4. Insert a label and name
5. Insert your object API name
6. Insert the field API name of the field recently created on the SharinPix Plan Item
7. In the section Plan Item Setting, add a Default color.
8. Check Auto Number (_if you want the auto numbering option to appear on the marker_).

Once the plan setting has been configured, assign the permission set **SharinPix Plan** to all users needing access to the Plan component. This permission set gives users the necessary access to the SharinPix Plan Item object and fields.

{% hint style="warning" %}
**Note:**

The auto-numbering will appear only on the new SharinPix Plan Item (marker) created in version 1.247 or later. SharinPix Plan Item created before version **1.247** will not have an auto-numbering option.
{% endhint %}

![](<../.gitbook/assets/plan_CM (1) (1) (1).png>)

## Final Setup

Now open your Lightning Builder for a record page. Add the appropriate configurations based on your business rule.

### Example

![preview plan](<../.gitbook/assets/Selection_014 (1) (1) (1).png>)
