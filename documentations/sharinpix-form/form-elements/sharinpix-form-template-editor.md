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

# SharinPix Form Template Editor

## Overview

{% hint style="info" %}
The SharinPix Form Template Editor is a dedicated tool within Salesforce that empowers users to create, edit, and manage form templates. With an intuitive drag-and-drop interface, the editor simplifies the form-building process by allowing users to add various field types, integrate media capture capabilities, preview their forms in real-time, and manage form template versions as each form evolves.

This documentation covers:

* [Form Elements](sharinpix-form-template-editor.md#form-elements)
* [Form Features](sharinpix-form-template-editor.md#form-features)
* [Work with Form Template Versions](sharinpix-form-template-editor.md#work-with-form-template-versions)
* [Demo - Constructing an Air Conditioning Inspection Form](sharinpix-form-template-editor.md#demo-constructing-an-air-conditioning-inspection-form)
* [Integration with SharinPix Mobile Form Launcher](sharinpix-form-template-editor.md#integration-with-sharinpix-mobile-form-launcher)
* [Integration with Salesforce Field Service](sharinpix-form-template-editor.md#integration-with-salesforce-field-service)
{% endhint %}

![](<../.gitbook/assets/Global Setting for the form template (1).jpg>)

{% hint style="warning" %}
**Prerequisites:**

Before using the **SharinPix Form Template Editor**, ensure the following:

* Users must have the **SharinPix Forms Admin** permission set assigned.
* You have the **latest** **SharinPix Package Version** Installed. Refer to [_this documentation_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to update your package.
{% endhint %}

## Getting Started

## Form Elements

Users can add the following types of elements to their forms:

![](<../.gitbook/assets/Global Setting for the form template.jpg>)

### Basic Elements

| Element                                                                                                           | Description                                                                                                                                                                               |
| ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Title**                                                                                                         | Adds a section title to the form.                                                                                                                                                         |
| **Paragraph**                                                                                                     | Inserts descriptive text or instructions in the form.                                                                                                                                     |
| **Rich Text**                                                                                                     | Adds formatted text, including bold, italics, lists, and links.                                                                                                                           |
| [**Section**](../form-sections-and-repeated-sections/sharinpix-form-sections-and-repeated-sections.md)            | Inserts a section divider to group related form elements.                                                                                                                                 |
| [**Repeated Section**](../form-sections-and-repeated-sections/sharinpix-form-sections-and-repeated-sections-1.md) | Similar to a Section, but allows users to dynamically add multiple instances of the same group of elements by pressing a **“+” button**. Useful when repeating details for multiple items |
| [**Table**](form-features-table.md)                                                                               | Displays repeated-section questions as columns in a table.                                                                                                                                |
| [**IFrame**](sharinpix-form-sections-and-repeated-sections.md)                                                    | Embeds a web page in the form.                                                                                                                                                            |
| **Spacer**                                                                                                        | Adds layout spacing and can insert a page break in PDFs.                                                                                                                                  |

### Input Elements

<table><thead><tr><th width="245.57421875">Element</th><th>Description</th></tr></thead><tbody><tr><td><strong>Text</strong></td><td>Single-line text input for short entries like names or email addresses</td></tr><tr><td><strong>Number</strong></td><td><p>Input field that only accepts numerical values, with optional min/max limits</p><p><strong>Constraint</strong>: Number entries support a maximum of 15 total digits. This precision includes all numerical digits across both integers and decimals.</p></td></tr><tr><td><strong>Date</strong></td><td><p>Input field for selecting a <strong>Date</strong>, <strong>Time</strong>, or <strong>Date and Time</strong> value.</p><p>Optional settings include:</p><ul><li>Specify the date format, such as <code>YYYY-MM-DD</code></li><li>Default the field to the current date or time</li><li>Enable <strong>Show "Now" button</strong> to display a button that sets the field to the current date or date and time</li></ul></td></tr><tr><td><strong>Radio</strong></td><td>Group of buttons that allow selecting one option from a group of choices</td></tr><tr><td><strong>Textarea</strong></td><td>Multi-line text input field for longer content like comments or descriptions</td></tr><tr><td><strong>Checkbox</strong></td><td>Toggle input for making yes/no or true/false selections</td></tr><tr><td><strong>Select</strong></td><td>Dropdown menu for choosing a single option from a list.</td></tr><tr><td><strong>Multi-Select</strong></td><td><p>Dropdown menu for choosing multiple options from a list.</p><p><strong>Note</strong>: Selected values are concatenated into a single string. Due to Salesforce platform limits, any characters beyond the 255-character limit are automatically trimmed.</p></td></tr><tr><td><a href="sharinpix-form-formula-functions-and-operators.md"><strong>Formula</strong></a></td><td>Displays calculated values or dynamic text based on formulas. Supports conditional logic, field references, and operations (e.g., IF statements, math, and logical operators). Useful for read-only fields, dynamic feedback, and advanced form logic.<br><br><strong>Constraint</strong>: For numerical calculations, the same 15-digit precision applies as with Number fields. Results exceeding this limit may be truncated.</td></tr><tr><td><strong>Rich Text Area</strong></td><td>Multi-line text input field for entering longer text with basic formatting options, such as font size, text color, bold, italic, underline, alignment, numbered lists, and bullet lists. Useful for formatted comments, descriptions, notes, instructions, or any content that needs more structure than plain text.</td></tr><tr><td><strong>Capture</strong></td><td>Use this element to capture photos in the field while completing a SharinPix Form. Users can add or remove photos at any time before submitting. <a href="mobile-app-configuration-in-form-template-editor.md">Configure the mobile app</a> to customize the photo capture experience.</td></tr><tr><td><strong>Signature</strong></td><td>Use this field to sign the form.<br><br>Configure its alignment in the <a href="../form-pdf-configuration/sharinpix-forms-pdf-configuration.md#signature-alignment">PDF Signature Alignment</a> settings.</td></tr><tr><td><strong>Sketch</strong></td><td>Use this sketch field to annotate an image.<br><br>This component can be configured to take the full width in a PDF.</td></tr></tbody></table>

### Advanced Tab

| Feature                                      | Description                                                                                                                                                                  |
| -------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Value when reopening the form**            | Controls data priority when the form is reopened. You can choose to retain the previous answer, reset it, or allow a new prefill from Salesforce or the URL to overwrite it. |
| **Allow blank to clear field on Salesforce** | When this setting is enabled, submitting an empty value in the input field will clear the existing data in the mapped Salesforce field.                                      |

### Global Setting

| Feature                                        | Description                                                                                                                                                                                                                                                                                                                                                |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Form Header**                                | Configure a customizable header for the form, which can include titles, logos, or instructions. This header will appear on all rendered forms and PDFs.                                                                                                                                                                                                    |
| **Form Footer**                                | Configure a footer to display at the bottom of the form or exported PDF. Useful for disclaimers, signatures, or company information.                                                                                                                                                                                                                       |
| **Language Support**                           | Forms can now be configured in multiple languages. Currently supported: **English** and **French**. This allows end-users to interact with the same form in their preferred language.                                                                                                                                                                      |
| **Edit Theme**                                 | Configure the primary color used across the form. This updates key UI elements such as buttons, links, and sections. For setup steps, see [Form Features - Theme Customisation](form-features-theme-customization.md).                                                                                                                                     |
| **Include hidden fields in Response**          | This setting determines whether the **SharinPix Form Answer records** are created in **Salesforce** for [**hidden**](form-features-conditional-visibility.md) **Form Elements**. When enabled, Form Answer records are created for hidden elements and when disabled, they are ignored during the Form Answer record creation.                             |
| **Geolocation Capture**                        | <p>Configures the form to automatically record the user's GPS coordinates at specific stages. You can enable two distinct triggers</p><p>• <strong>On Form Start:</strong> Captures the location the moment the user opens the form.</p><p>• <strong>On Form Submit:</strong> Captures the location the moment the user successfully submits the form.</p> |
| **Show confirmation when submitting the form** | Displays a confirmation dialog when users click **Submit** on the form.                                                                                                                                                                                                                                                                                    |

## Form Features

SharinPix Form Templates offer a range of features that enhance form behavior, data integrity, and user experience. These features can be configured for individual form elements as needed:

| **Feature**                                                                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Required                                                                         | Ensures that certain questions or input fields must be completed before the form can be submitted. When enabled, users will see a visual indicator (such as an asterisk) and receive a prompt if they attempt to submit the form without providing a value for these required fields. This feature helps enforce data completeness and ensures all necessary information is collected.                                                                                      |
| [Prefilled](form-features-default-or-prefill-values.md)                          | Allows specific form elements to be automatically populated with data pulled directly from Salesforce records. Prefilled fields can streamline the user experience, reduce manual data entry, and ensure consistency with existing Salesforce data. For example, a user's name, email, or other record details can be prefilled based on context.                                                                                                                           |
| [Visibility (Conditional Display)](form-features-conditional-visibility.md)      | Enables dynamic control over when a form element is shown or hidden based on the value of other fields or logical conditions (using formulas). This feature allows for more personalized and context-aware forms, showing users only the questions relevant to their responses or profile. For example, an additional comments field may appear only if a user selects "Other" as an option.                                                                                |
| [Magic Fill](form-features-magic-fill.md)                                        | Leverages AI to automatically extract and fill in information from an uploaded image. When Magic Fill is enabled for a field, users can upload a photo (such as an ID card, invoice, or document) and the system will use image recognition to populate the relevant form fields. This reduces manual entry, minimizes errors, and speeds up the form-filling process.                                                                                                      |
| Validation - [using Formulas](sharinpix-form-formula-functions-and-operators.md) | Lets you define custom rules and logic to validate user input before form submission. Validation can be configured using [formulas](sharinpix-form-formula-functions-and-operators.md) to check for specific criteria—such as number ranges, string patterns, or business rules. If a field does not meet the validation requirements, a custom error message can be shown, guiding the user to correct their input. This feature ensures higher data quality and accuracy. |

## Work with Form Template Versions

After building your form, use form template versions to manage future changes without creating a separate template.

A **Main Form Template** groups all versions of the same form and includes a dropdown for switching between them. When you click Save New Version for the first time, **Version 1** is created automatically.

Before a version is activated, any changes you make are saved to that version. Once the version is activated, saving further changes automatically creates a new version.

You can then review, test, and activate the new version when it is ready.

{% hint style="info" %}
Each version is stored as its own SharinPix Form Template record. Version records use the same name as the main template. Their `sharinpix__RecordType__c` value is `version`, and `sharinpix__VersionNumber__c` identifies the version number.
{% endhint %}

<figure><img src="../.gitbook/assets/Global Setting for the form template (2).jpg" alt=""><figcaption></figcaption></figure>

### Typical workflow

* Create a **Main Form Template**.
* Build the form and save it to create **Version 1**.
* Save any changes to update Version 1 before activation.
* Activate Version 1 when it is ready for use.
* Make and save a new change to create another version.
* Review and activate the new version when it is ready.

<figure><img src="../.gitbook/assets/Form template Editor Doc.jpg" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Only the active version can be launched and submitted. Each Form Response stays linked to the version used for submission.
{% endhint %}

## Demo - Constructing an Air Conditioning Inspection Form

To use the **SharinPix Form Template Editor**, follow these steps:

Step 1: **Access the Form Template Editor**

* Open the Salesforce App Launcher.
* Search for **SharinPix Form Templates**.
* Click on the **SharinPix Form Templates** object.

Step 2: **Create a Main Form Template**

* Click the **New** button to create a new record.
* Fill in the **Form Template Name** and **Description** fields.
* Click **Save** to create the Main Form Template record.

![](<../.gitbook/assets/Click on the (3) (2).png>)

Step 3: **Using the Form Builder**

* Use the [**available components**](sharinpix-form-template-editor.md#form-elements) to insert form elements such as text fields, checkboxes, and dropdowns.
* Arrange sections by dragging and dropping elements.

Step 4: **Saving, Activating, and Previewing the Form**

* When your form is ready, click **Save New Version** to create **Version 1**.
* Click **Activate** to make the form available for users to complete.
* Switch the **Use-Read** toggle to preview the PDF version of the form.

![](<../.gitbook/assets/Global Setting for the form template (7).jpg>)

![](<../.gitbook/assets/Global Setting for the form template (6).jpg>)

Step 5: **Managing Form Details**

* The **Details Tab** contains form metadata such as the template name and description.
* The **Related** tab includes:
  * For a **Main Form Template**, the Related tab shows its version templates, including each version number and activation status. It also shows Forms In Progress and Form Responses across all versions.
  * For a **Version Template**, the Related tab shows Forms In Progress, Form Responses, and Form Questions for that version. Form Questions are the components added to the version.

<figure><img src="../.gitbook/assets/Global Setting for the form template (4).jpg" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tips:**

* Frequently use the **Test** feature to verify the user experience.
* Keep forms concise to improve completion rates - using the [Section and Repeated Section elements](../form-sections-and-repeated-sections/sharinpix-form-sections-and-repeated-sections.md) can help here!
{% endhint %}

## Show SharinPix Form PDF Download Button On Submit

![](<../.gitbook/assets/Global Setting for the form template (8).jpg>)

Enable the "**Show PDF link on web form submission**" checkbox to display the button to download the submitted form response PDF as shown above.

{% hint style="warning" %}
**Note** :

This feature will only work in online mode.
{% endhint %}

## Integration with SharinPix Mobile Form Launcher

Form templates created with the **SharinPix Form Template Editor** can be linked with the [**SharinPix Mobile Form Launcher**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-form-launcher) component. This will allow forms to be filled in through the SharinPix Mobile App.

## Integration with Salesforce Field Service

Form templates created with **SharinPix Form Template Editor** can be launched on Salesforce Field Service via App Extension, where the form can be filled. Please follow the article below for more information on [**integrating SharinPix Form with SFS**](../form-mobile-integration/integration-of-sharinpix-form-with-sfs-app-using-app-extension.md).

{% hint style="warning" %}
**Warning:**

You **cannot** create form templates using the SharinPix Form Template Editor **on mobile**.
{% endhint %}

{% hint style="success" %}
**Tips for working with Beta Features**

\
When using beta features, you may see the following error message in the SharinPix Mobile App: **Please refresh or update your application and verify that a valid form template is used.**

This typically occurs because the beta feature included in the form is not yet supported in your current mobile app version. In the template builder, these features are marked with: **This requires the latest version of the mobile app. Deployment in progress.**

Please keep the following in mind regarding deployment:

* **App Propagation**\
  The mentioned two-week window is the estimated time required for the new version to propagate globally across the App Store and Google Play Store.
* **Manual Updates**\
  Users do not have to wait for the automatic rollout. They can still go to the App Store or Play Store to update the app manually to gain immediate access to the new features.
* **Regional Delays**\
  If you do not see a new version available for download, it may be due to a distribution delay for your specific region. In these cases, the update should appear shortly as the stores finish their rollout.

Use caution when deploying new tools; ensure all users are up to date with the latest app version before activating these features in your templates to prevent service interruptions.
{% endhint %}
