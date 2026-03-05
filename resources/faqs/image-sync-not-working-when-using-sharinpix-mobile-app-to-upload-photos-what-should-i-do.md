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
  anchors:
    visible: true
---

# Image Sync not working when using SharinPix Mobile App to upload photos. What should I do?

If you are encountering issues with SharinPix Image Sync when uploading photos via the **SharinPix mobile app**, here are some configurations that need to be looked into:

#### 1. Verify SharinPix API access

SharinPix requires API access to communicate with your Salesforce organization and process Webhooks.

To verify the connection:

1. Open the **SharinPix Settings** tab in Salesforce.
2. Confirm that API access has been granted.
3. If required, click **Grant** to re-authorize the connection.

For more information, refer to:

[Basic Setup – Step 2 – Register your Salesforce organization to SharinPix](https://docs.sharinpix.com/getting-started/basic-setup/basic-setup-step-2-register-your-salesforce-organization-to-sharinpix#connect-to-sharinpix-for-the-first-time-grant-api-access-go-to-admin-dashboard)

***

#### 2. Verify the Image Sync configuration

Make sure an **Image Sync** has been correctly configured for the Salesforce object where the photos are being uploaded.

Check the following:

* A SharinPix Image Sync setting for the same Salesforce object is created, and its configuration is **Active**.
* The **Parent Object Name** is correct. This value must correspond to the Salesforce **Object API Name**.\
  For example, for a custom object named **My Custom Object**, the value should be `My_Custom_Object__c`.
* The **Parent Field Name** is correct. This value must correspond to the **API name of the Lookup field** on the SharinPix Image object that links the image to the parent record.

To verify your configuration, refer to:\
[Setup SharinPix Image Sync](https://docs.sharinpix.com/documentation/image-sync/setup-sharinpix-image-sync)

***

**3. Verify the required permissions**

A commonly missed step is the assignment of the **SharinPix Image Sync Permission** permission set. Make sure the permission set is assigned to:

* The user uploading the photos
* The **API User**, meaning the user who granted API access to SharinPix

If your Image Sync configuration uses **custom fields on the SharinPix Image object**, such as a custom Lookup field used to associate the image with another Salesforce record, make sure the relevant users also have access to those fields.

For these custom fields, we recommend creating a dedicated **Permission Set** that provides at least:

* **Read access**
* **Edit access**

This Permission Set should also be assigned to the users and API User involved in the Image Sync process.

***

#### 4. Verify the SharinPix Webhook configuration

If Image Sync is still not working, review the Webhook configuration in the SharinPix Admin Dashboard.

Make sure the following values are configured correctly:

1. **Class Name:** `sharinpix.ImageSyncMigration`
2. **Method Name:** `synchronize`
3. **Event:** **Upload done** should be enabled

{% hint style="warning" %}
**Important:** When using the `synchronize` method, the Webhook must be configured to trigger on **Upload done** or another appropriate event.
{% endhint %}

You can use the following documentation to verify the configuration:

[Image Sync for pictures uploaded via SharinPix Mobile App](https://docs.sharinpix.com/documentation/image-sync/image-sync-for-pictures-uploaded-via-sharinpix-mobile-app)

{% hint style="success" %}
**Tip for developers:**

You can also access detailed information about the responses using the link to **Webhook Deliveries,** which is available on the SharinPix admin dashboard.

**Note:** Successful **Webhook Deliveries** logs are kept for a maximum of three months in our records.

To access the Webhook deliveries, go to the Admin Dashboard, then click on Webhooks in the top menu. The link to the Webhook deliveries will be available from there.
{% endhint %}

***

#### 5. Flows, Apex Triggers, or Validation Rules preventing creation of SharinPix Image records

It can happen that Flows, Apex Triggers, or Validation Rules block the creation of SharinPix Image records. If you have Flows, Apex Triggers, or Validation Rules on the SharinPix Image Object, it is advisable to investigate and check whether they are blocking the SharinPix Image Sync.

{% hint style="info" %}
For more troubleshooting on Image Sync/Webhook Errors, refer to this documentation: [Troubleshooting: Image Sync / Webhook Errors - Inaccessible Fields Error](troubleshooting-image-sync-webhook-errors-inaccessible-fields-error.md)
{% endhint %}
