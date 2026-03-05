# Form Features - Validations

## Overview

{% hint style="info" %}
SharinPix Form Questions can be configured to be valid only when certain conditions are met. Validations can be used to ensure that form answers are in the correct format and valid. This configuration is available in the [SharinPix Form Builder](sharinpix-form-template-editor.md).

This article covers the following:

* [Basic validations using required option](form-features-validations.md#adding-validations-using-required-option)
* [How to configure a Validation Rule](form-features-validations.md#configuring-a-validation-rule)
* [Demo of the Validation Rule feature with an Air Conditioning Inspection Example](form-features-validations.md#demo-serial-number-field-with-validation-rule)
{% endhint %}

## Getting Started

### Adding Validations using Required option

The simplest way to add validations to a Form Question is to use the **required** option. It makes a question mandatory and prevents form submission unless that question has an answer. This feature is available for most questions and can be enabled by ticking the _required_ checkbox as shown below.

![](<../.gitbook/assets/DOC SF - 1920 x 1080 (11) (2).png>)

The picture below demonstrates the required feature configured on the Date question:

1. The required Date field contains an asterisk \* in its label.
2. It is highlighted with a message if it has not been filled when trying to submit the form.
3. There are no error messages once the question has been answered.

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (6).png>)

### Configuring a Validation Rule

A validation condition can be configured for a SharinPix Form Question using the "**validation rule**" field in the SharinPix Form Builder.

This field can be found in the advanced tab for Question elements and takes as input an expression that evaluates to True or False (boolean).

![](<../.gitbook/assets/3 (10).png>)

The example below shows:

1. A validation rule that ensures the value of an input is exactly 10 characters in length.
2. A custom message is configured for that validation rule using the "Message when invalid" field. This field is a SharinPix Formula Field and takes as input an expression that evaluates to a string.

![](<../.gitbook/assets/2 (6) (1).png>)

{% hint style="success" %}
Tips:

For more information on the Functions and Expressions of the SharinPix Formula Field, please follow the article below: [Form Formulas](sharinpix-form-formula-functions-and-operators.md)
{% endhint %}

### Demo: Serial Number field with Validation Rule

This example demonstrates the Validation Rule feature within an Air Conditioning Inspection example. It ensures that the correct serial number is entered for an air conditioning unit.

The validation rule for the _text_ element - '_Air conditioning unit serial number_' is configured as shown below.

![](<../.gitbook/assets/DOC SF - 1920 x 1080 (7) (2).png>)

The diagram below shows:

1. No error messages are shown when the serial number question is empty and the form has not yet been submitted.
2. The serial number question is highlighted and a custom error message is shown when it is incorrectly filled.
3. There are no error messages when the correct serial number is entered.

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (1) (3).png>)
