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

# Image Sync not working when using SharinPix mobile app to upload photos. What should I do?

If you are encountering issues with SharinPix Image Sync when uploading photos via the **SharinPix mobile app** , here are some configurations that need to be looked into:

* **Check if API access has been granted to SharinPix**\
  \
  The first thing that needs to be checked is whether you have granted API access to SharinPix since this is required when using SharinPix Webhooks. To verify this, go to the **SharinPix Settings** tab on your organization and check if API access has been granted. For more information on this part, please refer to the following article:\
  \
  [Basic Setup - Step 2 - Register your Salesforce organization to SharinPix](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/basic-setup/basic-setup-step-2-register-your-salesforce-organization-to-sharinpix)
* **Check if the SharinPix Webhook has been configured correctly**

Issues linked to Image Sync when uploading photos via the Salesforce mobile app may also be due to an incorrect SharinPix Webhook configuration.

Some key-points that needs to be verified for a Webhook configuration are:

1\. whether the class name (that is, **sharinpix.ImageSyncMigration**) has been entered correctly

2\. whether the method name (that is, **uploadDone**) has been entered correctly

3\. whether the **Upload done** checkbox has been checked

{% hint style="warning" %}
**Note:**

When using the method **uploadDone** in the Webhook configuration, the **Upload done** checkbox should be checked.
{% endhint %}

You can refer to the following article as reference to cross-check Webhook configurations set up on your SharinPix global settings:

[Image Sync for pictures uploaded via SharinPix Mobile App](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/image-sync-for-pictures-uploaded-via-sharinpix-mobile-app)

{% hint style="success" %}
**Tip for developers:**

You can also access detailed information about the responses using the link to **Webhook Deliveries** which is available on the SharinPix admin dashboard.

**Note:** Successful **Webhook Deliveries** logs are kept for a maximum of three months in our records.

To access the Webhook deliveries, go on the admin dashboard then click on **Webhooks** on the top menu. The link to the Webhook deliveries will be available form there.
{% endhint %}
