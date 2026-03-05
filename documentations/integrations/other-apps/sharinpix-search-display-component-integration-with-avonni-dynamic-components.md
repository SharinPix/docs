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

# SharinPix Search Display component integration with Avonni Dynamic Components

## Overview

In this documentation, we will show you how to integrate the SharinPix Search Display component with Avonni Data LWC Container. At the end of this integration, you will be able to filter your query and based on the result, it will perform a SharinPix Search and display the result in the component.

{% hint style="info" %}
**Prerequisites:**

Install the Avonni Dynamic Component package from the AppExchange. Direct link here:\
[https://appexchange.salesforce.com/appxListingDetail?listingId=e855ec28-bf2c-47fa-aa38-30b43948ab4f\&tab=d](https://appexchange.salesforce.com/appxListingDetail?listingId=e855ec28-bf2c-47fa-aa38-30b43948ab4f\&tab=d)
{% endhint %}

## Setup

{% hint style="success" %}
Avonni primary documentation can be found here:\
[https://docs.avonnicomponents.com/dynamic-components](https://docs.avonnicomponents.com/dynamic-components)

Avonni Data LWC Container documentation is here:\
[https://docs.avonnicomponents.com/dynamic-components/components/data-lwc-container](https://docs.avonnicomponents.com/dynamic-components/components/data-lwc-container)
{% endhint %}

Drag and drop the Data LWC Container component onto the page layout. Afterwards, configure your query to fetch the corresponding records.

In the LWC Name, add **sharinpix/searchDisplay** and set the value of Record Key Fields Attribute Name to **recordIds**. You can customise this component to display a filter and a search based on a field.

<figure><img src="../../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

## Usage

To use this component dashboard, edit your page layout and drag and drop Avonni Dynamic Component onto your page. Change the Component Name in the builder and choose your component.

<figure><img src="../../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

## Demo

Open your page and play with the filters and search.

<figure><img src="../../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>
