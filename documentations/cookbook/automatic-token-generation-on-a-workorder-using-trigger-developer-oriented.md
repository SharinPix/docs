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

# Automatic token generation on a WorkOrder using Trigger (Developer-oriented)

In this demo, we will demonstrate how to generate a token automatically on any newly-created WorkOrder objects.

To implement this, we will:

1. Create a custom field on the WorkOrder object to hold the generated token.
2. Create a Trigger to generate a SharinPix token value upon creation of a WorkOrder record.

{% hint style="danger" %}
For more information about the implementation presented in this article, make sure that you go through the **Note** section highlighted in yellow at the end of the article.
{% endhint %}

## Creation of the custom field

Create a custom field on the object WorkOrder to retrieve the SharinPix token using the following information:

* Field Label: **SharinPix Token**
* Field Name: **SharinPix\_Token**
* Date Type: **Long Text Area**
* length: 32, 768

## Creation of the WorkOrder Trigger

Implement a WorkOrder Trigger to generate a SharinPix Token Value when a WorkOrder record is inserted. This token will match the SharinPix Album to its corresponding record. Implement the WorkOrder Trigger using the code snippet below:

```apex
trigger SharinPixWorkOrderTrigger on WorkOrder (after insert, before update) {
    sharinpix.Client clientInstance = sharinpix.Client.getInstance();
    String token, appUrl;
    List<WorkOrder> updatedWOrders = new List<WorkOrder>();
    for (WorkOrder wOrder : Trigger.new) {
        if (String.isBlank(wOrder.SharinPix_Token__c) || String.isBlank(wOrder.SharinPix_App_URL__c)) {
            token = sharinpix.Client.getInstance().token(
                new Map<String, Object> {
                    'album_id' => wOrder.Id,
                    'exp' => 0,
                    'path' => '/pagelayout/' + wOrder.Id,
                    'abilities' => new Map<String, Object> {
                        wOrder.Id => new Map<String, Object> {
                            'Access' => new Map<String, Boolean> {
                                'see' => true,
                                'image_list' => true,
                                'image_upload' => true,
                                'image_delete' => true
                            }
                        },
                        'Display' => new Map<String, Object> {
                            'tags'=> true
                        }
                    }
                }
            );
            appUrl = 'sharinpix://upload?token=' + token;
            if (Trigger.isInsert) {
                updatedWOrders.add(new WorkOrder(
                    Id = wOrder.Id,
                    SharinPix_Token__c = token,
                    SharinPix_App_URL__c = appUrl
                ));
            } else {
                wOrder.SharinPix_Token__c = token;
                wOrder.SharinPix_App_URL__c = appUrl;
            }
            
        }
    }
    if (Trigger.isInsert) { update updatedWOrders; }
}
```

The source code for the Apex Class of the above Apex Trigger can be found below:

```apex
@isTest
public class SharinPixWorkOrderTriggerTest {

    @isTest
    public static void testWorkOrderTrigger() {
        WorkOrder wOrder = new WorkOrder(Subject='Visiting Green Field');
        Test.startTest();
        insert wOrder;
        Test.stopTest();
        List<WorkOrder> expectedWorkOrder = [
                                            	SELECT Id, Subject, SharinPix_App_URL__c, SharinPix_Token__c
                                                FROM WorkOrder
                                                WHERE Id = :wOrder.Id
                                                LIMIT 1
 											];
        System.assertEquals('Visiting Green Field', expectedWorkOrder[0].Subject);
        System.assert(expectedWorkOrder[0].SharinPix_App_URL__c.startsWith('sharinpix://upload?token='));
        System.assert(expectedWorkOrder[0].SharinPix_Token__c.length() > 0);
    }
}
```

{% hint style="info" %}
You can find this **Trigger source** in Github here: [SharinPix Mobile App Launcher (FSL](https://github.com/SharinPix/demo-apex/tree/fsl_workorder_trigger/src))
{% endhint %}

{% hint style="warning" %}
**Note:**

1\. The value stored in the SharinPix App URL field is a link to the SharinPix mobile app. Such URL is used to upload images using the SharinPix app and store the uploaded images on the record specified in the token.

To use this link, you should ensure that the SharinPix mobile app has been installed on your device. For more information on where to install the SharinPix mobile app, refer to the article below:

[Where to find the App](../mobile-app/where-to-find-the-sharinpix-mobile-app.md)

2\. For more information about how to **only generate SharinPix mobile tokens automatically used to upload photos from the SharinPix mobile app** , refer to this article:

[SharinPix automatic upload token generation (Admin Friendly)](../mobile-app/sharinpix-automatic-mobile-upload-token-generation-admin-friendly.md)

2\. The token generated in the SharinPix Token field can also be used to open the SharinPix album within the SharinPix mobile app using the app's online mode feature. For more information on how to make use of the online mode feature, refer to the following article:

[SharinPix Mobile App: Online mode](../mobile-app/sharinpix-mobile-app-online-mode.md)
{% endhint %}

To test the previous implementations, create a new WorkOrder record. The generated token will be found in the **SharinPix Token** field of the newly-created record as shown below:

![](<../.gitbook/assets/ab1 (1) (2).png>)
