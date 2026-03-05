# Form Features - Spacer Element

## Overview

The **Spacer** element adds vertical spacing between form blocks. It can also act as a visual divider with a background color and it can create a page break in the generated PDF.

### Getting Started

#### How to add a Spacer

1. Open your form template in the **SharinPix Form Template Editor**.
2. From the left sidebar, under **Basic Elements**, select **Spacer**.
3. Drag the Spacer to the position where you want extra space (or a visual divider) between elements.
4. Click the Spacer in the form to open its configuration panel.

<figure><img src="../.gitbook/assets/Form Features - Spacer (1) (2).jpg" alt=""><figcaption></figcaption></figure>

#### Configuration Options

| Option                       | Description                                                                              |
| ---------------------------- | ---------------------------------------------------------------------------------------- |
| **Spacer height**            | Sets the vertical size of the Spacer: **Small**, **Medium**, or **Large**.               |
| **Insert page break on PDF** | When enabled, the Spacer starts a new page in the generated PDF.                         |
| **Color**                    | Sets a background color on the Spacer so it can act as a visual divider or colored band. |
| **Use full width**           | Makes the Spacer and its background color extend across the full form width.             |

Spacers also support conditional visibility, so you can show or hide a Spacer based on other answers.

#### How to configure Spacer height

1. Select the **Spacer** element in the form.
2. In the configuration panel, open the **General** tab.
3. Choose a value for **Spacer height**:
   * **Small** — compact gap (default)
   * **Medium** — moderate gap
   * **Large** — generous gap

The preview updates immediately, so you can adjust spacing between sections as you build the form.

#### How to set a Spacer color

1. Select the **Spacer** element.
2. In the **General** tab, use the **Color** picker to choose a background color.
3. To clear the color and return to a transparent Spacer, select the transparent option in the color picker.

A colored Spacer is useful as a section divider or accent band between groups of questions.

#### How to insert a page break in a PDF

Use this option when related content should stay together on one PDF page, or when a new section should start on a fresh page.

1. Select the **Spacer** element.
2. In the **General** tab, enable [**Insert page break on PDF**](../form-pdf-configuration/sharinpix-forms-pdf-configuration.md#add-page-breaks-on-sharinpix-form-pdf).

<figure><img src="../.gitbook/assets/Form Features - Spacer (2).jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Form Features - Spacer PDF.jpg" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Page break and color**

When **Insert page break on PDF** is enabled, the Spacer is used only to split pages. Its **Color** still appears in the form preview, but it is **not** rendered as a colored band on the PDF.
{% endhint %}

#### How to use full-width

1. Select the **Spacer** element.
2. In the **General** tab, enable **Use full width**.

This lets the Spacer stretch across the form. Any background color stretches with it.

{% hint style="success" %}
**Best Practices**

* Use **Small** / **Medium** / **Large** height to control rhythm between sections without adding empty Paragraph elements.
* Prefer **Insert page break on PDF** at natural section boundaries.
* Combine **Color** with **Use full width** when you want a clear visual band that separates major parts of the form.
{% endhint %}
