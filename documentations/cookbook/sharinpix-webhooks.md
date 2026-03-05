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
  actions:
    visible: true
---

# SharinPix Webhooks

## Enrich image data through Webhooks

### What is a Webhook?

A WebHook is a callback request (HTTP POST) made to a specific URL when something happens.

In our case, we have these configurable Webhooks available:

* New image
* Processed image
* New publication
* New tag image
* Delete image
* Delete tag image
* Upload done

These callbacks can be configured on the admin page, in the Webhooks section. You can provide the URL on which you want the Webhook (callback) to occur.

{% hint style="info" %}
Webhook delivery failures are **Technical Errors**. Choose their recipients in [Notification settings](../access-and-security/notification-settings.md).
{% endhint %}

{% hint style="danger" %}
Please note that the **New einstein prediction** event has been deprecated and should not be activated.
{% endhint %}

{% hint style="success" %}
**Tip**:

For more information on those events and how they are triggered, refer to the following article: [Types of SharinPix Events](../integrations/events/types-of-sharinpix-events.md)
{% endhint %}

{% hint style="warning" %}
**Note:**

1\. In order to use Webhooks, you should ensure that you have granted API access to SharinPix on your organization. To verify this, go to the **SharinPix Settings** tab and check if the second row, that is, **Sharinpix -> Salesforce full API access**, is highlighted in green.

In case the row, **Sharinpix -> Salesforce full API access** is still highlighted in red, simply click on the **Grant** button to grant API access.

For more detailed information on how to grant API access, please refer the the following article:

[Basic Setup - Step 2 - Register your Salesforce organization to SharinPix](../getting-started-with-sharinpix/basic-setup/basic-setup-step-2-register-your-salesforce-organization-to-sharinpix.md)

2\. All Webhooks of type **apex\_method** make use of Salesforce API and should be used only when needed.
{% endhint %}

![](<../.gitbook/assets/sharinpix (1) (2).png>)

### Types of webhooks

1. [Call to URL with JSON payload using HTTP POST](sharinpix-webhooks.md#call-to-url-with-json-payload-using-http-post)
2. [Call to a static method in an Apex class](sharinpix-webhooks.md#call-to-a-static-method-in-an-apex-class)

To configure a webhook along with its endpoint url, access the Admin Dashboard and follow the instructions below.

### Call to URL with JSON payload using HTTP POST

* Select the ‘**Webhooks** ’ menu item from the navigation bar.
* Click on the ‘**New Webhook** ’ button.
* Enter the relevant details for the Webhook.

![](<../.gitbook/assets/image (53) (3).png>)

### Call to a static method in an Apex class

In this case, we will use another type of webhook which will execute a static method on your Salesforce environment. The sample code below illustrates an example method which is called by a webhook.

```apex
public class Webhook {
    public static void perform(string payload, string webhookInformation){
        // your business logic here
    }
}
```

* **payload** is the json string containing the relevant actions.
* **webhookInformation** contains information about the webhook such as the event type.

Next:

1. Go to the SharinPix Administration dashboard.
2. Click on the **Webhooks** menu followed by the **New Webhook** button.
3. Select **apex\_method** as the _Action type_ and insert the class name and method name.
4. Then, select the desired event.
5. Click on **Update V2** to save the configuration.

![](<../.gitbook/assets/image (54) (3).png>)
