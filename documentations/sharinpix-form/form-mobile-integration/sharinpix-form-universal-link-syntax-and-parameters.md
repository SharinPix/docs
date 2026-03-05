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

# Launching a Form on the mobile app (link syntax)

### Overview

{% hint style="info" %}
The SharinPix Form supports **universal links** that allow you to launch a form directly inside the **SharinPix Mobile App** from any external application—such as the Salesforce Mobile App, Field Service Lightning App, or any custom mobile or web application.

Universal links provide a simple, URL-based way to:

* Open a specific SharinPix Form using a secure form token
* Pass additional parameters such as
  * [Prefilled values](sharinpix-form-universal-link-syntax-and-parameters.md#id-1.-prefilled-values)
  * [Enable comparative mode to make a comparative analysis](sharinpix-form-universal-link-syntax-and-parameters.md#id-2.-comparative-mode)
  * [Relaunch an existing form / Open a form with the values of a previously submitted form](sharinpix-form-universal-link-syntax-and-parameters.md#id-3.-relaunch-refill)

This document explains how the universal link works, its syntax, and all the optional parameters supported.
{% endhint %}

### Universal Link Syntax

All SharinPix Forms opened in the mobile app use the following base URL:

**https://app.sharinpix.com/native\_app/form?token=\<sharinpix-form-token>&\<parameter1>=\<value1>&\<parameter2>=\<value2>&....**

#### Components

| Component                                                                       | Description                                                                                                                                                 |
| ------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:$danger;">`https://app.sharinpix.com/native_app/form`</mark> | Entry point used by the SharinPix Mobile App to recognize and open a form                                                                                   |
| <mark style="color:$danger;">`token=<sharinpix-form-token>`</mark>              | **Required**. A [secure token](sharinpix-form-universal-link-syntax-and-parameters.md#understanding-the-sharinpix-form-token) to identify the form instance |
| <mark style="color:$danger;">`&form=<formURL>`</mark>                           | Only required when using **generic tokens**                                                                                                                 |
| <mark style="color:$danger;">`&<parameter>=<value>`</mark>                      | Optional [additional parameters](sharinpix-form-universal-link-syntax-and-parameters.md#parameters)                                                         |

### Understanding the SharinPix Form Token

A **token** is a secure identifier used by SharinPix to authenticate and open forms through a universal link.\
Without a valid token, the universal link cannot launch a form in the SharinPix Mobile App.

You can generate a token that is **linked to one specific form**.

* This type of token is intended for **one-to-one usage**
* The universal link will always open **the exact form**

You can generate this token using the link below: [Generate Token for a Form](../salesforce-integration/automatic-form-token-generation-using-flow-admin-oriented.md)

**Example of universal Link:**

**https://app.sharinpix.com/native\_app/form?token=\<sharinpix-form-token>**

{% hint style="warning" %}
**Note: Generic Token (Advanced / Flexible Use Case)**

In addition to single-form tokens, SharinPix also supports **generic tokens**.

What is a Generic Token?

A **generic token** is a reusable token that can open **multiple different forms**.

Instead of being tied to a specific form, the form is defined dynamically using an additional URL parameter:

<mark style="color:$danger;">`&form=<formTemplateURL>`</mark>

Example: One Token, Multiple Forms

<mark style="color:red;">`https://app.sharinpix.com/native_app/form?token=<sharinpix-form-token>&form=formTemplateURL1`</mark>\
<mark style="color:red;">`https://app.sharinpix.com/native_app/form?token=<sharinpix-form-token>&form=formTemplateURL2`</mark>

Each link opens a different form, even though the **same token** is used.
{% endhint %}

### Parameters

Additional parameters can be used to access **additional features** when using the SharinPix Form. The features that can be used are:

1. [_Prefilled values_](sharinpix-form-universal-link-syntax-and-parameters.md#id-1.-prefilled-values)
2. [_Comparative_](sharinpix-form-universal-link-syntax-and-parameters.md#id-2.-comparative-mode)
3. [_Re-launch (Refill)_](sharinpix-form-universal-link-syntax-and-parameters.md#id-3.-relaunch-refill)
4. [_Await Upload_](sharinpix-form-universal-link-syntax-and-parameters.md#id-3.-await-upload)

### 1. Prefilled Values

SharinPix Form can automatically **retrieve and display values** from related Salesforce records. This feature, known as _prefill functionality_ , allows form fields to be dynamically populated with data from the record where the form is launched.

#### Configuration Steps

1. **Set up in Form Builder**\
   The [_prefill configuration must first be defined within the **SharinPix Form Builder**_](../form-elements/form-features-default-or-prefill-values.md).
2. **Construct the Deeplink**\
   Once configured, you must construct the deeplink (SharinPix Form URL) with the values to prefill.

#### Prefill Parameter

To enable the prefill option, you must use the <mark style="color:$danger;">`pv`</mark> **parameter** followed by the API name of the form element.\
**Syntax:** <mark style="color:$danger;">`pv<ElementApiName>=<Encoded Prefill Value>`</mark>

The value must be **URL-encoded** before being passed.

#### Example Universal Link with Prefill

The following example shows a universal link that pre-fills the **Name** field with _John Doe_ :\
<mark style="color:$danger;">`https://app.sharinpix.com/native_app/form?token=<Your Form Token>&pvName=John%20Doe`</mark>

In this case:

* <mark style="color:$danger;">`pvName`</mark> = API name of the form element
* <mark style="color:$danger;">`John%20Doe`</mark> = URL-encoded value for “John Doe”

#### Multiple Prefills Using Formula Fields

If you need to prefill **multiple fields** in the same form, you can **concatenate the parameters in a Salesforce Formula field**.\
**Formula Example:** <mark style="color:$danger;">`"pvName=" & TEXT(Name) & "&pvAddress=" & TEXT(Address)`</mark>

{% hint style="warning" %}
**Note:**

When constructing deeplinks, **ensure that all values are properly URL-encoded before being passed**. This prevents unexpected behavior and guarantees that special characters are interpreted correctly.

To encode a field value in Salesforce, you can use the following formula:\
<mark style="color:$danger;">`SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(FieldName__c, '%', '%25'), '+', '%2B'), '&', '%26'), '#', '%23'), '?', '%3F'), ' ', '%20'), '_', '%5F'), '-', '%2D'))`</mark>
{% endhint %}

**Universal Link Example with Formula Field:**\
<mark style="color:$danger;">`https://app.sharinpix.com/native_app/form?token=<Your Form Token>&sp_params={!Formula_Field__c}`</mark>

This way, you can dynamically pass several prefill values at once using a single formula field.

{% hint style="info" %}
**Info:**\
For more information on the Prefill Feature, please follow the article below: [_**Default or Prefill Values**_](../form-elements/form-features-default-or-prefill-values.md)
{% endhint %}

### 2. Comparative Mode

The comparative mode enables comparison of previous and current form states. This is especially valuable for follow-up forms, recurring inspections, or progress tracking, where referencing past inputs helps provide updated or more accurate information.

#### Comparative Parameter

To enable the comparative option, you must include the <mark style="color:red;">`ref_response_url`</mark> parameter in the universal link.\
**Syntax:** <mark style="color:$danger;">`ref_response_url=latestFormResponse`</mark>

#### Example Universal Link with Comparative View

The following universal link demonstrates how to add the comparative parameter to a universal link:\
<mark style="color:$danger;">`https://app.sharinpix.com/native_app/form?token=<Your Form Token > &ref_response_url=latestFormResponse`</mark>

{% hint style="info" %}
**Info:**\
For more information on the Comparative Feature, please follow the article below: [_**Initial/Follow-up Form Responses (Comparative)**_](../advanced-form-configuration/form-features-initial-follow-up-form-responses-comparative-form.md)
{% endhint %}

### 3. Relaunch (Refill)

Reopens an existing submitted form with previous answers preloaded.

#### Relaunch Parameter

To enable the relaunch option, you must include the <mark style="color:$danger;">`form_response_url`</mark> parameter in the universal link.\
**Syntax:** <mark style="color:$danger;">`form_response_url=latestFormResponse`</mark>

#### Example Universal Link with Relaunch Parameter

The following universal link demonstrates how to add the relaunch parameter to a universal link:\
<mark style="color:$danger;">`https://app.sharinpix.com/native_app/form?token=<Your Form Token > &form_response_url=latestFormResponse`</mark>

{% hint style="info" %}
**Info:**\
For more information on the Relaunch Feature, please follow the article below: [_**Reopen A Previously Submitted SharinPix Form Using URL Parameters**_](../salesforce-integration/reopen-a-previously-submitted-sharinpix-form.md#reopen-a-previously-submitted-sharinpix-form-using-url-parameters)
{% endhint %}

### 4. Await Upload

A parameter used to show the upload progress of medias from different batches captured using the SharinPix mobile app after submitting a form.

<figure><img src="../.gitbook/assets/DOC Mobile - 1920 x 1080 (8).png" alt=""><figcaption></figcaption></figure>

To enable form await upload, you must include the <mark style="color:$danger;">`await_upload=form`</mark>  in the universal link.

The following demonstrates how to add await upload parameter to a universal link:

<mark style="color:$danger;">`https://app.sharinpix.com/native_app/form?token=<Your Form Token>&`</mark><mark style="color:$danger;">**`await_upload=form`**</mark>&#x20;

{% hint style="info" %}
**Info:**\
The await\_upload parameter can also be configured at the organization level. For more information on how to perform this configuration, refer to the following article:\
​[Await upload in Mobile App Global Configuration](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-global-configuration#configure-the-await_upload-parameter)
{% endhint %}

{% hint style="success" %}
**Best Practices**

* Always **URL-encode** parameter values
* Use generic tokens when managing multiple forms
{% endhint %}
