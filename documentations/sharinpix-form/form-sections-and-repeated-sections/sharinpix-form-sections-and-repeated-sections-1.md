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

# SharinPix Form - Repeated Section

## Overview

{% hint style="info" %}
**Repeated Sections** allow administrators to define a section that users can add multiple times while filling out a form. This is useful when the same group of fields may need to be completed more than once, such as when recording deficiencies, assets, rooms, or inspection items.

Repeated Sections are configured in the [SharinPix Form Template Editor](../form-elements/sharinpix-form-template-editor.md) and share the same core configuration options as standard **Sections**, including display styles and related behavior. For information about shared settings, refer to the [Section documentation.](sharinpix-form-sections-and-repeated-sections.md)

This documentation covers:

1. [Configuration options for the **Repeated Section** element](sharinpix-form-sections-and-repeated-sections-1.md#configuration-options)
2. [How to set up a **Repeated Section** element](sharinpix-form-sections-and-repeated-sections-1.md#configure-the-repeated-section)
3. [How to add default items](sharinpix-form-sections-and-repeated-sections-1.md#default-repeated-sections)
4. [How to configure preset items](sharinpix-form-sections-and-repeated-sections-1.md#preset-sections)
5. [Available actions for repeated section items](sharinpix-form-sections-and-repeated-sections-1.md#repeated-section-item-actions)
6. [Demo: Air Conditioning Unit Inspection Form](sharinpix-form-sections-and-repeated-sections-1.md#demo-air-conditioning-unit-inspection-form)
{% endhint %}

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (72).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (73).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Tips:

* **Repeated Sections** are ideal for capturing multiple items of the same type, such as deficiencies, equipment, observations, or rooms.
* Use **Repeated Sections** to handle unknown quantities of input instead of pre-creating a fixed number of sections.
* **Repeated Sections** can be used to create child records in Salesforce. See [**Creation of Child Records With Form Sections**](../create-child-records-with-form-sections.md).
* **Repeated Sections** can also pull, create, and update related Salesforce records. See [**Create and Update Related Salesforce Records with SharinPix Form**](../salesforce-integration/create-and-update-related-salesforce-records-with-sharinpix-form.md).
{% endhint %}

## Configuration Options

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-28T160949.637.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-28T161448.562 (1).png" alt=""><figcaption></figcaption></figure>

### General Options

| Option                                              | Description                                                                                                                                                                                                                                                                                                                             |
| --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Label                                               | Defines the display name of the **Repeated Section** element in the form.                                                                                                                                                                                                                                                               |
| Label Formula                                       | Dynamically generates the label of the **Repeated Section** element based on field values or defined conditions.                                                                                                                                                                                                                        |
| API Name                                            | Unique identifier for referencing the **Repeated Section** Element in logic or formulas.                                                                                                                                                                                                                                                |
| Edit Section                                        | Opens the section template for the **Repeated Section** element, where you can add and configure the elements that make up each item.                                                                                                                                                                                                   |
| Item style                                          | Defines how **items** in the **Repeated Section** element are displayed in the form, such as [**Full Page**](sharinpix-form-sections-and-repeated-sections.md#full-page), [**Collapsible**](sharinpix-form-sections-and-repeated-sections.md#collapsible) **and** [**Inline**](sharinpix-form-sections-and-repeated-sections.md#inline) |
| Label for each item                                 | Defines the display label for each item within the **Repeated Section** element. This label is shown for every added item unless overridden by an item label formula.                                                                                                                                                                   |
| Label formula for each item                         | Uses a formula to dynamically generate the label for each item in the **Repeated Section** element. For example, <mark style="color:$danger;">`"Room " + TEXT(index)`</mark> will display labels such as **Room 1**, **Room 2**, and so on.                                                                                             |
| PDF view                                            | Chooses whether the generated PDF uses **Classic View** or **Table View**. This does not change the form display. See [pdf-view-for-repeated-questions.md](../form-pdf-configuration/pdf-view-for-repeated-questions.md "mention").                                                                                                     |
| Configure background color of repeated title on PDF | Allows you to define a custom background color for the **Repeated Section** title in the generated PDF.                                                                                                                                                                                                                                 |
| Configure background color of sections title on PDF | Allows you to define a custom background color for the title of every item in the **Repeated Section** element in the generated PDF.                                                                                                                                                                                                    |

### Advanced Options

| Option                               | Description                                                                                                                                                                                                                                                                                                                  |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| item apiName                         | Sets a unique identifier for the repeated item. It is used for referencing in logic or formulas.                                                                                                                                                                                                                             |
| Sortable                             | Allows item reordering with drag and drop                                                                                                                                                                                                                                                                                    |
| Allow add sections when (formula)    | Uses a formula to control whether users can add new items to the **Repeated Section** element. By default, adding items is allowed. If a formula is provided, it must return a Boolean value. Users can add items only when the formula evaluates to **true**.                                                               |
| Allow delete sections when (formula) | Uses a formula to control whether users can delete items from the **Repeated Section** element. By default, deleting items is allowed. If a formula is provided, it must return a Boolean value. Users can delete items only when the formula evaluates to **true**.                                                         |
| Enable duplication of sections       | Allows you to configure when users can duplicate items in the **Repeated Section** element. This option uses a formula, and duplication is enabled only when the formula returns **true**.                                                                                                                                   |
| Visible When                         | [Conditional visibility](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/sharinpix-form/form-features-conditional-visibility) rule (show or hide the **Repeated Section** element and any item added based on a formula)                                                                                                      |
| Validation rule                      | Defines the [validation criteria](../form-elements/form-features-validations.md) that the **Repeated Section** element must satisfy. This can be used to enforce conditions on the collection of items. For example, <mark style="color:$danger;">`rooms.size > 3`</mark> ensures that more than three room items are added. |
| Use full width                       | This option removes the width constraint when displaying the **Repeated Section** element on the form.                                                                                                                                                                                                                       |
| Pull data from a Salesforce record   | Configuration for defining a mapping that will be used for prefilling the questions found inside the section using data from a Salesforce record.                                                                                                                                                                            |
| Create a Salesforce record           | Configuration for creating Salesforce child records using data from each of section items. Refer to [this documentation](../create-child-records-with-form-sections.md) for more information.                                                                                                                                |
| External field mapping               | Option for specifying a question found in the template section that will be used to store an external ID. This is useful for updating Salesforce records.                                                                                                                                                                    |

## Configure the Repeated Section

Each item in **Repeated Section** is based on a **Section Element** template.

To configure the **Section Element:**

1. Click on the **Edit section** button on the **Repeated Section** element settings.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (84).png" alt=""><figcaption></figcaption></figure>

2. In the section editor, use the left sidebar to add the elements you want to appear in every section item.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (85) (1).png" alt=""><figcaption></figcaption></figure>

The image below shows a **Repeated Section** element configured using the section template above.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (86).png" alt=""><figcaption></figcaption></figure>

## Default Repeated Sections

You can configure **default repeated items** for a **Repeated Section** element so that one or more items are already available when the form opens.

To configure default items, open the **Default** tab in the **Repeated Section** element settings and click the **+** button to add a default item.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (1920 x 600 px) (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-28T162123.668 (1).png" alt=""><figcaption></figcaption></figure>

The image above shows a **Repeated Section** element with two default room items added.

### Prefill repeated sections from a dataset

This option allows prefilling a large number of repeated items using dynamic Salesforce data.

See [Prefill repeated sections with a record dataset](https://docs.sharinpix.com/forms/form-elements/form-features-use-dynamic-salesforce-data-with-record-datasets#prefill-repeated-sections-with-a-record-dataset) for setup instructions.

## Preset Sections

**Preset Sections** allow you to define pre-configured sections or items that users can choose from when adding a new item to a **Repeated Section** element. Instead of adding a blank item, users select from a list of preset options, and the new item is added with the predefined values and structure.

You can configure preset items from the **Presets** tab in the **Repeated Section** element settings. Click the **+** button to add a preset item, then define its label and default values.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (1920 x 600 px) (4).png" alt=""><figcaption></figcaption></figure>

The images below illustrate two preset items configured for the **Repeated Section** element, labeled "Kitche&#x6E;**"** and "Bedroo&#x6D;**"** each having a different value for the **Name** field.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (81).png" alt=""><figcaption></figcaption></figure>

When preset items are configured, the **+** button becomes a picklist showing the available presets. Selecting a preset adds the corresponding pre-configured item to the **Repeated Section** element.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (83).png" alt=""><figcaption></figcaption></figure>

### Preset Configuration Options

| Option       | Description                                                                             |
| ------------ | --------------------------------------------------------------------------------------- |
| Label        | Sets the label of the preset item as it appears in the **Add** button picklist.         |
| Visible when | Uses a formula to control when the preset item is shown in the **Add** button picklist. |

## Repeated Section Item Actions

The image below illustrates the available actions for individual items in a **Repeated Section** element.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (88).png" alt=""><figcaption></figcaption></figure>

1. The **Delete item** action removes the selected item from the **Repeated Section** element. Deleting items is enabled by default, but it can be controlled using the **Allow delete sections when (formula)** setting.<br>
2. The **Reorder item** action allows users to change the order of items in the **Repeated Section** element. Users can click and drag the reorder handle next to an item to move it to a new position. This action is available when the **Sortable** option is enabled.<br>
3. The **Duplicate item** action creates a copy of the selected item, including its current values. This action can be controlled using the **Enable duplication of sections** setting.

{% hint style="warning" %}
The **Duplicate item** action does not duplicate images.
{% endhint %}

## Demo – Air Conditioning Unit Inspection Form

The image below shows a form configured with a **Repeated Section** element for recording multiple air conditioning units inspected within a building. The section or item template includes fields such as **Unit Number**, **Location of Unit**, **Any Leaks Detected**, and **Maintenance Performed If Any**, and is displayed using the **Inline** style. Two preset items have also been configured, **Small Unit** and **Big Unit**, each with its own predefined values.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (89).png" alt=""><figcaption></figcaption></figure>

The image below shows how air conditioning unit items can be added on the **Repeated Section** element using the **+** button.

<figure><img src="../.gitbook/assets/DOC Mobile - 1920 x 1080 (6) (1).png" alt=""><figcaption></figcaption></figure>
