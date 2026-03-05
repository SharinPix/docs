# Troubleshooting: Image Sync / Webhook Errors - Inaccessible Fields Error

If images uploaded to SharinPix display correctly in the album viewer, but the **corresponding Salesforce image records (**`sharinpix__SharinPixImage__c`) are not being created or updated, or if you receive webhook failure notifications mentioning **"fields being inaccessible"** or **"Access denied"**, follow the checklist below to verify and resolve the configuration.

### Common Symptoms & Error Messages

* **Missing Records**: Images appear in the SharinPix album component, but the `SharinPix Images` related list remains empty.
* **PDF / Query Errors**: Generating a PDF or running reports throws:\
  `"An error has occurred while querying for SharinPix Images. Please contact your System Administrator."`
* **Webhook Delivery Notifications**:
  * `"System.DmlException: Operation failed due to fields being inaccessible on Sobject sharinpix__SharinPixImage__c, check errors on Exception or Result!"`
  * `"Access to entity 'sharinpix__SharinPixImage__c' denied"`
  * `"You do not have access to the Apex class named: WS_ImageSync"`

{% hint style="warning" %}
Important:

Newer packages enforce stricter Salesforce security and Field-Level Security (FLS) checks, which may surface permission errors if existing profiles or permission sets lack access to newly validated fields.

Ensure the relevant permission sets or profile permissions are updated accordingly.
{% endhint %}

### Step-by-Step Resolution Guide

#### 1. Assign Required Permission Sets to the API User & End Users

The **API User** (the Salesforce user account that was used to [grant API access](https://docs.sharinpix.com/getting-started/basic-setup/basic-setup-step-2-register-your-salesforce-organization-to-sharinpix#connect-to-sharinpix-for-the-first-time-grant-api-access-go-to-admin-dashboard) to SharinPix during the initial setup), as well as the users involved in the Image Sync process, must have the appropriate permissions.

Make sure the following permission sets are assigned where applicable:

* **SharinPix Image Sync Permission** — provides the permissions required to work with SharinPix Image records.
* **SharinPix Lightning Components** — provides access required by the SharinPix components and related package functionality.
* **SharinPix Image Sync for Community Users** — assign this when Image Sync is being used by Community / Experience Cloud users.

#### Custom fields

If the Image Sync configuration uses **custom fields on the SharinPix Image object**, such as a custom Lookup field associating the image with another Salesforce record, those fields also require the appropriate Field-Level Security.

We recommend creating a dedicated Permission Set providing:

* **Read access**
* **Edit access**

Assign this Permission Set to both:

* Users uploading the images
* The SharinPix API User

If the Lookup points to a custom object, also verify that the API User has the necessary access to that Salesforce object.

***

#### 2. Verify the Image Sync Configuration

Make sure an active `SharinPixSyncSetting` Metadata exists for the Salesforce object where the images are being uploaded.

Go to:

**Setup → Custom Metadata Types → SharinPix Sync Setting → Manage Records**

Verify that:

* The configuration is **Active**.
* **Parent Object Name** contains the correct Salesforce Object API Name.
* **Parent Field Name** contains the correct API name of the Lookup field on the SharinPix Image object.

For example, if the Salesforce object is a custom object called **My Custom Object**, the Parent Object Name may be:

`My_Custom_Object__c`

Carefully check the custom field and object API names, including the `__c` suffix where applicable.

For more information, refer to: [Setup SharinPix Image Sync](https://docs.sharinpix.com/documentation/image-sync/setup-sharinpix-image-sync)

***

#### 3. Verify SharinPix Package License Assignment

Ensure the API User has an active package license:

1. From Salesforce Setup, search for **Installed Packages**.
2. Locate **SharinPix** and click **Manage Licenses**.
3. Confirm that the **API User** is listed under licensed users. If missing, click **Add Users** and assign a license.

Also, verify that the API User is **active and not frozen**.

***

#### 4. Verify & Refresh SharinPix API Access

If the OAuth session or Connected App authorization has expired:

1. Open the Salesforce **App Launcher** and search for **SharinPix Settings**.
2. Check the **API Connection** section.
3. If the connection is broken or expired, click [**Grant API Access**](https://docs.sharinpix.com/getting-started/basic-setup/basic-setup-step-2-register-your-salesforce-organization-to-sharinpix#connect-to-sharinpix-for-the-first-time-grant-api-access-go-to-admin-dashboard) (or **Re-Grant Access**) using an active System Administrator account with a SharinPix license.

***

### 🔄 How to Backfill / Resync Missing Images

Once the permissions and settings are corrected, any images uploaded while the sync was failing can be reprocessed in bulk without re-uploading.

_(Refer to_ [_How to use Image Sync on multiple albums (batch)_](https://docs.sharinpix.com/documentation/image-sync/how-to-use-image-sync-on-multiple-albums-batch) _for detailed information on the resync.)_
