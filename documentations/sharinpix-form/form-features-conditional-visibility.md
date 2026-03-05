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

![](<../.gitbook/assets/Copy of DOC SF - 1920 x 600 (4).png>)

{% hint style="success" %}
Tips:

For more information on the Functions and Expressions of the Visibility Feature, please follow the article below: [Form Formulas](sharinpix-form-formula-functions-and-operators.md)
{% endhint %}

### Demo: Air Conditioning Inspection Example

This example demonstrates the Conditional Visibility feature within an Air Conditioning Inspection example. If damage is detected, additional fields will be visible to provide more information on the damage.

The example below shows a _textarea_ element - _'Describe the damage'_ , configured with a visibility condition. This element will only be visible when the value of the previous question, _'Are there any signs of damage?'_ , is equal to _'Yes'_.

![](<../.gitbook/assets/DOC SF - 1920 x 600 (5) (2).png>)

The diagram below shows the form with only the first question, _'Are there any signs of damage?'_.

![](<../.gitbook/assets/3 (1) (1) (2).png>)

The diagram below shows the form with the two additional questions that became visible when the _'Are there any signs of damage?'_ question was set to _'Yes'_.

![](<../.gitbook/assets/4 (1) (1) (2).png>)
