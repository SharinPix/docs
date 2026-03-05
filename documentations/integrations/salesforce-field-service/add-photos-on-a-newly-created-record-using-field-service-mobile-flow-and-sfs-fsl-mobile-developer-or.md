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

# Add Photos on a Newly-Created Record Using Field Service Mobile Flow and SFS Mobile (Developer-Oriented)

In this article, we will demonstrate how to use the SharinPix app to add photos on a newly-created object record using the Field Service Mobile Flow on the SFS mobile app.

The scenario will be as follows:

* A field technician launches the Salesforce Field Service mobile app.
* He encounters an issue relating to a Work Order record and wants to document on same by adding a subject and a description on a new Case record. The technician also wants to add photos to the same Case record.
* To do so, the technician taps on a button labeled **Open a Case** within the Field Service mobile app to create a new Case record with the necessary information and photos. This button launches a Field Service Mobile Flow allowing the technician to enter information about the new Case record. The Flow also includes a deeplink to the SharinPix mobile app allowing the user to capture the photos that will be added to the newly-created Case record.

In the following sections, you will learn how to implement the above scenario using:

1. [A new field on the Case object as well as a new custom object, PendingAlbum, to store the information required to move the images to the newly-created Case records.](add-photos-on-a-newly-created-record-using-field-service-mobile-flow-and-sfs-fsl-mobile-developer-or.md#preconfiguration)
2. [A Field Service Mobile Flow to enter the Case details as well as to launch the SharinPix mobile app to take pictures.](add-photos-on-a-newly-created-record-using-field-service-mobile-flow-and-sfs-fsl-mobile-developer-or.md#creating-the-flow)
3. [A Webhook alongside the Apex classes to move the photos captured to the Case record when the latter is created.](add-photos-on-a-newly-created-record-using-field-service-mobile-flow-and-sfs-fsl-mobile-developer-or.md#creation-of-the-webhook-and-apex-classes-to-move-images-to-the-newlycreated-record-1)

### 1. Pre-configuration <a href="#preconfiguration" id="preconfiguration"></a>

Before setting up the Flow and Webhook, we need to add a custom field on the Case object. This field will be used later on to store a Case record identifier. We will explain the need for this identifier in a subsequent step. For now, go ahead and create the custom field on the Case object using the following details:

Label: **SharinPix Temporary ID**

Data Type: **Text Area**

Another object, **PendingAlbum** needs to be created with two fields: **Image Ids** which holds the image IDs, and **Temporary Id**, which retains a unique ID associated with the Case record. Proceed by creating the custom object and the fields as indicated below:

Object configuration:

* Name: **SharinPix Pending Album**
* Description (optional): _This custom object is used by SharinPix to store the metadata of images uploaded from the field service mobile app._

First field configuration:

* _Data Type: **Long Text Area**_
* _Label: **Image Ids**_
* _Description (optional): This field is used to store the image's Ids._

Second field configuration:

* Data Type: **Text**
* Label: **Temporary Id**
* Length: **150**
* Description (optional): _This field is used to store the temporary ID to retrieve the destination record._

### 2. Setup the Field Service Mobile Flow <a href="#creating-the-flow" id="creating-the-flow"></a>

To create the flow, follow the steps below:

* Go to Setup then type Flow in the Quick Find box. Under Process Automation, select **Flows**
* Click on New Flow. You will be directed to the Flow Designer
* Click on Show More and select **Field Service Mobile Flow**. Then click on **Create**

![](<../../.gitbook/assets/image (104).png>)

#### Retrieve the SharinPix Mobile Upload Token from the parent Work Order record <a href="#retrieve-sharinpix-token-from-the-work-order-record" id="retrieve-sharinpix-token-from-the-work-order-record"></a>

A mobile upload token is needed whenever the SharinPix mobile app is used to upload photos on any record. This token provides SharinPix with information such as the album on which the photos should be uploaded.

In our case, however, we do not have any token being generated for the new Case records. Therefore, to launch the SharinPix app and capture images, we will proceed as follows:

1. We will use the mobile upload token already present on the parent Work Order record instead to temporarily upload the photos to the Work Order record first.
2. Then, by using a Webhook that will call an Apex class to move the images captured from the Work Order record to the newly-created Case records.

In the following section, we will configure the Flow to retrieve the SharinPix mobile upload token from the Work Order record. To do so, follow the steps below:

* Go on the Manager tab and click on New Resource.
  * Resource Type: **Variable**
  * API Name: **Id**
  * Data Type: **Text**
  * Default Value: **{!$GlobalConstant.EmptyString}**
  * Availability Outside the Flow: **Available for input**
* Go to the **Manager** tab again and click on **New Resource**.
  * Resource Type: Variable
  * API Name: **WorkOrderRecord**
  * Data Type: Record
  * Object: Work Order
  * Click **Done**<br>
* Next, go to the **Elements** tab then drag and drop the **Get Records** element found under the Data section onto the blank canvas. For the Get Records:
  * Label: **getWorkOrder**
  * Object: **Work Order**
  * Conditions: **Id** (Field) equals (operator) **{!Id}** (newly-created resource named Id)
  * In the **How Many Records to Store**, check the **Only the first record** option
  * In the **Where to Store Field Values**, check the **Together in a record variable** option
  * Then in the **Select Variable to Store Work Order** section, use the **WorkOrderRecord** variable for the **Record** field
  * In the **Select Work Order Fields to Store in Variable** section, click on **Add Field** and select the token field, that is, **SharinPix\_Token\_\_c** for this demo
  * Click **Done** when finished
  * Then, connect  the **Get Records** (Get Work Order) element to the **Start** element

<figure><img src="../../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

#### Create the case record <a href="#create-the-case-record" id="create-the-case-record"></a>

The next step is to set up a **Screen** element to enter the Case record's details. To do so:&#x20;

* Go to the **Elements** tab then drag and drop the **Screen** element onto the blank canvas. Label the Screen element as **Create Case**
* Next, drag and drop two **Text** components on the screen canvas
* Label the first Text component as **Subject** and the second one as **Description**
* Click **Done** to save
* Then, connect the **Screen** (Create Case) element to the **Get Records** (Get Work Order) element previously added

<figure><img src="../../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>

Now, let's add a **Create Records** element to the canvas to create the **Case** record.&#x20;

First, we will create a variable to store the record using the steps below:

* Click on New Resource
  * Resource Type: **Variable**
  * API Name: **caseRecord**
  * Data Type: **Record**
  * Object: **Case**
  * Click **Done**

<figure><img src="../../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>

**Generate a temporary ID to identify the newly created Case record**

* Go to the **Manager** tab again and click on **New Resource**.
  * Resource Type: Text Template
  * API Name: **textTemporaryID**
  * In the Body section, select **View as Plain Text** in the dropdown
  * Resource Picker: **{!$Flow.CurrentDateTime}**
  * Click **Done**
* Go to the **Manager** tab again and click on **New Resource**.
  * Resource Type: Formula
  * API Name: **temporaryID**
  * Data Type: **Text**
  * Formula: **SUBSTITUTE({!textTemporaryID}, " ", "")**
  * Click **Done**

<figure><img src="../../.gitbook/assets/image (108).png" alt=""><figcaption></figcaption></figure>

Now, let us add the **Create Records** element to the canvas:

* Go to the **Elements** tab then drag and drop the **Create Records** element onto the blank canvas. For the Create Records:
* Label: **New Case Record**
* In the **How to Set the Record Fields** section, select **Use separate resources, and literal values**
* Object: **Case**
* In the **Set Field Values for the Case** section, choose **Description** as the field and **Description** as the matching value then click on the **Add** button. Next, choose **Subject** as the second field the variable **Subject** as value. For the **sharinPixTemporaryID\_\_c** has the variable **temporaryID** as Value. Both the **Origin** and **Status** fields need values to create a case, so assign **Phone** to the **Origin** field and the variable **New** to the **Status** field.
* In the **Store Case ID in Variable** section, choose **{!caseRecord.Id}** as value
* Click **Done** to save

<figure><img src="../../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>

* Next, connect the **Create Record** (New Case Record) element to the **Screen** (Create Case) element added previously

#### Add the deeplink (URL) to the SharinPix app <a href="#add-deeplink-to-sharinpix-app" id="add-deeplink-to-sharinpix-app"></a>

The next step is to add a **Screen** element to enable the launching of the SharinPix app to capture photos. To do so, follow the steps below.

Firstly, let's create a new resource that will store the deeplink to the SharinPix app with the following details:

* Resource Type: **Variable**
* API Name: **deeplink**
* Data Type: **Text**
* Default Value:

**\<a href="sharinpix://upload?token={!WorkOrderRecord.SharinPix\_Token\_\_c}\&caseTempId={!temporaryID}">Click to launch the SharinPix App\</a>**

{% hint style="info" %}
In the deeplink above, we are also passing the temporary ID as **caseTempId={!temporaryID}**.

For more details about the deeplink syntax, please refer to the following article:

[SharinPix mobile App : Deeplink syntax](../../mobile-app/sharinpix-mobile-app-deeplink-syntax.md)
{% endhint %}

<figure><img src="../../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>

Next, add a Screen element to launch the SharinPix app using the deeplink. Follow the steps below:

* Drag and drop a **Screen** element on the canvas with **Launch SharinPix App** as the label
* Next, drag and drop a **Display Text** component on the screen and add the following details:
  * API Name: **sharinpixAppLauncher**
  * In the **Insert a resource...** section, select **deeplink**
* Click **Done** to save

<figure><img src="../../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>

* To complete, connect the **Screen** (Launch SharinPix App) element to the **Create Records** (Create Case) element previously added.

The Flow should look like this at this point.

<figure><img src="../../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>

Save the Flow as **Create Case** and activate it. Then add the Flow as an **Action** labelled as **Open a Case** on the **FSL Work Order Layout** to make it visible on the FSL mobile app.

{% hint style="success" %}
**Tip:**

If you have difficulties adding the Flow on the SFS mobile app, click [here](integration-of-sharinpix-app-with-sfs-fsl-app-using-flows.md#adding-flow-in-an-action) for more details about how to implement this.
{% endhint %}

### Creation of the Webhook and Apex classes to move images to the newly created record <a href="#creation-of-the-webhook-and-apex-classes-to-move-images-to-the-newlycreated-record-1" id="creation-of-the-webhook-and-apex-classes-to-move-images-to-the-newlycreated-record-1"></a>

#### Setup the SharinPix Webhook <a href="#setup-the-webhook" id="setup-the-webhook"></a>

SharinPix Webhooks can be created to capture events such as image uploads to SharinPix. Webhook can also be used to invoke Apex methods to trigger the next actions when events are captured.

{% hint style="success" %}
**Tip:**

For more information about Webhook, please refer to the following article:[ SharinPix Webhooks](/broken/spaces/dhCgb93OIJaROCksbHJw/pages/xK9VntDTHzBbAnyVaEmf)
{% endhint %}

In this section, we will:

* Create a static method in an Apex class that will use transmitted data and Webhook information obtained from the SharinPix mobile app to move the images uploaded from the Work Order record to the newly-created Case record.
* Configure the SharinPix Webhook so that it detects the upload event and makes a call to the static method.

**Create a method to move images captured**

{% hint style="warning" %}
**Note:**

The SharinPix Pending Album object is used in this section. It has a field to store image IDs and another field to store the matching Case temporary ID. This is needed if the Case record is created after the image upload. When the Case is created, it fires an Apex Trigger to fetch all stored image IDs from the related Pending Album record and uploads the images to the corresponding Case record.
{% endhint %}

Use the Apex code below to implement the method that will move the images captured to the newly-created Case record:

```apex
global with sharing class SharinPixMoveImages {
	global static void uploadDone(String payload, String webhookInformation) {
        Map<String, Object> payloadMap = (Map<String, Object>)JSON.deserializeUntyped(payload);
        if (payloadMap.containsKey('app_url') && ((String)payloadMap.get('app_url')).contains('&caseTempId=') && payloadMap.containsKey('image_ids')) {
            //Retrieve the temporary ID from the Payload
            String tempID = ((String)payloadMap.get('app_url')).split('&caseTempId=')[1];
            
            //Retrieve Image Public IDs of images captured and add to list
            List<String> lstImageIDs = new List<String>();
            for(Object imageId : (List<Object>)payloadMap.get('image_ids')) {
                lstImageIDs.add(String.valueOf(imageId));
            }
            
            List<Case> cases = [SELECT Id FROM Case WHERE sharinPixTemporaryID__c = :tempID LIMIT 1];
            if (cases.isEmpty()) {
                try {
                    SharinPixPendingAlbum__c pendingAlbum = new SharinPixPendingAlbum__c();
                    pendingAlbum.ImageIds__c = JSON.serialize(lstImageIDs);
                    pendingAlbum.TemporaryId__c = tempID;
                    insert pendingAlbum;
                } catch(DmlException e) {
                    //handle error
                }
            } else {
                if(Test.isRunningTest()) { return; }
                sharinpix.Image.moveImages(lstImageIDs, cases[0].Id);
            }    
     	}
    }
}
```

{% hint style="success" %}
**Tip:**

* In the above code snippet, we made use of the SharinPix **moveImages** method to perform the move operation. For more information on the **moveImages**, refer to this documentation: [Image methods](../../cookbook/image-methods.md)
{% endhint %}

You can refer to the code snippet below to implement your test class.

```apex
@isTest
public class SharinPixMoveImagesTest {
    @isTest
    private static void uploadDoneTest() {
        Case cs = new Case(sharinPixTemporaryID__c = 'Test Temp ID'); 
        insert cs;
        String payload = '{"app_url":"https://app.sharinpix.com/upload?token=tokenID&caseTempId=' + cs.sharinPixTemporaryID__c + '","count":1,"platform":"mobile","album_id":"testAlbumId","image_ids":["adca4739-1466-4c2a-b04c-c7bcaee4eb91"]}';
        String webhookInformation = '{"id":37384143,"event_type":"upload_done","type":"Webhooks::V2"}';
 
        Test.startTest();
        SharinPixMoveImages.uploadDone(payload, webhookInformation);
        Test.stopTest();
        
    }
    
    @isTest
    private static void testUploadDoneWithNoMatchingCase() {
        String tempId = 'TEMP123';
        String payload = '{"app_url":"https://app.sharinpix.com/upload?token=tokenID&caseTempId=' + tempId + '","count":1,"platform":"mobile","album_id":"testAlbumId","image_ids":["adca4739-1466-4c2a-b04c-c7bcaee4eb91"]}';
		String webhookInformation = '{"id":37384143,"event_type":"upload_done","type":"Webhooks::V2"}';
        
        Test.startTest();
        SharinPixMoveImages.uploadDone(payload, webhookInformation);
        Test.stopTest();
        
        List<SharinPixPendingAlbum__c> pendingAlbums = [SELECT Id, TemporaryId__c FROM SharinPixPendingAlbum__c WHERE TemporaryId__c =: tempId LIMIT 1];
        Assert.areEqual(pendingAlbums.size(), 1); 
    }
}
```

Now that our method is ready, we can configure our SharinPix Webhook as explained in the section below.

**Configure the SharinPix Webhook**

To configure the Webhook, go to the **SharinPix Admin Dashboard** and follow the instructions below:

* From the top menu bar, select **Webhooks**
* Then click on the button **New Webhook** located at the top right corner
* Next, enter the Webhook details as indicated below:
  * For the **Action type**, choose **apex\_method**
  * For the **Class name**, enter the name of the Apex class created above, that is **SharinPixMoveImages**
  * For the **Method name**, enter the name of the method using the transmitted data and Webhook information to move the images, that is, **uploadDone**
  * Leave the field **Type** as **Webhook::V2**
  * To complete, check the event **Upload done**. This event is triggered once all images have been uploaded to SharinPix&#x20;
* Click on **Create V2** when done

#### Setup the Trigger on Case and Queueable <a href="#setup-the-trigger-on-case" id="setup-the-trigger-on-case"></a>

The **SharinPixCase** Apex Trigger automatically processes image uploads for new Case records using the **SharinPixCaseHandler** class. The trigger on the Case object will fire after the creation of a Case record and will initiate the 'move image' operation from the related Pending Album record to the Case record.

```apex
trigger SharinPixCase on Case (after insert) {
	SharinPixCaseHandler handler = new SharinPixCaseHandler();
	if (Trigger.isAfter && Trigger.isInsert) {
		handler.uploadImageOnCase(Trigger.new);
	}
}
```

The **SharinPixCaseHandler** class manages image 'move image' operations to Case records by retrieving temporary IDs associated with the Case records. It first collects these temporary IDs, retrieves corresponding _Pending Album_ records, and maps them to their IDs. For each Case record, it checks for associated albums, extracts the image IDs, and enqueues a job to transfer these images and delete the temporary Pending Album records.

```apex
public with sharing class SharinPixCaseHandler  {  
    public void uploadImageOnCase(List<Case> lstNewCase) {
        // Collect SharinPixTemporaryID values from new Case records
        Set<String> tempIds = new Set<String>();
        List<Case> lstFilteredCase = new List<Case>();
        for (Case cas : lstNewCase) {
            if (cas.sharinPixTemporaryID__c != null) {
                tempIds.add(cas.sharinPixTemporaryID__c);
                lstFilteredCase.add(cas);
            }
        }

        if (tempIds.isEmpty()) { return; }
        
        // Query temporary records (Pending Album records)
        Map<String, List<String>> tempIdToImageIdsMap = new Map<String, List<String>>();  
        List<SharinPixPendingAlbum__c> pendingAlbums = [SELECT Id, ImageIds__c, TemporaryId__c FROM SharinPixPendingAlbum__c WHERE TemporaryId__c IN :tempIds];
        for (SharinPixPendingAlbum__c pendingAlbum : pendingAlbums) {
            // Deserialize JSON string from ImageIds__c into a List<String> to handle image IDs
            List<String> lstImageIds = (List<String>) JSON.deserialize(pendingAlbum.ImageIds__c, List<String>.class);
            if (tempIdToImageIdsMap.containsKey(pendingAlbum.TemporaryId__c)) {
                tempIdToImageIdsMap.get(pendingAlbum.TemporaryId__c).addAll(lstImageIds);
            } else {
                tempIdToImageIdsMap.put(pendingAlbum.TemporaryId__c, lstImageIds);
            }
        }
        
        for (Case cas : lstFilteredCase) {   
            if (tempIdToImageIdsMap.get(cas.sharinPixTemporaryID__c) != null){
                System.enqueueJob(new ImageMoveQueueable(tempIdToImageIdsMap.get(cas.sharinPixTemporaryID__c), cas.Id, cas.sharinPixTemporaryID__c ));
            }
        }
    }
}
```

You can refer to the code snippet below to implement your test class.

```apex
@IsTest
public class SharinPixCaseHandlerTest {

    // method to create mock Case records
    private static List<Case> createMockCases(Integer count, Boolean withTempId) {
        List<Case> cases = new List<Case>();
        for (Integer i = 0; i < count; i++) {
            Case cas = new Case(Subject = 'Test Case ' + i);
            if (withTempId) {
                cas.sharinPixTemporaryID__c = 'TEMPID' + i;
            }
            cases.add(cas);
        }
        return cases;
    }

    // method to create mock SharinPixPendingAlbum__c records
    private static void createMockPendingAlbums(List<String> tempIds) {
        List<SharinPixPendingAlbum__c> albums = new List<SharinPixPendingAlbum__c>();
        for (String id : tempIds) {
            SharinPixPendingAlbum__c album = new SharinPixPendingAlbum__c(
                TemporaryId__c = id,
                ImageIds__c = JSON.serialize(new List<String>{'IMG1' + id, 'IMG2' + id})
            );
            albums.add(album);
        }
        insert albums;
    }

    @IsTest
    static void testCasesWithNoTemporaryId() {
        List<Case> cases = createMockCases(3, false);
        insert cases;
        SharinPixCaseHandler handler = new SharinPixCaseHandler();
        Test.startTest();
        handler.uploadImageOnCase(cases);
        Test.stopTest();
    }

    @IsTest
    static void testCasesWithTemporaryId() {
        List<Case> cases = createMockCases(2, true);
        insert cases;
        createMockPendingAlbums(new List<String>{'TEMPID0', 'TEMPID1'});

        SharinPixCaseHandler handler = new SharinPixCaseHandler();
        Test.startTest();
        handler.uploadImageOnCase(cases);
        Test.stopTest();
    }
    
    @IsTest
    static void testCasesWithMultipleSameTemporaryId() {
        List<Case> cases = createMockCases(2, true);
        insert cases;
        createMockPendingAlbums(new List<String>{'TEMPID0', 'TEMPID0'});

        SharinPixCaseHandler handler = new SharinPixCaseHandler();
        Test.startTest();
        handler.uploadImageOnCase(cases);
        Test.stopTest();
    }
}
```

The **ImageMoveQueueable** class is designed to manage the transfer of images to specific Case records in Salesforce asynchronously. It stores image IDs and a Case ID. When launched, it moves the images to the designated Case record. This process is done in the background, allowing other tasks to process without delay.

```apex
public with sharing class ImageMoveQueueable implements Queueable, Database.AllowsCallouts {
    private List<String> imageIds;
    private Id caseId;
    private String TemporaryID;

    public ImageMoveQueueable(List<String> imageIds, Id caseId, String TemporaryID) {
        this.imageIds = imageIds;
        this.caseId = caseId;
        this.TemporaryID = TemporaryID;
    }

    public void execute(QueueableContext context) {
       	List<SharinPixPendingAlbum__c> pendingAlbumsToDelete = [SELECT Id FROM SharinPixPendingAlbum__c WHERE TemporaryId__c =: TemporaryID];
        delete pendingAlbumsToDelete;
        if(Test.isRunningTest()) { return; }
        sharinpix.Image.moveImages(imageIds, caseId);
    }
}
```

You can refer to the code snippet below to implement your test class.

```apex
@IsTest
public class ImageMoveQueueableTest {

    @IsTest
    static void testImageMoveQueueableExecution() {
        // Setup test data
        Case testCase = new Case(Subject = 'Test Case');
        insert testCase;
        List<String> imageIds = new List<String>{'Image1', 'Image2', 'Image3'};
        String tempID = 'TEMP123';
        ImageMoveQueueable queueable = new ImageMoveQueueable(imageIds, testCase.Id, tempID);
        
        Test.startTest();
        Id jobId = System.enqueueJob(queueable);
        Test.stopTest();

        AsyncApexJob job = [SELECT Status, JobType FROM AsyncApexJob WHERE Id = :jobId];
        System.assertEquals('Completed', job.Status, 'Job has completed after execution.');
    }
}
```

We are now all set!

To test this new implementation, go ahead and open the Flow on the Field Service app to create a new Case record and capture images.

### Demo: See the Photo Upload and Move in Actions <a href="#demo" id="demo"></a>

To test our new implementation:

* Open the SFS mobile app
* Go on a Work Order record
* From the **Show Actions** menu, select the option **Open a Case** to launch the Field Service Mobile Flow
* Once inside the flow, enter the new Case details and click **Next**:

<figure><img src="../../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>

* Next, click on the link **Click to launch the SharinPix App** to launch the SharinPix mobile app so as to capture photos:

<figure><img src="../../.gitbook/assets/image (114).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

* Once back in the Flow, then click on **Next** again followed by **Finish**

Now that the Flow is completed, the images captured will be moved to the newly created Case record when the latter becomes available.

<figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tip:**

SharinPix Images can also be added to SFS Service Reports. How more information about how this is done, please refer to the following article:

[Display Images in Service Report (Salesforce Field Service / FSL)](display-images-in-service-report-salesforce-field-service-fsl.md)
{% endhint %}
