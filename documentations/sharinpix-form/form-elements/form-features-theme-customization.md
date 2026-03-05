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

# Form Features - Theme Customization

## Overview

The **Theme Customization** feature allows you to customize the colors used across your form.\
You can configure both the main color and the dark mode appearance to match your branding.

These colors are applied to key UI elements such as buttons, links, and sections.

This article explains:

* [How to configure the **primary color**](form-features-theme-customization.md#how-to-configure-the-primary-color)
* [How to configure **dark mode**](form-features-theme-customization.md#how-to-configure-dark-mode)
* [Demo of **a Theme Customization with a Car Inspection Form**](form-features-theme-customization.md#demo-car-inspection-form-example)

## Getting Started

### How to configure the primary color

Follow these steps to configure the primary color on your form.

1. In the **Form Editor**, open the [**Advanced** tab](sharinpix-form-template-editor.md#advanced-tab).
2. Click **Edit Theme**.
3. Select a color with the color picker.

Once selected, the color will be applied immediately to the form preview.

<figure><img src="../.gitbook/assets/1 (5).png" alt="Theme editor with color picker"><figcaption><p>Use the color picker to choose the primary color for your form.</p></figcaption></figure>

### How to configure dark mode

Follow these steps to configure dark mode on your form.

1. In the **Form Editor**, open the [**Advanced** tab](sharinpix-form-template-editor.md#advanced-tab).
2. Click **Edit Theme**.
3. Toggle the **Theme Mode** to **Dark**.
4. Select the colors you want to use in dark mode.

Once configured, the dark mode colors will be used when the form is displayed in dark mode.

<figure><img src="../.gitbook/assets/3 (9).png" alt="Car Inspection form in dark mode"><figcaption><p>Use the theme mode toggle to choose the dark theme for your form.</p></figcaption></figure>

### Demo: Car Inspection Form Example

This example demonstrates the Theme Customization feature within a **Car Inspection** form.

<figure><img src="../.gitbook/assets/Copy of DOC SF - 1920 x 1080 (1).png" alt="Car Inspection form using theme customisation"><figcaption><p>Example of theme customization applied to a Car Inspection form.</p></figcaption></figure>

<figure><img src="../.gitbook/assets/4 (8).png" alt=""><figcaption><p>End result of theme customization applied in dark mode.</p></figcaption></figure>

{% hint style="success" %}
**Best Practices**

* Choose a color that provides good contrast with text and backgrounds
* Use dark mode colors that remain easy to read
* Ensure accessibility by avoiding overly light colors
* Use your brand’s primary color for consistency across your applications
{% endhint %}

{% hint style="warning" %}
**Notes**

* Only valid HEX color values are supported (e.g. `#FF5733`)
* The system automatically converts the color into the required format for styling
* Check both light mode and dark mode after updating the theme
* Changes are applied dynamically without requiring a page reload
{% endhint %}
