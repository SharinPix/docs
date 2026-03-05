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

# Release Notes - Q4 2025

## 🛠 Bug Fixes

### Mobile App

* Offline Mode: Fixed a bug that incorrectly redirected users to an error page when opening forms in offline mode.
* Camera Performance: Fixed front camera behavior during image capture and corrected camera preview freezing issues on iOS.

### SharinPix Form

* Formula Loading: Corrected formula loading issues to ensure forms open quickly and calculate values reliably.
* Date/Time Modifiers: Fixed date/time modifier behavior to ensure date and time values are applied accurately.
* Data Ordering: Corrected answer value ordering when retrieving submitted form responses.
* Flash Reduction: Fixed a bug where hidden form elements would briefly flash on screen before disappearing.
* External ID Relaunch: Corrected form relaunch behavior when relying on external IDs.
* Data Integration: Fixed issues when submitting a form and returning to the Salesforce Field Service (SFS) app on iOS.
* Large Templates: Fixed errors that occurred when trying to save very large form templates.
* Data Exports: Default values can now be configured to export in data payloads only upon formal submit or save.

### Media & Text

* Magic Fill Textareas: Fixed Magic Fill bugs on textarea fields to ensure generated content inserts properly.
* Label Overlaps: Corrected rich-text image link layouts where they previously overlapped with the submit label.
* Disabled Text Images: Fixed an issue where images failed to display when text inputs were set to disabled.
* Relaunch Images: Fixed image loading and display issues on the form relauncher.
* Safe Filenames: File names with invalid characters are now sanitized and handled more safely during upload.

### PDF Generation

* Photo Volume Fix: Fixed image display issues and corrected form PDF image rendering on mobile devices.
* Blank Pages: Fixed an issue that caused blank PDF pages when forms contained specific sections.
* Fresh Rendering: Reduced PDF cache time to ensure users always download the freshest rendered version.
* URL Parameter Rules: Conditional rules now apply correctly to PDFs when overridden through URL parameters.

## New Features

### SharinPix Form

* Targeted Prefilling: Forms now support prefilling only specific, selected parts of a form, including specific repeated sections.
* QR & Barcode Scanning: Built-in QR code scanning is now available natively within forms to populate fields instantly.
* Automatic Geolocation: Forms can now automatically capture and log GPS coordinates upon form submission.
* "NOW" Quick Select: Added a “NOW” button for date/time fields to make current date and time selection faster for field users.
* Advanced Sharing: Added flexible sharing capabilities for more controlled form access and public distribution.
* Enhanced Navigation: Added new navigation options to move smoothly and quickly between long form sections.
* Preset Sections: Create forms faster in the builder by dragging in pre-configured, reusable preset blocks.
* PDF Page Breaks: Added page break support in generated PDFs to prevent layout cutoff issues.
* PDF Branding: Added PDF branding options, including a main color selection tool to match your company style.
* Formula-Based Question Labels: Labels on questions can now change dynamically based on live formula calculations.
* Smart Option Visibility: Added support for conditional visibility rules on radio, select, and multi-select dropdown choices.
* Advanced List Functions: Added support for `REMOVEBLANKS` and `JOIN` list functions inside the form formula engine.
* AI-Assisted Form Generation: Build forms faster using natural language through a new conversational chat experience.
* Fullscreen Sketch: Added fullscreen sketch capabilities for precise, distraction-free drawings on mobile and web devices.

### Mobile App

* Advanced PDF Photo Fields: Mobile PDF photo fields now support confirmation, document scanning, visual overlays, watermarks, and target size parameters.
* PDFs as Templates: Single-page PDFs can now be handled natively as template images for visual reference.
* Natively Integrated Checklists: PDF photo fields can now open the SharinPix checklist screen directly.
* Dual-Camera Toggle: Users can now select and switch between both front and back cameras for image capture directly within the form interface.
* Offline Formatting: Added support for handling new offline file priming formats to improve offline field usage.

### Salesforce Package

* Online Token Generation: Added a new invocable method to generate SharinPix online tokens dynamically from Salesforce Flows.
* Offline Token Generation: Added an invocable method to generate offline form tokens for disconnected workers.
* In-Progress Launching: Added native support for launching _Form In Progress_ records directly from the Form Launcher component.
* Answer Objects Relations: Added support for tracking repeated sections related to the _Form Answer_ object.

## Enhancements

### User Experience

* Flexible Text Inputs: Text areas in forms are now resizable, allowing users more space to write detailed notes.
* Fullscreen Inputs: Fullscreen input behavior has been improved for active form elements to make typing easier.
* Clean Option Layouts: Beta features are now hidden by default for a cleaner user experience, and form tooltips have been polished.
* Visual Builders: Trash icons, hover behavior, and section reorder handles have been visually improved in the builder.
* WYSIWYG Editing: Added a What-You-See-Is-What-You-Get rich text editor directly inside the form builder for easier layout customization.
* Form Layout Control: Added a hidden block button component and improved section copy-and-paste behavior.

### SharinPix Form

* Reliable Field Formulas: Formula answers can now reference other answers and repeated section values more reliably.
* Dynamic Data Arrays: Added support for array and array-related functions in formulas.
* Formula Preset Rules: Visibility formulas can now be applied directly to preset choices.
* Smart Field Overwrites: Added ability to overwrite Salesforce fields from form configuration, managed by a new boolean field toggle.
* Form Locks: Repeated sections can now be locked dynamically when controlled by formulas.
* Formula Field Controls: Disabled formula handling and display options have been improved.
* Submission Controls: Form launch is now restricted when required token security keys are missing.
* Salesforce Record Criteria: Form answers on Salesforce can now be set to create records only when specific criteria are met.
* Consistent Prefills: Prefill parameters now overwrite existing values more consistently when a form launches.
* Automated Data Routing: Form response URLs are now automatically handled in the _Generate Form URL_ automation.
* Image Sync Timestamps: Image sync completed dates are now tracked and handled directly on the Form Response record.
* Conditional Overwrites: Magic Fill overwrite behavior is now fully configurable by administrators.
* Submission Safety: The form Save button is now automatically disabled while images are still uploading to prevent data loss.
* Magic Fill Expansion: Enabled AI-powered Magic Fill for standard textarea fields.
* Scanner Input Text: Code scanning capabilities have been extended to populate data directly into textarea fields.
* Optimized Image Loading: Form image loading speeds have been improved, and administrators can disable image quality settings where required.
* Offline File Priming: Primed template URLs are now available as offline files in settings requests. Form templates can be marked for priming directly from the builder.
* Version Cleanup: Older primed template versions are automatically unprimed when a newer version takes priority. Unsubmitted drafts and abandoned images are cleaned up more reliably.
* Media Deletion Options: Images can now be deleted directly from web-based form views, relaunch flows, and mobile apps.
* Flexible Action Buttons: A submit button can now be pinned to the bottom bar of the very last form section.

### Mobile App

* OS Support: Improved notification permission handling specifically for Android 14 and iOS devices.
* Watermark Labels: Salesforce tags can now be embedded directly into image watermarks.

### Album Gallery

* Section by Date: Date-sectioned albums now display a clearer placeholder section name when no date metadata is available.
* Dynamic Gallery Buttons: Next and previous navigation buttons are now automatically hidden when only one item is present in the gallery.
* Flicker Reduction: Gallery refresh behavior has been optimized to drastically limit screen flickering.

### Salesforce Integration

* Split Permissions: Different permission sets are now available out-of-the-box for Form Builders (Admins) vs. Form Users (End-users).
* AI Model Selection: Added an automated model selection toggle for the _AI Connect_ automation.&#x20;
* Tab Accessibility: Standard SharinPix tabs are now easier to locate and access within the package layout.

{% hint style="warning" %}
**Note:**

Latest Version containing the above Bug Fixes and New Features:

* SharinPix Mobile App: v.2.6.76077
* SharinPix on Salesforce App Exchange: v.1.388
{% endhint %}

## Release Notes Publication Frequency

{% hint style="danger" %}
**IMPORTANT ANNOUNCEMENT**\
\
Starting from the next publication, SharinPix will align its release notes communication with the Salesforce seasonal release model.

This means our release notes will now be published three times per year, following the **Spring**, **Summer**, and **Winter** release cycles.

This change is intended to provide a clearer, more predictable release communication rhythm for our users, making it easier to follow product updates, improvements, new features, and bug fixes over time.

Future release notes will therefore be structured around these three seasonal releases, while urgent or critical communications may still be shared separately when required.
{% endhint %}
