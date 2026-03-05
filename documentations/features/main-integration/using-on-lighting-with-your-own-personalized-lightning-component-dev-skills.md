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

# Using on Lighting with your own personalized Lightning Component (Dev Skills)

In this article, we will be able to understand the degree of flexibility gained through the use of the SharinPix Lightning Component and how it is possible to personalize its implementation in order to fit a particular use case scenario.

**Note:** The use case scenario as presented in this article is only meant to procure an intuitive sense on what the SharinPix Lightning Component is capable of and offer you the tools to fit this component into your own context.

* [View SharinPix Lightning Component](using-on-lighting-with-your-own-personalized-lightning-component-dev-skills.md#view-sharinpix-lightning-component)
* [Use Case Scenarios](using-on-lighting-with-your-own-personalized-lightning-component-dev-skills.md#use-case-scenario-1)
* [Scenario 1: Change the Album Id and Height of the SharinPix Album dynamically](using-on-lighting-with-your-own-personalized-lightning-component-dev-skills.md#scenario-1-change-the-album-id-and-height-of-the-sharinpix-album-dynamically)
* [Implementation of the Wrapper Component](using-on-lighting-with-your-own-personalized-lightning-component-dev-skills.md#implementation-of-the-wrapper-component)
* [Implementation of SharinPix Lightning Component](using-on-lighting-with-your-own-personalized-lightning-component-dev-skills.md#implementation-of-sharinpix-lightning-component)
* [Implementation of the Wrapper Component](using-on-lighting-with-your-own-personalized-lightning-component-dev-skills.md#implementation-of-the-wrapper-component)
* [Scenario 2: Allow or Deny SharinPix Abilities based on Profile Type](using-on-lighting-with-your-own-personalized-lightning-component-dev-skills.md#scenario-2-allow-or-deny-sharinpix-abilities-based-on-profile-type)
* [Implement the Lightning Wrapper Component](using-on-lighting-with-your-own-personalized-lightning-component-dev-skills.md#implement-the-lightning-wrapper-component)

## View SharinPix Lightning Component

The **SharinPix Package** that you installed from the AppExchange comes with a wide-range of components. However, in our present context we will be using the **SharinPix Lightning Component** that can be viewed by following the subsequent steps.

Go to the **Home Page** of your organization.

1\. Click on the **Setup** icon.

2\. Select **Setup.**

![](<../../.gitbook/assets/image (36) (2).png>)

Once you are on the **Setup Home**:

3\. Enter **Installed Packages in the Quick Find Box.**

4\. Under **Apps**, select **Installed Packages.**

![](<../../.gitbook/assets/image (37) (2).png>)

5\. The **Installed Packages** view will open.

6\. Find the **SharinPix Package** with the name **ImagesManagementBySharinPix**. (Note: the Version Number and other properties might differ for your package.)

![](<../../.gitbook/assets/image (38) (2).png>)

Click on the **ImagesManagementBySharinPix** package name.

7\. The **Package Details** view will open.

8\. Click on the **View Components** button.

![](<../../.gitbook/assets/image (39) (2).png>)

The list of components for the package will appear.

9\. In the **Package Components** section, look for:

10\. **SharinPix** of Type **Lightning Component Bundle**.

![](<../../.gitbook/assets/image (40) (2).png>)

### Use Case Scenarios <a href="#use-case-scenario-1" id="use-case-scenario-1"></a>

The following use case scenario will present **2** possibilities on how to personalize the SharinPix Lightning Component:

* [Scenario 1: Personalize the SharinPix Lightning Component so as to change its Album Id and Height dynamically.](using-on-lighting-with-your-own-personalized-lightning-component-dev-skills.md#scenario-1-change-the-album-id-and-height-of-the-sharinpix-album-dynamically)
* [Scenario 2: Personalize the SharinPix Lightning Component so as to enable or disable its abilities based on the Profile of the current user.](using-on-lighting-with-your-own-personalized-lightning-component-dev-skills.md#scenario-2-allow-or-deny-sharinpix-abilities-based-on-profile-type)

## Scenario 1: Change the Album Id and Height of the SharinPix Album dynamically

In the present scenario, we will see how it is possible to change the values for the parameters:

* **Album Id**&#x20;
* **Height,**

of a SharinPix Lightning Component. This will allow you to personalize:

1. What images are displayed on the SharinPix Album
2. How the SharinPix Album appears

This scenario will be implemented through the use of a **Wrapper Component** within which the **SharinPix Lightning Component** will be referenced along with the corresponding input fields for modifying both **Album Id** and **Height**.

The diagram below provides a high-level view on how this will be achieved.

![](<../../.gitbook/assets/image (41) (2).png>)

## Implementation of SharinPix Lightning Component

The code snippet below shows how the \*\*SharinPix Lightning Component \*\*can be referenced.

The parameters:

* **AlbumId** : identify the album/record from which the images are to be displayed.
* **height:** specify the height of the SharinPix Album.

Note: **<\<album-id>>** and **<\<height>>** are both placeholder values and should be replaced with appropriate ones.

```html
<sharinpix:SharinPix AlbumId="<<album-id>>" height="<<height>>"/>
```

## Implementation of the Wrapper Component

The **Wrapper Component** designates the Lightning Component  which will reference the **SharinPix Lightning Component** and which will also contain the fields that will modify the **album id** as well as the **height** of the SharinPix album. The code snippet below shows the implementation of this **Wrapper Component.**&#x20;

{% hint style="info" %}
The **aura:id** attribute is important as it is used as an identifier in the event there are multiple SharinPix Lightning Components on the same record page.
{% endhint %}

**SharinPixLightningWrapper.cmp**

{% code lineNumbers="true" %}
```html
<aura:component access="GLOBAL"
                implements="force:hasRecordId,force:appHostable,
                            flexipage:availableForAllPageTypes,
                            forceCommunity:availableForAllPageTypes" >
    <aura:attribute name="albumId" type="String"/>
    <aura:attribute name="recordId" type="String"/>
    <aura:attribute name="height" type="Integer" default="500"/>
    <aura:handler name="init" value="{! this }" action="{! c.doInit }"/>

    <sharinpix:SharinPix aura:id="sharinpix-cmp" AlbumId="{! v.albumId }" height="{! v.height }"/>

    <ui:inputText aura:id="album-id" placeholder="AlbumId"/>
    <ui:inputText aura:id="record-id" placeholder="recordId"/>
    <ui:button label="Set AlbumId or recordId" press="{! c.changeId }"></ui:button>

    <ui:inputText aura:id="height" placeholder="height" value="500"/>
    <ui:button label="Set height" press="{! c.changeHeight }"></ui:button>
</aura:component>
```
{% endcode %}

**SharinPixLightningWrapperController.js**

```javascript
({
    doInit : function(component) {
        var id = component.find('album-id').get('v.value') || component.find('record-id').get('v.value');
        component.set('v.albumId', (id != null) ? id : component.get('v.recordId'));
    },
    changeId : function(component) {
        var id = component.find('album-id').get('v.value') || component.find('record-id').get('v.value');
        component.set('v.albumId', id);
    },
    changeHeight : function(component) {
        var height = component.find('height').get('v.value');
        component.set('v.height', height);
    }
})
```

The code snippet shown above  (found in the client-side controller **SharinPixLightningWrapperController** ) serves the following functions respectively:

* **doInit:** This function is called when the component is loaded.
* **changeId:** This function is meant to change the album id of the SharinPix Lightning Component
* **changeHeight:** This function is meant to change the parameter value of the height of the SharinPix Lightning Component

The following screen-grab shows how the **Component Wrapper**  appears.

![](<../../.gitbook/assets/image (42) (2).png>)

The following steps demonstrate how to set up the component.

Create a custom tab to access the **Wrapper Component** more easily.

Go to **Setup:**

1. Enter **tabs** in the **Quick Find Box**.
2. Select **Tabs**.
3. On the **Custom Tabs** Page, go to section **Lightning Component Tabs**.
4. Click on **New**.
5. In the **Lightning Component** picklist, click on the name of the **Wrapper Component**.
   * It should be in the format: **<\<namespace>>:SharinPixLightningWrapper,** where **<\<namespace>>** corresponds to the namespace of your current organization.
6. Enter a name of your choice inside the field **Tag Label.**
7. Select a **Tab Style.**
8. Click on **Save** when you are done.

1\. In this context, the custom component is accessed via a custom tab. Access the record which contains the images you wish to display on the **SharinPix Lightning Component** and obtain its record Id which coincidentally corresponds to its album Id. Use this value to fill into the field as designated below.

![](<../../.gitbook/assets/image (43) (2).png>)

2\. After filling in the **AlbumId** field with the adequate album Id, you will need to click on the **Set AlbumId or RecordId** button so that the SharinPix Album displays the images found on the record which corresponds to the **Album Id** obtained in the precedent step.

![](<../../.gitbook/assets/image (44) (2).png>)

3\. It can be observed, from the previous screen-grab that after clicking on the **Set AlbumId or recordId** button, the SharinPix album appears with the images that match those found on the record the **album id** belonged to.

4\. In order to change the height of the **SharinPix Lightning Component,** you will need to to fill in the **Set height** as shown in the screen-grab below.

![](<../../.gitbook/assets/image (45) (2).png>)

5\. Fill in the **height** field with an appropriate height value.&#x20;

**Note: The height value is evaluated in pixels.**

![](<../../.gitbook/assets/image (46) (2).png>)

6\. Click on the **Set Height** button so as for the change in height to take effect.

![](<../../.gitbook/assets/image (47) (2).png>)

7\. It can be observed from the screen-grab below that the size of the SharinPix album has indeed changed and registered an increase from 500 pixels (which represents the default album height) to 1000 pixels. This can be useful when you are trying to display many images without the use of pagination.

![](<../../.gitbook/assets/image (48) (2).png>)

## Scenario 2: Allow or Deny SharinPix Abilities based on Profile Type

In this scenario, we will see how it is possible to modify the permissions on the SharinPix Album on a **SharinPix Lightning Component** so as to personalize what behavior is allowed or denied by the user.

The table below shows some of the names of these abilities and the features they control respectively.

| Ability Name   | Feature                                              |
| -------------- | ---------------------------------------------------- |
| image\_list    | The ability to display images on an album            |
| image\_upload  | The ability to add an image to an album.             |
| image\_delete  | The ability to delete an image from an album.        |
| fullscreen     | The ability to view an album in **fullscreen** mode. |
| image\_caption | The ability to add a caption to a specific image.    |

In the present case scenario, the SharinPix ability we want to allow/deny based on the profile type of the current user is the ability to delete(**image\_delete**) an image from an album.

1\. From the **App Launcher,**  click on **SharinPix Permissions**

![](<../../.gitbook/assets/image (49) (2).png>)

2\. Click on **New**.

![](<../../.gitbook/assets/image (50) (2).png>)

3\. In the **Name** field, enter **DisableDelete**.

4\. Make sure the input fields correspond to those shown in the screenshot below:

* Display images: **checked**
* Add images: **checked**
* Delete image: **unchecked**

Leave all other fields as they are.

![](<../../.gitbook/assets/image (51) (2).png>)

5\. Click on **Save** when you are done.

![](<../../.gitbook/assets/image (52) (2).png>)

Once saved, make sure that the field **Json** contains the following value:

```json
{"Access":{"see":true,"image_list":true,"image_upload":true,"image_delete":false}}
```

6\. Copy the value from the **ID** field, as it will be used in the next sections.

![](<../../.gitbook/assets/image (53) (2).png>)

### Implement the Lightning Wrapper Component

In this section, we will implement a Lightning Wrapper Component which serves the purpose of granting or denying the **ability to delete** an image based on whether the **Profile Type** of the current user is that of a **System Administrator** or not.&#x20;

The code snippet below shows the markup of the **Lightning Wrapper Component**, containing the required attributes as well as referencing the SharinPix Lightning Component.

```html
<aura:component access="global" implements="force:hasRecordId,force:appHostable,flexipage:availableForAllPageTypes,forceCommunity:availableForAllPageTypes" 	controller="SharinPixProfileController">
	<aura:handler name="init" value="{! this }" action="{! c.doInit }"/>
	<aura:attribute type="string" name="recordId"/>
	<aura:attribute type="string" name="albumId"/>
	<aura:attribute type="string" name="PermissionRecordId" access="global"/>
	<sharinpix:SharinPix aura:id="sharinpix-cmp" permissionId="{! v.PermissionRecordId }" AlbumId="{! v.albumId}" height="500px"/>
</aura:component>
```

The code snippet below shows the client-side controller of the **Wrapper Lightning Component**.

{% code lineNumbers="true" %}
```javascript
({
	doInit : function(component, event, helper) {
		var action = component.get('c.PermissionId');
		action.setParams({albumId: component.get('v.recordId')});
		action.setCallback(this, function(response){
			if(response.getState() === 'SUCCESS') {
				component.set('v.PermissionRecordId', response.getReturnValue());
				component.set('v.albumId', component.get('v.recordId'));
			}else {}
		});
		$A.enqueueAction(action);
	}
})
```
{% endcode %}

The code snippet below shows the server-side controller of the **Wrapper Lightning Component**.

{% code lineNumbers="true" %}
```apex
public with sharing class SharinPixProfileController {

public SharinPixProfileController() {}

@AuraEnabled
public static String PermissionId(String albumId) {
String permissionId = '';
Profile userProfile =  [SELECT Name FROM Profile WHERE Id = :UserInfo.getProfileId()];
if(!userProfile.Name.equals('System Administrator')) {
sharinpix__SharinPixPermission__c permission = [SELECT Id FROM sharinpix__SharinPixPermission__c WHERE Name = 'DenyDelete'];
permissionId = permission.Id;
}
return permissionId;
}
```
{% endcode %}

The screenshot below illustrates the **Wrapper Component** that have been added to the page of an Account Record.

![](<../../.gitbook/assets/image (54) (2).png>)

When the **Profile Type** of the current user is not that of a **System Administrator**, the SharinPix Ability of image deletion (**image\_delete**) is not available.

![](<../../.gitbook/assets/image (55) (2).png>)

On the other hand, when the **Profile Type** of the current user is that of a **System Administrator**, the ability to delete an image is available on the **SharinPix Album**.

![](<../../.gitbook/assets/image (56) (2).png>)
