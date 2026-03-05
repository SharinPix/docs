# Changelog - August 2026

## New Features

### SharinPix Forms

* **Form Template Versioning**: SharinPix Form Templates now use [Form Template Versions](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-template-editor#work-with-form-template-versions) to track changes and keep each Form Response linked to the version used for submission.
* **Rich Text Area Image Grid**: The [Rich Text Area](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-sections-and-repeated-sections-1) now supports image grids using images captured in the form.
* **Web-Based PDF Filling**: Users can now fill [PDF forms](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-pdf-form-builder) directly in the web interface and prefill fields with data from a SharinPix Form.

### Mobile App

* **Camera Aspect Ratio**: Administrators can now configure the [mobile camera aspect ratio](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-global-configuration#configure-the-aspect_ratio-parameter), such as 9:16 or 4:3.

### Core Platform

* **Automated Error Notifications**: Administrators can now subscribe to email alerts for technical failures, including failed form responses and import errors.

## 📈 Enhancements

### SharinPix Forms

* **Media Required**: A new [Media Required When formula](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-formula-functions-and-operators) is available for [Capture elements](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-template-editor#form-elements).
* **Optimized Screen Layout**: [Sections](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-sections-and-repeated-sections/sharinpix-form-sections-and-repeated-sections) and [tables](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-table) can now use the full screen width.
* **Full-Width Sketches in PDFs**: [Sketch elements](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-template-editor#form-elements) can now be configured to display at full width in generated PDFs.
* **Form Editor Select All**: The [SharinPix Form Template Editor](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-template-editor) now includes Select All to manage and move multiple elements more efficiently.
* **Manual Retry**: The [SharinPix Form Response](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/salesforce-integration/sharinpix-form-response) view in the Admin dashboard now provides an Upsert on Salesforce option to manually retry data pushback and [related-record creation](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/salesforce-integration/create-and-update-related-salesforce-records-with-sharinpix-form).
* **Conditional Visibility Configuration**: Fixed [Conditional Visibility](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-conditional-visibility) so hidden field values are cleared before submission unless explicitly retained.

### Mobile App

* **Standardized Navigation**: The Exit icon has been replaced with a standard Back button for a more familiar mobile navigation experience.
* **Auto File Export Configuration**: A new configuration option has been added to the [Mobile App Configuration](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/mobile-app-configuration-in-form-template-editor) to automatically save photos captured during form filling to the user's device gallery.

### Salesforce Integration

* **Offline Dataset Control**: Administrators can now choose which [Record Datasets](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/salesforce-integration/record-datasets#flow-input-parameters) are prepared for offline use on mobile devices.

## 🛠️ Bug Fixes

### SharinPix Forms

* **PDF Table Layouts**: Fixed an issue where images in [form tables](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-table) could split across pages or be cut off in generated PDFs.

### Salesforce Integration

* **Salesforce Record Mapping Field Length**: Increased the length of the Salesforce record-mapping field to support larger mappings.

### Core Platform

* **Thumbnail Performance**: Fixed a delay when displaying [tags on image thumbnails](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/user-interface/thumbnail-view-tags).
* **Google Maps Drawing API Compatibility**: Added a compatibility workaround so the [SharinPix Map](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-map) Lightning Web Component continues to work after the Google Maps Drawing API deprecation.
