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

# SharinPix Custom Upload Button

{% hint style="info" %}
This component is only available for developers only. It is not available on the Lightning App Builder. Only available on aura framework.
{% endhint %}

![](<../.gitbook/assets/image (16) (2) (1).png>)

The purpose of this component is to allow image upload from a lightning button which is fully customisable in term user interface using the Lightning Design System framework.

```html
<aura:component implements="force:hasRecordId,flexipage:availableForAllPageTypes">
    <aura:attribute name="recordId" type="Id" />
    <aura:attribute name="permissionId" type="String"/>

    <!-- SharinPix Custom Upload Button start -->
    <sharinpix:UploadButtonCustom recordId="{!v.recordId}" permissionId="{!v.permissionId}" enableToast="true" enableImageSync="true" enableAction="true" height="500" refreshView="true" fileExtensions=".jpg,.heic,.pdf">
        <span class="slds-button slds-button_brand">
            <lightning:icon size="x-small" iconName="utility:copy_to_clipboard" variant="inverse"></lightning:icon>
            <span>&nbsp;&nbsp;Upload Photos</span>
        </span>
    </sharinpix:UploadButtonCustom>
    <!-- SharinPix Custom Upload Button end -->
</aura:component>
```

The content of the button needs to start with a \<span> instead of an anchor \<a> or \<button> tag.

| Attribute               | Description                                                                                                         | Data Type              |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| recordId                | Reference the recordId on which the images will be uploaded to                                                      | Salesforce Id          |
| <p>permissionId<br></p> | <p>Record ID or Name of the SharinPix Permission object to be applied on the Custom Upload Button component<br></p> | <p>String<br></p>      |
| enableToast             | A toast will appear on upload completed                                                                             | Boolean                |
| height                  | Height of the SharinPix Album component which displays the upload progression                                       | integer (default: 400) |
| enableImageSync         | Activate image sync functionality                                                                                   | Boolean                |
| enableAction            | Activate Tag action functionality                                                                                   | Boolean                |
| refreshView             | Refresh various component on the lightning record when image sync or tag action has been performed                  | Boolean                |
| fileExtensions          | File extensions that will be accepted only for upload.                                                              | String                 |

{% hint style="warning" %}
Link to LDS: [https://www.lightningdesignsystem.com/components/buttons/](https://www.lightningdesignsystem.com/components/buttons/)

Note: you need to use a span instead of the link or button version for the component to work.
{% endhint %}
