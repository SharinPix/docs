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

# SharinPix Plan to Album

{% hint style="warning" %}
**Note:**

This component is dependent on the SharinPix Plan component.
{% endhint %}

{% hint style="info" %}
The **SharinPix Plan To Album** component permits to extract a Plan as an image and save it in a specific SharinPix Album.
{% endhint %}

![](<../.gitbook/assets/image (17) (1) (1) (1).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used on:

* On Page Builder
* On Desktop
* On Mobile
* Salesforce Community _(Note: Community users need access to the SharinPix object,**SharinPix Plan Items** , to use the SharinPix Plan to Album component)_
{% endhint %}

## Getting Started

To use the SharinPix Plan to Album component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

![](<../.gitbook/assets/image (18) (1) (1) (1).png>)

## Lightning Component Parameters

![](<../.gitbook/assets/image (19) (1) (1) (1).png>)

* **Generate Plan Button Label:** Used to specify the button's label. The default value is **Export Plan to Album**.
* **Record ID:** The record Id of the current record.
* **Plan Data Source Record Id:** Id of Record containing the field specified by Plan Data Field API Name from where the plan data is to be retrieved. Leave blank to use the current record Id.
* **Plan Data Field API Name:** API name of the field containing plan-related information. Current Record Id will be used if Plan Data Source Id is not specified. This field needs to be a Long Text Area.
* **SharinPix Plan Setting Name:** SharinPix Plan Setting Name configured for the related plan component.
* **Marker label field API Name:** Field API Name of the marker title to be displayed on the Plan.
* **Album ID:** Used to specify the album ID to which images will be saved. To use the current record ID, leave this field blank.
* **Export Plan in Full View:** If checked, the whole plan will be exported as an image instead of the current zoomed-in view on the SharinPix Plan Component.
* **Component Id:** Component ID to be matched by the SharinPix Album component on the page.

{% hint style="info" %}
**Note:**

* For the [SharinPix Image Sync](../image-sync/setup-sharinpix-image-sync.md) feature to be activated on the destination album when the image is exported from the Plan to Album component, you should specify a value for the **Component ID** parameter on the **Plan to Album** component and use the same value for the **SharinPix Album**'s **Component ID** parameter.
* To capture the plan including marker labels, the **Marker label field API Name** should be specified. Omitting the Marker Label field API Name will only capture the plan including the markers but excluding the marker labels.
{% endhint %}

## Demo

The picture below shows a plan in the SharinPix Plan component

![](<../.gitbook/assets/planToAlbum4 (1) (1) (1).png>)

The picture below shows the target album on an Account record **before** using the SharinPix Plan To Album component:

![](<../.gitbook/assets/image (20) (1) (1).png>)

To export an image of a plan from the SharinPix Plan component to the target album, click on the button **Export Plan to Album**.

The picture below shows the result in the target album **after** using the SharinPix Plan To Album component:

![](<../.gitbook/assets/image (21) (2) (1).png>)

If the option **Export Plan in Full View is enabled,** the image will be in full view as shown in the picture below.

![](<../.gitbook/assets/image (22) (1) (1) (1).png>)
