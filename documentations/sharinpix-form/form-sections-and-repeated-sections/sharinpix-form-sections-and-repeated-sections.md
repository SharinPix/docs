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

# SharinPix Form - Section

## Overview

{% hint style="info" %}
Sections are powerful layout elements that help administrators organize forms into clear, logical groups of related fields. A section can be added to a form through the [SharinPix Form Template Editor](../form-elements/sharinpix-form-template-editor.md).



This documentation covers :

1. [The configuration options of the Section Element](sharinpix-form-sections-and-repeated-sections.md#configuration-options)
2. [How to add questions in Sections](sharinpix-form-sections-and-repeated-sections.md#adding-questions-to-a-section)
3. [The different display styles of Sections](sharinpix-form-sections-and-repeated-sections.md#section-styles)


{% endhint %}

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (56) (3).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Tips:

* Use Sections to break a form into clear, logical parts, such as **Personal Information** and **Inspection Details**.
* In longer forms, Sections make the layout easier to understand by grouping related fields and elements.
* **Sections** can be used to create Child Records on Salesforce. Refer to the documentation on [**Creation of Child Records With Form Sections**](../create-child-records-with-form-sections.md) for more informatio&#x6E;**.**
{% endhint %}

## Configuration Options

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (58).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (59).png" alt=""><figcaption></figcaption></figure>

### General Options

| Option                                                 | Description                                                                                          |
| ------------------------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| Label                                                  | Name of the section displayed to users.                                                              |
| Label Formula                                          | Dynamically generate section titles based on values or conditions.                                   |
| API Name                                               | Unique identifier for referencing in logic or formulas.                                              |
| Edit Section                                           | Click to enter the section presented as a blank form template. Customize it by adding your elements. |
| Style                                                  | Choose a display style (e.g., Full Page/Collapsible/inline).                                         |
| PDF Answer Column Labels                               | Option to display column labels when rendering the form in PDF.                                      |
| Configure background color of the section title on PDF | Option to configure the background color of the section title in PDF.                                |

### Advanced Options

| Option                             | Description                                                                                                                                                          |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Visible When                       | [Conditional visibility](../form-elements/form-features-conditional-visibility.md) rule (show/hide based on formulas).                                               |
| Pull data from a Salesforce record | Configuration for defining a mapping that will be used for prefilling the questions found inside the section using data from a Salesforce record.                    |
| Create a Salesforce record         | Configuration for creating a Salesforce record using data from the section. Refer to [this doc](../create-child-records-with-form-sections.md) for more information. |
| External field mapping             | Option for specifying a question found in the section that will be used to store an external ID. This is useful for updating Salesforce records.                     |

## Adding questions to a section

To add questions to a section:

1. Click on the **Edit section** button on the Section element settings.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (61).png" alt=""><figcaption></figcaption></figure>

2. In the section editor, use the left sidebar to add the elements you want to appear in that section.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (62).png" alt=""><figcaption></figcaption></figure>

## Section Styles

A Section can be displayed in different styles. To configure the style of a Section element, use the **Style** option in the element’s settings.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (63).png" alt=""><figcaption></figcaption></figure>

### Full Page&#x20;

The **Full Page** style is the default Section style. It displays the Section as a button. When the button is clicked, a new page opens and displays the elements contained within that Section. This is demonstrated below.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (65).png" alt=""><figcaption></figcaption></figure>

The image below shows all navigation options available in a **Full Page** section.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (66).png" alt=""><figcaption></figcaption></figure>

1. The **Exit Section** button closes the current section and returns the user to the parent **Full Page** section. If there is no parent section, the user is returned to the main form page.
2. The **Previous Section** button navigates to the previous **Full Page** section. If there is no previous section, it changes to a button that returns the user to the main form page.
3. The **Next Section** button navigates to the next **Full Page** section. If there is no next section, it changes to a button that allows the user to submit the form.
4. The **Navigation Menu** button opens the navigation menu.

The image below shows the navigation menu when opened.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (67).png" alt=""><figcaption></figcaption></figure>

It displays a list of all **Full Page** sections in the form and highlights the current section. Click any section in the list to navigate to it.

{% hint style="warning" icon="triangle-exclamation" %}
The navigation buttons in the bottom bar and the navigation menu are available only when the form contains **Full Page** sections.
{% endhint %}

### Inline

The **Inline** style displays the Section directly within the current form page. Instead of opening on a new page, the Section appears as a grouped container with its fields shown inside it.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (70).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Tip:

This style is useful when you want to group related fields together while keeping them visible in the main form layout.
{% endhint %}

### Collapsible

The **Collapsible** style works like the **Inline** style by displaying the Section directly within the current form page. The difference is that a **Collapsible** Section can be expanded or collapsed, allowing users to show or hide the fields inside as needed.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (71).png" alt=""><figcaption></figcaption></figure>

## Demo: Building Inspection Form

The image below illustrates a form with an **Inline** section for general information and three **Full Page** sections for the building inspection. It also shows how users can use the navigation menu to open other page sections.

<figure><img src="../.gitbook/assets/DOC Mobile - 1920 x 1080 (7).png" alt=""><figcaption></figcaption></figure>
