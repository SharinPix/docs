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

# Extract Parameters from URL to display Album

It is possible to extract the **SharinPix URL** which is assigned as a parameter.

* [Get Parameters inside a Visualforce Page](extract-parameters-from-url-to-display-album.md#get-parameters-inside-a-visualforce-page)
* [Get Parameters inside Lightning Component](extract-parameters-from-url-to-display-album.md#get-parameters-inside-lightning-component)

## Structure of the SharinPix URL

```
https://app.sharinpix.com/pagelayout/album_id?token=token_value
```

From the above sample,

* The whole **SharinPix URL** is passed as a parameter **url.**
* Within the **SharinPix URL,**
  * <mark style="color:$danger;">`album_id`</mark> represents the actual value of the album Id.
  * <mark style="color:$danger;">`token_value`</mark> represents the actual token value.

## Get Parameters inside a Visualforce Page

* The code snippet below shows how it is possible to use a merge-field to extract the **url** parameter inside a **Visualforce Page.**

```apex
{!$CurrentPage.parameters.url}
```

* The code snippet below shows that the extracted **url** parameter value can be assigned to the **src** attribute of an **iframe** html element for displaying the **SharinPix Album**.

```apex
<apex:page >
    <iframe src="{!$CurrentPage.parameters.url}&annotate={! $CurrentPage.Parameters.annotation}" width="100%" height="500px">
    </iframe>
</apex:page>
```

## Get Parameters inside Lightning Component

* To extract the value of the parameter **url** inside the markup of a Lightning Component, you will need to define an <mark style="color:$danger;">`aura:attribute`</mark> and assign its **name** attribute with the name of the parameter (in this case, the parameter is **url**). The type of the <mark style="color:$danger;">`aura:attribute`</mark> is <mark style="color:$danger;">`String`</mark>.

```html
<aura:attribute name="url" type="String"></aura:attribute>
```

* To use the value of the extracted value, you will need to use the merge-field as shown below.

```apex
{! v.url }
```

* The sample code below shows how the extracted value is used to display the **SharinPix Album** inside the markup of a Lightning Component.

```html
<aura:application >
	<aura:attribute name="token" type="String"></aura:attribute>
    <iframe src="{! v.token }" width="100%" height="500px"></iframe>
</aura:application>
```

## Retrieve SharinPix Parameters from a personalized URL

In the following example it will be shown how it is possible to launch SharinPix with the use of a **personalized URL**. To achieve the latter objective, we will accomplish the following steps:

* Obtain a SharinPix URL
* Create a Visualforce Page that will display the SharinPix Album.
* Create a custom link that will open the Visualforce Page in a new tab.

### Obtain a SharinPix URL

* The **SharinPix URL** should be in the following form:

```
https://app.sharinpix.com/pagelayout/album_id?token=token_value
```

* <mark style="color:$danger;">`album_id`</mark> - corresponds the Salesforce Id of a specific record.
* <mark style="color:$danger;">`token_value`</mark> - the **SharinPix Token**. Refer to the following article to learn how to generate a **SharinPix Token** : [SharinPix automatic token generation (Admin Friendly)](../mobile-app/sharinpix-automatic-mobile-upload-token-generation-admin-friendly.md)

### Create a Visualforce Page for SharinPix Album

The following code corresponds to the Visualforce Page that will be implemented. (In this case, this Visualforce Page is named **SharinPixParamsDemo**)**.**

```html
<apex:page >
    <iframe src="{! $CurrentPage.Parameters.url }&fullscreen={! $CurrentPage.Parameters.fullscreen }" width="100%" height="500px" style="border: 0;"></iframe>
</apex:page>
```

The syntax <mark style="color:$danger;">`{! $CurrentPage.Parameters.fullscreen }`</mark>and <mark style="color:$danger;">`{! $CurrentPage.Parameters.url }`</mark> are used to extract the **fullscreen** and url **parameter values respectively.**

### Create a custom link

* Head over to an Object of your choice and create a new custom link.
* Its **Display Type** is **Detail Page Link.**
* Its **Behaviour** is **Display in new window.**
* Its **Content Source** is **URL.**
* In the **content editor** of the custom link, insert the following URL:

<mark style="color:$danger;">`/apex/SharinPixParamsDemo?fullscreen=true`</mark><mark style="color:$danger;">&</mark><mark style="color:$danger;">`url=https://app.sharinpix.com/pagelayout/album_id?token=token_value&`</mark>

The above URL starts with **/apex/SharinPixParamsDemo** which indicates that it will access a Visualforce Page named **SharinPixParamsDemo(**&#x61;s implemented previousl&#x79;**)** found in the current Salesforce organization. The **url** parameter value takes the **SharinPix URL** to display the **SharinPix Album.** The **fullscreen** parameter value is an arbitrary value (In this case, it is "**true**").

{% hint style="success" %}
**Personalize your own URL**: The parameter **fullscreen** that takes as value **true** is only meant for illustrative purposes only. You can supply any parameters with the corresponding values of your own choice and use them in the Visualforce Page.
{% endhint %}

* **Next step**: Add the custom link to the page-layout of the object.
* Upon clicking on the custom link, the Visualforce Page displays the SharinPix Album and is able to read the parameter value for both **url** and **fullscreen.**
