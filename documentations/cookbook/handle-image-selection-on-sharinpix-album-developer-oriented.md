# Handle Image Selection on SharinPix Album (Developer-Oriented)

## Overview

The `updateAlbumSelection` method lets you handle image selection within the SharinPix Album Component without requiring manual user interaction.&#x20;

{% hint style="warning" %}
**Prerequisites**

Before implementing it, ensure your Salesforce environment meets the following requirements:

* **Package Version:**\
  Ensure you have the **latest SharinPix Package** installed. Follow this [guide](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to upgrade your SharinPix Managed Package to the latest version.
* **Permissions:**\
  Users must have the **SharinPix Lightning Components** permission set assigned. For more information on permission sets, check [SharinPix Permission Sets](https://docs.sharinpix.com/documentation/access-and-security/sharinpix-permission-sets).
{% endhint %}

## Method Signature

`updateAlbumSelection(imageIds)`

## **Parameters**

<table><thead><tr><th width="137.140625">Parameter</th><th width="162.125">Type</th><th>Description</th></tr></thead><tbody><tr><td>imageIds </td><td>Array of String </td><td><p>An array of SharinPix Public Image IDs to select. </p><p><em><strong>Note: To clear all current selections, pass an empty array.</strong></em></p></td></tr></tbody></table>

## Setup

To use the updateAlbumSelection method, you must implement the SharinPix Album (LWC) as a child component within your own custom Lightning Web Component.

The recommended approach is to create an 'Album Wrapper' component that encapsulates the SharinPix Album (LWC).

Sample Album Wrapper component:&#x20;

```html
<!-- albumWrapper.html -->
<template>
        <c-album
            lwc:ref="album"
            record-id={recordId}
            album-id={albumId}
            height={height}>
        </c-album>
</template>
```

```javascript
// albumWrapper.js
import { LightningElement, api } from 'lwc'
export default class AlbumWrapper extends LightningElement {
    @api recordId
    @api albumId
    @api height = 500
    // Define the IDs of the images you want to select.
    samplePublicImageIds = ['id1', 'id2', 'id3'] //You can also pass an empty array [] to clear all selections

    selectImages() {
        this.refs.album?.updateAlbumSelection(this.samplePublicImageIds)
    }
}

```

When `updateAlbumSelection(this.samplePublicImageIds)` is invoked, the images with the IDs that were passed in the array will be selected in the SharinPix Album (LWC).

{% hint style="warning" %}
**Important Notes**

* **Parameter Validation:** Only valid string SharinPix Image Public IDs are processed. Non-string values and empty strings are automatically filtered.&#x20;
* **Null handling:** Passing null is treated as an empty array.
{% endhint %}
