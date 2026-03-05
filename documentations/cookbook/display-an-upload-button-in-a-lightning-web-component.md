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

# Display an upload button in a Lightning Web Component

This article explains how to embed the [SharinPix Upload Button](../lightning-web-component/sharinpix-upload-button.md) component in a Lightning Web Component.

## Call the SharinPix Upload Button (LWC) inside Lightning Web Component

The sample code below demonstrates how to call the **SharinPix Upload Button (LWC)** inside the markup of a Lightning Web Component.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<LightningComponentBundle xmlns="http://soap.sforce.com/2006/04/metadata">
    <apiVersion>60.0</apiVersion>
    <isExposed>true</isExposed>
    <targets>
        <target>lightning__RecordPage</target>
    </targets>
</LightningComponentBundle>
```

```html
<template>
  <sharinpix-sharinpix-upload
      album-id={recordId}
      label={label}
      component-id={componentId}
      enable-action={enableAction}
      enable-image-sync={enableImageSync}
      enable-toast={enableToast}
      permission-id={permissionId}
      auto-tags={autoTags}>
  </sharinpix-sharinpix-upload>
</template>
```

```javascript
import { LightningElement, api } from 'lwc';

export default class UploadButton extends LightningElement {
    @api recordId
    label = // label
    componentId = // componentId
    enableAction = // enableAction
    enableImageSync = // enableImageSync
    enableToast = // enableToast
    permissionId = // permission Name or Id
    autoTags = // autoTags
    
    //The parameters are explained in more details below.
}
```

{% hint style="warning" %}
**Note:**

* The parameter's value can be modified as per your use-case.
* The **SharinPixPermissionName** highlighted above should be replaced with the name or Id of a [SharinPix Permission](../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md).
{% endhint %}

The table below details the parameters available of the SharinPix Upload Button (LWC).

| Parameter       | Type    | Description                                                                                                                                                                                                                                                               |
| --------------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| albumId         | String  | Corresponds to the Salesforce record ID (album ID) to which the photos should be uploaded. This parameter is <mark style="color:$danger;">**mandatory**</mark>.                                                                                                           |
| label           | String  | Used to configure the button label.                                                                                                                                                                                                                                       |
| componentId     | String  | Takes the user-defined component ID as value to identify this component when using multiple components.                                                                                                                                                                   |
| enableAction    | Boolean | Enables the [Tag Action](../features/working-with-tags/tag-action.md) feature on the upload button                                                                                                                                                                        |
| enableImageSync | Boolean | Enables the [Image Sync](../image-sync/what-are-the-uses-of-image-sync.md) feature on the upload button.                                                                                                                                                                  |
| enableToast     | Boolean | Enables toast on successful image upload.                                                                                                                                                                                                                                 |
| permissionId    | String  | Includes the Salesforce record ID or Name of a [SharinPix Permission record](../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md) which can be created to control access rights for the _SharinPix Upload Button_ component. |
| autoTags        | String  | Used to pass one or more tags to be automatically applied on files uploaded using the \_SharinPix Upload Button \_component. If multiple auto-tags are needed, they should be delimited by a semi-colon. Example: TagA;TagB;TagC                                          |
