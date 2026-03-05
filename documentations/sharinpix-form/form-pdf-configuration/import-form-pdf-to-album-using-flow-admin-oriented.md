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

# Import Form PDF to Album using Flow (Admin-Oriented)

## Overview

{% hint style="info" %}
The <mark style="color:$danger;">`ImportFormPdfAutomation`</mark> Invocable Apex method allows users to automatically import a PDF generated from a SharinPix Form Response into a designated [SharinPix Album Component](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-album-lwc). This can be used across various business scenarios where form submissions must be archived and associated with a record (e.g., sites, cases, inspections).

This invocable method is designed for use in Salesforce Flows and is compatible with automation for different types of form workflows.

This article covers the following :

1. [ImportFormPdfAutomation's Input Parameters](import-form-pdf-to-album-using-flow-admin-oriented.md#input-parameters)
2. [Form Setup](import-form-pdf-to-album-using-flow-admin-oriented.md#flow-setup)
   * [Step 1: Configure a Record-Triggered Flow](import-form-pdf-to-album-using-flow-admin-oriented.md#step-1-configure-a-record-triggered-flow)
   * [Step 2: Assign Variables for the Action](import-form-pdf-to-album-using-flow-admin-oriented.md#step-2-assign-variables-for-the-action)
   * [Step 3: Add the Import Action](import-form-pdf-to-album-using-flow-admin-oriented.md#step-3-add-the-import-action)
   * [Step 4: Save and Activate the flow](import-form-pdf-to-album-using-flow-admin-oriented.md#step-4-save-and-activate)
3. [Demo: Fire Safety Inspection Example](import-form-pdf-to-album-using-flow-admin-oriented.md#demo-fire-safety-inspection-example)
{% endhint %}

{% hint style="warning" %}
**Prerequisites**

Before configuring this automation, ensure the following:

* You have the latest **SharinPix Package** installed. You can follow [this guide](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to upgrade your SharinPix Managed Package to the newest version.
* Users must have the **SharinPix Forms** **Admin** or **SharinPix Forms User** permission set assigned. For more information on these two permission sets, check [SharinPix Permission Sets](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/sharinpix-permission-sets).
* A form template has been created using the [SharinPix Form Template Editor](../form-elements/sharinpix-form-template-editor.md) and has been set up using the [SharinPix Form Launcher](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-form-launcher).
{% endhint %}

## Input Parameters

Below are the inputs required when using the <mark style="color:$danger;">`ImportFormPdfAutomation`</mark> invocable method in a Salesforce Flow. These parameters must be provided to successfully import the PDF into a SharinPix album.

| Parameter      | Description                                                                                                                                                                                                         |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| formResponseId | The ID of the <mark style="color:$danger;">`Form_Response__c`</mark> record from which the PDF will be imported. _(Required)_                                                                                       |
| albumId        | The ID of the SharinPix album where the PDF will be stored. This corresponds to the **destination record ID** , typically the record (e.g., Site, Inspection, or Case) to which the album is attached. _(Required)_ |

## Flow Setup

This flow is setup using a **fire safety inspection** scenario as example.

### Step 1: Configure a Record-Triggered Flow

1. Go to **Setup** > **Flows** > Click **New Flow**
2. Choose **Record-Triggered Flow** and click **Create**
3. Set the following values:

| Setting               | Value                                                            |
| --------------------- | ---------------------------------------------------------------- |
| Object                | SharinPix Form Response                                          |
| Trigger               | A record is created or updated                                   |
| When to Run           | Only when a record is updated to meet the condition requirements |
| Optimize Flow For     | Actions and Related Records                                      |
| Add Asynchronous Path | On                                                               |

{% hint style="danger" %}
**Warning:**

Starting with the Salesforce **Winter’26 release**, Apex Actions can no longer be executed directly in the **Run Immediately** path of a record-triggered flow. Instead, they must be placed in an **asynchronous path**, as the synchronous execution option is no longer supported.

For more details, please refer to the documentation here:\
[_Unable to save a flow with an Apex Action after the Salesforce Winter ’26 release – What should I do?_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/i-am-unable-to-save-a-flow-with-an-apex-action-after-the-salesforce-winter-26-release-what-should-i)
{% endhint %}

**Set Entry Condition**

| Field       | Operator | Value |
| ----------- | -------- | ----- |
| ProcessedAt | Is Null  | False |

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (6).png>)

This configuration ensures the Flow runs only when the `ProcessedAt` field on the [SharinPix Form Response](../salesforce-integration/sharinpix-form-response/) has a value.

### Step 2: Assign Variables for the Action

Use an **Assignment** element to set the values to be passed to the invocable method.

In this fire safety inspection scenario, assume the album is stored, for example, on a related <mark style="color:$danger;">`Inspection__c`</mark> record.

| Variable           | Value                                             |
| ------------------ | ------------------------------------------------- |
| Album\_Id          | Triggering Form\_Response\_\_c > Parent Record ID |
| Form\_Response\_Id | Triggering Form\_Response\_\_c > Record ID        |

![](<../.gitbook/assets/Click on the (13) (2).png>)

### Step 3: Add the Import Action

1. Add an **Action** element
2. Search for <mark style="color:$danger;">`sharinpix__ImportFormPdfAutomation`</mark>
3. Set the input values:

| Field            | Value              |
| ---------------- | ------------------ |
| Album ID         | Album\_Id          |
| Form Response ID | Form\_Response\_Id |

![](<../.gitbook/assets/Click on the (14) (1) (1).png>)

This step ensures the inspection report PDF is imported directly into the correct album for the site or building.

### Step 4: Save and Activate

* Save the Flow
* Click **Activate** to begin automating PDF imports

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (7).png>)

## Demo: Fire Safety Inspection Example

This example demonstrates importing the **fire safety inspection PDF** into the related site’s SharinPix album when a form is submitted.

* The diagram below demonstrates the PDF version of the form on the <mark style="color:$danger;">`Inspection__c`</mark> record's album.

![](<../.gitbook/assets/Click on the (17) (2).png>)

![](<../.gitbook/assets/Template (5) (2).png>)
