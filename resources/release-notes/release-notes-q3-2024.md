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

# Release Notes - Q3 2024

Known Bug with correction

* SharinPix Mobile App: When Audio Permission is disabled, images were captured twice in Snap & Say mode
* SharinPix Mobile App: Black screen when switching from landscape → portrait after opening Scan and then cancelling
* SharinPix Mobile App: Memory usage increased each time the camera page was opened
* SharinPix Mobile App: Camera crashed when _Wide Angle_ was set to **true**
* SharinPix Mobile App: Unable to submit a PDF form when a required signature field was present, even after signing
* SharinPix Form Checklist: Incorrect Status Rearrangement
* SharinPix Form Checklist: Infinite upload “wait” screen
* SharinPix Album: Incorrect image-selection order
* SharinPix Album: Incorrect page count when exporting a grouped PDF
* SharinPix Album: Sorting an album didn’t update the _Sort Position_ field
* SharinPix Single-Image Component: Large-size image displayed at incorrect scale

New Features

* SharinPix Mobile App: [Roomplan](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-roomplan)
* SharinPix Mobile App: [SharinPix Video on Android](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/upload-images/sharinpix-video-capabilities)
* SharinPix Mobile App: [OCR](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-text-recognition-on-scan-ocr)
* SharinPix Mobile App: Swipe gesture on media preview page
* SharinPix Mobile App: [Auto Tags](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-deeplink-syntax#auto_tags) on PDF Form
* SharinPix Mobile App: Handle [return URL ](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-deeplink-syntax#ret_url)when using PDF
* SharinPix Form Checklist: UI Enhancement
* SharinPix Album: Copy and paste images along with the title and description
* SharinPix Album: [Thumbnail for 3D Animation](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-roomplan)
* SharinPix Album: Download types available for both [full and original images](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/the-sharinpix-image-object#image-urls).
* Document Builder: [SharinPix Image Gallery](/broken/spaces/5EvYRrLbUyvRh8o1jmMG/pages/SYMU6s4oYERHwdzeUJ6n) Component to display images on generated documents
* SharinPix Webform: [Handle album validated event](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/upload-images/upload-using-webforms#lightning-web-component)
* SharinPix Permission: [Upload with custom metadata](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/cookbook/upload-images-with-custom-metadata-developer-oriented)
* SharinPix Permission: Filter according to specific custom metadata
* SharinPix Permission: Language translation ability
* Download: Force to download in JPG format instead of AVIF
* Annotations Configurator: UI Enhancement
* Annotations Configurator: Able to save Annotation Configs

{% hint style="warning" %}
**Note:**

Latest Version containing the above Bug Fixes and New Features:

* SharinPix Mobile App: v2.6.40907
* SharinPix on Salesforce App Exchange: v.1.320
{% endhint %}
