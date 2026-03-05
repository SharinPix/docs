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

# Troubleshoot Common Image Sync Issues

{% hint style="info" %}
The most common configurations mistakes when setting up Image Sync are:

* [Enable Image Sync option not checked for the SharinPix Album component](troubleshoot-common-image-sync-issues.md#verify-if-image-sync-option-has-been-enabled-for-the-sharinpix-album-component)
* [Object API names not entered correctly in the SharinPix Image Sync custom metadata](troubleshoot-common-image-sync-issues.md#check-the-sharinpix-image-sync-configuration)
* [Incorrect configuration of Webhook used for Image Sync (this applies for cases in which uploads are performed via the SharinPix mobile app)](troubleshoot-common-image-sync-issues.md#image-sync-not-working-when-using-salesforce-mobile-app)

This article outlines the solutions regarding the points listed above as well as other common SharinPix Image Sync issues.
{% endhint %}

## SharinPix Image records not updated/created

### Verify if Image Sync option has been enabled for the SharinPix Album component

The first thing to verify is whether the option **Enable Image Sync** has been applied to the SharinPix Album component on which images are being uploaded.

If you need help to verify this part, please refer to the following article:

[Enable Image Sync for Lightning](enable-image-sync-for-lightning.md)

### Verify that only one Image Sync entry is created per object

If the problem still persists, verify if only one Image Sync setting has been created for your object.

For this verification, review the Image Sync entries in the **SharinPix Sync Setting** custom metadata and ensure that only one entry has been created for your object.

If two or more Image Sync entries are created for one object, the Image Sync feature will not work as expected.

{% hint style="success" %}
**Tip:**

In such cases, you may also encounter the following error message:

**No SharinPix Sync Setting found for the object&#x20;**_**\<Object name will appear here>**_
{% endhint %}

#### Revise the SharinPix Image Sync configuration <a href="#check-the-sharinpix-image-sync-configuration" id="check-the-sharinpix-image-sync-configuration"></a>

If the problem still persists after enabling the **Enable Image Sync** option and ensuring that **only one Image Sync entry has been created for the object**. You should first:

* Verify if you have SharinPix Image Sync settings for the same Salesforce object. If that's the case, delete the extra setting.
* Verify if any two or more SharinPix Image Sync settings have the same object API name in the Parent Object Name field. If that is the case, this means that such Image Sync settings belong to the same object. The extra settings should be deleted.
* Verify if the Image Sync setting for the object is **active**:

<figure><img src="../.gitbook/assets/test (16).png" alt=""><figcaption></figcaption></figure>

If the **Active** field is not available on the custom setting layout, follow the steps below to add the same:

* Go to the **Custom Metadata Types** page and click on **SharinPix Sync Setting**.
* Scroll down to the _Page Layouts_ section and click on **Edit** next to **SharinPix Sync Setting Layout**.
* Add the **Active** field on the layout and save.
* Then go to the object's Image Sync settings and verify that the **Active field** is checked.

If the above does not apply to your organization or if the issue still persists after performing the steps, it is advisable to go through the SharinPix image Sync configuration process again for the object on which the SharinPix Image records are not being updated/created and check if you have not missed anything there.

{% hint style="warning" %}
**Note:**

One thing that needs to be revised carefully here is whether the values entered for the  **Parent Object Name** and **Parent Field Name** have been entered correctly.

* The field **Parent Object Name** refers to the **object's API Name**. In case you are using a custom object, you should ensure that the API name is correctly entered. For example, if you are using a custom object named **My Custom Object**, the value to be entered for the field **Parent Object Name** will be **My\_Custom\_Object\_\_c**.

&#x20;    To find an object's API Name:

&#x20;      1\. From Setup, go on Object Manager

&#x20;      2\. Search and select the required object

&#x20;      3\. Once the object is selected, go to the Details section. The object's API name is available from the field **API Name**.

<br>

* The field **Parent Field Name** on the other hand refers to the **field name** of the **lookup relationship**. You should ensure that the value entered for the field **Parent Field Name** matches the corresponding **field name** value in the lookup relationship.&#x20;

&#x20;    To find the field name:

&#x20;      1\. From Setup, go on Object Manager

&#x20;      2\. Search and select the required object

&#x20;      3\. Once object is selected, go on the **Fields & Relationships** section. The field name will be available from there.
{% endhint %}

{% hint style="success" %}
**Tip:**

To cross-check if you have configured the Image Sync properly, you can refer to the steps presented in the following article: [Setup SharinPix Image Sync](setup-sharinpix-image-sync.md)
{% endhint %}

In case you are using a Visualforce page embedding the SharinPix Visualforce component, make sure that the **SharinPix Image Sync component** is also included on the page.

The SharinPix Image Sync Component's syntax is as follows:

```html
<sharinpix:ImageSync recordId="{! $CurrentPage.Parameters.Id }"/>
```

{% hint style="success" %}
**Tip:**

For more information about how to implement a Visualforce page embedding the **SharinPix Visualforce component** and the **SharinPix Image Sync componen**t, click on the following link:

[The SharinPix Image Sync Component](enable-image-sync-for-classic.md#the-sharinpix-image-sync-component)
{% endhint %}

### SharinPix Image records not updated/created for some users <a href="#sharinpix-image-records-not-updated-created-for-some-users" id="sharinpix-image-records-not-updated-created-for-some-users"></a>

If SharinPix Image records are not being created/updated for some users, check if the Permission Set named **SharinPix Image Sync Permission** has been assigned to those users.

This Permission Set ensures that users are given proper access rights to the SharinPix Image object.

### SharinPix Image records not updated/created for Community users <a href="#sharinpix-image-records-not-updated-created-for-community-users" id="sharinpix-image-records-not-updated-created-for-community-users"></a>

In case, SharinPix Image records are not being updated/created for Community users, check if the Permission Set named **SharinPix Image Sync for Community Users** has been assigned to those users.

This Permission Set ensures that Community users are given proper access rights to the SharinPix Image object.

{% hint style="success" %}
**Tip:**

For more details about Community users' access to SharinPix, please refer to the following article:

[SharinPix Community users access rights](../access-and-security/sharinpix-community-users-access-rights.md)
{% endhint %}

### Image Sync not working when uploading photos via the SharinPix mobile app <a href="#image-sync-not-working-when-using-salesforce-mobile-app" id="image-sync-not-working-when-using-salesforce-mobile-app"></a>

If the SharinPix Image Sync is not working as expected when uploading images via the **SharinPix mobile app**, please refer to the following article which details the configurations that need to be looked into:

[Image Sync not working when using SharinPix mobile app to upload photos. What should I do?](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/image-sync-not-working-when-using-sharinpix-mobile-app-to-upload-photos-what-should-i-do)

### Process Builders or Validation Rules preventing creation of SharinPix Image records <a href="#process-builders-or-validation-rules-preventing-creation-of-sharinpix-image-records" id="process-builders-or-validation-rules-preventing-creation-of-sharinpix-image-records"></a>

It can happen that Process Builders or Validation Rules block the creation of SharinPix Image records. If you have Process Builders or Validation Rules on the object you intend to upload the images, it is advisable to perform some investigations and check if they are blocking the SharinPix Image Sync.
