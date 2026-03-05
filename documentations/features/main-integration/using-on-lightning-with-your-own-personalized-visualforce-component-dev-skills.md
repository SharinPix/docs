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

# Using on Lightning with your own personalized Visualforce Component (Dev Skills)

In this article, we will gain an understanding on the degree of flexibility acquired through the use of the SharinPix Visualforce Component and we will see how it is possible to personalize its implementation so as to make it fit a particular use case scenario.

{% hint style="success" %}
**Note:** The use case scenario as presented in this article is only meant to procure an intuitive sense on what the **SharinPix Visualforce Component** is capable of and to offer you the tools to fit this component into your own context.
{% endhint %}

* [Access the SharinPix Visualforce Component](using-on-lightning-with-your-own-personalized-visualforce-component-dev-skills.md#access-the-sharinpix-visualforce-component)
* [Use Case Scenarios](using-on-lightning-with-your-own-personalized-visualforce-component-dev-skills.md#use-case-scenarios)
* [Configuration for Visualforce Component](using-on-lightning-with-your-own-personalized-visualforce-component-dev-skills.md#configuration-for-visualforce-component)
* [Scenario 1: Change height and album Id dynamically](using-on-lightning-with-your-own-personalized-visualforce-component-dev-skills.md#scenario-1-change-height-and-album-id-dynamically)
* [Scenario 2: Assign SharinPix Ability based on Profile Type](using-on-lightning-with-your-own-personalized-visualforce-component-dev-skills.md#scenario-2-assign-sharinpix-ability-based-on-profile-type)

## Access the SharinPix Visualforce Component

1\. Go to **Setup.** In the **Quick Find Box,** type **Installed Packages.**

2\. Select **Installed Packages.**

![](<../../.gitbook/assets/image (25) (1).png>)

3\. Click on **ImagesManagementBySharinPix** which corresponds to the **SharinPix Package**.

![](<../../.gitbook/assets/image (14).png>)

4\. Click on **View Components**.

![](<../../.gitbook/assets/image (15).png>)

5\. The Visualforce component **SharinPix** can be accessed.

The **SharinPix Package** that you installed from the AppExchange comes with a wide-range of components.

However, in our present context we will be using the **SharinPix Visualforce Component** that can be viewed by following the subsequent steps.

![](<../../.gitbook/assets/image (16).png>)

## Configuration for Visualforce Component

The subsequent steps are meant to enable an adequate communication and transmission of information between your **Salesforce Organization** and **SharinPix** and vice-versa.

6\. Go to **App Launcher.** And select **SharinPix Settings.**

![](<../../.gitbook/assets/image (17) (1).png>)

Once the page is loaded, make sure the **Salesforce -> SharinPix API access** and the **SharinPix -> Salesforce API access** are highlighted in green as shown in the screenshot below.

![](<../../.gitbook/assets/image (18) (1).png>)

## Use Case Scenarios

In the following use cases, we will get a glimpse on the flexibility that the Visualforce Component provides, and it will hopefully provide you with an intuitive sense on how to tailor the **SharinPix Visualforce Component** so as to fit your needs.

The next use case scenarios will present  **2** possibilities on how to personalize the **SharinPix Visualforce**

**Component:**

* [Scenario 1: Change height and album Id dynamically](using-on-lightning-with-your-own-personalized-visualforce-component-dev-skills.md#scenario-1-change-height-and-album-id-dynamically)
* [Scenario 2 : Assign SharinPix Ability based on Profile Type](using-on-lightning-with-your-own-personalized-visualforce-component-dev-skills.md#scenario-2-assign-sharinpix-ability-based-on-profile-type)

## Scenario 1: Change height and album Id dynamically

In this scenario, we will wrap the **SharinPix Visualforce Component** found  in the SharinPix Package within a **Visualforce Page**, and implement a solution that will allow the user to dynamically set the **Height** and **Album Id** of the SharinPix Album.

The code referencing the **SharinPix Visualforce Component** is shown below.

```html
<sharinpix:SharinPix parameters="{! parameters }" height="{! height }px" componentId="component1" />
```

In this context, the **SharinPix Visualforce Component** is referenced inside a **Visualforce Page** as demonstrated in the code snippet below.

```html
<apex:page showHeader="true" controller="SharinPixDynamicCtrl" sidebar="true">
	<apex:form>
		<apex:outputPanel id="frame">
			<sharinpix:SharinPix parameters="{! parameters }" height="{! height }px"/>
		</apex:outputPanel>
		<label>Album Id:</label><apex:inputText value="{! albumId }"/>
		<label>Height:</label><apex:inputText value="{! height }"/>	
		<apex:commandButton value="Execute changes" reRender="frame"></apex:commandButton>
	</apex:form>
</apex:page>
```

The code for the Apex Controller, referenced within the above Visualforce Page, is presented below.

```apex
public with sharing class SharinPixDynamicCtrl {
    public String height {get;set;}
    public Id albumId {get;set;}

    public SharinPixDynamicCtrl() {
        albumId = ApexPages.CurrentPage().getparameters().get('id');
    }

    public String getParameters() {
         Map<String, Object> claims = new Map<String, Object> {
            'Id' => albumId,
            'abilities' => new Map<String, Object> {
                albumId => new Map<String, Object> {
                      'Access' => new Map<String, Object> {
                      'see' => true,
                      'image_list' => true,
                      'image_upload' => true,
                      'image_delete' => true
                    }
                }
            }
        };
        String parameters = JSON.serialize(claims);
        return parameters;
    }
}
```

The Visualforce Page, referencing the **SharinPix Visualforce Component** , is added to the page of an Object. (In this context, the Object is an **Account**)**.**

![](<../../.gitbook/assets/image (19) (1).png>)

The fields **Album Id** and **Height** as shown in the screenshot, are meant to modify the values of the corresponding parameters for the **SharinPix Visualforce Component.**

7\. The **Album Id** field modifies the Album Id passed through the parameters named **parameters** for the SharinPix Visualforce Component.

8\. The **Height** field modifies the height of the SharinPix Album by accepting the relevant values in pixels.

9\. Once the new values are entered, you are required to click on the button **Execute Changes** to make the changes reflect on the **SharinPix Album**.

### Changing the Album Id

If you enter a new value in the **Album Id** field, click on the button **Execute changes**. The changes on how the Album appears should be effective immediately.

![](<../../.gitbook/assets/image (21).png>)

As it can be seen in the screenshot above, when the new album Id is used, the images displayed on the album are no longer those displayed before. These new images that are displayed correspond to the images found on the record as referenced by the new **Id** value used.

### Changing the Height

If you enter a new value for the **Height** field, you will need to click on the button **Execute Changes** to make the changes reflected on the SharinPix Album immediately.

![](<../../.gitbook/assets/image (20).png>)

Once you click on the button **Execute Changes**, you will see the SharinPix Album with a new **height** as shown in the screenshot below.

![](<../../.gitbook/assets/image (22) (1).png>)

## Scenario 2 : Assign SharinPix Ability based on Profile Type

In this scenario, we will wrap the SharinPix Visualforce Component inside a Visualforce Page and implement a solution that will detect whether the current user is of a particular **Profile Type** and modify the SharinPix Abilities based on that result.

In this particular case, the current implementation will check if the **Profile Type** of the current user is of type **System Administrator**.

The code referencing the **SharinPix Visualforce Component** is shown below.

```html
<sharinpix:SharinPix parameters="{! parameters }" />
```

In this context, the **SharinPix Visualforce Component** is referenced inside a **Visualforce Page** as demonstrated in the code snippet below.

```html
<apex:page showHeader="true" sidebar="true" controller="SharinPixDynamicProfile">
	<sharinpix:SharinPix parameters="{! parameters }" />
</apex:page>
```

The code for the Apex Controller, referenced within the above Visualforce Page, is presented below.

```apex
public with sharing class SharinPixDynamicProfile {
	public String parameters {get;set;}

	public SharinPixDynamicProfile() {
		Id albumId = ApexPages.CurrentPage().getParameters().get('id');
		Boolean isAdmin = true;
		Profile userProfile = [SELECT Name FROM Profile WHERE Id = :UserInfo.getProfileId()];
		
		if(!userProfile.Name.equals('System Administrator')) {
			isAdmin = false;
		}

		Map<String, Object> claims = new Map<String, Object>{
			'Id' => albumId,
			'abilities' => new Map<String, Object> {
				albumId => new Map<String, Object> {
					'Access' => new Map<String, Object> {
						'see' => true,
						'image_list' => true,
						'image_upload' => true,
						'image_delete' => isAdmin
					}
				}
			}
		};
		parameters = JSON.serialize(claims);
	}
}
```

The Visualforce Page can be added to any Object's page (in this case, it is on the **Contact** object page). As it can be seen below: since the **Profile Type** of the current user is not of type **System Administrator**, the ability to delete an image(**image\_delete**) is not available as indicated in the screenshot below.

![](<../../.gitbook/assets/image (23) (1).png>)

The screenshot below shows that the ability to delete an image is available when the **Profile Type** of the current user is **System Administrator.**

![](<../../.gitbook/assets/image (24) (1).png>)
