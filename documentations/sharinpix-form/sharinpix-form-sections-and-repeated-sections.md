# SharinPix Form - Sections and Repeated Sections

## Overview

{% hint style="info" %}
Sections and Repeated Sections are powerful layout elements in the [**SharinPix Form Template Editor**](sharinpix-form-template-editor.md). They allow administrators to structure forms into logical groups of fields and, when necessary, capture repeating sets of information dynamically.

* **Section**: Used to group related form fields under a labeled block.
* **Repeated Section**: Extends the Section by letting users duplicate the same block multiple times with a “+” button — useful for variable numbers of items (e.g., inspections across multiple floors, multiple deficiencies, or repeating details).

This documentation covers :

1. [The Section Element](sharinpix-form-sections-and-repeated-sections.md#section-element)
2. [The Repeated Section Element](sharinpix-form-sections-and-repeated-sections.md#repeated-section-element)\
   \
   2.1 [Reordering of Repeated Section Elements](sharinpix-form-sections-and-repeated-sections.md#reordering-of-repeated-sections)
3. [Demo – Air Conditioning Inspection Form](sharinpix-form-sections-and-repeated-sections.md#demo-air-conditioning-inspection-form)
4. [Presets sections on Repeated Section Element](sharinpix-form-sections-and-repeated-sections.md#presets-sections-on-repeated-section-element)
{% endhint %}

<figure><img src="../.gitbook/assets/Click on the (18) (1) (1) (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Prerequisites:**

Before using Sections or Repeated Sections:

* Ensure the [**SharinPix Forms Admin**](../access-and-security/sharinpix-permission-sets.md) permission set is assigned.
* The **latest version of the SharinPix Package** must be installed. Refer to [_this documentation_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to update your package.
{% endhint %}

## Elements

### Section Element

The **Section element** is used to group related inputs and content. It helps keep forms clear and organized.

![](<../.gitbook/assets/Copy of DOC SF - 1920 x 600 (3) (1).png>)

#### Configuration Options

| Option                   | Description                                                                                           |
| ------------------------ | ----------------------------------------------------------------------------------------------------- |
| Label                    | Name of the section displayed to users.                                                               |
| API Name                 | Unique identifier for referencing in logic or formulas.                                               |
| Label Formula            | Dynamically generate section titles based on values or conditions.                                    |
| Edit Section             | Clieck to enter the section presented as a blank form template. Customize it by adding your elements. |
| Style                    | Choose a display style (e.g., default/fold/inline).                                                   |
| PDF Answer Column Labels | Option to display column labels when rendering the form in PDF.                                       |
| Advanced → Visible When  | [Conditional visibility](form-features-conditional-visibility.md) rule (show/hide based on formulas). |

#### When to use ?

* Organize form into logical parts (e.g., “Personal Information,” “Inspection Details”).
* Add clarity for long forms by grouping elements.
* Use Label Formula to personalize section headings dynamically.

### Repeated Section Element

The **Repeated Section element** allows administrators to create a template for a group of fields that can be repeated by the end user as many times as needed.

![](<../.gitbook/assets/Copy of DOC SF - 1920 x 600 (1) (1) (1).png>)

#### Configuration Options

| Option                     | Description                                                                                                                                                                       |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Label                      | Name of the repeated section.                                                                                                                                                     |
| API Name                   | Unique identifier for referencing in logic or formulas.                                                                                                                           |
| Edit Section               | Click to enter the repeated section presented as a blank form template. Customize it by adding your elements.                                                                     |
| Style                      | Layout style (e.g., default/fold/inline).                                                                                                                                         |
| Label for each item        | Defines the display label for each repeated item (e.g., “Deficiency”).                                                                                                            |
| Item API Name              | Technical identifier for the repeated item.                                                                                                                                       |
| Label Formula              | Automatically generates dynamic labels for repeated items (e.g., <mark style="color:$danger;">`label + " " + TEXT(index)`</mark> will show “Deficiency 1,” “Deficiency 2,” etc.). |
| Advanced → Visible When    | [Conditional visibility](form-features-conditional-visibility.md) rule (show/hide based on formulas).                                                                             |
| Advanced → Validation Rule | Define [validation criteria](form-features-validations.md) that each repeated block must satisfy.                                                                                 |
| Advanced → Sortable        | Allows section reordering with drag and drop                                                                                                                                      |

#### When to use ?

* Collecting details for multiple items of the same type (e.g., one form per air conditioning unit per floor).
* Capturing lists of issues or defects.
* Handling unknown quantities of input (instead of pre-creating fixed sections).

## Demo – Air Conditioning Inspection Form

### Step 1: Add a Section

* Create a **Section** labeled _“General Inspection Information”_.
* Click the "Edit Section" button.
* Place fields like Inspector Name, Date, and Location inside it.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (8) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Click on the (20) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Step 2: Add a Repeated Section

* Create a **Repeated Section** labeled _“Air Conditioning Unit”_.
* Label for each item: “AirCon Unit”
* Label Formula: <mark style="color:red;">`label + " " + TEXT(index)`</mark> → generates “AirCon Unit 1,” “AirCon Unit 2,” etc.
* Click the "Edit Section" button.
* Inside the repeated section, add fields for:
  * Unit Number
  * Observed Deficiencies (Text Area)
  * Photo Capture (Capture element)

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (9) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Click on the (22) (1) (1) (2).png" alt=""><figcaption></figcaption></figure>

#### Reordering Of Repeated Sections

* The user can enable Reordering Repeated Sections by checking Sortable in the advanced settings.
* They can then see handles on the side of sections and reorder them with **drag and drop**.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (10) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Step 3: Test in Preview

The user can fill in the "General Inspection Information" section and add one section per floor’s unit by clicking “+ AirCon Unit”.

![](<../.gitbook/assets/Copy of DOC SF - 1920 x 600 (2) (1) (1).png>)

{% hint style="success" %}
**Tips**

* Use **Sections** to structure the form into easy-to-digest blocks.
* Use **Repeated Sections** when you don’t know in advance how many instances a user will need.
* Apply **Label Formulas** to auto-number items for clarity.
* Add **Validation Rules** in Repeated Sections to enforce quality (e.g., each deficiency must include a description).
* Keep labels consistent to avoid user confusion when multiple instances are created.
* Sections or Repeated Sections can be used to create Child Records on Salesforce. Refer to the documentation below for more information on [**Creation of Child Records With Form Sections**](create-child-records-with-form-sections.md)
{% endhint %}

## Presets sections on Repeated Section Element

* Users can create **Preset Sections** on a Repeated Section element.
* Each preset includes a label and can be configured with predefined default values.

In the example below, two preset sections have been created: **Small Unit** and **Medium Unit**.\
Both presets have been configured with a default value for the **Unit Number** field.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (11) (1) (2).png" alt=""><figcaption></figcaption></figure>

A **Repeated Section Element** with presets displays a dropdown containing all available Presets. Selecting a preset will add the corresponding preconfigured section.

<figure><img src="../.gitbook/assets/DOC Mobile - 1920 x 1080 (3) (3).png" alt=""><figcaption></figcaption></figure>
