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

# Using SharinPix in Salesforce Community

This article demonstrates how to:

* [Enable the usage of SharinPix in Salesforce Community](using-sharinpix-in-salesforce-community.md#enable-the-usage-of-sharinpix-in-salesforce-community)
* [Add the SharinPix Album component to Community home page](using-sharinpix-in-salesforce-community.md#add-the-sharinpix-album-component-to-a-community-home-page)
* [Add a SharinPix album to Community record page](using-sharinpix-in-salesforce-community.md#add-the-sharinpix-album-to-a-community-record-page)

{% hint style="warning" %}
**Prerequisites:**

Salesforce Communities should be enabled on your organisation.
{% endhint %}

## Enable the usage of SharinPix in Salesforce Community

To enable the usage of SharinPix in Salesforce Community, a **CSP Trusted Site** entry has to be added for SharinPix. To do so, follow the steps below:

1\. Go to **Setup**. Enter **CSP** in the **Quick Find Box**.

2\. Under **Security**, select **CSP Trusted Sites**.

3\. Then, click on **New Trusted Site** as shown below:

![](<../../.gitbook/assets/image (76) (1).png>)

You will be directed to the page below:

![](<../../.gitbook/assets/image (77) (1).png>)

4\. For the field **Trusted Site Name** , enter **SharinPix**

5\. For the field **Trusted Site URL** , enter **https://app.sharinpix.com**

![](<../../.gitbook/assets/image (78) (1).png>)

6\. Then, click on **Save**

7\. Next, repeat steps 3 to 6 to create new trusted sites using the following SharinPix endpoint URL as the **Trusted Site URL**: **https://p.sharinpix.com**

## Add the SharinPix Album component to a Community home page

To add a SharinPix Album component to a Community Home Page, follow the steps below:

* Go to **Setup** , then enter **Communities** in the **Quick Find Box**
* Under **Communities**, select **All Communities**
* Click on **Builder** next to the **Community** you intend to modify

![](<../../.gitbook/assets/image (79) (1).png>)

* Once inside the **Builder,** select the **Components** menu from the home page. Then, scroll down to the **Custom Components** section
* Drag and Drop the **SharinPix Album** component onto the desired region

![](<../../.gitbook/assets/image (80) (1).png>)

* To display images on the SharinPix Album, you will need to supply a record Id in the **AlbumId** field available in the component's property editor. The SharinPix Album will then display all the images corresponding to that record

![](<../../.gitbook/assets/image (81) (1).png>)

![](<../../.gitbook/assets/image (82) (1).png>)

Make sure to publish the community in order to make the changes visible to your given audience.

## Add the SharinPix Album to a Community record page

There are two ways of adding a SharinPix album to a Community record page:

1. By either adding the SharinPix Album lightning component to the record page
2. Or by adding a Visualforce page embedding a SharinPix album component to the record page

{% hint style="warning" %}
**Note:**

If you intend to use a Salesforce object on a Community, you should ensure that proper access rights has been given to the object so as to view the records.
{% endhint %}

### Add the SharinPix Album component to a Community record page

To add the SharinPix Album to the Community record page:

* Edit the record page in **Builder** mode
* From **Components**, find the **SharinPix Album** component under the **Custom Components**
* Drag and drop the **SharinPix Album** component onto the desired region on the record page

The result should be as follows:

![](<../../.gitbook/assets/image (83) (1).png>)

### Add a Visualforce page embedding a SharinPix album to the record page

It is possible to add a Visualforce page containing a SharinPix album on a Community record page. To do so:

* Implement a Visualforce page embedding the SharinPix album. You can use the code snippet below for this implementation:

```html
<apex:page standardController="Account">   
    <sharinpix:SharinPix height="500px" 
		parameters="{
        	'Id': '{!CASESAFEID($CurrentPage.parameters.Id)}', 
            'abilities':{
            	'{!CASESAFEID($CurrentPage.parameters.Id)}':{
                'Access': {
                	'image_upload':true,
                    'image_list':true,
                    'see':true,
                    'image_delete':true
                    }
				}
			}
		}"
	/> 
</apex:page>
```

* Once your Visualforce page is ready, go ahead and edit the desired record page in **Builder** mode
* From **Components** , drag and drop the **Visualforce Page** found under the **Content** section onto the desired region on the record page
* In the component's property editor, make sure that the field **Record ID** has **{!recordId}** as value

![](<../../.gitbook/assets/image (84) (1).png>)

The result should be as follows:

![](<../../.gitbook/assets/image (85) (1).png>)

{% hint style="info" %}
**Information:**

If a Visualforce page embedding a SharinPix album is already present on an object's page layout, the Visualforce page will also be visible in the **Details** section of the corresponding records inside a Salesforce Community.

The screenshot below depicts an Account record's **Details** section with a Visualforce page embedding the SharinPix Album component:
{% endhint %}

![](<../../.gitbook/assets/image (86) (1).png>)

![](<../../.gitbook/assets/image (87) (1).png>)

{% hint style="success" %}
**Tip:**

Community users do not have all access rights to SharinPix by default.

If you encounter issues regarding Community users not having proper access to the SharinPix Image Sync or SharinPix components, please refer to the following article:

[SharinPix Community users access rights](../../access-and-security/sharinpix-community-users-access-rights.md)
{% endhint %}
