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

# Spring '26 Release Notes

This release introduces significant enhancements to the SharinPix Form engine, a modernized drawing experience, and improved data synchronization between mobile devices and Salesforce.

{% hint style="danger" %}
**IMPORTANT ANNOUNCEMENT**\
\
Starting from this publication, SharinPix will align its release notes communication with the Salesforce seasonal release model.

This means our release notes will now be published three times per year, following the **Spring**, **Summer**, and **Winter** release cycles.

Exceptionally, the Spring '26 Release Notes include only releases starting in January 2026.

This change is intended to provide a clearer, more predictable release communication rhythm for our users, making it easier to follow product updates, improvements, new features, and bug fixes over time.

Future release notes will therefore be structured around these three seasonal releases, while urgent or critical communications may still be shared separately when required.
{% endhint %}

***

## 🛠️ Bug Fixes

### Mobile App

* Sync Stability: Resolved an issue that caused "orphan batches" when submitting forms from the mobile sync page.
* Offline Mode: Fixed a bug that incorrectly redirected users to an error page when opening forms in offline mode.
* iOS Layout: Fixed a visual bug where a black bar would appear at the bottom of the Settings page on certain iOS devices.

### SharinPix Form

* Sketch/Signature Fix: Corrected an issue where sketch and signature images were occasionally missing or distorted on the final PDF.
* Logic Loops: Fixed a rare "infinite loop" crash involving default values in repeated sections.
* Photo Sync: Resolved a performance issue that caused missing photos in certain high-volume form responses.

### Annotations & Drawing

* Rotation Fix: Fixed a bug where arrows and double-arrows were not properly aligned when an image was rotated during the drawing process.

***

## New Features

### SharinPix Forms

* Multi-Level Data Creation: You can now create complex record hierarchies in Salesforce (e.g., repeated sections within repeated sections) directly from a single form submission.
* CSV Datasets: Upload external CSV files to act as data sources for your forms, making it easier to reference external product lists or employee directories.
* Custom PDF Cover Pages: Enhance your professional documentation by adding a customizable cover page to your generated Form PDFs.
* Background Sketches: Provide users with a template or blueprint as a background for "Sketch" questions to ensure more accurate annotations.
* Advanced Formula Logic: New support for "Regex" (pattern matching) and "MediaCount" (counting photos) within your form formulas.

### Drawing & Annotation

* Compact Annotation Menu: A new, draggable, and minimized menu for drawing tools allows you to focus on the image without the interface getting in the way.
* Secondary Color Transparency: New controls to cycle through Transparent, Translucent, and Opaque settings for your drawing tools.

### Mobile App

* Video Gallery Uploads: In addition to capturing live video, you can now select existing videos directly from your device’s photo library.
* Front-Camera Priority: Administrators can now configure specific photo fields to open the front-facing camera by default (ideal for "selfie" style verification).

***

## Enhancements

### User Experience

* Flexible Text Inputs: Text areas in forms are now resizable, allowing users more space to write detailed notes.
* Smarter Sub-questions: Use the "Further Information" feature to trigger additional questions within the same field block, keeping forms compact.
* Improved Form Search: New filters in the Admin Dashboard allow for faster navigation through form responses.
* Localization: Enhanced support for German tags and French date/time formatting.

### Salesforce Integration

* Automated URL Generation: Improved Salesforce Flow actions to generate form URLs with pre-filled parameters and expiry settings.
* Field Visibility in PDFs: Visibility rules for repeated sections now render accurately within generated PDF documents.
* Better Error Handling: New "Retry" mechanisms for failed form responses help ensure your data always reaches Salesforce.

{% hint style="warning" %}
**Note:**

Latest Version containing the above Bug Fixes and New Features:

* SharinPix Mobile App: v.2.6.97944
* SharinPix on Salesforce App Exchange: v.1.395
{% endhint %}
