# Form Features - Default or Prefill Values

## Overview

{% hint style="info" %}
SharinPix Form Elements can be configured to automatically retrieve and display values from related Salesforce records. This prefill functionality allows dynamic population of form fields using data linked to the record from which the form is launched. The configuration is done directly within the [SharinPix Form Builder](sharinpix-form-template-editor.md) and supports traversing up to five levels of related (lookup) records.

This document covers:

* [How to Configure Prefill in a Form Element](form-features-default-or-prefill-values.md#how-to-configure-prefill-in-a-form-element)
* [Prefill Syntax and Examples](form-features-default-or-prefill-values.md#prefill-syntax-and-examples)
* [Demo: Pre-Filling Values in a Fire Safety Inspection Form](form-features-default-or-prefill-values.md#demo-pre-filling-values-in-a-fire-safety-inspection-form)
{% endhint %}

**Prerequisite**

{% hint style="warning" %}
**Prerequisite**

Before using this feature, ensure:

* Ensure that you are using the most recent SharinPix Package Version. Follow this document to [upgrade the SharinPix package](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)
* Users have the [SharinPix Forms Admin permission set](../access-and-security/sharinpix-permission-sets.md) assigned.
{% endhint %}

## Getting Started

### How to Configure Prefill in a Form Element

To configure prefilling for a question in a SharinPix Form:

1. Open the **SharinPix Form Builder** from the relevant Form Template.
2. Select a **Question** element in the form.
3. Navigate to the **Advanced** tab of the question configuration.
4. Enter the appropriate **Salesforce Field API Name** into the _Field API name_ field.

![](<../.gitbook/assets/Prefill doc (2) (1).png>)

### Prefill Syntax and Examples

The prefill logic uses dot notation to access related Salesforce fields. The general format is:

* **`FieldApiName`**
* **`LookupApiName.FieldApiName`**
* **`LookupApiName.LookupApiName.FieldApiName`**

{% hint style="warning" %}
**Note**: SharinPix supports up to **5 levels of nested lookup relationships**.
{% endhint %}

**Syntax Components**

* **`LookupApiName`**: The API name of a lookup field on the current object (e.g., `AccountId` on the `Contact` object).
* **`FieldApiName`**: The API name of the target field from which to pull the value (e.g., `Description` on the `Account` object).

#### Example

If the form is launched from a **Contact** record and you want to prefill a field with the related **Account’s description,** use the following configuration:

`AccountId.Description`

This will fetch the description value of the account, which is related to the contact through the AccountId field.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (2) (1).png" alt=""><figcaption></figcaption></figure>

#### Advanced Example (Up to 5 Levels)

Example: `AssetId.ContactId.ReportsToId.AccountId.CreatedById.Name`

This fetches the name of the user who created the Account that is related through a multi-level chain from the current Asset record.

{% hint style="warning" %}
**Note:** This is subject to Salesforce’s current maximum of 5 lookup relationship levels per query.
{% endhint %}

## Demo: Pre-Filling Values in a Fire Safety Inspection Form

In this example, you have a **Form Template** designed for fire safety inspections. The form is launched from a custom **Inspection** object. Your goal is to dynamically pre-fill:

* The **inspection date** using a field on the **Inspection** record itself.
* The **address** using a field on the related **Account** record (the parent of the Inspection).

### Step 1 : Build a SharinPix Form

If you do not already have a Form Template available, go on [_**SharinPix Form Template**_](sharinpix-form-template-editor.md) and create a new Form Template record. Use the Form Builder to create a SharinPix Form.

Once you have configured your form, you can select the element you want to have a value pre-filled from its parent record or related parent records.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (3) (1).png" alt=""><figcaption></figcaption></figure>

### Step 2: Prefill the Inspection Date

Begin by selecting the Date element, which opens the configuration panel to configure pre-fill for it.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (5) (1).png" alt=""><figcaption></figcaption></figure>

To pull the inspection date directly from the `Inspection` record:

* Field API Name: `Inspection_Date__c`

This retrieves the value from the `Inspection_Date__c` field on the record used to launch the form.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (6) (1).png" alt=""><figcaption></figcaption></figure>

### Step 3: Prefill the Address from the Account

To pre-fill the **address** from the related Account record, we use:

`Account__c.Address__c`

Configuring the pre-fill value to **Account\_\_c.Address\_\_c** will do the following steps:

1. **Account\_\_c** is the Lookup Field API name on Inspection object. This will look for the parent Account record.
2. **Address\_\_c** is a field in the Account parent record. It will then fetch the Address value of this Account.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (7) (1).png" alt=""><figcaption></figcaption></figure>

### Step 4: Test the form

Once the prefill values are set:

* Launch the form from a Salesforce record (e.g., an `Inspection`).
* The prefill logic will automatically populate the specified fields as shown in the diagram below.
* If a referenced field is empty (null), the form field will remain empty.
