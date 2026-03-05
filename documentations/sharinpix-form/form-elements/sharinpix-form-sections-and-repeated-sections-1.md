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

# Form Features - Rich Text Area

## Overview

The **Rich Text Area** element lets users enter longer text with text formatting options inside a SharinPix Form. It can be used for formatted notes, comments, instructions, descriptions, reports, or any field where plain text is not enough.

The Rich Text Area can be added to a form in the [SharinPix Form Template Editor](sharinpix-form-template-editor.md).

This article covers:

* [Element preview](sharinpix-form-sections-and-repeated-sections-1.md#element-preview)
* [Rich Text Area toolbar options](sharinpix-form-sections-and-repeated-sections-1.md#toolbar-options)

## Element preview

The image below shows the Rich Text Area element in the [SharinPix Form Template Editor](sharinpix-form-template-editor.md).

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-28T175541.402 (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

The submitted value for this element is stored in the `RichTextArea__c` field on the `FormAnswer__c` object. This field supports up to `131,072` characters. Values that exceed this limit are not stored. In this case, the error is surfaced in the `FormResponse__c` 's `ErrorMessages__c` field.
{% endhint %}

{% hint style="success" %}
**Tip:**

You can also map this value to a custom Salesforce field. Follow [this documentation](../salesforce-integration/form-features-sync-form-values-to-salesforce.md) to sync form values to Salesforce.

To preserve formatting, map the value to a compatible rich text field.
{% endhint %}

### Toolbar Options

The toolbar appears at the top of the Rich Text Area and provides formatting options for the text entered by the user.

| Tool                         | Description                                                         |
| ---------------------------- | ------------------------------------------------------------------- |
| Font Size                    | Changes the size of the selected text.                              |
| Text Color                   | Changes the color of the selected text.                             |
| Background / Highlight Color | Applies a background or highlight color to the selected text.       |
| Bold                         | Makes the selected text bold.                                       |
| Italic                       | Makes the selected text italic.                                     |
| Underline                    | Underlines the selected text.                                       |
| Align Left                   | Aligns the selected text or paragraph to the left.                  |
| Align Center                 | Centers the selected text or paragraph.                             |
| Align Right                  | Aligns the selected text or paragraph to the right.                 |
| Numbered List                | Creates an ordered list with numbers.                               |
| Bulleted List                | Creates an unordered list with bullet points.                       |
| Merge Field                  | Inserts dynamic values from form fields into the Rich Text content. |
| Image Grid                   | Inserts an image grid from a selected form field.                   |

### Merge Field Tool

The **Merge Field** tool allows you to insert dynamic values from your form into Rich Text content. When the form is submitted and processed, each merge field is replaced with the corresponding value from the selected form field.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T105206.982.png" alt=""><figcaption></figcaption></figure>

#### Demo: Inserting a merge field

1. Click the **Merge Field** button in the Rich Text toolbar.
2. Select the desired **Form Field**.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T111544.108.png" alt=""><figcaption></figcaption></figure>

3. Select the **Attribute** you want to display.
4. Click **Add**.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T111611.432.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Tip:

The available Fields and Attributes are based on the form elements in your form. Different field types expose different attributes (for example, value, label, or other field-specific properties).

For more information about supported form fields and their available attributes, see the [Form Fields & Attributes](sharinpix-form-formula-fields-and-attributes.md) documentation.
{% endhint %}

A merge field is inserted into the Rich Text editor using the syntax shown in the picture below.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T111938.194.png" alt=""><figcaption></figcaption></figure>

The image below shows the rendered output when "Passed" is selected on the **Status** radio question.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T112033.013.png" alt=""><figcaption></figcaption></figure>

### Image Grid Tool

The **Image Grid** tool allows you to display images from a form field in Rich Text content. It inserts a merge field that renders as an image grid when the form is submitted and processed.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T112440.721.png" alt=""><figcaption></figcaption></figure>

The grid's columns and image sizing can be configured after selecting a form field as shown below.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T120514.635.png" alt=""><figcaption></figcaption></figure>

The configuration options are:

1. **Number of columns** — Sets the number of images displayed in each row.
2. **Display in full width** — Expands the grid to use the available content width.
3. **Image size in px** — Sets each image's size in pixels. This option is available when **Display in full width** is not enabled.

#### Demo: Inserting an image grid

1. Click the **Image Grid** button in the Rich Text toolbar.
2. Select the form field whose images you want to display in the grid, then click **Configure**.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T120847.699.png" alt=""><figcaption></figcaption></figure>

3. Set the desired grid layout and click **Save** to insert the image grid field.

The example below uses two full-width columns.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T120928.082.png" alt=""><figcaption></figcaption></figure>

An image grid field is inserted into the Rich Text editor using the syntax shown in the picture below.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T121027.583.png" alt=""><figcaption></figcaption></figure>

The rendered grid can be viewed by switching to the preview tab as show below.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T121058.524.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Tip: The Title and Description added to each photo captured can also be rendered in the Image Grid.
{% endhint %}

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T121448.561 (1).png" alt=""><figcaption></figcaption></figure>

The example below shows an alternative grid layout that uses three columns with images sized at 100 pixels.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-31T121605.421.png" alt=""><figcaption></figcaption></figure>
