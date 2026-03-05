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

# Form Features - Table

## Overview

The **Table** element is a display style of the [Repeated Sections](../form-sections-and-repeated-sections/sharinpix-form-sections-and-repeated-sections-1.md) element. It presents a set of predefined questions in a tabular format, where each row represents a separate entry and can contain its own values.

You can add a Table element to a form by selecting **Table** from the left sidebar in the SharinPix Form Builder.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-28T163224.680.png" alt=""><figcaption></figcaption></figure>

You can also create one by adding a **Repeated Sections** element and then changing its **Style** setting to **Table**, as shown below.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (1920 x 600 px).svg" alt=""><figcaption></figcaption></figure>

## Configure the questions for each column

You can define which questions appear in each column of the table.

To configure questions:

1. In the **Repeated Sections** element settings, click **Edit Section**.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-28T170819.329.png" alt=""><figcaption></figcaption></figure>

2. In the section editor, use the left sidebar to add the elements you want to appear in each column. Each added element becomes a column in the table. In the example below, two questions have been added, so the table displays two question columns.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (51).png" alt=""><figcaption></figcaption></figure>

The image below shows the resulting **Table** element with those row questions applied.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (1920 x 600 px) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Configuration Options

### Advanced Options

| Option                      | Description                                            |
| --------------------------- | ------------------------------------------------------ |
| Hide empty columns on table | Hides columns whose questions are hidden in every row. |

{% hint style="success" %}
Tip:

All other configuration options for a [Repeated Sections](../form-sections-and-repeated-sections/sharinpix-form-sections-and-repeated-sections-1.md#configuration-options) element are also available for the "Table" display style.
{% endhint %}

#### Hide empty columns in the table

When [conditional visibility](form-features-conditional-visibility.md) hides all answers in a column, this option removes the column rather than leaving it empty.

The example below shows the **External ID** column hidden when this option is enabled.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-28T172326.328.png" alt=""><figcaption></figcaption></figure>

## Configure the default number of rows

A **Repeated Sections** element can be configured with a default number of initial sections. For a **Table** element, this setting determines how many rows are shown by default.

To configure the default number of rows, open the **Default** tab in the **Repeated Sections** element configuration, then click the **+** button to add rows, as shown below.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 - 2026-08-28T173311.069.png" alt=""><figcaption></figcaption></figure>
