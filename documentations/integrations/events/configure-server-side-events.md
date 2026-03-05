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

# Configure Server-side Events

The current article demonstrates how to configure Server-side SharinPix Events.

{% hint style="success" %}
**Tip:**

For more information about the types of server-side events, you can refer to the following article:

[Types of SharinPix Events](types-of-sharinpix-events.md).
{% endhint %}

{% hint style="warning" %}
**Note:**

1. The following sections make use of Webhooks.

In order to use Webhooks, you should ensure that you have granted API access to SharinPix on your organization. To verify this, go to the **SharinPix Settings** tab and check if the second row, that is, **Sharinpix - > Salesforce full API access**, is highlighted in green.

In case the row, **Sharinpix - > Salesforce full API access** is still highlighted in red, simply click on the **Grant** button to grant API access.

For more detailed information on how to grant API access, please refer the the following article:

[Basic Setup - Step 2 - Register your Salesforce organization to SharinPix](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/basic-setup/basic-setup-step-2-register-your-salesforce-organization-to-sharinpix)

2. All Webhooks of type **apex\_method** make use of Salesforce API and should be used only when needed.
{% endhint %}

## Configure Server-side Events

* Access the SharinPix Admin Dashboard to configure a server-side event.
* Select the **'Webhooks'** menu item from the navigation bar.
* Click on the **'New Webhook'** button.
* Select your current **Salesforce Organization**.
* Select whether to execute an **Apex method** or **make a request to a specific endpoint.**
* Select the type of event to be detected.

<figure><img src="../../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

* Click on **Create V2**, when you are done.

## Webhook in action

The objective of this section is to show how to detect the **New Image** event and call an Apex Method found on the SharinPix Package. The **New Image** event is triggered when a new image is added to a SharinPix Album. After detecting this event, the **newImage** method from the **ImageSyncMigration** class will be called and therefore perform a **resync** on the newly-added image.

* The Webhook is configured as shown in the screenshot below where the method to be executed and the event that triggers this execution, are specified.

![](<../../.gitbook/assets/image (58).png>)

* In this context, the related list of SharinPix Images and the SharinPix Album is present on the page-layout and page of the Account Object respectively.
* A new image is added to the SharinPix Album as shown below.

<figure><img src="../../.gitbook/assets/image (59) (1).png" alt=""><figcaption></figcaption></figure>

* Once the image has been uploaded, you need to refresh the current page. A new entry in the SharinPix Images related list has been added as shown in the image below.

<figure><img src="../../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>
