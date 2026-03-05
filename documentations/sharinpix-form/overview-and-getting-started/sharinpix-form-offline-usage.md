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

# SharinPix Form Offline Usage

## Overview

{% hint style="info" %}
SharinPix Form Offline Usage allows field users to complete forms without an internet connection. To make this possible, each form template must be opened once while online so it is saved (primed) to the device. After this one-time step, the form can be opened, filled out, and submitted completely offline. When the device reconnects to the internet, the completed form is automatically synced back to Salesforce and attached to the correct Salesforce Object.

**Assumption:** This guide assumes that the integration of SharinPix Form with the Salesforce Field Service (SFS/FSL) mobile app **is already set up** in your org (App Extension, token field, etc.). If you still need to do that setup, follow this guide first: [_Integration of SharinPix Form with SFS (FSL) App using App Extension_](../form-mobile-integration/integration-of-sharinpix-form-with-sfs-app-using-app-extension.md)
{% endhint %}

## Prerequisites

{% hint style="warning" %}
Before using SharinPix Form Offline Usage, ensure the following:

* The **SFS (FSL) integration with SharinPix Form is already in place** (see link in Overview).
* The **Salesforce Field Service Mobile App** is installed on the device.
* The **SharinPix Mobile App** is installed.
* At least one **form template** has been saved on your Salesforce Org.
* The device has an **internet connection for the very first opening** of each form (to save it to the device).
{% endhint %}

## Getting Started

### Priming a Form for Offline Use (one-time per device & per Form template)

1. Connect the device to the **internet**.
2. Open the relevant **Work Order** (or any other record) in the Field Service Mobile App.
3. Tap the action that opens the **SharinPix Form** (from the App Extension).
4. When the form loads, you can close it. The form is now **saved** (primed) on the device.
5. From now on, this form can be used **offline** on this device.

{% hint style="warning" %}
**When to re‑prime?**

If the form template is updated later on, open it **once online** again to refresh the saved version on the device.
{% endhint %}

## Error Message

The screenshot below illustrates the error message that appears when attempting to open a SharinPix Form in the mobile app without having completed the priming step beforehand.

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (1) (3).png>)
