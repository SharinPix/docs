# SharinPix Generate PDF on Form Response

## Overview

The **SharinPix Generate PDF on Form Response** component is a customizable button designed specifically for use on the **Form Response** record page. It enables users to instantly generate a PDF version of the current form response with a single click.

Users can configure the button to, either open the generated form response PDF in a new tab for immediate viewing or import it into a [SharinPix Album](sharinpix-album-lwc.md)—either on the current Form Response record or its parent record.

![](<../.gitbook/assets/DOC SF - 1920 x 360 (1920 x 600 px) (1920 x 240 px) (1) (1) (1) (1).png>)

{% hint style="info" %}
**Info**

This feature is only available on **Lightning Experience**.\
It can only be used on the **Form Response record page** , including:

* On Page Builder
* On Desktop
* On Mobile
* In your own Lightning Component development

⚠️ This component cannot be used in Flows or Community Builder.
{% endhint %}

{% hint style="warning" %}
**Prerequisites**

* **Permissions:**\
  Users must have the **SharinPix Forms** **Admin** or **SharinPix Forms User** permission set assigned. For more information on these two permission sets, check [_SharinPix Permission sets_](../access-and-security/sharinpix-permission-sets.md).
* **Package Version:**\
  Ensure that SharinPix Package Version 1.355 (or later) is installed.
* A **SharinPix Form Template** is needed beforehand.
{% endhint %}

## Getting Started

To use the SharinPix Generate PDF on Form Response component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

![](../.gitbook/assets/QQQQQ.png)

### Lightning Component Parameters

![](<../.gitbook/assets/DOC SF - 1920 x 360 (1920 x 600 px) (1) (1) (1) (1).png>)

| Parameter                 | Description                                                                                                                                                                                                                              | Default/Notes                        |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ |
| Button Label              | The text displayed on the button that users will click to generate the SharinPix form response PDF.                                                                                                                                      | Default value: Download PDF          |
| Select Action             | This dropdown lets you choose what to do with the generated PDF. You can either open it in a new browser tab, or import it directly into a SharinPix album linked to the same record.                                                    | Default value: Open Pdf in a New Tab |
| Save PDF to Parent Record | When this checkbox is enabled, the generated PDF will be stored in the SharinPix Album associated with the parent record object. (e.g., `Account`) Else, the PDF will be stored in the album linked to the current Form Response record. | Default: Unchecked                   |

### Demo: Fire Safety Inspection Example

The image below shows the **SharinPix Generate PDF on Form Response** component configured in the Salesforce App Builder, with properties filled:

* **Select Action** set to _Import to SharinPix album_
* _Enable_ **Save PDF to Parent Record** checkbox

![](<../.gitbook/assets/DOC SF - 1920 x 360 (1920 x 600 px) (2) (1) (1) (1).png>)

Assuming at least one form response exists for the _Fire Safety Inspection_ form template, clicking the button will generate a PDF of the current form response and automatically import it into the SharinPix album associated with its _parent record_.

To confirm that the feature works as expected, navigate to the parent record as illustrated in **Step 2** in the image below. **Step 3** shows the generated PDF stored within the **SharinPix album** linked to that parent record.

![](<../.gitbook/assets/DOC SF - 1920 x 360 (1920 x 600 px) (1920 x 1200 px) (2) (1) (1).png>)

![](<../.gitbook/assets/DOC SF - 1920 x 360 (1920 x 600 px) (1920 x 1200 px) (1) (1) (1) (1).png>)

{% hint style="danger" %}
**Alert**

The import to the SharinPix album will **only** occur once the **PDF URL** for the form response is **available**. For example, if the SharinPix form response includes images that are still uploading, the PDF may not be immediately generated.
{% endhint %}
