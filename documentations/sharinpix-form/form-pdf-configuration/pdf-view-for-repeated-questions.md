---
description: Choose how repeated questions appear in generated PDFs.
---

# PDF view for repeated questions

### PDF view for repeated questions

Use **PDF view** to choose how a **Repeated** question appears in a generated PDF. It does not change the form or mobile app layout.

This setting is for people who build forms in the form editor. It is stored as `pdfStyle` in the form template.

### The two views

| Option           | What the PDF shows                                                                                                                                                             |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Classic View** | Each repeated item appears as its own block. The PDF shows the item title, then label-and-answer pairs. Images appear below the answers. This is the standard form PDF layout. |
| **Table View**   | The repeated question appears as one table. The PDF shows its title, a header row, and one row per item.                                                                       |

#### Classic View:

<figure><img src="../.gitbook/assets/Form Component Doc  (5).png" alt=""><figcaption></figcaption></figure>

#### Table View:

<figure><img src="../.gitbook/assets/Form Component Doc  (6).png" alt=""><figcaption></figcaption></figure>

### Set the PDF view

1. Select the **Repeated** question.
2. Open the **General** tab in its settings.
3. Choose **Classic View** or **Table View** under **PDF view**.

<figure><img src="../.gitbook/assets/Form Component Doc  (7).png" alt=""><figcaption></figcaption></figure>

### Default behaviour

{% hint style="info" %}
If **PDF view** is not set, the PDF follows the existing display style.

A **Table Question** defaults to **Table View**. **Repeated sections** and **Plotted Sections** default to **Classic View**.
{% endhint %}
