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

# SharinPix Plan Items Related List

The SharinPix Plan Items Related List component enables users to select specific SharinPix Plan Items added to the SharinPix Plan component. The selected Plan Item is highlighted on the plan component.

{% hint style="warning" %}
**Note:**

The **SharinPix Plan Items Related List** component works alongside the **SharinPix Plan** componen&#x74;**.** Therefore, before configuring the **SharinPix Plan Items Related List**, ensure that the **SharinPix Plan** **component** has been configured correctly.

For more information on how to configure the SharinPix Plan component, please refer to the following article: [SharinPix Plan](sharinpix-plan.md).
{% endhint %}

![](<../.gitbook/assets/SPI Overview (1) (1) (1).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
* In your own Lightning Component development
{% endhint %}

## Getting Started

To use the **SharinPix Plan Items Related List** component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/image (12) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

![](<../.gitbook/assets/relatedList (1) (1) (1).png>)

* **Display Lookup Field:** The field API Name of the Lookup relationship to filter SharinPix Plan Items to be displayed based on record ID.
* **Plan Component Id:** The Component Id value should be equal to the targeted Sharinpix Plan component Id
* **Field Set API Name:** The API Name of the Field Set that contains the list of columns to be displayed in the related list.
* **Custom Permission ID or Name:** Used to specify the ID or Name of a custom permission.
* **Field Set Name:** To be displayed on the SharinPix plan item record.
* **SharinPix Plan Setting Name:** SharinPix Plan Setting Name configured for a Plan Item.
* **Height:** The Height of the component (in px) and is set as default to 500.
* **Display button to add new SharinPix Plan Items:** If true, a button to add a new SharinPix Plan Item will appear. Plan Items created with the button will not be shown on the SharinPix Plan component and will only be present on Salesforce.
* **OverrideLabels:** Used to replace the labels shown on the component. To do so, use a JSON-formatted text to specify the new labels. The keys are "header" to replace the title of the component (SharinPix Plan Item Related list) by default and "columns" to replace the column header texts in the data table. "header" takes the new text as value. "columns" takes an object of key-values where the keys are API names for the field to replace and the values are the respective new labels. For example: **{"header": "Related Work", "columns": {"Name": "Work ref", "sharinpix\_\_Title\_\_c": "Work Title", "sharinpix\_\_Description\_\_c": "Work description"\}}**

## Demo

The image below depicts the **SharinPix Plan** component and the **SharinPix Plan Items Related List** component on a record page:

![](<../.gitbook/assets/SPI Overview (1) (1) (1).png>)

The image below shows the corresponding **SharinPix Plan Item** being selected on the **SharinPix Plan** component according to the row selected on the **SharinPix Plan Items Related List.**

![](<../.gitbook/assets/SPI Overview (1) (1) (1).jpg>)

{% hint style="warning" %}
**Note:**

The different interactions between the **SharinPix Plan** component and the **SharinPix Plan Items** Related List **component** are as follows:

* When a row is selected on the \*\*SharinPix Plan Items Related List \*\*component, the corresponding **SharinPix Plan Item** is selected on the **SharinPix Plan** component.
* When the hyperlink in the first column of the **SharinPix Plan Items Related List** component is clicked, the corresponding **SharinPix Plan Item** is selected on the **SharinPix Plan** component.
* When a **SharinPix Plan Item** is selected on the **SharinPix Plan** component, the corresponding row is selected on the **SharinPix Plan Items Related List** component.
* You should make sure that the **Plan Component Id** field on the **SharinPix Plan Item Related List** should equal to the **SharinPix Plan Component Id** for you to double click to open the sharinPix plan item modal on the **SharinPix Plan Component**.
* The field **SharinPix Plan Setting Name** should not be empty so that it can display the values when the **SharinPix Plan Item** modal is opened.
* **SharinPix Plan Items** created with the button will not be shown on the SharinPix Plan component and will only be present on Salesforce.
{% endhint %}

### Demo with parameter overrideLabels

overrideLabels = {"header": "Related Work", "columns": {"Name": "Work ref", "sharinpix\_\_Title\_\_c": "Work Title", "sharinpix\_\_Description\_\_c": "Work description"\}}

![](<../.gitbook/assets/plansss (1) (1) (1).png>)
