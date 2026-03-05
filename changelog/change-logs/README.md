# Changelog - October 2026

## New Features <a href="#new-features" id="new-features"></a>

### Salesforce Package <a href="#sharinpix-forms" id="sharinpix-forms"></a>

* [**Merge PDF**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/cookbook/merge-multiple-pdf-urls-into-a-single-merged-pdf-url): Ability to merge multiple PDF URLs into one PDF URL, using the `mergePdfUrls` global Apex method or the `MergePdfUrlAutomation` Flow action.

## 📈 Enhancements <a href="#enhancements" id="enhancements"></a>

### SharinPix Forms <a href="#forms" id="forms"></a>

* [**Sketch Image Full Width Rendering in PDF**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-sketch-component-with-dynamic-background): Sketch images are now rendered in full width in the generated PDF.
* [**Improved Formula Completion**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-formula-fields-and-attributes): Better autocomplete for formulas.
* [**Rich Text Content Rendering in PDF**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-sections-and-repeated-sections-1)**:** Improved splitting of rich text content across pages in the PDF.
* [**Work with AI File Attachment Warning**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/overview-and-getting-started/generate-forms-with-ai)**:** Added a warning when using large file attachments.
* [**Increased Form Response Error Message Field Size**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/salesforce-integration/sharinpix-form-response#fields-and-relationships): Increased the field length of `sharinpix__ErrorMessages__c` on Form Response records to 50,000 characters to prevent truncation of detailed Salesforce database upsert errors.

### Salesforce Package <a href="#salesforce-package" id="salesforce-package"></a>

* [**Tag Actions for Media Imports**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/cookbook/sharinpix-media-import-feature#overview): Added a checkbox to specify whether tag actions should be triggered for that media.
* [**Tag Options in uploadFromUrl Util Method**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/cookbook/utils-methods#uploadfromurl_2)**:** Added an option to provide a list of tags to be applied to the image being uploaded.

### Core Platform <a href="#core-platform" id="core-platform"></a>

* [**Tag Assignment on Image/Album Duplication**:](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/cookbook/utils-methods#duplicatealbum-with-additional-tags) When duplicating an image or an entire album via API, tags can now be supplied directly in the duplicate request.

## 🛠️ Bug Fixes <a href="#bug-fixes" id="bug-fixes"></a>

### SharinPix Forms <a href="#forms.1" id="forms.1"></a>

* **Duplicate Record Prevention**: Implemented a verification process to prevent the creation of duplicate records during "Upsert on Salesforce" operations from the admin dashboard.
* **Large Dataset Loading**: Fixed a bug that caused an infinite loading screen when using large datasets.
* **Relaunch Form Token Expiry**: Fixed an issue where form relaunch tokens would expire if a user saved a form locally and reopened it after several hours.
* **Object Query Namespace:** Fixed a conflict where Salesforce orgs with custom objects with the same name as internal SharinPix objects (such as `Visit__c`) failed to prefill or push back data in repeated sections.

### Mobile App <a href="#mobile-app" id="mobile-app"></a>

* **Salesforce Field Service Return URL Navigation**: Fixed an issue where completing tasks in the SharinPix Mobile App failed to redirect users back to the Salesforce Field Service Mobile App.

### Salesforce Package <a href="#salesforce-package.1" id="salesforce-package.1"></a>

* **Copy To Clipboard**: Fixed an issue where copy to clipboard would fail or keep previous values when the "Open preview in new tab" setting was enabled.
