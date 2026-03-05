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

# Create Child Records With Form Repeated Section & Section

## Overview

{% hint style="info" %}
In SharinPix Forms, every form response is directly linked to a **parent record**, which represents the object from which the form was initially launched. Beyond capturing information for the parent, the platform also provides the flexibility to create **child records** associated with it.

For example, if the parent record is an **Account**, the form can generate multiple **Contact** records linked to that account. This is achieved through form sections: each section can be mapped to a single child record. In cases where repeated sections are used, each repetition creates a new record—so if a user completes 10 repeated sections, 10 corresponding child records (e.g., Contacts) will be created.

This feature ensures that SharinPix Forms not only capture structured data but also seamlessly extend Salesforce’s relational model, making it easier to manage and organize information.



This article covers the following:

* [Configure sections on your Form Template to create child records for Template parent object.](create-child-records-with-form-sections.md#how-to-configure-sections-on-your-form-template-to-create-child-records-for-template-parent-object)
* [Creating multi-level records with nested repeated sections](create-child-records-with-form-sections.md#creating-multi-level-records-with-nested-repeated-sections)
{% endhint %}

{% hint style="warning" %}
**Prerequisite:**

Before using this feature, ensure:

* You are using the most recent version of the SharinPix Package. Follow this document to [_upgrade the SharinPix package_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)
* Users must have the **SharinPix Forms** **Admin** or **SharinPix Forms User** permission set assigned. For more information on these two permission sets, check [SharinPix Permission Sets](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/sharinpix-permission-sets).
{% endhint %}

## Getting Started

### How to configure sections on your Form Template to create child records for Template parent object

The first step is to **create and configure a section** that will serve as the basis for generating the child record — or multiple records if it is set up as a [**Repeated Section**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-sections-and-repeated-sections).

![](<../.gitbook/assets/Form template Editor Doc (10).jpg>)

Each section of the form includes an **Advanced Tab** configuration in which you will find **Salesforce Record Mapping**.\
This configuration is divided into three key parts:

1. **Child Object API Name** – specifies the Salesforce object to be created.
2. **Lookup API Name** – defines the lookup field on the child object that links it to the form’s parent record.
3. **Lookup value field API name** – specifies a field on the form’s parent record containing the ID to use for the child record’s lookup. Use this when the child record should be linked to a record other than the form’s parent record.
4. **Salesforce record creation rule** – determines the criteria under which the child record(s) should be created.

<figure><img src="../.gitbook/assets/Form template Editor Doc (11).jpg" alt=""><figcaption></figcaption></figure>

Once the child object details have been configured, you can define how data from the form will populate Salesforce fields. Click the **“+”** icon to add new mappings, each representing a link between a **form field** and its corresponding **Salesforce field**. This ensures that when a form response is submitted, the captured data is accurately updated in the appropriate fields within the newly created child record.

![](<../.gitbook/assets/3 (4) (1).png>)

A dropdown list containing all **Form Question API Names** from the current section will be available for selection. After choosing a question, enter the corresponding **Salesforce Field API Name** of the child record to which the selected question should be mapped.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (24).png" alt=""><figcaption></figcaption></figure>

As shown in the picture above, the "Inspection Checklist" section has been configured to create Fire Inspection records with 2 fields to input:

1. [Fire extinguishers present ?](https://documentation-dev-ed.develop.lightning.force.com/lightning/setup/ObjectManager/01IfJ000001bh2D/FieldsAndRelationships/00NfJ00000Ill2j/view)
2. [Last date fire extinguisher serviced](https://documentation-dev-ed.develop.lightning.force.com/lightning/setup/ObjectManager/01IfJ000001bh2D/FieldsAndRelationships/00NfJ00000IliGA/view)

On the **Inspection** record page, when a SharinPix Form is launched, completed, and submitted, a corresponding **Form Response** is created in Salesforce. If the _Create Records_ condition evaluates to **true**, a new child record is automatically generated and linked to the **Inspection** record. This relationship can then be viewed under the **Fire Inspection** related list.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (25).png" alt=""><figcaption></figcaption></figure>

The corresponding values are then automatically populated in the newly created child record — **Fire Inspection** in this example as illustrated below.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (26).png" alt=""><figcaption></figcaption></figure>

### Creating multi-level records with nested repeated sections

You can create child records in a nested tree structure. By configuring your Form Repeated Sections in a nested tree structure, for example, Contact -> Case

To build a form with nested repeated sections representing each object, follow these steps:

1.  **Define the Parent and Child Objects**:

    * Start by defining the primary object, such as **Contact**, as the parent record.
    * Next, introduce the **Case** as a child record under the Account.
    * This can go on and continue for child objects of Case, etc.

    By following these steps, you can efficiently set up a form that handles multi-level data structures in a coherent manner.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (26).png" alt=""><figcaption></figcaption></figure>

The picture above showcases how a simple form containing 2 repeated sections is built.

At the root, we have 2 Form Questions:

* Inspector name: Text question
* Contacts: Repeated Section configured to create contacts from the parent object (Account in this example)

Inside the Repeated Section Contacts, we have 3 questions:

* Last name: Text question representing the LastName of the contact child record being created
* First name: Text question representing the FirstName of the contact child record being created
* Cases: Repeated Section configured to create cases from its corresponding contact parent object&#x20;

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (27) (1).png" alt=""><figcaption></figcaption></figure>

The picture above illustrates the completed form. It shows two contact sections: one for Thorne, which includes two Case child records for Contact Thorne, and another for Vance, which contains one Case child record.

Once the form is submitted (from an Account record in our scenario) it will create 2 contacts **Julian Thorne** and **Elena Vance.**

Contact Julian Thorne will have two Case records, and Elena Vance will have one Case record, as shown in the picture below.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (28) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
In summary, the above example demonstrates how to efficiently create multiple levels of related records within a form. By utilizing nested Repeated Sections, you can streamline the process of associating child records with parent records, enhancing data organization. You can create child records nested deeper than 2 levels (Contacts -> Cases) as needed to suit your data hierarchy requirements.
{% endhint %}

{% hint style="warning" %}
**Warning:**

There is no limit on the number of nested Repeated Sections creating records. But beware that this will increase your organization's [governor limit for DML operations](https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_apexgov.htm) for each nested level
{% endhint %}
