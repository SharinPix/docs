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

# Form Features - Capture Additional Details for Radio Answers using the Further Info Feature

## Overview

**Further Info** is a feature available for **Radio** form questions. It lets you add follow-up questions to a radio option when you need extra details.

The answers to these follow-up questions do **not** create separate **SharinPix Form Answer** records in Salesforce. Instead, they are stored directly on fields mapped to the main **Radio Form Answer** record which allows for better reporting.

This feature is useful when you want to capture related details while keeping the data linked to a single radio answer.\
\
This article covers:

* [Air Conditioning Demo: Configure Further Info for a radio question](form-features-capture-additional-details-for-radio-answers-using-the-further-info-feature.md#air-conditioning-demo-configure-further-info-for-a-radio-question)

## Air Conditioning Demo: Configure Further Info for a radio question

#### Step 1: Add the additional fields required

* Go to **Object Manager** and open the **SharinPix Form Answer** object.

<figure><img src="../.gitbook/assets/1 (1).png" alt=""><figcaption></figcaption></figure>

* Add one or more fields for the additional information you want to store on the answer record.

<figure><img src="../.gitbook/assets/2 (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/3 (1).png" alt=""><figcaption></figcaption></figure>

#### Step 2: Configure Further Info on the Radio Form Element

* Add a radio question and ensure that you enter its API name.

<figure><img src="../.gitbook/assets/4 (1).png" alt=""><figcaption></figcaption></figure>

* Go to the **Further Info** tab and click on **Edit questions**.

<figure><img src="../.gitbook/assets/5 (1).png" alt=""><figcaption></figcaption></figure>

* Add a follow-up question and enter its API name.

<figure><img src="../.gitbook/assets/6 (1).png" alt=""><figcaption></figcaption></figure>

* You can also configure these questions with [Visibility](form-features-conditional-visibility.md) or [Validations](form-features-validations.md) to fit the use case.

<figure><img src="../.gitbook/assets/7 (1).png" alt=""><figcaption></figcaption></figure>

* Go back to the **Further Info** tab of the radio element.
* Add one or more mappings.
* In each mapping, the [formula](sharinpix-form-formula-fields-and-attributes.md) entry should reference the API name of a **Further Info** question that you defined earlier in **Edit questions**.
* Each mapping writes that value to a Salesforce field on the radio **SharinPix Form Answer** record.

<figure><img src="../.gitbook/assets/8 (1).png" alt=""><figcaption></figcaption></figure>

#### Step 3: Test the form

<figure><img src="../.gitbook/assets/9 (1).png" alt=""><figcaption></figcaption></figure>

* Submit the form and open the related radio **SharinPix Form Answer** record.
* Check if each field used in the mapping has the value from the corresponding _Further Info_ form field.
* Make sure the fields have been added to the layout.

<figure><img src="../.gitbook/assets/10 (1).png" alt=""><figcaption></figcaption></figure>
