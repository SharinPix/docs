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

# SharinPix LWC Custom Upload Button (Developer-Oriented)

## Overview

The **SharinPix Custom Upload Button LWC** is a Lightning Web Component component designed to create a customized button that uploads images to SharinPix from a Salesforce record. It is intended for use as a child component in your own custom Lightning Web Component (the “parent”), where you pass in a button layout (or any UI) via a `<span>` or other HTML wrapper element.

![](<../.gitbook/assets/Untitled design (1) (1) (2).png>)

{% hint style="warning" %}
**Prerequisites:**

* SharinPix Package **Verison 1.329** is needed to get access to this component. Refer to [this documentation](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to update your package.
* Make sure to have the [**SharinPix Lightning Components**](../access-and-security/sharinpix-permission-sets.md) permission set assigned to be able to use this component.
* Make sure that **Lightning Web Security** is enabled in your org. More details here: [Lightning Web Security FAQ](https://help.salesforce.com/s/articleView?id=000392327\&type=1)
{% endhint %}

## Getting Started

This component uploads images using a Lightning button, which is fully customizable using the Lightning Design System framework.

### Usage Example (Parent LWC)

Below is a simple **parent LWC** demonstrating how to use the SharinPix Custom Upload Button

#### HTML (Parent LWC)

```html
    <template>
        <div style="display: inline-block;">
            <sharinpix-upload-button-custom-lwc
                record-id={recordId}
                permission-id={permissionId}
                enable-toast={enableToast}
                enable-image-sync={enableImageSync}
                enable-action={enableAction}
                file-extensions={fileExtensions}>
    
                <span class="slds-button slds-button_brand">
                    <lightning-icon size="x-small" icon-name="utility:upload" variant="inverse"></lightning-icon>
                    <span>&nbsp;&nbsp;Custom Upload Photos</span>
                </span>
            </sharinpix-upload-button-custom-lwc>
        </div>
    </template>
```

**Warning:**

You must start the component’s slot content with a `<span>` (rather than a `<button>` or `<a>`) for compatibility reasons.

#### JavaScript (Parent LWC)

```javascript
    import { LightningElement, api } from 'lwc';
    
    export default class UploadButtonCustomParent extends LightningElement {
        @api recordId;
        @api permissionId;
        @api enableToast = false;
        @api enableImageSync = true;
        @api enableAction = false;
        @api fileExtensions; // e.g., '.jpg,.png,.pdf'
    }
```

### Attributes

| Attribute       | Description                                                                | Data Type |
| --------------- | -------------------------------------------------------------------------- | --------- |
| recordId        | Reference to the Salesforce record where images will be uploaded.          | Id        |
| permissionId    | SharinPix Permission record ID or Name to be applied on the component.     | String    |
| enableToast     | If `true`, shows a toast message after uploads complete.                   | Boolean   |
| enableImageSync | Activates the image sync functionality.                                    | Boolean   |
| enableAction    | Activates the Tag Action functionality.                                    | Boolean   |
| fileExtensions  | Restricts the file types that can be uploaded (e.g., `.jpg, .heic, .pdf`). | String    |

{% hint style="success" %}
**Tip:**

For styling references and button design, refer to the [Lightning Design System Buttons](https://www.lightningdesignsystem.com/components/buttons/) documentation.
{% endhint %}
