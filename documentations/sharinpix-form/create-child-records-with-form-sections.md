# Create Child Records With Form Sections

## Overview

{% hint style="info" %}
In SharinPix Forms, every form response is directly linked to a **parent record**, which represents the object from which the form was initially launched. Beyond capturing information for the parent, the platform also provides the flexibility to create **child records** associated with it.

For example, if the parent record is an **Account**, the form can generate multiple **Contact** records linked to that account. This is achieved through form sections: each section can be mapped to a single child record. In cases where repeated sections are used, each repetition creates a new record—so if a user completes 10 repeated sections, 10 corresponding child records (e.g., Contacts) will be created.

This feature ensures that SharinPix Forms not only capture structured data but also seamlessly extend Salesforce’s relational model, making it easier to manage and organize information.
{% endhint %}

**Prerequisite:**

Before using this feature, ensure:

* You are using the most recent version of the SharinPix Package. Follow this document to [_upgrade the SharinPix package_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)
* Users have the [_**SharinPix Forms Admin**_ _permission set_](../access-and-security/sharinpix-permission-sets.md) assigned.

## Getting Started

### How to configure sections on your Form Template to create child records for Template parent object.

The first step is to **create and configure a section** that will serve as the basis for generating the child record — or multiple records if it is set up as a repeated section.

![](<../.gitbook/assets/2 (3) (2).png>)

Each section of the form includes an **Advanced** tab configuration in which you will find **Salesforce Record Mapping**.\
This configuration is divided into three key parts:

1. **Child Object API Name** – specifies the Salesforce object to be created.
2. **Lookup API Name** – defines the lookup field on the child object that links it to the form’s parent record.
3. **Formula Condition** – determines the criteria under which the child record(s) should be created.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (17).png" alt=""><figcaption></figcaption></figure>

Once the child object details have been configured, you can define how data from the form will populate Salesforce fields. Click the **“+”** icon to add new mappings, each representing a link between a **form field** and its corresponding **Salesforce field**. This ensures that when a form response is submitted, the captured data is accurately updated in the appropriate fields within the newly created child record.

![](<../.gitbook/assets/3 (4) (2).png>)

A dropdown list containing all **Form Question API Names** from the current section will be available for selection. After choosing a question, enter the corresponding **Salesforce Field API Name** of the child record to which the selected question should be mapped.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (18).png" alt=""><figcaption></figcaption></figure>

As shown in the picture above, the "Inspection Checklist" section has been configured to create Fire Inspection records with 2 fields to input:

1. [Fire extinguishers present ?](https://documentation-dev-ed.develop.lightning.force.com/lightning/setup/ObjectManager/01IfJ000001bh2D/FieldsAndRelationships/00NfJ00000Ill2j/view)
2. [Last date fire extinguisher serviced](https://documentation-dev-ed.develop.lightning.force.com/lightning/setup/ObjectManager/01IfJ000001bh2D/FieldsAndRelationships/00NfJ00000IliGA/view)

On the **Inspection** record page, when a SharinPix Form is launched, completed, and submitted, a corresponding **Form Response** is created in Salesforce. If the _Create Records_ condition evaluates to **true** , a new child record is automatically generated and linked to the **Inspection** record. This relationship can then be viewed under the **Fire Inspection** related list.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (19).png" alt=""><figcaption></figcaption></figure>

The corresponding values are then automatically populated in the newly created child record — **Fire Inspection** in this example as illustrated below.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (20).png" alt=""><figcaption></figcaption></figure>
