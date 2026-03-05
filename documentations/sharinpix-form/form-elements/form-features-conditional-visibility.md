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

# Form Features - Conditional Visibility

## Overview

{% hint style="info" %}
SharinPix Form Elements can be configured to be visible only when a particular condition is met. This configuration is available in the [SharinPix Form Builder](sharinpix-form-template-editor.md).

This article covers the following:

* [How to configure a Visibility Condition](form-features-conditional-visibility.md#configure-visibility-conditions)
* [Demo of the Conditional Visibility feature with an Air Conditioning Inspection Example](form-features-conditional-visibility.md#demo-air-conditioning-inspection-example)
{% endhint %}

## Getting Started

### Configure Visibility Conditions

The visibility condition of a SharinPix Form Element can be configured using the "**visible when**" field in the SharinPix Form Builder.

This field can be found in the advanced tab for Question elements and takes as input an expression that evaluates to True or False (boolean).

![](<../.gitbook/assets/conditional visibility.png>)

{% hint style="success" %}
Tips:

For more information on the Functions and Expressions of the Visibility Feature, please follow the article below: [Form Formulas](sharinpix-form-formula-functions-and-operators.md)
{% endhint %}

### Submit answer even when hidden

Use **Submit answer even when hidden** to submit one question's answer when it is hidden.

Questions can be hidden by a visibility condition. By default, answers to hidden questions are not included in a submitted response. They do not reach Salesforce.

The form-level **Include hidden fields in Response** setting controls this default. **Submit answer even when hidden** overrides it for one question. Other hidden questions keep the form's default behavior.

#### Turn on the option

1. Open the form template in the **Form Template Editor**.
2. Select the question you want to configure.
3. Open the question's **Advanced** tab.
4.  Select **Submit answer even when hidden**.

    _Screenshot: Submit answer even when hidden in the Advanced tab._
5. Save and activate the new template version.

<figure><img src="../.gitbook/assets/Form template Editor Doc.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Good to know**

* If the question is inside a hidden section, enable the same option on the section. This keeps the answer in its response location.
{% endhint %}

### Demo: Air Conditioning Inspection Example

This example demonstrates the Conditional Visibility feature within an Air Conditioning Inspection example. If damage is detected, additional fields will be visible to provide more information on the damage.

The example below shows a _textarea_ element - _'Describe the damage'_ , configured with a visibility condition. This element will only be visible when the value of the previous question, _'Are there any signs of damage?'_ , is equal to _'Yes'_.

![](<../.gitbook/assets/conditional visibility 2 .png>)

The diagram below shows the form with the questions 'Is the unit operating properly?' and 'Are there any signs of damage?' only and the elements with conditional visibility not showing.

![](<../.gitbook/assets/conditional visibility 3.png>)

The diagram below shows the form with the two additional questions that became visible when the _'Is the unit operating properly?'_ question was set to '_No_' and _'Are there any signs of damage?'_ question was set to _'Yes'_.

![](<../.gitbook/assets/conditional visibility 4.png>)
