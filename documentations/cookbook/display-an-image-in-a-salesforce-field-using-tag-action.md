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

# Display an image in a Salesforce field using Tag Action

SharinPix offers an easy way to generate image URLs upon tagging images using a process known as **Tag Action**.

Tag Actions can be configured in such a way so that when a specific tag is applied to an image, an image URL is generated and is automatically stored in a specified field. Therefore, this makes it possible to retrieve the URL generated and use the same in a Salesforce formula field to display the image on a record page.

For this demo, we will use the **Account** object.

To demonstrate how to add an image in a Salesforce field using Tag Action, we will:

1. Create Salesforce fields to store the image URL and to display the specified image
2. Create a tag to identify the required image
3. Configure a Tag Action to automate everything

## Create the Salesforce fields

For this implementation, you will first need to create two fields:

* A field of type **URL** to store the image URL generated after the tag has been applied. For this demo, we will configure the field as follows:
  * Type: **URL**
  * Label: **First Image URL**
* A **Formula** field which will use the image URL stored in the field created above, that is **First Image URL**, to display the image. For the formula field:
  * Field label: **Image**
  * Formula Return Type: **Text**
  * Formula:

<mark style="color:$danger;">`IF(ISBLANK(First_Image_URL__c), "Image Not Found", IMAGE(First_Image_URL__c, ""))`</mark>

{% hint style="success" %}
**Tip:**

It is possible to use a single formula field to display multiple images. In this case all you have to do is to store the image URLs in different URL fields, then use the fields in a Formula field using the following formula to display all images:

<mark style="color:$danger;">`IF( OR( ISBLANK( First_Image_URL__c ), ISBLANK( Second_Image_URL ) ), "Image Not Found", IMAGE( Second_Image_URL__c , "" )& " " & IMAGE( Second_Image_URL , "" ) )`</mark>
{% endhint %}

{% hint style="warning" %}
**Note:**

For the Tag Action to work properly, you should ensure that the users have access to the fields created above.
{% endhint %}

## Create the tag and configure the Tag Action

Now that the fields are ready, go ahead and create a tag and a Tag Action by following the steps below:

* Click on **App Launcher** and search for **SharinPix Settings**
* On the SharinPix Settings tab, click on **Go to administration dashboard** button

![](<../.gitbook/assets/image (31) (3).png>)

* Once on the dashboard, click on **Tags** from the top menu bar
* Then, create the tag that will perform the tag action. Here, we will create a new tag named **First Image** using the following parameters:

![](<../.gitbook/assets/image (32) (3).png>)

* After creating the tag, scroll down and click on the button named **New Tag Action**

![](<../.gitbook/assets/image (33) (3).png>)

* Then, configure the new Tag Action as indicated below:
  * Field name: enter the API name of the newly-created **URL** field, that is **First\_Image\_URL\_\_c**
  * Field value: here, you can choose your desired value, but for this demo we will opt for the **Mini url** value which will display the image in a smaller format

![](<../.gitbook/assets/image (34) (3).png>)

* Click on **Update Tag** when done.

{% hint style="success" %}
**Tip:**

For more detailed information about Tag Actions' configuration, you can refer to the following article:

[Tag Action](../features/working-with-tags/tag-action.md)
{% endhint %}

## Demo

Now that everything has been set up, we can go ahead and test our new implementation!

To do so:

* Go to the Account record
* From the SharinPix Album, tag the desired image with the **First Image** tag

![](<../.gitbook/assets/image (35) (3).png>)

{% hint style="warning" %}
**Note:**

For the Tag Action to work correctly, you must ensure that the option **Enable Action** has been checked for SharinPix Album component added to the record page layout.
{% endhint %}

* After applying the tag, check if the **Image** and **First Image URL** fields have been populated correctly as demonstrated below:

![](<../.gitbook/assets/image (36) (3).png>)

{% hint style="warning" %}
**Tip:**

Using Tag action to add images to Salesforce fields is the generic way of doing things.

SharinPix also provides another method to perform the same process but this time, using one of its components which is the **SharinPix To Rich Text Area** component.

The SharinPix To Rich Text Area component allows users to select and send one or more images from a SharinPix album to a **Rich Text** field. This method is easier to configure and provides more flexibility.

For more information about this component, please refer to the following article:

[SharinPix To Rich Text Area](../lightning-web-component/sharinpix-to-rich-text-area.md)
{% endhint %}
