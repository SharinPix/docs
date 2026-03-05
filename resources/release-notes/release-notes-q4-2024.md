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

# Release Notes - Q4 2024

Known Bug with correction

* SharinPix Mobile App: Torch behaves weirdly (flash icon not appearing) when opening deeplink multiple times with flash=torch
* SharinPix Mobile App: Issue playing video when changing orientation
* SharinPix Mobile App: Uppercase for first character when filling title and description
* SharinPix Mobile App: PDF not opening after executing Delete All Jobs
* SharinPix Album: Fullscreen padding feature was not working as expected on Album and related album components.
* SharinPix Album: When deleting all PDF pages inside a group PDF, the scope does not change back to the album; we were still on the group PDF, and can still delete pages from other PDFs
* SharinPix Album: Very large multi-page PDFs were not rendering
* SharinPix Album: Zoom slider was not working after annotating and saving an image
* SharinPix Album: Zoom Slider was not working when viewing PDFs in fullscreen
* SharinPix Album - 3D viewer: It was not working on the Safari browser
* SharinPix Album: Tag filter not working while having custom sort
* SharinPix PDF Form Builder: Save button visibility Bug when editing field properties
* SharinPix PDF Form Builder: Fix Access Denied on PDF History Download Button
* SharinPix PDF Form Builder: Fix the Copy Link Button disappearing bug when hovering over the PDF template
* SharinPix Search: Blinks when having multiple search components on the same record
* SharinPix Search: Fix token malformed issue for Search Section by Date
* SharinPix Share: Share Link was invalid after some images were deleted
* SharinPix Tag Action Feature: Multiple timeouts occurred on Tag Action creation

New Features

* SharinPix Mobile App: Handle [return URL](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-deeplink-syntax#ret_url) on the [view album](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-deeplink-syntax#view_album) page on the SharinPix Mobile App
* SharinPix Mobile App: Video support on IOS
* SharinPix Mobile App: [Text Recognition on Scan](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-text-recognition-on-scan-ocr)
* SharinPix Mobile App: Set Snap & Say text language to match device language
* SharinPix Mobile App: Make title & description mandatory
* SharinPix Mobile App: Can start and stop video using the volume button
* SharinPix Mobile App: Can take photos while recording a video
* SharinPix Mobile App: Store [OCR data in the SharinPix Image SF field](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-text-recognition-on-scan-ocr#access-scanned-text-on-sharinpix-image-object)
* SharinPix Album: Able to filter an album to display images with specific tags
* SharinPix Album - 3D viewer: Dynamically move point of measurements
* SharinPix Album: [PDF Viewer](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/user-interface/image-and-pdf-quality-settings#quality-original)
* SharinPix Mobile Launcher Component: Dropdown parameter to select Mobile Launcher opening mode
* [SharinPix PDF Form Builder](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-pdf-form-builder): Prefilled value for Checkbox Field
* [SharinPix Related Album Component](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-related-record-albums-lwc): Lightning web component version
* [SharinPix Tag Action](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/working-with-tags/tag-action): Supported on the SharinPix Mobile App
* SharinPix Video: [Video Player on Album Component](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/upload-images/sharinpix-video-capabilities)
* Methods for Automation Use: Implemented new methods ([Purge & Delete](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/cookbook/delete-or-purge-sharinpix-images)) to match RGPD policy
* Document Builder: Added [filter by tag](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/working-with-tags/filter-albums-by-tags-tag-filter) and section by tag on Image Gallery
* File Format: Supports JPEG XL format.
* Utils Methods: Able to [duplicate Images with tags](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/cookbook/utils-methods#duplicatealbum-with-tags-true)
* SharinPix Offline Components for Field Service
* [SharinPix Form](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/overview-and-getting-started/welcome-to-sharinpix-forms)

{% hint style="warning" %}
**Note:**

Latest Version containing the above Bug Fixes and New Features:

* SharinPix Mobile App: v2.6.52216
* SharinPix on Salesforce App Exchange: v.1.334
{% endhint %}
