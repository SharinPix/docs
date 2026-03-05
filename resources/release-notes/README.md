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

# Summer '26 Release Notes

This release introduces significant enhancements to the SharinPix Form engine, a modernized drawing experience, and improved data synchronization between mobile devices and Salesforce.

***

## New Features

### SharinPix Forms

* [**Customizable Form Themes**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-theme-customization) — Set primary colors and enable dark mode for a fully branded form experience
* [**Rating Input** ](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-template-editor#input-elements)— New rating question type for collecting numeric scores visually
* [**Further Info**](https://docs.sharinpix.com/forms/form-elements/form-features-capture-additional-details-for-radio-answers-using-the-further-info-feature) — Add follow-up questions within a single question for richer data capture
* [**Duplicate Repeated Sections**](https://docs.sharinpix.com/forms/form-sections-and-repeated-sections/sharinpix-form-sections-and-repeated-sections-1) — Quickly duplicate an existing repeated section along with its content
* [**Rich Text Area Input**](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-sections-and-repeated-sections-1) — Configure which formatting options appear in rich text fields
* [**Cover Page Merge Fields**](https://docs.sharinpix.com/forms/form-pdf-configuration/sharinpix-forms-pdf-configuration) — Use dynamic merge fields on form cover pages for personalized documents
* [**Sketch With Dynamic Background**](https://docs.sharinpix.com/forms/form-elements/form-features-sketch-component-with-dynamic-background) — Add a background image to sketch/drawing questions for guided annotations
* [**Date Formula**](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-formula-functions-and-operators) — Auto-populate date fields using formula expressions
* [**Display Values in Formulas**](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-formula-fields-and-attributes) — Show user-friendly display values alongside raw formula results
* [**Iframe**](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-sections-and-repeated-sections) — Add an iFrame element to display external links or resources within a form
* [**Record Dataset (Online & Offline)**](https://docs.sharinpix.com/forms/form-elements/form-features-use-dynamic-salesforce-data-with-record-datasets) — Define reusable datasets for dropdown options, with offline support on mobile
* [**Create Record Dataset via Salesforce Flow**](https://docs.sharinpix.com/forms/salesforce-integration/record-datasets#how-to-create-a-record-dataset) — New invocable action to generate a record dataset and upload it to your storage
* [**Form Relauncher in Flows & Digital Experience**](https://docs.sharinpix.com/forms/salesforce-integration/reopen-a-previously-submitted-sharinpix-form) — Use the Form Relauncher component in Salesforce Flows and Experience Cloud sites

### Drawing & Annotation <a href="#drawing-and-annotation" id="drawing-and-annotation"></a>

* [**Compact Drawing Menus**](https://docs.sharinpix.com/documentation/features/user-interface/large-view-toolbar-new-annotation-toolbar) — Redesigned compact menus for action, color, size, and tool selection, providing more workspace on screen

### Mobile App <a href="#mobile-app.1" id="mobile-app.1"></a>

* [**PDF Form Filling**](https://docs.sharinpix.com/forms/form-elements/mobile-app-configuration-in-form-template-editor) — Fill PDF templates with SharinPix Forms directly on mobile
* [**Dual Camera Capture**](https://docs.sharinpix.com/documentation/mobile-app/sharinpix-mobile-app-deeplink-syntax#direction) — New option to launch dual camera directly from capture
* [**Wait For Photo Uploads Before Submitting Form**](https://docs.sharinpix.com/forms/form-mobile-integration/sharinpix-form-universal-link-syntax-and-parameters) — Option to wait for all photo uploads to complete before submitting a form

***

## Enhancements <a href="#enhancements" id="enhancements"></a>

### SharinPix Forms <a href="#sharinpix-forms" id="sharinpix-forms"></a>

* **Rich Text Sync to Salesforce** — Rich text answers now sync back to Salesforce rich text fields
* **Pre-populate Repeated Sections** — Repeated section values are now pre-populated when relaunching a follow-up form
* **Relaunch Response Lookup** — Relaunched form responses are now linked back to the original response via a lookup field
* **Multi-Select Field Sanitization** — Multi-select field values are properly sanitized during Salesforce sync
* **15-Digit Number Field Limit** — Number fields now enforce a maximum of 15 digits (including decimals)
* **Copy & Cut Multiple Elements** — Copy and cut multiple form elements at once in the editor
* **Drag and Drop Reordering** — Drag and drop support for rearranging elements in the form editor
* **Submit Confirmation Dialog** — A new confirmation modal appears before final form submission to prevent accidental submits
* **Custom Submit Button Translations** — Submit button now supports custom translations
* **PDF Image Overflow Fix** — Images in PDFs with headers/footers no longer overflow the page
* **Dataset Duplicate Filtering** — Datasets automatically filter duplicate entries
* **Rich Text URL Handling** — Improved rich text URL handling
* [**Relaunch Preserves Filled Values**](https://docs.sharinpix.com/forms/salesforce-integration/reopen-a-previously-submitted-sharinpix-form#prefill-behavior-when-reopening-a-form) — Form relaunch no longer overwrites values that were already filled in
* **Nested Repeated Section Support** — Support for nested (multi-level) repeated section record creation in Salesforce
* **Clearer Sync Error Messages** — Clearer error messages when Salesforce sync fails
* **Full-Width Form Tables** — Form tables now display at full width
* **AI Chat Auto-Scroll** — Improved AI form generation chat experience (auto-scroll)
* **Increase Share Redirect URL Field Length** — Increased `RedirectUrl__c` field length in SharinPix Share\_\_c object to support longer redirect URL
* **Formula Editor Auto-Complete** — Intelligent, scoped suggestions when writing formulas in the editor

### Drawing & Annotation <a href="#drawing-and-annotation" id="drawing-and-annotation"></a>

* **Compact Tool Menu Layout** — Streamlined tool menus with compact layout for action, color, size, and tool panels

### Mobile App <a href="#mobile-app" id="mobile-app"></a>

* **Upload Reliability on App Close** — Improved upload reliability when the app is closed mid-submission
* **Orphan Upload Batch Fix** — Fixed orphan upload batches, ensuring all queued photos are synced
* **App Version Tracking** — App version is now tracked in form submissions for easier support troubleshooting
* **Expired Token Session Security** — Improved session security — prevents job creation with expired token

***

## Bug Fixes <a href="#bug-fixes" id="bug-fixes"></a>

### Mobile App <a href="#mobile-app" id="mobile-app"></a>

* **Camera Distortion on iPad** — Fixed camera distortion issue on iPad devices
* **Dual Camera Video Crash** — Fixed crash when using dual camera in video mode
* **Camera Not Active Error** — Fixed "camera not active" error when switching between camera modes
* **Deep Link Crash on iOS** — Fixed app crash when opening deep links on iOS
* **Background Upload on Android** — Fixed background photo upload failing on Android
* **Wide-Angle Lens Init Error** — Fixed wide-angle lens camera initialization error
* **Form Redirection After Submit** — Fixed form redirection issue after submission on mobile
* **Black Bar on Settings Page** — Fixed black bar appearing at the bottom of the Settings page on iOS
* **Delete Draft Forms Error** — Fixed error when deleting draft forms
* **Volume Button Controls** — Fixed volume button controls not responding
* **Camera Reopen After Close** — Fixed issue where the camera could not be reopened after closing

### SharinPix Forms <a href="#sharinpix-forms" id="sharinpix-forms"></a>

* **Photo Upload Overwriting Fields** — Fixed issue where photo uploads could overwrite other form field values during Salesforce sync
* **Set to Current Date / Today Buttons** — Fixed "Set to Current Date" and "Today" buttons not working in date fields
* **Blank Form Answers** — Fixed form responses occasionally having blank/null answers
* **Responses Stuck in Processing** — Fixed form responses getting stuck in "Processing" status
* **PDF Generation Error 503** — Fixed error 503 when generating form PDFs
* **Sync Status Message Not Clearing** — Fixed sync status message not clearing after a successful Salesforce submission
* **Formula Field Data Type Handling** — Fixed formula field data type handling when creating form answers
* **Special Characters in Export File Names** — Fixed exported file names not rendering correctly when containing special characters
* **Permission Validation on Sync** — Fixed permission validation issue when syncing form data to Salesforce
* **Salesforce Upload Auth Error** — Fixed authentication error when loading the Salesforce upload page
* **Duplicate IDs in Repeated Sections** — Fixed duplicate IDs appearing when copying repeated sections
* **Formula Calculations in Sub-Questions** — Fixed formula calculations not working correctly in sub-questions
* **Salesforce Error Handling** — Fixed form error handling when Salesforce returns an error

***

{% hint style="warning" %}
**Note:**

Latest Version containing the above Bug Fixes and New Features:

* SharinPix Mobile App: v2.7.6819
* SharinPix on Salesforce App Exchange: v.1.403
{% endhint %}
