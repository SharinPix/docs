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

# Import Form PDF as Content Document using Flow (Admin-Oriented)

## Overview

{% hint style="info" %}
The <mark style="color:red;">`FormResponseContentDocAutomation`</mark> Invocable Apex method allows users to automatically import a PDF generated from a SharinPix Form Response into Salesforce as a Content Document.

This invocable method is designed for use in Salesforce Flows and is compatible with automation for different types of form workflows.

This article covers the following :

1. [FormResponseContentDocAutomation's Input Parameters](import-form-pdf-as-content-document-using-flow-admin-oriented.md#input-parameters)
2. [Flow Setup](import-form-pdf-as-content-document-using-flow-admin-oriented.md#flow-setup)
   * [Step 1: Configure a Record-Triggered Flow](import-form-pdf-as-content-document-using-flow-admin-oriented.md#step-1-configure-a-record-triggered-flow)
   * [Step 2: Add the Import Action](import-form-pdf-as-content-document-using-flow-admin-oriented.md#step-2-add-the-import-action)
   * [Step 3: Save and Activate the flow](import-form-pdf-as-content-document-using-flow-admin-oriented.md#step-3-save-and-activate)
   * [Step 4: Fill and Submit Form](import-form-pdf-as-content-document-using-flow-admin-oriented.md#step-4-fill-and-submit-the-form)
{% endhint %}

{% hint style="warning" %}
**Prerequisites**

Before configuring this automation, ensure the following:

* You have the latest **SharinPix Package** installed. You can follow [this guide](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to upgrade your SharinPix Managed Package to the newest version.
* Users must have the **SharinPix Forms** **Admin** or **SharinPix Forms User** permission set assigned. For more information on these two permission sets, check [SharinPix Permission Sets](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/sharinpix-permission-sets).
* A form template has been created using the [SharinPix Form Template Editor](../form-elements/sharinpix-form-template-editor.md) and has been set up using the [SharinPix Form Launcher](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-form-launcher).
{% endhint %}

## Input Parameters

Below are the inputs required when using the <mark style="color:red;">`FormResponseContentDocAutomation`</mark> invocable method in a Salesforce Flow. These parameters must be provided to successfully import the PDF as a Content Document on Salesforce.

| Parameter            | Description                                                                                                               |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| formResponsePublicId | The ID of the <mark style="color:red;">`Form_Response__c`</mark> record from which the PDF will be imported. _(Required)_ |
| recordId             | The ID of the Salesforce Record the Content Document will be linked to. (_Required)_                                      |
| filename             | The Filename to be assigned to the Content Document.                                                                      |

## Flow Setup

This flow is setup to be triggered when a SharinPix Form Response record is created or updated with a value set for `ProcessedAt__c` and does the following:

* Generates a Content Document of the response
* Imports the Content Document on Salesforce
* Links it to the Form Response's parent record

### Step 1: Configure a Record-Triggered Flow

1. Go to **Setup** > **Flows** > Click **New Flow**
2. Choose **Record-Triggered Flow** and click **Create**
3. Set the following values:

| Setting                | Value                                                            |
| ---------------------- | ---------------------------------------------------------------- |
| Object                 | SharinPix Form Response                                          |
| Trigger                | A record is created or updated                                   |
| Condition Requirements | All Conditions Are Met (AND)                                     |
| Field                  | ProcessedAt                                                      |
| Operator               | Is Null                                                          |
| Value                  | False                                                            |
| When to Run            | Only when a record is updated to meet the condition requirements |
| Optimize Flow For      | Actions and Related Records                                      |
| Add Asynchronous Path  | On                                                               |

{% hint style="danger" %}
**Alert:**

Starting with the Salesforce **Winter’26 release**, Apex Actions can no longer be executed directly in the **Run Immediately** path of a record-triggered flow. Instead, they must be placed in an **asynchronous path**, as the synchronous execution option is no longer supported.

For more details, please refer to the documentation here:\
[_Unable to save a flow with an Apex Action after the Salesforce Winter ’26 release – What should I do?_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/i-am-unable-to-save-a-flow-with-an-apex-action-after-the-salesforce-winter-26-release-what-should-i)
{% endhint %}

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (6).png>)

This configuration ensures the Flow runs only when the `ProcessedAt` field on the [SharinPix Form Response](../salesforce-integration/sharinpix-form-response/) has a value.

### Step 2: Add the Import Action

1. Add an **Action** element
2. Search for <mark style="color:red;">`Sharinpix__FormResponseContentDocAutomation`</mark>
3. Set the input values:

| Field                                                             | Value                                                                     |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------- |
| Salesforce record ID to which the Content Document will be linked | <mark style="color:red;">`{!$Record.sharinpix__ParentRecordId__c}`</mark> |
| SharinPix Form Response Public ID                                 | <mark style="color:red;">`{!$Record.sharinpix__PublicId__c}`</mark>       |
| Filename of the Content Document                                  | <mark style="color:red;">`{!$Record.Name}`</mark>                         |

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (5).png>)

This step ensures the inspection report PDF is imported directly into the Salesforce Record where the form was launched.

### Step 3: Save and Activate

* Save the Flow
* Click **Activate** to begin automating PDF imports as Content Documents.

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (4).png>)

### Step 4: Fill and Submit the Form

Once the form has been submitted with the value set for `ProcessedAt__c`. The Content Document is generated and linked to the parent Salesforce record (where the form was launched) in the Notes & Attachments section.

![](<../.gitbook/assets/Form Response PDF Content Doc (2).png>)

![](<../.gitbook/assets/Form Response PDF Content Doc (3).png>)
