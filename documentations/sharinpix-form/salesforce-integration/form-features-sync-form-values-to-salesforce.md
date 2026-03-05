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

# Form Features - Sync Form values to Salesforce

{% hint style="info" %}
SharinPix Form Elements can be configured and mapped to Salesforce record fields, enabling the automatic updating of those fields with the responses provided in your form. This functionality allows for the update of the parent record from which the form was initiated. The configuration process is carried out directly within the [_SharinPix Form Template Editor_](../form-elements/sharinpix-form-template-editor.md).



This documentation covers:

* [How to Configure your Form to Sync with Salesforce Record Fields](form-features-sync-form-values-to-salesforce.md#how-to-configure-your-form-template-to-synchronize-with-your-salesforce-parent-object-record)
* [Demo: Synchronizing SharinPix Form values to an Account record](form-features-sync-form-values-to-salesforce.md#demo-synchronizing-sharinpix-form-values-to-a-parent-account-record)
* [Demo: Synchronizing SharinPix Form values to the Response record](form-features-sync-form-values-to-salesforce.md#demo-synchronizing-sharinpix-form-values-to-the-response-record)
{% endhint %}

{% hint style="warning" %}
**Prerequisite:**



Before using this feature, ensure:

* Ensure that you are using the most recent version of the SharinPix Package. Follow this document to [upgrade the SharinPix package](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)
* Users have the [**SharinPix Forms Admin permission set**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/sharinpix-permission-sets) assigned.
{% endhint %}

## Getting Started

### How to configure your Form Template to synchronize with your Salesforce parent object record.

To configure your Form Template for the Sync feature, please follow these steps:

1. Open the [**SharinPix Form Template Editor**](../form-elements/sharinpix-form-template-editor.md) for the relevant Form Template.
2. Select the desired **Question** element within the form.
3. Navigate to the **"Advanced" tab** in the question configuration settings.
4. In the **"Push this value to update a Salesforce field"** section, enter the appropriate Salesforce Field API Name of the parent object in the Field API Name field.

{% hint style="danger" %}
**Alert**\
\
The synchronization of Form Responses with parent record fields will only function if the response contains a ParentRecordId. For instance, when a response is submitted through a [**Form Launcher LWC**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-form-launcher) on an Account record, the ParentRecordId will be set to the Account's record ID.
{% endhint %}

Once the configuration is completed, submitting a Form Response will automatically update the corresponding fields of the parent record with the answers provided in the form. This update will align with the field data type and access rights, ensuring that the data is correctly mapped and reflected in the parent record.

## Demo: Synchronizing SharinPix Form values to a Parent Account record

### Step 1: Build and configure a SharinPix Form with the Sync Feature

<figure><img src="../.gitbook/assets/Sync back to salesforce documentation (3).png" alt=""><figcaption></figcaption></figure>

The above image illustrates the configuration process:

1. Identify the field on your parent record that you wish to update upon submission of the form response.
2. Copy the Salesforce Field API Name of the identified field and paste it into the **Push** section of the form question's configuration.

Once the configuration is complete, the specified field will be updated every time a form response is submitted with the corresponding parent record. The update will be performed based on the field's data type and the user's edit access rights.

### Step 2: Launch your Form from your parent record

The screenshot below shows a form being launched from an _Inspection_ record, and we want to sync the following fields:

* Inspector
* Fire doors open and close correctly
* Number of Fire Extinguishers
* Fire Extinguisher Visible

<figure><img src="../.gitbook/assets/Sync back to salesforce documentation (1) (1).png" alt=""><figcaption></figcaption></figure>

Our SharinPix Form Template has already been configured with the above field API names to synchronize back to the parent record and update the corresponding fields.

### Step 3: Fill and submit the SharinPix Form

Once the form has been submitted, the Inspection record fields will be updated.

<figure><img src="../.gitbook/assets/3 (3).png" alt=""><figcaption></figcaption></figure>

## Demo: Synchronizing SharinPix Form values to the Response record

<figure><img src="../.gitbook/assets/Sync back to salesforce documentation.png" alt=""><figcaption></figcaption></figure>

To automatically map form answers to specific fields on your Form Response Object, follow these steps:

1. Identify the Target Field: Choose the field on your Form Response record that you want to update.
2. Copy the API Name: Locate the Salesforce Field API Name for that field.
3. Configure the Sync: In the form question’s settings, paste the API name into the **Push** section using this syntax: `$response.<FIELD_API_NAME>`.

Upon submission, the field will update automatically on the Response record that was created.

<figure><img src="../.gitbook/assets/Sync back to salesforce documentation (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

If an error occurs while updating one of the fields (e.g., the Salesforce field's datatype trying to update is incompatible, or the user does not have access to the field), it will stop the sync process and the other configured fields will not be synced.&#x20;
{% endhint %}
