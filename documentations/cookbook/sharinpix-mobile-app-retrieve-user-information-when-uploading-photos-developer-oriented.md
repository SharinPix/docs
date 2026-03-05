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

# SharinPix Mobile App: Retrieve User Information When Uploading Photos (Developer-Oriented)

{% hint style="info" %}
The SharinPix mobile app uses tokens to authenticate itself and upload photos that can be viewed on Salesforce.&#x20;

Since the app is built for offline use, the tokens are usually generated beforehand and stored in Salesforce fields on records. Multiple users can also upload photos to a single Salesforce record. As such, the tokens cannot be tied to any specific user to avoid relating the user to all photos uploaded by anyone to the record.  Thus, the tokens are "anonymous".

This article demonstrates how to:

1. Pass the current user's identifier in the URL.
2. Retrieve them when the photos are uploaded.&#x20;
3. &#x20;Save the user identifier in a custom field on the SharinPix Image record.
{% endhint %}

{% hint style="warning" %}
**Note:**

The user identifier will be saved on a SharinPix Image record. To enable the use of the SharinPix Image object, kindly ensure that the SharinPix Image Sync has been activated on the Salesforce object on which users are uploading photos.

For more information on SharinPix Image Sync, refer to this article:&#x20;

[What is SharinPix Image Sync?](../image-sync/what-is-sharinpix-image-sync.md)

For steps on how to activate the SharinPix Image Sync on an object, refer to this article:

[Setup SharinPix Image Sync](../image-sync/setup-sharinpix-image-sync.md)
{% endhint %}

{% hint style="success" %}
**Tips:**

* For more information on SharinPix tokens and how they work, refer to this article: [Working with SharinPix Tokens](../best-practices/working-with-sharinpix-tokens.md)
* This article also applies to photo uploads launched from the **Salesforce Field Service** mobile app.
{% endhint %}

To retrieve the user information in anonymous tokens, you will need to:

1. [Create a Flow to capture the user information and launch the SharinPix app to upload photos.](sharinpix-mobile-app-retrieve-user-information-when-uploading-photos-developer-oriented.md#create-the-flow)
2. [Create an Apex class to retrieve and save the user info in a Salesforce field.](sharinpix-mobile-app-retrieve-user-information-when-uploading-photos-developer-oriented.md#create-the-apex-class)
3. [Configure a Webhook to capture the mobile upload requests.](sharinpix-mobile-app-retrieve-user-information-when-uploading-photos-developer-oriented.md#create-the-sharinpix-webhook)

## Create the Flow

This section demonstrates how to create a Flow that will capture the username of the user opening the SharinPix mobile app to upload photos.

{% hint style="info" %}
* For this demo, we will use the WorkOrder object.
* For steps to create a Screen Flow, refer to [Create a Screen Flow](sharinpix-mobile-app-retrieve-user-information-when-uploading-photos-developer-oriented.md#create-a-screen-flow) below.
* For steps to create a Field Service Mobile Flow, refer to [Create Field Service Mobile Flow](sharinpix-mobile-app-retrieve-user-information-when-uploading-photos-developer-oriented.md#create-field-service-mobile-flow) below.
{% endhint %}

### Create a Screen Flow

To create the Flow, follow the steps below:

* Go to Setup then type Flow in the Quick Find box. Under Process Automation, select **Flows**.
* Click on **New Flow**. You will be directed to the Flow Designer.
* Select _Screen_ Flow, then click on **Create**.



*   Go to the **Manager** tab and click on **New Resource**.

    * Resource Type: Variable
    * API Name: Enter **recordId**
    * Data Type: Text
    * Default Value: **{!$GlobalConstant.EmptyString}**
    * Availability Outside the Flow: Available for input
    * Click **Done**


*   To retrieve the current user ID, proceed as follows:

    1. Go to the **Manager** tab and click on **New Resource**.
    2. Resource Type: Formula
    3. API Name: UserId
    4. Data Type: Text
    5. In the formula editor, enter the following formula to retrieve the current user ID: **{!User.Id}**
    6. Click **Done**


*   Go to the **Manager** tab again and click on **New Resource**.

    * Resource Type: Variable
    * API Name: Enter any API name. For this demo, we will use **WorkOrderRecord**
    * Data Type: Record
    * Object: Work Order
    * Click **Done**


*   Go to the **Elements** tab then drag and drop the **Get Records** element under the **Data** section onto the blank canvas. For the Get Records element:

    * Label: lookupWorkOrder
    * Object: Work Order
    * Conditions: **Id** (Field) equals (operator) **{!recordId}**
    * In the **How Many Records to Store**, check the **Only the first record** option
    * In the **How to Store Record Data,** check the **Choose fields and assign variables (advanced)** option
    * In the **Where to Store Field Values**, check the **Together in a record variable** option
    * Then in the **Select Variable to Store Work Order** section, use the **WorkOrderRecord** variable for the **Record** field
    * In the **Select Work Order Fields to Store in Variable** section, click on **Add Field** and select the token field, that is, **SharinPix\_Token\_\_c** for this demo
    * Click **Done**



    * Go to the Manager tab and click on New Resource:
      * Resource Type: Variable
      * API Name: **Launch\_SharinPix\_App**
      * Data Type: Text
      * Default Value: **\<a href="sharinpix://upload?token={!WorkOrderRecord.SharinPix\_Token\_\_c}\&user\_id=UserId">Take Pictures\</a>**
      * Click **Done**

### Create Field Service Mobile Flow

To create the Flow, follow the steps below:

* Go to Setup then type Flow in the Quick Find box. Under Process Automation, select **Flows**.
* Click on **New Flow**. You will be directed to the Flow Designer.
* Click on Show More and select _Field Service Mobile Flow_. Then click on **Create**.



* Go to the **Manager** tab and click on **New Resource**.
  * Resource Type: Variable
  * API Name: Enter **Id**
  * Data Type: Text
  * Default Value: **{!$GlobalConstant.EmptyString}**
  * Availability Outside the Flow: Available for input
  * Click **Done**



*   To retrieve the current user ID, proceed as follows:

    1. Go to the **Manager** tab and click on **New Resource**.
    2. Resource Type: Variable
    3. API Name: Enter **UserId**
    4. Data Type: Text
    5. Availability Outside the Flow: Available for input
    6. Click **Done**


*   Go to the **Manager** tab again and click on **New Resource**.

    * Resource Type: Variable
    * API Name: Enter any API name. For this demo, we will use **WorkOrderRecord**
    * Data Type: Record
    * Object: Work Order
    * Click **Done**


*   Go to the **Elements** tab then drag and drop the **Get Records** element under the **Data** section onto the blank canvas. For the Get Records element:

    * Label: lookupWorkOrder
    * Object: Work Order
    * Conditions: **Id** (Field) equals (operator) **{!Id}**
    * In the **How Many Records to Store**, check the **Only the first record** option
    * In the **Where to Store Field Values**, check the **Together in a record variable** option
    * Then in the **Select Variable to Store Work Order** section, use the **WorkOrderRecord** variable for the **Record** field
    * In the **Select Work Order Fields to Store in Variable** section, click on **Add Field** and select the token field, that is, **SharinPix\_Token\_\_c** for this demo
    * Click **Done**


* Go to the Manager tab and click on New Resource:
  * Resource Type: Variable
  * API Name: **Launch\_SharinPix\_App**
  * Data Type: Text
  * Default Value: **\<a href="sharinpix://upload?token={!WorkOrderRecord.SharinPix\_Token\_\_c}\&user\_id=UserId">Take Pictures\</a>**
  * Click **Done**

{% hint style="info" %}
How to use the flow:

* [Add the Flow in an Action](../integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-flows.md#adding-flow-in-an-action)
* [Create an App Extension embedding a Flow](../integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-app-extension.md#creation-of-an-app-extension-embedding-a-field-service-mobile-flow)
{% endhint %}

{% hint style="success" %}
**Tips:**

* The user values passed in the URL can be modified as desired.
* Other values can be passed in the SharinPix URL. The value, **record\_id**, for instance, will move the uploaded photo to the specified record ID:

`sharinpix://upload?token={!WOLI.SharinPix_Token__c}&record_id={!WorkOrderID}`
{% endhint %}

## Create the Apex Class

{% hint style="warning" %}
**Note:**

It is important that the value passed in the URL is saved in a custom field on the SharinPix Image object and not in one of the fields managed by the SharinPix package.

This is because the SharinPix Image object's managed fields can be updated after performing SharinPix actions such as image synchronizations. Updating these manage fields outside the SharinPix package may lead to data alterations.

_The type of field to be used will depend on the use case. In the example below, a lookup field to the User object has been created to save the username corresponding to the user ID passed_
{% endhint %}

Next, create an Apex class to will retrieve the user information passed to the **user\_id** parameter and save the value in the custom field on the related SharinPix Image record.

Here's the sample code for the Apex class:

```apex
trigger SharinPixImageUserIdReplace on sharinpix__SharinPixImage__c (before insert) {
    Map<String, Object> metadatas;
    String appUrl;
    List<sharinpix__SharinPixImage__c> updatedUserName = new List<sharinpix__SharinPixImage__c>();
    for (sharinpix__SharinPixImage__c image : Trigger.new) {
        if (String.isBlank(image.sharinpix__Metadatas__c)) { continue; }
        try {
            metadatas = (Map<String, Object>) JSON.deserializeUntyped(image.sharinpix__Metadatas__c);
            appUrl = String.valueOf(metadatas.get('sharinpix_mobile_app_url'));
        } catch (Exception e) {
            // No JSON in field
            continue;
        }
        if (String.isBlank(appUrl)) { return; }
        if(!(appUrl.contains('&user_id='))) {return;}

        //Retrieve the user ID from the metadata
        List<String> urlParams = appUrl.split('&user_id=');
        Id username = urlParams[1].substring(0,18);

        //Update the custom field with value stored in variable username.
        image.Uploaded_By__c = username;
    }
}
```

The Apex test class is as follows:

```apex
@isTest
private class SharinPixImageUserIdReplaceTest {
    private static List<sharinpix__SharinPixImage__c> lstSpxImages = new List<sharinpix__SharinPixImage__c>();
    private static User usr;

    static {
        usr = new User(
            UserName = 'test_user@testorgxyz.com' + String.valueof((Math.random() * 1000)),
            Alias = 'TU', 
            Email='testuser@testorg.com',
            FirstName = 'Test',
            LastName='User',
            EmailEncodingKey = 'UTF-8',
            LanguageLocaleKey = 'en_US',
            LocalesIdKey = 'en_US',
            TimezonesIdKey = 'America/Los_Angeles',
            ProfileId = [SELECT Id, Name FROM Profile WHERE Name = 'System Administrator' Limit 1].Id
        );
        insert usr;
        sharinpix__SharinPixImage__c img1 = new sharinpix__SharinPixImage__c(sharinpix__Metadatas__c = '{"sharinpix_mobile_app_url" : "sharinpix://upload?token=REMOVED&user_id=' + usr.Id + '"}');
        sharinpix__SharinPixImage__c img2 = new sharinpix__SharinPixImage__c(sharinpix__Metadatas__c = '{"sharinpix_mobile_app_url" : "sharinpix://upload?token=REMOVED&user_id=' + usr.Id + '"}');
        lstSpxImages.add(img1);
        lstSpxImages.add(img2);
    }

    @isTest static void testUpdateUserInfo() {        
        Test.startTest();
        insert lstSpxImages;
        Test.stopTest();

        User testUser = [SELECT Id, Name FROM User WHERE Name = 'Test User'];
        sharinpix__SharinPixImage__c image1 = [SELECT Id, sharinpix__User__r.Name FROM sharinpix__SharinPixImage__c WHERE Id =: lstSpxImages[0].Id];
        sharinpix__SharinPixImage__c image2 = [SELECT Id, sharinpix__User__r.Name FROM sharinpix__SharinPixImage__c WHERE Id =: lstSpxImages[1].Id];
        System.assertEquals(testUser.Name, image1.sharinpix__User__r.Name);
        System.assertEquals(testUser.Name, image2.sharinpix__User__r.Name);
    }
}
```

## Create the SharinPix Webhook

For this implementation to work, you will need **either** a SharinPix Webhook of type\*\* Upload Done\*\* or **New Image**.

To verify your Webhook settings, [go to the SharinPix Administration Dashboard](../getting-started-with-sharinpix/overview-of-the-sharinpix-administration-dashboard.md), then click on Webhooks.

The Webhook settings should be as follows:

* Action type: apex\_method
* Class name: **sharinpix.ImageSyncMigration**
* Method name: **synchronize**
* The Webhook should be either of type **Upload Done** or **New Image**

If no Webhook has been created for your organization, create one as indicated above.

{% hint style="success" %}
**Tip:**

For more information on SharinPix Webhooks, refer to this article: [SharinPix Webhooks](sharinpix-webhooks.md)
{% endhint %}

### DEMO: How to test your implementation? <a href="#demo-how-to-test-your-implementation" id="demo-how-to-test-your-implementation"></a>

To test your implementation:

1. Open the newly-created Flow on the Salesforce or Field Service mobile app.
2. Tap on the SharinPix deeplink (i.e., the link to the SharinPix mobile app) added to the Flow.
3. Capture and upload photos.
4. Open the related SharinPix Image record created for any newly-uploaded photo.
5. Verify that the **Uploaded By** field is populated with the username of the user who uploaded the photos:

<figure><img src="../.gitbook/assets/test (18).jpg" alt=""><figcaption></figcaption></figure>

