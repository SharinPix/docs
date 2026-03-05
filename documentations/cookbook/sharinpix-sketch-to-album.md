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

# SharinPix Sketch to Album

The **SharinPix Sketcher** is a Salesforce custom Object that stores your sketch templates with its annotations. To view your sketches, you must add the **SharinPix Sketcher** Lightning Web Component on your record page.

{% hint style="info" %}
**Pre-requisites**

* [SharinPix Album](../lightning-web-component/sharinpix-album-lwc.md)
* [SharinPix Sketcher](../lightning-web-component/sharinpix-sketcher.md) already set up
* [SharinPix Sketch Permission set](../access-and-security/sharinpix-permission-sets.md).
{% endhint %}

SharinPix provides a feature to upload your sketches to your specified SharinPix Album. A global class, **SharinPixSketch**, is available in the package with the **uploadSketchToAlbum** method to upload the sketch template to an album. When a SharinPix Sketch is uploaded to a SharinPix Album, the image is saved as an SVG with its annotations. These annotations can still be edited on the SharinPix Album (with the required SharinPix Album Permission).

![](<../.gitbook/assets/SharinPix Sketch 1 (1).png>)

## How to use the SharinPixSketch upload feature

The global class **SharinPixSketch** provides the method upload which takes 2 parameters:

* Object Record Id (The record Id where the destinated SharinPix Album is situated)
* SharinPix Sketch Id (The Id of the Sketch you want to upload)

### Using SharinPixSketch upload in a Record Triggered Flow

You can use the upload method in a record triggered flow by implementing an InvocableMethod in a global Apex class. Below is an example:

```apex
global with sharing class sketchToAlbumAutomation {
    @InvocableMethod
    public static void uploadSketchToAlbum(List<Params> paramsList) {
        for (Params param : paramsList) {
            sharinpix.SharinPixSketch.upload(param.recordId, param.sketchId);
        }
    }

    global class Params {
        @InvocableVariable(label='Album Id' description='Record Id of the record the SharinPix Album you want to upload' required=true)
        global Id recordId;

        @InvocableVariable(label='Sketch Id' description='The Id of the SharinPix Sketch you want to upload' required=true)
        global Id sketchId;
    }
}
```

This class contains an InvocableMethod invoking the upload method from the **SharinPixSketch** class.

A global class Params is defined with 2 InvocableVariables recordId and sketchId. This class can now be used as an Apex Action in our Record Triggered Flow.

Below is an example how to build our flow:

![](<../.gitbook/assets/image (56) (4).png>)

* Here we have configure of our flow to trigger upon creation or update of an existing Sketch.
* The entry condition is set to whenever the last modified date is changed.
* We have also to include an Asynchronous path since the upload method performs a callout.

![](<../.gitbook/assets/image (57) (4).png>)

* On the asynchronous path we include an Apex action and select the newly created global class sketchToAlbumAutomation.
* We set the Album Id to the triggering SharinPix Sketch's Parent Id (Which is the record Id on which the sketch was created and where my SharinPix Album is found) Note: If your SharinPix Album is not found on the same record page your sketch was created, create a new resource to store the Album Id and assign it to the InvocableVariable Album Id.
* We set the Sketch Id to the triggering record's Id

{% hint style="info" %}
Please note that this is a simple example how to use the **SharinPixSketch** upload feature in a record trigger flow. The final result will look like this:&#x20;
{% endhint %}

![](<../.gitbook/assets/image (58) (4).png>)

### Using SharinPixSketch upload in an Apex Trigger

An Apex trigger can also be implemented to use the sketch upload feature.

* Create a new Apex class including a method with the @future(callout=true) annotation. This method will call the **SharinPixSketch** upload method.

{% hint style="success" %}
This new method is needed because callout cannot be done synchronously in Apex Trigger.
{% endhint %}

```apex
public with sharing class sketchUploadController {
    @future(callout=true)
    public static void uploadSketch(Id recordId, Id sketchId) {
        try {
            sharinpix.SharinPixSketch.upload(recordId, sketchId);
        } catch (Exception e) {
            throw new Exception(e.getMessage());
        }
    }
}
```

* The method uploadSketch will invoke the upload method from **SharinPixSketch** with parameters recordId (Album Id) and Sketch Id
* Create an Apex Trigger that will call the sketchUploadController.

```apex
trigger SharinPixSketchToAlbumTrigger on sharinpix__Sketch__c (after insert) {
    if(Trigger.isAfter) {
        if(Trigger.isInsert) {
            for (sharinpix__Sketch__c sketch : Trigger.new) {
                sketchUploadController.uploadSketch(sketch.sharinpix__ParentId__c, sketch.Id);
            }
        }
    }
}
```

This apex trigger will be invoked every time a SharinPix Sketch is created. For each sketch it will call the sketchUploadController which in turn will perform the sketch upload to SharinPix Album.

### Using SharinPixSketch upload in a LWC

This section provides an example how to integrate the **SharinPixSketch** upload feature in a LWC

One simple example is to create a Lightning button that will upload all SharinPix Sketches from the record to its SharinPix Album.

Step 1 is to build an upload controller

```apex
public with sharing class sketchUploadController {
    @AuraEnabled
    public static void uploadSketch(Id recordId) {
        try {
            List<sharinpix__Sketch__c> lstSketch = [SELECT Id FROM sharinpix__Sketch__c WHERE sharinpix__ParentId__c = :recordId WITH USER_MODE];
            for(sharinpix__Sketch__c sketch : lstSketch) {
                sharinpix.SharinPixSketch.upload(recordId, sketch.Id);
            }
        } catch (Exception e) {
            throw new AuraHandledException(e.getMessage());
        }
    }
}
```

Then create a LWC with a Lightning button calling the uploadSketch function.

Html:

Javascript:

```javascript
import { LightningElement, api } from 'lwc'
import uploadSketch from '@salesforce/apex/sketchUploadController.uploadSketch'

export default class UploadSketchToAlbum extends LightningElement {
@api recordId

async handleSketchToAlbum () {
    try {
        await uploadSketch({ recordId: this.recordId })
    } catch (error) {
        console.error(`error uploading sketch to album ${error}`)
    }
}
}
```

The **SharinPixSketch** upload feature can be implemented in various ways according to your use case. Above were some basic implementations in each category how to use the global **upload** method to upload your **SharinPix Sketches** onto a **SharinPix Album**.

## Need help to implement your SharinPixSketch upload ?

The visual experts are here to help. Just send an email to <mark style="color:blue;">support@sharinpix.com</mark> to get some help so we can explain you how we can deliver services through our experts to assist you on that duty!
