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

# Changelog - July 2026

## New Features

### SharinPix Forms <a href="#sharinpix-forms" id="sharinpix-forms"></a>

* **Rich Text Input**: The [Rich Text Area](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-sections-and-repeated-sections-1) can now be used as a standalone form question, giving administrators more flexibility when designing forms.
* **Merge Fields in Rich Text**: Dynamic merge fields can now be inserted into [rich text content](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-sections-and-repeated-sections-1).
* **Rich Text Image Grid**: Image grids can now be embedded directly inside [Rich Text Areas](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-sections-and-repeated-sections-1), making it easier to combine organized photos with written notes.
* **Dark Mode for Form Themes**: [Theme Customization](https://docs.sharinpix.com/forms/form-elements/form-features-theme-customization#how-to-configure-dark-mode) now includes a dark mode.
* **Plotted Sections**: The new [Plotted Sections](https://docs.sharinpix.com/forms/form-elements/form-features-plotted-sections) element lets users place markers on a sketch or drawing and automatically create linked repeated sections for visual inspections and location-based reporting.
* **Record Datasets in Repeated Sections**: Repeated sections can now be prefilled using [Record Datasets](https://docs.sharinpix.com/forms/form-elements/form-features-use-dynamic-salesforce-data-with-record-datasets), bringing structured Salesforce data into forms automatically.
* **Form Editor Fullscreen Mode**: The [SharinPix Form Template Editor](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-template-editor) can now be expanded to fullscreen for a more focused design experience.
* **Voice-to-Form Input Highlighting**: Fields populated automatically through voice input are now highlighted, making captured values easier to review.

### Mobile App <a href="#salesforce-integration" id="salesforce-integration"></a>

* **Dual Camera Video Recording**: The [SharinPix Video Capabilities](https://docs.sharinpix.com/documentation/features/upload-images/sharinpix-video-capabilities) now allow the capture of footage from the front and rear cameras at the same time for more complete field documentation.
* **Dual Camera Preview on Android**: Android users can now see a live preview while recording in dual camera mode. See [SharinPix Video Capabilities](https://docs.sharinpix.com/documentation/features/upload-images/sharinpix-video-capabilities).
* **Upload Status on Checklist Thumbnails**: [Checklist](https://docs.sharinpix.com/documentation/mobile-app/sharinpix-mobile-app-checklist) thumbnails now show upload progress so users can quickly identify which images have synced.&#x20;

## 📈 Enhancements

### SharinPix Forms <a href="#sharinpix-forms.1" id="sharinpix-forms.1"></a>

* **Table Rendering in Form PDFs**: Tables are now rendered in generated form PDFs.
* **Cleaner** [**PDF Tables**](https://docs.sharinpix.com/forms/form-elements/form-features-table): Empty columns are automatically removed from PDF tables to keep exported documents easier to read.
* **Email Alerts for Form Response Sync Failures:** Administrators can now receive email alerts when a SharinPix Form Response fails to sync, making it easier to identify and resolve issues.
* **Prefill Plotted Section Markers from Data**: [Plotted Sections](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-plotted-sections) can now open with markers already positioned from existing data pulled from Salesforce.
* **Marker and Section Linking in Plotted Sections**: Selecting a marker in [Plotted Sections](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-plotted-sections) highlights its corresponding section, and selecting a section highlights its marker, making navigation faster and clearer.
* **PDF File Size**: Reduced generated PDF file sizes.

### Mobile App

* **Configurable Camera Aspect Ratio**: The mobile camera can now open with different [aspect ratios](https://docs.sharinpix.com/documentation/mobile-app/sharinpix-mobile-app-global-configuration#configure-the-aspect_ratio-parameter) to better support varied capture requirements.

### Salesforce Integration <a href="#core-platform.5" id="core-platform.5"></a>

* **Form Template Versioning**: Form templates now support [version tracking](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-template-editor#work-with-form-template-versions), making it easier to manage updates while maintaining compatibility with older configurations.

### Core Platform <a href="#core-platform.5" id="core-platform.5"></a>

* **Download Images as PDF**: One or more images can now be [exported directly as a PDF](https://docs.sharinpix.com/documentation/features/download-images/single-image-download-1).
* **AVIF Image Format Support**: Added support for viewing and rendering AVIF images.
* **PNG Image Rendering**: Images can now be exported in PNG format.
* **Sort Icon Display**: Updated the sort icon display to make its meaning clearer.

## 🛠️ Bug Fixes

### SharinPix Forms <a href="#sharinpix-forms.2" id="sharinpix-forms.2"></a>

* **PDF Generation Timeouts**: Fixed an issue where form PDFs could become stuck instead of generating successfully.
* **Sketch Backgrounds on Android**: Fixed sketch background loading issues on Android.
* **Row Visibility in Form Tables**: Fixed form table rows to follow visibility rules correctly in PDFs.
* **Checkbox Prefill Behavior**: Fixed checkbox prefilling so false values display correctly as unchecked.
* **Images Splitting Across PDF Pages**: Fixed an issue where images could be cut off or split across PDF pages.
* **Comparative Images in PDFs**: Fixed before-and-after comparison images so they display correctly in PDFs.

### Mobile App <a href="#salesforce-integration.1" id="salesforce-integration.1"></a>

* **Sync Page Freeze**: Fixed an issue where the app could remain stuck on the sync page in some launch cases.
* **Mobile Submission with Geolocation**: Fixed crashes that blocked mobile form submission when geolocation fields were used.
* **Black Screen in Dual Camera**: Fixed a black screen issue affecting dual camera mode.
* **Overlapping Pictures in Form PDFs**: Fixed an issue where photos could overlap in PDF exports generated from mobile-captured forms.

### Drawing & Annotation <a href="#salesforce-integration.1" id="salesforce-integration.1"></a>

* **Save Button Visibility**: Fixed an issue where the annotation menu could cover the Save button.
* **Arrow Tools Creating Plotted Sections**: Fixed arrow-based tools so they correctly create linked Plotted Sections.
* **Arrow Tools Without Text**: Fixed arrow tools so they work properly when no text is entered.
* **Delete in Plotted Sections**: Fixed deletion behavior so removing a marker also removes its linked section.

### Core Platform <a href="#salesforce-integration.1" id="salesforce-integration.1"></a>

* **Imports with Empty Filenames**: Fixed import failures caused by blank or unusual filenames.
* **Memory-Related Processing Failures**: Fixed intermittent processing failures caused by memory limits.
* **Dataset Upload Failures**: Fixed an issue that could block some record-dataset uploads.

{% include ".gitbook/includes/this-has-been-generated-wit....md" %}
