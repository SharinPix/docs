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

# Auto Tags

The SharinPix **Auto-tag** feature is used to automatically tag images with one or more specified tags upon image upload.

This feature can be configured through the following methods:

* [Through the SharinPix Global Settings](auto-tags.md#setting-up-the-auto-tag-through-the-sharinpix-global-settings)
* [Using a SharinPix Permission record](auto-tags.md#setting-up-the-auto-tag-using-a-sharinpix-permission-record)
* [Through SharinPix Parameters](auto-tags.md#implementing-the-auto-tag-feature-in-sharinpix-parameters-developer-oriented)
* [Using SharinPix Tokens or URLs](auto-tags.md#configuring-the-auto-tag-feature-using-sharinpix-tokens-or-urls)

## Setting up the Auto-tag through the SharinPix Global Settings

The Auto-tag feature can be configured using the SharinPix Global Settings as follows:

* Open the SharinPix Global Settings. To do so, from App Launcher, search for **SharinPix Settings**, then click on the button **Go to administration dashboard** to open the global settings
* On the SharinPix Global Settings, select **Settings** from the top menu bar, then click on the button labeled as **Edit Organization**
* Next, under the **Tags** section, select the tag to be automatically applied to all newly uploaded images from the list next to the field labeled as **Auto-tag**

![](<../../.gitbook/assets/image (27) (4).png>)

* Click on **Update Organization** when done to save your changes

{% hint style="warning" %}
**Note:**

* By configuring the Auto-tag feature in the global settings, the tag used will be applied to all images uploaded to standard SharinPix albums unless a customized SharinPix permission has been assigned to specific albums
* Only one tag can be selected when configuring the Auto-tag feature in the SharinPix Global Settings
* If the Auto-tag drop-down menu is empty, it may be because you have no tags available yet
* Tags having the **public** attribute set to **true** will not appear in the drop-down as these are used for sharing images outside of Salesforce
{% endhint %}

## Setting up the Auto-tag using a SharinPix Permission record

The Auto-tag feature can be configured using a SharinPix Permission record as follows:

* From App Launcher, type **SharinPix Permission**
* Click on the button **New** to create a new SharinPix Permission record
* Next, under the **Tags** section, enter the tag(s) to be automatically applied to newly uploaded images for the field labeled as **Auto-tag**. If you intend to use multiple tags here, use the semicolon symbol (";") to separate them as follows:

![](../../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.05.03-21_26_00.png)

* Select the other desired abilities if needed and click **Save** when done
* Next, assign the created SharinPix Permission record to the desired SharinPix standard album or your custom album

{% hint style="success" %}
**Tip:**

For more information about the SharinPix Permission object and how it is configured, refer to the following article:

[SharinPix Permission object](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md)
{% endhint %}

{% hint style="warning" %}
**Note:**

* Using a SharinPix Permission record, multiple tags can be applied in the Auto-tag feature. The tags should be separated by semicolons
* The value(s) inserted for the Auto-tag field should correspond to the tags' **Name**
{% endhint %}

## Implementing the Auto-tag feature in SharinPix Parameters (Developer-Oriented)

The Auto-tag feature can also be implemented using SharinPix Parameters for customized albums.

The code snippet that follows demonstrates how the Auto-tag feature has been implemented for a customized SharinPix Album in a Visualforce page using the SharinPix Parameters:

```html
<sharinpix:SharinPix parameters="{'abilities':{'{!CASESAFEID($CurrentPage.Parameters.Id)}':{'Tags':{'Land':{'fr':'Terre','en':'Land'},'Sea':{'fr':'Mer','en':'Sea'}},'Access':{'image_upload':true,'image_tag':true,'image_list':true,'see':true}},'tags':{'auto_tag':'Sea'}},'Id':'{!CASESAFEID($CurrentPage.Parameters.Id)}'}"/>
```

In the above example, the tag, **Sea** , is being used as the auto-tag.

You can also specify multiple tags in the SharinPix Permission as follows:

```html
<sharinpix:SharinPix parameters="{'abilities':{'{!CASESAFEID($CurrentPage.Parameters.Id)}':{'Tags':{'Land':{'fr':'Terre','en':'Land'},'Sea':{'fr':'Mer','en':'Sea'}},'Access':{'image_upload':true,'image_tag':true,'image_list':true,'see':true}},'tags':{'auto_tag':['Sea','River']}},'Id':'{!CASESAFEID($CurrentPage.Parameters.Id)}'}"/>
```

{% hint style="warning" %}
**Note:**

* The value(s) inserted for the Auto-tag field should correspond to the tags' **Name**.
{% endhint %}

## Configuring the Auto-tag feature using SharinPix Tokens or URLs

The Auto-tag feature can be configured to be used within the SharinPix Mobile app. This is done by appending the **auto\_tags** parameter to the URL as shown below:

<mark style="color:$danger;">`auto_tags=automatic;manual`</mark>

* The auto\_tags parameter takes as value(s) the tag(s) **Name(s)**
* If multiple tags are being used, their names should be separated by semicolons ";"
