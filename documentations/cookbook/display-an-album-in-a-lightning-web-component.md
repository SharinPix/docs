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

# Display an Album in a Lightning Web Component

In this article, you will learn how to call the component SharinPix Album (LWC) as a child in another parent component.

## Call SharinPix Album (LWC) inside Lightning Web Component

* The sample code below shows how to call the **SharinPix Album (LWC)** inside the markup of a Lightning Web Component.

```html
<template>
    <sharinpix-album record-id={recordId} enable-image-sync={enableImageSync} 
    height={height} fullscreen-allowed={fullscreenAllowed} 
    enable-action={enableAction} enable-toast={enableToast} 
    permission-id={permissionId} tags={tags} auto-tags={autoTags} 
    component-id={componentId}></sharinpix-album>
</template>
```

```javascript
import { LightningElement, api } from 'lwc';

export default class ParentAlbum extends LightningElement {
    @api recordId
    enableImageSync = true
    height = 600
    fullscreenAllowed = true
    enableAction = true
    enableToast = true
    permissionId = 'SharinPixPermissionName'
    tags = 'tag1;tag2'
    autoTags = 'autoTag1'
    componentId = 'album'
}
```

{% hint style="warning" %}
**Note:**

* The parameter's value can be modified as per your use-case.
* The _**SharinPixPermissionName**_ highlighted above should be replaced with the name or Id of a [SharinPix Permission](../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md).
{% endhint %}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<LightningComponentBundle xmlns="http://soap.sforce.com/2006/04/metadata">
    <apiVersion>63.0</apiVersion>  //Add recent API version
    <isExposed>true</isExposed>
    <targets>
        <target>lightning__RecordPage</target>
    </targets>
</LightningComponentBundle>
```
