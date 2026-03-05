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

# Integration of SharinPix Form with SFS App using App Extension

## Overview

{% hint style="info" %}
SharinPix Form can be integrated with the SFS (FSL) App using App Extension.

This article covers the following:

* [Creation of the App Extension with SharinPix Form universal Link or deeplink](integration-of-sharinpix-form-with-sfs-app-using-app-extension.md#creation-of-the-app-extension)
* SharinPix Form - Additional Parameters
  * [Prefill Functionality](integration-of-sharinpix-form-with-sfs-app-using-app-extension.md#prefill-functionality-in-sharinpix-form)
  * [Pre-Populate Select/Multi-Select Options](integration-of-sharinpix-form-with-sfs-app-using-app-extension.md#pre-populate-select-multi-select-options)
  * [Comparative View](integration-of-sharinpix-form-with-sfs-app-using-app-extension.md#comparative-view)
* [Creation of an App Extension embedding a Field Service Mobile Flow](integration-of-sharinpix-form-with-sfs-app-using-app-extension.md#creation-of-an-app-extension-embedding-a-field-service-mobile-flow)
{% endhint %}

{% hint style="warning" %}
**Assumptions:**

* The **Work Order** object will be used throughout this article.
* The **Work Order** object has a custom field named **SharinPix\_Form\_Token\_\_c** that holds a form token. If you haven't implemented this yet, refer to the article [SharinPix automatic form token generation](../salesforce-integration/automatic-form-token-generation-using-flow-admin-oriented.md) to generate the form token.
{% endhint %}

## Getting Started

One way to launch the SharinPix App from the SFS App using the SharinPix Form is to create an **App Extension**. The latter can embed a URL referring to the SharinPix Form on the SharinPix App, where the form can be filled out.

In this article, you will learn how the SharinPix Form URL is integrated into the SFS mobile App using the SFS App Extension.

## SharinPix Form URLs

### SharinPix Form Universal Link

The format for **universal links** (URL) to open a form in the SharinPix app is as follows:

<mark style="color:$danger;">`https://app.sharinpix.com/native_app/form?token=<sharinpix-form-token>`</mark>

### SharinPix Form Deeplink

The format for **deeplinks** to open a form in the SharinPix app is as follows:

<mark style="color:$danger;">`sharinpix://form?token=`</mark><mark style="color:$danger;">**`<sharinpix-form-token>`**</mark>

## Creation of the App Extension

An App Extension lets users quickly access the SharinPix Form in the SharinPix Mobile App. In this section, we will create an App Extension that launches the SharinPix app from the SFS app.

* Go to Setup, then type Field Service Mobile Settings in the Quick Find box. Click on **Field Service Mobile Settings**.
* Click on the **Field Service Mobile Settings** item (Or any settings relevant to your Organization).

<figure><img src="../.gitbook/assets/1 (3).png" alt=""><figcaption></figcaption></figure>

* Scroll down towards App Extensions Section.
* Click on **Add**. You will be prompted with the screen below:

<figure><img src="../.gitbook/assets/2 (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

* For the **Field Service Mobile Settings**, select the relevant record for your Organization. In our case, it is **Field Service Mobile Settings**.
* For the **Type**, select **Android** if you intend to use the App Extension on Android platforms or select **iOS** if you want to use it on iOS platforms.
* For the **Launch Value**, enter the following SharinPix Deeplink URL for **Android platforms**:

```
    https://app.sharinpix.com/native_app/form?token={!SharinPix_Form_Token__c}
```

Or use the following SharinPix Deeplink URL if you intend to use the App Extension on **iOS platforms**:

```
    https://app.sharinpix.com/native_app/form?token={!$SharinPix_Form_Token__c}
```

{% hint style="warning" %}
**Warning:**

When referencing a Salesforce field name on iOS, you must prefix it with an additional <mark style="color:red;">`$`</mark> (dollar sign). This is required by the iOS App Extension to interpret the field reference correctly.
{% endhint %}

{% hint style="success" %}
**Tips:**

**https://app.sharinpix.com/native\_app/form** refers to the URL that will launch the SharinPix Form through the SharinPix Mobile App. **SharinPix\_Form\_Token\_\_c** refers to the custom field containing the SharinPix form token value defined in the previous sections.
{% endhint %}

* For the field **Label** , enter **Fill Fire Safety Form**
* For the field **Name** , enter **Fire\_Safety\_Form**
* For the field **Scoped To Object Types** , enter **WorkOrder**
* Click on **Save**

{% hint style="warning" %}
**Warning:**

* An App Extension is only visible on the record page of its associated object. You should always ensure that you enter the correct object API name when creating the App Extension.\
  \
  For example, suppose you are creating an App Extension for the Work Order object, the API name entered in the field **Scoped To Object Types** should be **WorkOrder**.\
  \
  If you are using a custom object named MyVisitObject, with MyVisitObject\_\_c as the API name, you should enter **MyVisitObject\_\_c** in the **Scoped To Object Types** field.&#x20;



*   For the following test, ensure that you have installed the SharinPix mobile app on your device.

    You will find more information on where to find the SharinPix app in the article below:\
    \
    [Where to find the SharinPix mobile app](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/where-to-find-the-sharinpix-mobile-app)
{% endhint %}

## SharinPix Form - Additional Parameters

Additional parameters can be used to access **additional features** when using the SharinPix Form. The features that can be used are:

* [Prefilled values](integration-of-sharinpix-form-with-sfs-app-using-app-extension.md#prefill-functionality-in-sharinpix-form)
* [Comparative](integration-of-sharinpix-form-with-sfs-app-using-app-extension.md#comparative-view)
* [Context Parameters](../advanced-form-configuration/sharinpix-forms-context-parameters.md)

{% hint style="info" %}
**Working around Salesforce App Extension limitations**<br>

Since there is a restriction on the number of characters an App Extension can have, a custom field can be added with the value containing all other mobile app parameters. The Universal URL will then be as follows:

<mark style="color:$danger;">`https://app.sharinpix.com/native_app/form?token={!SharinPix_Form_Token__c}&{!Your__Custom_Field__c}`</mark>

On **iOS,** since the Universal Link is encoded by Salesforce Field Service (SFS), the Universal Link URL should then be written as follows:

<mark style="color:$danger;">`https://app.sharinpix.com/native_app/form?token={!$SharinPix_Form_Token__c}&sp_params={!$Your_Custom_Field__c}`</mark>

For example **Your\_Custom\_Field\_\_c** can have the following value:

<mark style="color:$danger;">`pvName=John%20Doe&pvCount=23`</mark>
{% endhint %}

## Prefill Functionality in SharinPix Form

SharinPix Form can automatically **retrieve and display values** from related Salesforce records. This feature, known as _prefill functionality_ , allows form fields to be dynamically populated with data from the record where the form is launched.

### Configuration Steps

1. **Set up in Form Builder**\
   The [prefill configuration must first be defined within the **SharinPix Form Builder**](../form-elements/form-features-default-or-prefill-values.md).
2. **Construct the Deeplink**\
   Once configured, you must construct the deeplink (SharinPix Form URL) with the values to prefill.

### Prefill Parameter

To enable the prefill option, you must use the <mark style="color:$danger;">`pv`</mark> **parameter** followed by the API name of the form element.

* **Syntax:** <mark style="color:$danger;">`pv<ElementApiName>=<Encoded Prefill Value>`</mark>

The value must be **URL-encoded** before being passed.

### Example Universal Link with Prefill

The following example shows a universal link that pre-fills the **Name** field with _John Doe_ :

<mark style="color:$danger;">`https://app.sharinpix.com/native_app/form?token=<Your Form Token>&pvName=John%20Doe`</mark>

In this case:

* <mark style="color:$danger;">`pvName`</mark> = API name of the form element
* <mark style="color:$danger;">`John%20Doe`</mark> = URL-encoded value for “John Doe”

### Multiple Prefills Using Formula Fields

If you need to prefill **multiple fields** in the same form, you can **concatenate the parameters in a Salesforce Formula field**.

* **Formula Example:** <mark style="color:$danger;">`"pvName=" & TEXT(Name) & "&pvAddress=" & TEXT(Address)`</mark>

{% hint style="warning" %}
**Note:**

When constructing deeplinks, **ensure that all values are properly URL-encoded before being passed**. This prevents unexpected behavior and guarantees that special characters are interpreted correctly.

To encode a field value in Salesforce, you can use the following formula:\
<mark style="color:$danger;">`SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(FieldName__c, '%', '%25'), '+', '%2B'), '&', '%26'), '#', '%23'), '?', '%3F'), ' ', '%20'), '_', '%5F'), '-', '%2D'))`</mark>
{% endhint %}

* Universal Link Example with Formula Field:\
  <mark style="color:$danger;">`https://app.sharinpix.com/native_app/form?token=<Your Form Token>&sp_params={!Formula_Field__c}`</mark>

This way, you can dynamically pass several prefill values at once using a single formula field.

{% hint style="info" %}
**Info:**\
\
For more information on the Prefill Feature, please follow the article below: [**Default or Prefill Values**](../form-elements/form-features-default-or-prefill-values.md)
{% endhint %}

## Pre-Populate Select/Multi-Select Options

Select/Multi-Select field values can be prefilled by appending the form URL with the po, the API name of the Select/Multi-Select input field, followed either by the **label;value pair** or by only providing the **value**.

The following shows the **two** options:

| Method                                                                                   | Description                                                                                                                                                                        |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:$danger;">`pomulti_select=value1;value2`</mark>                       | Passing only the value will result in the form using the value as label also.                                                                                                      |
| <mark style="color:$danger;">`poselect=label1:value1;label2:value2;label3:value3`</mark> | Passing the label and value will result in the form using the label as label and value as value. This can be used for specific cases where the label is not the same as the value. |

{% hint style="warning" %}
**Note:**&#x20;

* The value has been URL encoded.
* This will populate the list of options available in the Select/Multi-Select input field and not actually select a value.
* To prefill the Select/Multi-Select input field, use **pv, the apiName of the Select/Multi-Select input field,** followed by the **value, e.g pvselect=value** (value should be in the list of options for that field).
* More details can be found in the [Prefill Functionality in SharinPix Form section](integration-of-sharinpix-form-with-sfs-app-using-app-extension.md#prefill-functionality-in-sharinpix-form).
{% endhint %}

## Comparative View

The **Comparative View** feature allows users to compare current form responses with previous submissions. This is especially valuable for follow-up forms, recurring inspections, or progress tracking, where referencing past inputs helps provide updated or more accurate information.

### Comparative Parameter

To enable the comparative option, you must include the <mark style="color:$danger;">`ref_response_url`</mark> parameter in the universal link.

* Syntax: <mark style="color:$danger;">`ref_response_url=latestFormResponse`</mark>

### Example Universal Link with Comparative View

The following universal link demonstrates how to add the comparative parameter to a deeplink:

<mark style="color:$danger;">`https://app.sharinpix.com/native_app/form?token=<Your Form Token>&ref_response_url=latestFormResponse`</mark>

{% hint style="info" %}
**Info:**

For more information on the Comparative Feature, please follow the article below: [**Initial/Follow-up Form Responses (Comparative)**](../advanced-form-configuration/form-features-initial-follow-up-form-responses-comparative-form.md)
{% endhint %}

## Creation of an App Extension embedding a Field Service Mobile Flow

You can also use App Extensions to launch **Field Service Mobile Flows** from the SFS app.

To do so, you simply need to select **Flow** as the **Type and use the Flow's API name as the Launch Value** in the App Extension detail page, as demonstrated below:

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (5) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tip:**

To learn how to integrate the SharinPix App with SFS using Flows, refer to the following article:

[Integration of SharinPix App with SFS (FSL) App using Flows](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-flows)
{% endhint %}

## Launching the SharinPix app

{% hint style="warning" %}
**Warning:**

1. Please make sure **each form is prime** before using it offline. For more information, follow this article.
2. App Extensions are cached on the Salesforce Field Service mobile app. Therefore, it may happen that changes made to App Extensions are not applied instantly on devices. To ensure that the changes are applied, you can clear the cache on the SFS app as follows:\
   \
   On the SFS app, go to **Profile** → **Settings** → **Advanced Settings** → **Clear Cached Metadata**

If the changes made to the App Extension are still unavailable after clearing the cache, try logging out and back in to the SFS app to force a refresh.
{% endhint %}

You can now launch the SharinPix app from SFS.

* Open the SFS app.
* Choose the Service Appointment record of a WorkOrder record.
* Select **Actions.**
* Then select **Inspection Form**. This option refers to the newly-created App Extension.
* You will then be directed to the SharinPix Form via the SharinPix app.

<figure><img src="../.gitbook/assets/DOC Mobile - 1920 x 1080 (1) (4).png" alt=""><figcaption></figcaption></figure>
