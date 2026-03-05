# SharinPix Mobile App: Online mode

This article demonstrates how to construct a SharinPix URL or deeplink that allows access to online features such as SharinPix images, albums and search within the SharinPix mobile app itself.

## Deeplink format

The SharinPix online mode has the the following deeplink format:

<mark style="color:red;">`sharinpix://online?token=`</mark>_<mark style="color:red;">**`<SharinPix Online Token>`**</mark>_<mark style="color:red;">`&host=app.sharinpix.com`</mark>

{% hint style="warning" %}
**Note:**

* The section _<mark style="color:red;">**`<SharinPix Online Token>`**</mark>_ should be replaced by the desired [SharinPix Online Token](../access-and-security/online-token-generation-methods.md).
* The SharinPix online mode is also compatible with SharinPix universal links. The SharinPix online mode format for universal links is as follows:

https://app.sharinpix.com/native\_app/online?token=_**\<SharinPix Online Token>**_\&host=app.sharinpix.com
{% endhint %}

{% hint style="info" %}
**Limitations:**

The SharinPix Online mode works only when there's an active internet connection.
{% endhint %}

### Title Parameter

The **title** parameter can be added to the SharinPix online mode deeplink to display a title on the page within the SharinPix mobile app.

The deeplink format with a title parameter (View Album) is as follows:

<mark style="color:red;">`sharinpix://online?token=`</mark>_<mark style="color:red;">**`<SharinPix Online Token>`**</mark>_<mark style="color:red;">`&`</mark><mark style="color:red;">**`title=View%20Album`**</mark><mark style="color:red;">`&host=app.sharinpix.com`</mark>

Being a URL, the space is encoded to be <mark style="color:red;">`%20`</mark>.

<figure><img src="../.gitbook/assets/Image from Gradio (29).png" alt=""><figcaption></figcaption></figure>

### Online Mode Use Case Examples

The above deeplink can take SharinPix various types of SharinPix Online Token such as token that allows:

* Access a specific SharinPix album. The code snippet below demonstrates how to generate a token that will open a SharinPix album and save the generated token in a Salesforce field:

```apex
trigger SharinPixWorkOrderTrigger on WorkOrder (after insert, before update) {
    sharinpix.Client clientInstance = sharinpix.Client.getInstance();
    String token;
    List<WorkOrder> updatedWOrders = new List<WorkOrder>();
    for (WorkOrder wOrder : Trigger.new) {
        if (String.isBlank(wOrder.SharinPix_Online_Token__c)) {
            token = sharinpix.Client.getInstance().token(
                new Map<String, Object> {
                    'Id' => wOrder.Id,
                    'exp' => 0,
                    'path' => '/pagelayout/' + wOrder.Id,
                    'is_mobile' => true,
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
                    },
                    'anonymousUser' => true
                }
            );
            if (Trigger.isInsert) {
                updatedWOrders.add(new WorkOrder(
                    Id = wOrder.Id,
                    SharinPix_Online_Token__c = token
                ));
            } else {
                wOrder.SharinPix_Online_Token__c = token;
            }
            
        }
    }
    if (Trigger.isInsert) { update updatedWOrders; }
}
```

You can refer to the code snippet below to implement the test class.

```apex
@isTest
public class SharinPixWorkOrderTriggerTest {
	private static WorkOrder wOrder;

    @isTest
    public static void testWorkOrderTrigger() {
        wOrder = new WorkOrder(Subject='Test Work Order');
        Test.startTest();
        insert wOrder;
        List<WorkOrder> expectedWorkOrder = [
            SELECT Id, Subject, SharinPix_Token__c
            FROM WorkOrder
            WHERE Id = :wOrder.Id
            LIMIT 1
        ];
        Test.stopTest();
        System.assertEquals('Test Work Order', expectedWorkOrder[0].Subject);
        System.assert(expectedWorkOrder[0].SharinPix_Token__c.length() > 0);
    }

    @isTest
    public static void testWorkOrderUpdate() {
        WorkOrder expectedWorkOrder = [
            SELECT Id, Subject, SharinPix_Token__c
            FROM WorkOrder
            LIMIT 1
        ];
        expectedWorkorder.Subject = 'Test Work Order';
        Test.startTest();
        update expectedWorkOrder;
        Test.stopTest();
        System.assert(expectedWorkOrder.SharinPix_Token__c.length() > 0);
    }
}
```

{% hint style="warning" %}
**Note:**

To enable the [SharinPix Image Sync feature](../image-sync/what-is-sharinpix-image-sync.md) on the Online Mode albums, a Wehbook configuration is needed on top of the [standard SharinPix Image Sync configuration](../image-sync/setup-sharinpix-image-sync.md).

To trigger the SharinPix Image Sync when images are uploaded and deleted, the Webhook should be configured with the **Upload Done** and **Delete Image** events as depicted below.

In case you want to trigger the SharinPix Image Sync when tagging and untagging images, the **New Tag Image** and **Delete Tag Image** events should be enabled.

For steps on how to configure the Webhook, refer to [this link](../image-sync/image-sync-for-pictures-uploaded-via-sharinpix-mobile-app.md#how-to-configure-the-webhook).
{% endhint %}

![](<../.gitbook/assets/Screenshot 2024-03-13 at 11.55.26 AM.png>)

* Access a specific SharinPix image for viewing or annotation. For more information on how to generate a token that will open a specific image, refer to this article: [Open a specific image in Full View](../cookbook/open-a-specific-image-in-full-view.md)
* Access to a SharinPix Search. The code snippet below demonstrates how to generate a token that will open a SharinPix search:

```apex
List<Contact> contacts = [SELECT Id FROM Contact WHERE AccountId =: accountId];
String queryStr = '';
for (Contact contact : contacts) {
	queryStr += '"' + contact.Id + '" ';
}

String token = sharinpix.Client.getInstance().token(
                new Map<String, Object> {
                    'path' => '/search?search_bar=false',
                    'q' => queryStr,
                    'download' => true
                }
            );
```

{% hint style="success" %}
**Tip:**

For more information on the SharinPix Search implementation, refer to the following article:

[Using your personalized Search](../features/search-images/using-your-personalized-search.md)
{% endhint %}
