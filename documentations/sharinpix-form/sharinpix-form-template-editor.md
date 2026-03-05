# SharinPix Form Template Editor

## Overview

{% hint style="info" %}
The SharinPix Form Template Editor is a dedicated tool within Salesforce that empowers users to create, edit, and manage form templates. With an intuitive drag-and-drop interface, the editor simplifies the form-building process by allowing users to add various field types, integrate media capture capabilities, and preview their forms in real-time.

This documentation covers:

* [Form Elements](sharinpix-form-template-editor.md#form-elements)
* [Form Features](sharinpix-form-template-editor.md#form-features)
* [Demo - Constructing an Air Conditioning Inspection Form](sharinpix-form-template-editor.md#demo-constructing-an-air-conditioning-inspection-form)
* [Integration with SharinPix Mobile Form Launcher](sharinpix-form-template-editor.md#integration-with-sharinpix-mobile-form-launcher)
* [Integration with Salesforce Field Service](sharinpix-form-template-editor.md#integration-with-salesforce-field-service)
{% endhint %}

![](<../.gitbook/assets/Click on the (15) (2).png>)

{% hint style="info" %}
**Prerequisites:**

Before using the **SharinPix Form Template Editor** , ensure the following:

* Users must have the **SharinPix Forms Admin** permission set assigned.
* You have the **latest** **SharinPix Package Verison** Installed. Refer to [_this documentation_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to update your package.
{% endhint %}

## Getting Started

## Form Elements

Users can add the following types of elements to their forms:

### Basic Elements

| Element                                                                  | Description                                                                                                                                                                               |
| ------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Title**                                                                | Adds a section title to the form.                                                                                                                                                         |
| **Paragraph**                                                            | Inserts descriptive text or instructions in the form.                                                                                                                                     |
| **Rich Text**                                                            | Adds formatted text, including bold, italics, lists, and links.                                                                                                                           |
| [**Section**](sharinpix-form-sections-and-repeated-sections.md)          | Inserts a section divider to group related form elements.                                                                                                                                 |
| [**Repeated Section**](sharinpix-form-sections-and-repeated-sections.md) | Similar to a Section, but allows users to dynamically add multiple instances of the same group of elements by pressing a **“+” button**. Useful when repeating details for multiple items |

### Input Elements

| Element                                                          | Description                                                                                                                                                                                                                                            |
| ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Text**                                                         | Single-line text input for short entries like names or email addresses                                                                                                                                                                                 |
| **Number**                                                       | Input field that only accepts numerical values, with optional min/max limits                                                                                                                                                                           |
| **Date**                                                         | Date picker for selecting calendar dates.                                                                                                                                                                                                              |
| **Rating**                                                       | Star rating input. You can configure how many stars are displayed.                                                                                                                                                                                     |
| **Radio**                                                        | Group of buttons that allow selecting one option from a group of choices                                                                                                                                                                               |
| **Textarea**                                                     | Multi-line text input field for longer content like comments or descriptions                                                                                                                                                                           |
| **Checkbox**                                                     | Toggle input for making yes/no or true/false selections                                                                                                                                                                                                |
| **Select**                                                       | Dropdown menu for choosing a single option from a list.                                                                                                                                                                                                |
| **Multi-Select**                                                 | Dropdown menu for choosing multiple options from a list.                                                                                                                                                                                               |
| [**Formula**](sharinpix-form-formula-functions-and-operators.md) | Displays calculated values or dynamic text based on formulas. Supports conditional logic, field references, and operations (e.g., IF statements, math, and logical operators). Useful for read-only fields, dynamic feedback, and advanced form logic. |

### Media & Signature Elements

| Element       | Description                                                                                                               |
| ------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **Capture**   | Allows users to take and attach photos via the SharinPix Mobile App. Actions available: Capture, PDF, and Template-Image. |
| **Signature** | Captures drawn signatures.                                                                                                |
| **Sketch**    | Provides a drawing canvas for freehand sketches and annotations.                                                          |

### Advanced Tab

| Feature                           | Description                                                                                                                                                                                                                                                                                                                                                |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Form Header                       | Configure a customizable header for the form, which can include titles, logos, or instructions. This header will appear on all rendered forms and PDFs.                                                                                                                                                                                                    |
| Form Footer                       | Configure a footer to display at the bottom of the form or exported PDF. Useful for disclaimers, signatures, or company information.                                                                                                                                                                                                                       |
| Language Support                  | Forms can now be configured in multiple languages. Currently supported: **English** and **French**. This allows end-users to interact with the same form in their preferred language.                                                                                                                                                                      |
| Include hidden fields in Response | This setting determines whether the **SharinPix Form Answer records** are created in **Salesforce** for [**hidden**](form-features-conditional-visibility.md) **Form Elements**. When enabled, Form Answer records are created for hidden elements and when disabled, they are ignored during the Form Answer record creation.                             |
| Geolocation Capture               | <p>Configures the form to automatically record the user's GPS coordinates at specific stages. You can enable two distinct triggers</p><p>• <strong>On Form Start:</strong> Captures the location the moment the user opens the form.</p><p>• <strong>On Form Submit:</strong> Captures the location the moment the user successfully submits the form.</p> |

![](<../.gitbook/assets/Click on the (14) (2).png>)

## Form Features

SharinPix Form Templates offer a range of features that enhance form behavior, data integrity, and user experience. These features can be configured for individual form elements as needed:

| **Feature**                                                                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Required                                                                         | Ensures that certain questions or input fields must be completed before the form can be submitted. When enabled, users will see a visual indicator (such as an asterisk) and receive a prompt if they attempt to submit the form without providing a value for these required fields. This feature helps enforce data completeness and ensures all necessary information is collected.                                                                                      |
| [Prefilled](form-features-default-or-prefill-values.md)                          | Allows specific form elements to be automatically populated with data pulled directly from Salesforce records. Prefilled fields can streamline the user experience, reduce manual data entry, and ensure consistency with existing Salesforce data. For example, a user's name, email, or other record details can be prefilled based on context.                                                                                                                           |
| [Visibility (Conditional Display)](form-features-conditional-visibility.md)      | Enables dynamic control over when a form element is shown or hidden based on the value of other fields or logical conditions (using formulas). This feature allows for more personalized and context-aware forms, showing users only the questions relevant to their responses or profile. For example, an additional comments field may appear only if a user selects "Other" as an option.                                                                                |
| [Magic Fill](form-features-magic-fill.md)                                        | Leverages AI to automatically extract and fill in information from an uploaded image. When Magic Fill is enabled for a field, users can upload a photo (such as an ID card, invoice, or document) and the system will use image recognition to populate the relevant form fields. This reduces manual entry, minimizes errors, and speeds up the form-filling process.                                                                                                      |
| Validation - [using Formulas](sharinpix-form-formula-functions-and-operators.md) | Lets you define custom rules and logic to validate user input before form submission. Validation can be configured using [formulas](sharinpix-form-formula-functions-and-operators.md) to check for specific criteria—such as number ranges, string patterns, or business rules. If a field does not meet the validation requirements, a custom error message can be shown, guiding the user to correct their input. This feature ensures higher data quality and accuracy. |

## Demo - Constructing an Air Conditioning Inspection Form

To use the **SharinPix Form Template Editor** , follow these steps:

Step 1: **Access the Form Template Editor**

* Open the Salesforce App Launcher.
* Search for **SharinPix Form Templates**.
* Click on the **SharinPix Form Templates** object.

Step 2: **Create a New Form Template**

* Click the **New** button to create a new record.
* Fill in the **Form Template Name** and **Description** fields.
* Click **Save** to create the template record.

![](<../.gitbook/assets/Click on the (3) (2) (1).png>)

Step 3: **Using the Form Builder**

* Use the [**available buttons**](sharinpix-form-template-editor.md#form-elements) to insert form elements such as text fields, checkboxes, and dropdowns.
* Arrange sections by dragging and dropping elements.
* The **Preview** **panel** on the right-hand side allows users to see the form in real-time.

![](<../.gitbook/assets/Click on the (16) (2).png>)

Step 4: **Managing Form Details**

* The **Details Tab** contains form metadata such as the template name and description.
* The **Related Objects Section** includes:
  * **Form Elements** : Displays components added to the form.
  * **Form Responses** : Stores submitted form data.

Step 5: **Saving and Previewing the Form in PDF**

* Click **Save** to store the current template.
* In the **preview panel** , switch the Use-Read toggle to preview the PDF version of the form

![](<../.gitbook/assets/Template (3) (2) (1).png>)

{% hint style="success" %}
**Tips:**

* Frequently use the **Preview** feature to verify the user experience.
* Keep forms concise to improve completion rates - using the [Section and Repeated Section elements](sharinpix-form-sections-and-repeated-sections.md) can help here!
{% endhint %}

## Show SharinPix Form PDF Download Button On Submit

![](<../.gitbook/assets/Show Pdf Link On Submit (2).png>)

Check the "**Show PDF link on web form submission** " checkbox to enable the download button to download the submitted form response pdf as shown above.

{% hint style="warning" %}
**Note** :

This feature is will only work in online mode.
{% endhint %}

## Integration with SharinPix Mobile Form Launcher

Forms templates created with **SharinPix Form Template Editor** can be linked with the [**SharinPix Mobile Form Launcher**](/broken/spaces/Hhhsz8OAg6xcF0k0DJhg/pages/Nt8NRMnhV6xJ29Cqi1dY) component. This will permit the filling in of forms through the SharinPix Mobile App.

## Integration with Salesforce Field Service

Forms templates created with **SharinPix Form Template Editor** can be launched on Salesforce Field Service via App Extension where the form can be filled. Please follow the article below for more information on [**integrating SharinPix Form with SFS**](integration-of-sharinpix-form-with-sfs-app-using-app-extension.md).

{% hint style="info" %}
**Info:**

You **cannot** create form templates using the SharinPix Form Template Editor **on mobile**.
{% endhint %}
