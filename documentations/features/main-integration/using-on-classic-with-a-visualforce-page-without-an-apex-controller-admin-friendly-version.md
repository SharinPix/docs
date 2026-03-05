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

# Using on Classic with a Visualforce Page WITHOUT an Apex Controller (Admin Friendly version)

This article demonstrates how to make use of:

1. The [SharinPix Visualforce Component](using-on-classic-with-a-visualforce-page-without-an-apex-controller-admin-friendly-version.md#sharinpix-visualforce-component)
2. The [SharinPix Canvas App](using-on-classic-with-a-visualforce-page-without-an-apex-controller-admin-friendly-version.md#sharinpix-canvas-app)

to display a SharinPix album within the Salesforce Classic Experience without the use of an Apex Controller.

{% hint style="warning" %}
**Note:**

Since Canvas apps have some limitations such as limited number of calls within 24-hour, we strongly recommend the usage of the **SharinPix Visualforce Component** over the **SharinPix Canvas App** for implementations. The SharinPix Canvas App can still be used for testing purposes however.

For more information about Canvas app limitations, please refer to the following link:

[https://developer.salesforce.com/docs/atlas.en-us.platform\_connect.meta/platform\_connect/canvas\_framework\_limits.htm](https://developer.salesforce.com/docs/atlas.en-us.platform_connect.meta/platform_connect/canvas_framework_limits.htm)
{% endhint %}

## SharinPix Visualforce Component

Here's how to reference the **SharinPix Visualforce Component** inside a Visualforce Page as well as defining the **SharinPix Abilities** inline without the use of an Apex Controller. Rather than using an Apex class controller, the values will be referenced inline.

* **In Classic: Setup**
* **Type Visualforce Pages into the QuickFind in the left column.**
* **Click on Visualforce Pages**
* **Click New**

![](<../../.gitbook/assets/image (36) (1).png>)

* Enter a **name** for your Visualforce Page. In this example, we called it **SharinPixVisualforceComponent.**
* **Check the box to specify where you want this VF Page to be seen.**

![](<../../.gitbook/assets/image (37) (1).png>)

{% hint style="info" %}
* The Visualforce Page implemented in the current example is intended to be displayed on the page-layout of the Account object, however if you want to display it on another object, you will need, to assign the right object to the Standard Controller of the Visualforce Page.
{% endhint %}

```html
<apex:page StandardController="Account">
</apex:page>
```

To reference the SharinPix Visualforce Component inside the Visualforce Page, we will use the code snippet below.

* Paste it into the Visualforce Markup window on your new Visualforce Page.
* Click Save.

```html
<apex:page StandardController="Account">
    <sharinpix:SharinPix height="600px" parameters="{'Id': '{!CASESAFEID($CurrentPage.parameters.Id)}', 'abilities':{'{!CASESAFEID($CurrentPage.parameters.Id)}':{'Access': {'image_upload':true,'image_list':true,'see':true,'image_delete':true}}}}"></sharinpix:SharinPix>
</apex:page>
```

The SharinPix Visualforce Component possesses the following attributes:

* **height:** refers to the Height of the **SharinPix Album** in pixel units. In the present example, the height used is **600px.**
* **parameters:** refers to the set of SharinPix Abilities enabled or disabled upon the SharinPix Album.

The following code refers to a merge-field that retrieves the current Id of the record to which the Visualforce Page is added.

```apex
{!$CurrentPage.parameters.Id}
```

{% hint style="info" %}
The next remaining step is to add the Visualforce Page to the page-layout of the Account object:
{% endhint %}

* Go to any record of Type **Account.** Click on **Edit Layout.**

Inside the **Page Layout Editor,** click on the **Visualforce Pages item.**

![](<../../.gitbook/assets/image (38) (1).png>)

Drag and Drop the **SharinPixVisualforceComponent** page onto the desired area of the page-layout. Optionally, you can create a section where you can drop the visualforce page.

As it can be seen in the screenshot below, the **SharinPixVisualforceComponent** page has been added to the section **SharinPix** of the Page-Layout.

![](<../../.gitbook/assets/image (39) (1).png>)

{% hint style="success" %}
**Tip:**

The SharinPix Visualforce component can be modified in such a way to only display an upload button.

For such implementation, refer to the article that follows:

[Implement a SharinPix upload button in a Visualforce page](../../cookbook/implement-a-sharinpix-upload-button-in-a-visualforce-page.md)
{% endhint %}

## SharinPix Canvas App

The present section will lay out the steps on how to reference the **SharinPix Canvas App** inside a Visualforce Page as well as defining the **SharinPix Abilities** inline without the use of an Apex Controller.

{% hint style="info" %}
To know more about **SharinPix Abilities** , refer to the following article: [SharinPix abilities](../../access-and-security/sharinpix-abilities.md)
{% endhint %}

* **In Classic: Setup**
* **Type Visualforce Pages into the QuickFind in the left column.**
* **Click on Visualforce Pages**
* **Click New**

## Create the Visualforce Page

![](<../../.gitbook/assets/image (40) (1).png>)

* Enter a **name** for your Visualforce Page. In this example, we called it **SharinPixVisualforceComponent.**
* **Check the box to specify where you want this VF Page to be seen.**
* **Save**

![](<../../.gitbook/assets/image (41) (1).png>)

* Paste the code below inside the Visualforce Page.

```html
<apex:page standardController="Account">
    <apex:canvasApp developerName="Albums" namespacePrefix="sharinpix" height="500px" 
        parameters="{
           	'Id': '{!$CurrentPage.parameters.Id}',
            abilities:{
            '{!CASESAFEID($CurrentPage.Parameters.Id)}':
                { 
                    Access: {
                        image_upload:true,
                        image_list:true,
                        see:true,
                        image_delete:false
                    }
                }
            }
        }" 
    width="100%"/>
</apex:page>
```

The following parameters are used inside the **SharinPix Canvas App**:

* developerName (value: **Albums**)
* namespacePrefix (value: **sharinpix**)
* height (recommended value: **500px**)
* parameters
* width (value: **100%**)

The value for the **parameters** parameter contains:

* The **Album Id**
* The list of **abilities** allowed on the SharinPix Album.

### Album Id

The **Album Id** corresponds to the record Id of the record within which the Visualforce Page is present. This value is passed through the formula function **CASESAFEID()** which makes sure than the value corresponds to a 18-character record Id.

```apex
'{!CASESAFEID($CurrentPage.Parameters.Id)}'
```

{% hint style="info" %}
_**CASESAFEID**_**() is a formula function that replaces the 15 character ID (case sensitive) with a 18 character ID (case insensitive).**
{% endhint %}

### SharinPix Abilities

The **abilities** allowed on the SharinPix can be defined as shown in the code snippet below.

```json
Access: {
    image_upload:true,
    image_list:true,
    see:true,
    image_delete:false
}
```

The **parameters** variable is then referenced inside the Visualforce Page through the parameter **parameters** as shown in the code snippet below.

```html
<apex:page>
    <apex:canvasApp developerName="Albums" namespacePrefix="SharinPix" parameters="{! parameters }"/>
</apex:page>
```

Once you complete the necessary steps above, you will be able to add the Visualforce Page to the page-layout of a corresponding record.

### Adding Canvas App to Page-Layout

* Go to any record of Type **Account.** Click on the **Quick Access Menu**

![](<../../.gitbook/assets/image (42) (1).png>)

* Click on **Edit Layout.**
* Inside the **Page Layout Editor,** click on the **Visualforce Pages item.**

![](<../../.gitbook/assets/image (43) (1).png>)

* Drag and Drop the Visualforce page created in the steps above onto the desired area of the page-layout. Optionally, you can create a section where you can drop the Visualforce Page.
* **Save.**

In the screenshot below, the SharinPix Album is displayed where the Visualforce Page has been added.

![](<../../.gitbook/assets/image (44) (1).png>)

### Inline Visualforce page example with almost all parameters

Find below a quick example of almost all parameters included:

```html
<apex:page StandardController="Account">
<sharinpix:SharinPix height="500px" parameters="{'abilities':{'{! CASESAFEID($currentPage.parameters.Id) }':{'Access':{'see':true,'image_list':true,'image_upload':true,'image_delete':true,'fullscreen':true,'image_caption':true,'image_tag':true,'image_copy':true,'paste':true,'share':true,'image_duplicate':true,'image_annotate':true,'image_rotate':true,'image_crop':true,'image_download':true},'Tags':{'Before':{'en':'Before'},'After':{'en':'After'}},'Display':{'filename':true,'tags':true,'group_pdf':true,'confirm_delete':true,'annotation_toggle':true,'add_tag_first':true}},'tags':{'read':true,'create':true,'filter_any_of':true}},'Id':'{! CASESAFEID($currentPage.parameters.Id) }'}"></sharinpix:SharinPix>
</apex:page>
```

{% hint style="success" %}
Please note that you can rely on the SharinPix Permission object to generate most of this code by just point and click. Then use the place/name/value generated to insert into your Visualforce code page or even your apex code.

Check it out here: [SharinPix Permission Object](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md)
{% endhint %}
