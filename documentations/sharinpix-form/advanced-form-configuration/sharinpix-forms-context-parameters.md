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

# SharinPix Form - Context Parameters

## Overview

**Context Parameters** allow you to pass custom values to a SharinPix Form when it is launched. These parameters become available throughout the form and can be used in formulas to control behavior, customize content, and adapt the form to different use cases.

This documentation covers:

* [What are Context Parameters](sharinpix-forms-context-parameters.md#what-are-context-parameters)
* [Passing Context Parameters](sharinpix-forms-context-parameters.md#passing-context-parameters)
* [Using Context Parameters in Formulas](sharinpix-forms-context-parameters.md#using-context-parameters-in-formulas)

{% hint style="warning" %}
**Prerequisites:**

* A SharinPix Form Template should already be created. Refer to the [SharinPix Form Template Editor documentation](../form-elements/sharinpix-form-template-editor.md).
* Basic understanding of [SharinPix Form Formulas](../form-elements/sharinpix-form-formula-functions-and-operators.md).
{% endhint %}

## What are Context Parameters

Context parameters are key-value pairs passed to the form via the URL when launching it. Once passed, these values become available throughout the form and can be accessed using the <mark style="color:red;">`form.params object`</mark>.

Example: If you launch a form with <mark style="color:red;">`&context=inspection`</mark> in the URL, you can access this value anywhere in the form using <mark style="color:red;">`form.params.context`</mark>. This returns "inspection".

## Passing Context Parameters

Context parameters are passed as URL query parameters when launching the form.

### URL Format

**Universal Link:**

```
https://app.sharinpix.com/native_app/form?token=<your_form_token>&<param_name>=<value>
```

**Deeplink:**

```
sharinpix://form?token=<your_form_token>&<param_name>=<value>
```

## Using Context Parameters in Formulas

Below are usage examples of **Context Parameters** in **Formulas** for a dynamic **SharinPix Form**.

### Conditional Visibility

Show different form sections based on the context

#### Visibility Formula:

```
form.params.context = "inspection"
```

This makes the element visible only when context=inspection is passed in the URL.

![](<../.gitbook/assets/DOC SF - 1920 x 1080 (12).png>)

#### Example URL:

```
https://app.sharinpix.com/native_app/form?token=<your_form_token>&context=inspection
```

The form launches with the inspection section. The section was not visible on the editor since the **Context Parameter** was not present there.

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (4) (1).png>)

**Use Case**

Create a single form template that adapts to different scenarios:

* context=inspection → Shows inspector-related fields
* context=customer → Shows customer-related fields

### Dynamic Default Values

#### Pre-populate fields with values from the URL:

```
form.params.stage
```

When launched with \&stage=Initial, the field defaults to "Initial".

![](<../.gitbook/assets/DOC SF - 1920 x 1080 (15).png>)

**Example URL:**

```
https://app.sharinpix.com/native_app/form?token=<your_form_token>&stage=Initial
```

The image below shows the form launched with the **Context Parameter** <mark style="color:red;">`stage=Initial`</mark>.

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (6).png>)
