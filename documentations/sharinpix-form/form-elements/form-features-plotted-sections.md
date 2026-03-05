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

# Form Features - Plotted Sections

## Overview

This article explains how to configure the **Plotted Sections** element on a SharinPix Form Template.

The **Plotted Sections** element uses a sketch as the entry point for a [**Repeated Section**](../form-sections-and-repeated-sections/sharinpix-form-sections-and-repeated-sections-1.md).

Each time a user places a marker on the sketch:

* A new repeated section item is created.
* That item stores the details related to that marker.
* The form can capture structured data for every marked location.

This creates a direct link between the marker location and the data entered for it.

This pattern works well when users need to mark a visual position first and then describe what they found.

{% hint style="info" %}
Use the repeated section template to define which fields are created for each marker.
{% endhint %}

This article explains:

* [How **Plotted Sections** work](form-features-plotted-sections.md#how-plotted-sections-work)
* [How to configure **Plotted Sections**](form-features-plotted-sections.md#how-to-configure-plotted-sections)
* [Using the Marker's Annotation Type in Formulas](form-features-plotted-sections.md#using-the-markers-annotation-type-in-formulas)
* [Demo of **Plotted Sections** with a Building Inspection Example](form-features-plotted-sections.md#demo-building-inspection-example)

## Getting Started

### How to configure Plotted Sections

Follow these steps to configure **Plotted Sections** on your form.

* On the Form Template Editor page, add the **Plotted Sections** element to your form.
* Open the **Plotted Sections** configuration.
* Click **Edit section** to define the repeated section template that will be created for each marker.
* Add the background image and configure the markers that users will work on.

<figure><img src="../.gitbook/assets/1 (9).png" alt=""><figcaption></figcaption></figure>

* Add the fields that users must complete for each marked point, such as **Area Inspected**, **Condition**, **Are there any issues?**, and **Description of Issues**.

<figure><img src="../.gitbook/assets/2 (13).png" alt=""><figcaption></figcaption></figure>

Each time a user places a marker on the sketch, the form creates one repeated section item linked to that marker.

{% hint style="info" %}
**Info:**

For more information on configuring repeated section items, please follow the article: [SharinPix Form - Repeated Section](../form-sections-and-repeated-sections/sharinpix-form-sections-and-repeated-sections-1.md)
{% endhint %}

### Using the Marker's Annotation Type in Formulas

Each repeated section item created from a marker stores its tool's type and name. Use these attributes in formulas to tailor fields and logic for each marker.

It can be used when marker types identify different assets. For example, a red marker can identify an antenna. A blue marker can identify a splitter. Each item then displays the questions that apply.

| Attribute           | Purpose                                                |
| ------------------- | ------------------------------------------------------ |
| annotation.toolType | Returns the type of the tool used to place the marker. |
| annotation.toolName | Returns the name of the tool used to place the marker. |

<figure><img src="../.gitbook/assets/Form Component Doc  (12).png" alt=""><figcaption></figcaption></figure>

Check the tool in the [Annotations Configurator](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/user-interface/annotations-configurator "mention") before writing a formula. Use the exact configured values.

For example, a free-sketch tool uses the type `path`, not `Path`. A configured tool named `Antenna` uses `Antenna` as its tool name.

```
annotation.toolType = "sticker"
annotation.toolName = "Antenna"
```

{% hint style="success" %}
**Tips:**

* Inside the repeated section item created for a marker, reference these directly: annotation.toolType and annotation.toolName.
* From a nested question inside that section, reference them through the parent section: parent.annotation.toolType and parent.annotation.toolName.
{% endhint %}

#### Formula Example

<figure><img src="../.gitbook/assets/Copy of DOC SF - 1920 x 1080 (2).png" alt=""><figcaption></figcaption></figure>

Used as the visibility formula on an "Antenna Details" field inside the repeated section template, this field only appears on section items created with the "Antenna" sticker.

{% hint style="info" %}
**Info:**

For more information on writing formulas, please follow these articles: [SharinPix Form Formula Functions and Operators](sharinpix-form-formula-functions-and-operators.md) and [SharinPix Form Formula: Fields and Attributes](sharinpix-form-formula-fields-and-attributes.md)
{% endhint %}

## Demo: Building Inspection Example

This section demonstrates how to use **Plotted Sections** for a building inspection. The inspector marks locations on a building sketch, then captures the condition and any issues found for each marked area.

Follow these steps to configure **Plotted Sections** on your form:

* Add the **Plotted Sections** element to the form.
* Open **Edit section** and add the fields that should be completed for each sticker:

| Label                              | Question Type |
| ---------------------------------- | ------------- |
| Area Inspected (Interior/Exterior) | Select        |
| Condition                          | Text          |
| Are there any issues?              | Radio         |
| Description of Issues              | Text Area     |

* When filling out the form, place a marker on each inspected area of the sketch.
* Complete the repeated section item created for each sticker.

#### Example:

* When the inspector places a marker on the building sketch, the form creates a repeated section item at that location.
* The inspector can then record whether the area is **Interior** or **Exterior**, describe the condition, and note any issues.

<figure><img src="../.gitbook/assets/3 (11).png" alt=""><figcaption></figcaption></figure>



* If the inspector places several markers on the sketch, the form creates one repeated section item for each marker.
* This allows each inspection point to retain its own details while remaining linked to its location on the sketch.

<figure><img src="../.gitbook/assets/4 (10).png" alt=""><figcaption></figcaption></figure>
