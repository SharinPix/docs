# Form Features - Initial/Follow-up Form Responses (Comparative Form)

## Overview

{% hint style="info" %}
SharinPix Form can be configured to **compare current form responses with previous submissions**. This comparative view is particularly useful for follow-up forms, recurring inspections, or progress tracking, where users need to refer to their past inputs to provide updated or more accurate information.

This configuration is made directly from the **SharinPix Form Launcher**.

This article covers the following:

* [How to configure the comparative feature on the SharinPix Form Launcher](form-features-initial-follow-up-form-responses-comparative-form.md#configure-comparative-feature-on-the-sharinpix-form-launcher)
* [How to enable comparative mode on a Universal Link](form-features-initial-follow-up-form-responses-comparative-form.md#enable-comparative-mode-on-a-universal-link)
* [Demo of the Conditional Visibility feature with an Air Conditioning Inspection Example](form-features-initial-follow-up-form-responses-comparative-form.md#demo-air-conditioning-inspection-example)
{% endhint %}

## Getting Started

{% hint style="success" %}
Every submitted form automatically generates a [**Form Response**](/broken/spaces/Hhhsz8OAg6xcF0k0DJhg/pages/73oGMIQ6Qv6yTfqiSkOk), which includes a unique **Form Response Data URL**.
{% endhint %}

### Configure Comparative Feature on the SharinPix Form Launcher

The comparative feature for the SharinPix Form can be configured from the **SharinPix Form Launcher** via the parameter **Initial Form Response** and takes as input <mark style="color:$danger;">`Use the latest form response`</mark> as shown in the diagram below.

After specifying to use the latest form response on the form launcher, the SharinPix Form Template will be opened in comparative mode by using the latest Form Response answers as previous values to compare from.

![](<../.gitbook/assets/DOC SF - 1920 x 1080 (5) (2) (1).png>)

### Enable comparative mode on a Universal Link

{% hint style="info" %}
The user can also enable comparative mode by directly modifying the [SharinPix Form Universal Link URL](integration-of-sharinpix-form-with-sfs-app-using-app-extension.md)
{% endhint %}

* To load a new form that displays answers from a previous submission, add the following custom parameter when opening the form:\
  <mark style="color:$danger;">`ref_response_url=<Form Response Data URL>`</mark>\
  The value for **ref\_response\_url** is the **FormResponseDataURL\_\_c** Field value\*\*,\*\* which stores all the data, including images, of a submitted [_SharinPix Form Response_](sharinpix-forms.md).
* If the referenced response is based on the **same template** , the form will automatically switch to **Comparative Mode**.

### Demo: Air Conditioning Inspection Example

After the user submits the form:

* The form is opened with **Initial Form Response** configured on the [SharinPix Form Launcher](/broken/spaces/Hhhsz8OAg6xcF0k0DJhg/pages/Nt8NRMnhV6xJ29Cqi1dY) or with a <mark style="color:$danger;">`Form Response Data URL`</mark> directly appended to the **SharinPix Form Universal Link.**
* The diagram below shows a form in **Comparative Mode** on the right after the submission on the left.
* This layout helps users quickly identify changes or ensure consistency.

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (3) (2).png>)

When Comparative Mode is activated:

* The form loads your current editable fields **just above** the answers from the referenced submission.
* This makes it easy to **compare** , **verify** , or **update** information based on past responses.
