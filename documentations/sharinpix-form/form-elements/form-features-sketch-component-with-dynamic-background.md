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
  anchors:
    visible: true
---

# Form Features - Sketch Component with Dynamic Background

## Overview

This article explains how to configure the **SharinPix Sketch Component** with a customizable background.

This article explains:

* [How to configure a **background image**](form-features-sketch-component-with-dynamic-background.md#sketch-with-static-url)
* [Demo of a **dynamic background image using a URL with a Car Inspection Example**](form-features-sketch-component-with-dynamic-background.md#sketch-with-dynamic-url)

## Getting Started

### How to configure a background image

Follow these steps to add a static background URL to your form sketch.

* On the Form Editor Page, select a sketch component and find "Background Image URL" under the "General" tab.
* Configure the formula to accept the URL of an image.

<figure><img src="../.gitbook/assets/DOC - Sketch with Dynamic Background (2).png" alt=""><figcaption></figcaption></figure>

You can also use an image captured in another question as the dynamic background of the **Sketch** component. To do this, reference the Capture question’s `media` attribute and select either `firstUrl` or `lastUrl`, depending on which captured image you want to use.

In the example below, `roof_photos.media.lastUrl` uses the most recently captured image from the **Roof Photos** question as the Sketch background.

<figure><img src="../.gitbook/assets/Copy of DOC SF - 1920 x 1080 (2) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Info:**

For more information on the Functions and Expressions of the Background Image URL, please follow these articles:  [Form Formulas](sharinpix-form-formula-functions-and-operators.md) and [Formula Fields and Attributes](sharinpix-form-formula-fields-and-attributes.md)
{% endhint %}

### Demo: Car Inspection Example

This section will demonstrate how to configure the sketch element with a dynamic background in the context of a car inspection. The use case here is a car inspection after a lease, and one of the steps required is to highlight areas of damage on the vehicle.

Follow these steps to configure a dynamic background URL on your sketch:

* Configure a text component on the SharinPix Form so that it [pulls data from Salesforce](form-features-default-or-prefill-values.md) and makes it disabled. We need the text component in order to have a field that contains the value of `Car_Model__c` which will be used as the background for the sketch.

<figure><img src="../.gitbook/assets/DOC - Sketch with Dynamic Background (3).png" alt=""><figcaption></figcaption></figure>

* Configure the API name of the text component.

<figure><img src="../.gitbook/assets/DOC - Sketch with Dynamic Background (4).png" alt=""><figcaption></figcaption></figure>

* On the SharinPix Sketch component, go to the "Background Image URL" configuration and set it to use the value of the text element 'Car Model URL' that was just configured.

<figure><img src="../.gitbook/assets/DOC - Sketch with Dynamic Background (5).png" alt=""><figcaption></figcaption></figure>

### Results:

#### Example 1 - Sedan Record

<figure><img src="../.gitbook/assets/3 (7).png" alt=""><figcaption></figcaption></figure>

* When opening a Car Inspection record for a Sedan, the form will load the Sedan background image.

<figure><img src="../.gitbook/assets/4 (6).png" alt=""><figcaption></figcaption></figure>

#### Example 2 – Hatchback Record

<figure><img src="../.gitbook/assets/5 (2).png" alt=""><figcaption></figcaption></figure>

* If the same form is opened on a Hatchback record, the Sketch component will display the Hatchback background image.

<figure><img src="../.gitbook/assets/6 (2).png" alt=""><figcaption></figcaption></figure>

### Demo: Roof Inspection example

In this example, the technician first captures a photo of the roof using the **Roof photo** Capture question. The captured image is then automatically reused as the background of the **Mark damage** Sketch component, allowing the technician to annotate the photo directly and highlight any damaged areas.

<figure><img src="../.gitbook/assets/Copy of DOC SF - 1920 x 1080 (3) (2).png" alt=""><figcaption></figcaption></figure>

The Sketch component uses `capture.media.lastUrl` as its dynamic background, which retrieves the most recently captured image from the **Roof photo** question.

The **Visible When** formula `capture.media.count > 0` ensures that the Sketch component is only displayed after at least one image has been captured.

Once the roof photo is captured, it is displayed automatically as the Sketch background. The technician can then draw directly on the image to identify and document the damaged area as shown in the example below.

<figure><img src="../.gitbook/assets/Copy of DOC SF - 1920 x 1080 (5).png" alt=""><figcaption></figcaption></figure>
