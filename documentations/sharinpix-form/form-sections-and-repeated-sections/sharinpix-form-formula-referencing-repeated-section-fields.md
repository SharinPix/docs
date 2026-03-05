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

# SharinPix Form Formula: Referencing Repeated Section Fields

## Overview

{% hint style="info" %}
The Repeated Section question can be used to add any number of pre-defined sections when filling out a form. Each added section can contain its own set values which can be referenced inside formula fields.

This article covers the following:

* [Referencing Repeated Section Fields](sharinpix-form-formula-referencing-repeated-section-fields.md#referencing-repeated-section-fields)
* [Demo: Displaying Comments Field Based on Broken Item Count](sharinpix-form-formula-referencing-repeated-section-fields.md#demo-displaying-comments-field-based-on-broken-item-count)
{% endhint %}

## Getting Started

### Referencing Repeated Section Fields

To reference a nested question from a repeated section in a formula field, use:

<mark style="color:$danger;">`<RepeatedQuestionApiName>.<NestedQuestionApiName>`</mark>

The above expression returns a **list** of all <mark style="color:$danger;">`<NestedQuestionApiName>`</mark> values.

#### Example:

Consider a repeated section with API name <mark style="color:$danger;">`RoomItems`</mark> with a nested question having API name <mark style="color:$danger;">`Status`</mark>

![](<../.gitbook/assets/1 (1) (1) (1).png>)

![](<../.gitbook/assets/4 (1) (1).png>)

In a formula field, you can reference the nested <mark style="color:$danger;">`Status`</mark> field as shown below:

![](<../.gitbook/assets/2 (1) (1) (1).png>)

Because <mark style="color:$danger;">`Status`</mark> is inside the <mark style="color:$danger;">`RoomItems`</mark> repeated section, <mark style="color:$danger;">`RoomItems.Status`</mark> returns a **list of values** – one value for each added _Room Item_

<mark style="color:$danger;">`RoomItems.Status`</mark> will return <mark style="color:$danger;">`['Dirty', 'Clean', 'Broken']`</mark> for the _Room Items_ below:

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (2) (1).png>)

## Demo: Displaying Comments Field Based on Broken Item Count

This example demonstrates referencing a repeated section field in a formula field within a Room Inspection example. If two or more items are broken, an additional required question will be visible to provide more information on the damage and follow-up actions required.

The diagram below shows a _text area_ question configured with a visibility formula. This question is configured to be visible when two or more _Room Items_ have _Status_ "Broken"

The formula uses the <mark style="color:$danger;">`COUNTMATCHES`</mark> function to count the number of times the value <mark style="color:$danger;">`"Broken"`</mark> is found in the list returned by <mark style="color:$danger;">`RoomItems.Status`</mark>.

![](<../.gitbook/assets/3 (2).png>)

The diagram below shows the form filled with only one broken _Room Item._

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (3) (1).png>)

The diagram below shows the form with the _text area_ question visible once a second broken _Room Item_ is added.

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (4).png>)
