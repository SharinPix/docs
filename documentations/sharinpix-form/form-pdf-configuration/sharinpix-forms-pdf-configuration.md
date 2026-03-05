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

# SharinPix Form - PDF Configuration

## Overview

The **PDF Configurations** feature in SharinPix Forms allows you to customize the appearance and layout of the generated PDF when a form is submitted. These settings help you create professional, branded PDF documents that meet your organization's needs.

This documentation covers:

* [Header & Footer Configuration](sharinpix-forms-pdf-configuration.md#configuring-header-and-footer-on-sharinpix-form-pdf)
* [Add Page Breaks on Form PDF](sharinpix-forms-pdf-configuration.md#add-page-breaks-on-sharinpix-form-pdf)
* [Customize Colors on PDF](sharinpix-forms-pdf-configuration.md#color-customization-on-sharinpix-form-pdf)
* [pdf-view-for-repeated-questions.md](pdf-view-for-repeated-questions.md "mention")
* [Full Page element](sharinpix-forms-pdf-configuration.md#full-page-element)
  * [Configuring the Full Page element](sharinpix-forms-pdf-configuration.md#configuring-the-full-page-element)
* [Signature Alignment](sharinpix-forms-pdf-configuration.md#signature-alignment)

## Configuring Header and Footer on SharinPix Form PDF

The **Header** and **Footer** allow you to add branded content that appears on every page of the generated PDF

Use them to display your company logo, form title, disclaimers, contact information, or any other branding elements.

### How to Configure

* In the Form Template Editor, click the **Settings** button in the top bar

![](<../.gitbook/assets/1 (2).png>)

* In the settings panel, locate the **Header** and **Footer** fields

![](<../.gitbook/assets/2 (2) (1).png>)

* Use the **Rich Text** editor to add your content
* Click **Save** to apply your changes

### Supported Content

Both Header and Footer fields support the same content types:

| Content Type          | Description                                                                     |
| --------------------- | ------------------------------------------------------------------------------- |
| **Text**              | Add formatted text including bold, italics, and different font sizes            |
| **Images**            | Insert logos or other images by clicking the image icon in the rich text editor |
| **Links**             | Add hyperlinks to external resources                                            |
| **Dynamic Variables** | Insert form values that update automatically (see below)                        |

{% hint style="success" %}
**Tip:** Keep headers and footers concise to maximize space for form content on each page.
{% endhint %}

Here is an example demonstrating how to a configure a header with company logo and a footer with contact information in a **Fire Inspection Form** :

![](<../.gitbook/assets/3 (1) (1) (1).png>)

PDF generated after Form submission:

![](<../.gitbook/assets/4 (2).png>)

### Using Dynamic Variables

You can insert dynamic values into your header and footer using the [Merge Field tool](../form-elements/sharinpix-form-sections-and-repeated-sections-1.md#merge-field-tool) on the Rich Text Editor. These variables are automatically replaced with actual form data when the PDF is generated.

#### Example Variables

| Variable                                                      | Description                                                                                                  |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| <mark style="color:red;">`{!form.response.sfid}`</mark>       | The Salesforce Record ID linked to the form response                                                         |
| <mark style="color:red;">`{!form.response.sfname}`</mark>     | The Salesforce Record Name linked to the form response                                                       |
| <mark style="color:red;">`{!form.template.sfid}`</mark>       | The Form Template ID                                                                                         |
| <mark style="color:red;">`{!form.template.sfname}`</mark>     | The Form Template Name                                                                                       |
| <mark style="color:red;">`{!form.params.<form_param>}`</mark> | Any [SharinPix Form Context Parameter](../advanced-form-configuration/sharinpix-forms-context-parameters.md) |
| <mark style="color:red;">`{!<formula>}`</mark>                | Any [SharinPix Form Formula](../form-elements/sharinpix-form-formula-functions-and-operators.md) result      |

The image below illustrates how to use dynamic variables in a footer, for example:\
<mark style="color:red;">`{!address.value}`</mark>

![](<../.gitbook/assets/5 (1) (1) (1).png>)

## Add Page Breaks on SharinPix Form PDF

Page breaks allow you to control where content splits across pages in the generated PDF. This is useful for keeping related information together or starting new sections on fresh pages.

Page breaks can be added to the PDF by using the "Insert page break on PDF" option on a **Spacer** element as shown below.

![](<../.gitbook/assets/6 (1) (1).png>)

PDF generated after Form submission:

![](<../.gitbook/assets/7 (1) (1).png>)

## Color Customization on SharinPix Form PDF

### Customize Titles on the PDF

The user can configure the **Background Color** of individual titles on the **Form PDF:**

| Element Type         | Configuration                                                                                                                                               |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Title**            | Configure background color of the title on **PDF**                                                                                                          |
| **Repeated Section** | <p>Configure background color of the repeated title on <strong>PDF</strong><br>Configure background color of the sections title on <strong>PDF</strong></p> |
| **Section**          | Configure background color of the section title on **PDF**                                                                                                  |

Here is an example demonstrating how to apply a red color to a title in a **Fire Inspection Form** :

![](<../.gitbook/assets/8 (1) (1).png>)

![](<../.gitbook/assets/10 (1) (1).png>)

PDF generated after Form submission:

![](<../.gitbook/assets/DOC SF - 1920 x 1080 (16).png>)

## PDF view for repeated questions

You can choose a PDF-only layout for each **Repeated Section** element. See [pdf-view-for-repeated-questions.md](pdf-view-for-repeated-questions.md "mention") for setup and export behaviour.

## Full Page element

The **Full Page** element lets you add a full page to a PDF using richtext content and dynamic fields.

The example below shows a **Full Page** element used as a cover page in a PDF.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (94).png" alt=""><figcaption></figcaption></figure>

To add it to a form, select the **Full Page** element from the left sidebar in the Form Editor.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (90).png" alt=""><figcaption></figcaption></figure>

### Configuring the Full Page element

To configure the content of a **Full Page** element, click **Edit Richtext** in the element settings.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (95).png" alt=""><figcaption></figcaption></figure>

This opens the editor in full-screen mode as shown below.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (96).png" alt=""><figcaption></figcaption></figure>

1. Click on an empty area of the page to add a new item. You can then move and resize it anywhere on the page
2. Use the richtext editor to update the content of the selected item.
3. Delete the selected item using the **Delete** button.
4. Set the page background color using the color picker.
5. Add a background image to the page by entering an image URL.
6. Exit the **Full Page** editor.

[Dynamic variables](sharinpix-forms-pdf-configuration.md#using-dynamic-variables) can be added and configured in the richtext editor, as shown below.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (97).png" alt=""><figcaption></figcaption></figure>

### Signature Alignment

Configure the **Signature** element’s alignment in the generated PDF.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080.png" alt=""><figcaption></figcaption></figure>

Different alignments on PDF:

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (1) (4).png" alt=""><figcaption></figcaption></figure>
