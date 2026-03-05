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

# Integrating SharinPix with Salesforce Mobile App using Lightning Action and Visualforce

![](<../.gitbook/assets/sf_mobile (1).png>)

The present section will enumerate the steps required in order for the SharinPix mobile application to be launched from the Salesforce Mobile App.

The objective of this demo is to launch the SharinPix Mobile app from the Salesforce mobile application using  a custom action and the **Case** object.

## Implementation of the Visualforce Page

The **Action Type** of the **Custom Action** will be **Custom Visualforce Page**,  within which a link will be used to launch the SharinPix Mobile App.

The code snippet implementing the Visualforce Page is shown below:

```html
<apex:page StandardController="Case" showHeader="false" sidebar="false" applyBodyTag="false">
    <a href="sharinpix://upload?token={!Case.SharinPix_Token__c}">Take Pictures with Camera</a><br/>
    <a href="sharinpix://upload?token={!Case.SharinPix_Token__c}&mode=roll">Choose Pictures from the Roll</a><br/>
    <a href="sharinpix://upload?token={!Case.SharinPix_Token__c}&camera=true&confirmation=true">Take Pictures with Camera and Confirmation</a> 
</apex:page>
```

The merge-field **{! Case.SharinPix\_Token\_\_c }** references the **SharinPix Token** field containing the token value on the current of the current **Case** record.

{% hint style="success" %}
Note: If you want this Visualforce Page to work on any Salesforce Object, you will need to replace **Case** with the **API Name** of the your object.
{% endhint %}

The Visualforce Page is saved as **SharinPixOpenMobileFromCase.**

### Add action <a href="#add-action" id="add-action"></a>

* Go to **Setup**, then to **Object Manager** to access the **Case** object.
* Select the **Buttons, Links and Actions** section.
* Click on **New Action.**
* In the picklist **Action Type**, select **Custom Visualforce.**
* In the picklist **Visualforce Page**, select the Visualforce Page created above.
* In the field **Height**, enter 500px.
* In the field **Label,** enter **Take Pictures.**
* &#x20;In the field **Icon,** select **ActionSharinPixAlbum** icon (which comes with the installed **SharinPix Package**).&#x20;

<figure><img src="../.gitbook/assets/test (28).png" alt=""><figcaption></figcaption></figure>

* Click on **Save** when done.

## Add action to page-layout of Case

* Go to the **Case Page Layouts** section.
* Select the layout which is relevant to your context.
* From **Mobile & Lightning Actions,** drag and drop **Take Pictures** inside the **Salesforce mobile and Lightning Experience Actions** section.
* Click on **Save** when done.
* Access a **Case** record on the **Salesforce Mobile App.** The custom action **Take Pictures** can be found on the **Action Bar** as shown in the image below.

<figure><img src="../.gitbook/assets/test (5).jpg" alt=""><figcaption></figcaption></figure>

* Tap on **Take Pictures**. The Visualforce Page **SharinPixOpenMobileAppFromCase**, as implemented previously, is displayed.
* Each link corresponds to a SharinPix URL that will launch a particular camera mode:
  * Launch Camera only.
  * Launch Image Roll only.
  * Launch Camera and enable confirmation prompt.
* Refer to the article on **Launch SharinPix Offline Mobile App** section for a more in-depth view into the different camera modes available in the SharinPix offline mobile app.

<figure><img src="../.gitbook/assets/test (6).jpg" alt=""><figcaption></figcaption></figure>

If you tap on the **Take Pictures with Camera** link, the SharinPix mobile App will launch and the camera view will open by default.
