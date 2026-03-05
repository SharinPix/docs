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

# Using on Salesforce flow (Developer skills required)

{% hint style="info" %}
This demo only serves as a broad example on how **SharinPix** be used in Salesforce Flow. You are not restricted to using **Contacts** or **Accounts** objects. To get a technical grasp on how the VisualFlow was implemented, please head over to the Cookbook section: [Create Contacts from an Account using VisualFlow](../../cookbook/create-contacts-from-an-account-using-visualflow.md)
{% endhint %}

In this demo, we will see how it possible to create one or more **Contacts** starting from a particular **Account** record and upload a profile picture corresponding to the **SharinPix Album** for each newly-created **Contact** record.

## Overview

To implement the present demo, we will reference a **Visual Flow** inside a **Visualforce Page**. The following steps provide a high-level overview of the objective we want to achieve in this demo:

**Visual Flow:**

1. Look up the **Id** of Account Record from which the Screen Flow was launched.
2. Display the input fields to so as to create the **Contact** record(s) while using the **Account Id** (collected in the previous step) in order to create a **LookUp relationship** between the **Account** and the recently-created **Contact** record(s).
3. Display the **SharinPix Album** for the user to upload the profile picture of the newly-created **Contact(s).**

**Visualforce Page:**

4\. Reference the newly-created **Flow** inside a **Visualforce Page.**

**Account Page-Layout:**

5\. Create a **custom action** to launch the **Visualforce Page** created in the previous step.

6\. Add the custom action to the Account's **page-layout.**

## Integrating SharinPix with the VisualFlow

In order to be able to use the SharinPix Album alongside a VisualFlow, we references both the SharinPix Album and the VisualFlow inside a custom Visualforce Page.

The code snippet below shows how both the VisualFlow and SharinPix Album is referenced inside a Visualforce Page.

```html
<apex:page StandardController="Account" extensions="FlowController">
<flow:interview name="SharinPix_Account_Contacts" interview="{! sp_flow }" finishLocation="/{!$CurrentPage.parameters.Id}"></flow:interview>
<sharinpix:SharinPix height="400px" rendered="{! sp_flow.RenderAlbum == true }" parameters="{'Id': '{! sp_flow.ContactId }', 'abilities':{'{! sp_flow.ContactId }':{'Access': {'image_upload':true,'image_list':true,'see':true,'image_delete':true}}}}" />	
</apex:page>
```

* The code snippet below references a **VisualFlow**.

```html
<flow:interview name="SharinPix_Account_Contacts" interview="{! sp_flow }" finishLocation="/{!$CurrentPage.parameters.Id}"></flow:interview>
```

* As it can bee seen above, the flow element has the following properties:
  * **Name:** the name of the flow created.
  * **Interview:** a reference to the flow interview as declared in the Apex Controller of the current Visualforce Page. This reference will allow us to access the variables found in the flow.
* The code snippet below references the **SharinPix Visualforce Component**.

```html
<sharinpix:SharinPix height="400px" rendered="{! sp_flow.RenderAlbum == true }" parameters="{'Id': '{! sp_flow.ContactId }', 'abilities':{'{! sp_flow.ContactId }':{'Access': {'image_upload':true,'image_list':true,'see':true,'image_delete':true}}}}" />	
```

As it can be seen in the above code snippet, the SharinPix Visualforce Component has the properties:

* **height:** corresponds to the height of the SharinPix Album as rendered inside the SharinPix Visualforce Component.
* **rendered:** corresponds to the Boolean flag that dictates whether the SharinPix Visualforce Component is to be rendered, hence displayed on the Visualforce Page.
* **parameters:** corresponds to the set of SharinPix Abilities enabled/disabled on the SharinPix Album.

The code snippet below shows the implementation of the Apex Class used as the controller for the Visualforce Page implemented above.

```apex
public class FlowController {
    public Flow.Interview.SharinPix_Account_Contacts sp_flow { get; set; }
    public FlowController (ApexPages.StandardController controller) {}
}
```

The declared variable **sp\_flow** represents the reference for the Flow. It will allow us to access the variables present within the flow.

For example, within the **SharinPix Visualforce Component** referenced inside the Visualforce Page, shown above, uses the Flow reference to access the following variables:

* **sp\_flow.RenderAlbum:** The **RenderAlbum** variable is used to dictate whether the SharinPix Visualforce Component is to be displayed or not on the Visualforce Page.
* **sp\_flow.ContactId:** The **ContactId** variable is used to associate the SharinPix Album to the relevant Contact Record.
