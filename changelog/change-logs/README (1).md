# Changelog - September 2026

## New Features

### SharinPix Forms

* [**Plotted Section - Annotation-Based Questions**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-plotted-sections#using-the-markers-annotation-type-in-formulas): Display different questions based on the annotation tool name or type.

## 📈 Enhancements

### SharinPix Forms

* [**Image Titles and Descriptions in Rich Text Grids**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-sections-and-repeated-sections-1#demo-inserting-an-image-grid): Titles and descriptions added to captured photos can now be displayed in Rich Text Area image grids.
* Repeated Section[ **Form and PDF Layouts**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-pdf-configuration/pdf-view-for-repeated-questions#pdf-view-for-repeated-questions): Choose how repeated sections are displayed independently in the form and in the generated PDF, for example, inline, table, and plotted layouts.
* [**Full-Width Plotted Sections in PDFs**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-plotted-sections#how-to-configure-plotted-sections): Plotted section sketches can now use the full available page width in generated PDFs.
* [**Conditional Table Column visibility:**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-table#hide-empty-columns-in-the-table) A table column is no longer rendered in the PDF when all of its contents are hidden.
* [**Spacer Element background color**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-spacer-element#configuration-options): Set a background color for Spacer elements.

### Salesforce Integration

* [**Programmatic Image Selection via custom events**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/cookbook/handle-image-selection-on-sharinpix-album-developer-oriented#setup): Album images can now be selected or cleared from custom Salesforce components.

### Core Platform

* **Updated SharinPix Settings Page**: Organization, Mobile App Configuration, and [notification settings](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/notification-settings#open-the-notifications-tab) tabs are now easier to access from the SharinPix Settings page in Salesforce.

## 🛠️ Bug Fixes

### SharinPix Forms

* [**Hidden Dataset Display Values**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-use-dynamic-salesforce-data-with-record-datasets#set-up-dataset-mapping): Fixed hidden dependent dataset fields submitting a Salesforce record ID instead of the configured display value
* [**Nested Record Creation**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-sections-and-repeated-sections/create-child-records-with-form-sections#creating-multi-level-records-with-nested-repeated-sections): Fixed nested Salesforce record creation when configured within a section.&#x20;
* [**Plotted Section Backgrounds**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-plotted-sections#how-to-configure-plotted-sections): Fixed an issue where plotted sections opened with a blank canvas instead of the configured sketch background.
* [**Form Activation Safeguards**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-template-editor#work-with-form-template-versions): Fixed an issue where unsaved form templates could be activated, and unchanged templates could be saved.
* **Deleted Draft Images**: Photos removed from an in-progress Form are no longer added to the submitted answer album.
* [**Images in Generated PDFs**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-generate-form-response-pdf#demo-fire-safety-inspection-example): Fixed an issue where a PDF could be generated before all uploaded images were ready.
* **Mobile Capture Settings**: Forms now correctly apply the configured image preview and upload confirmation options.

### Mobile App

* [**Post-Submission Navigation**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-global-configuration#configure-the-submit_after-parameter): Fixed an issue where submitting a form returned users to the synchronization screen instead of the configured exit page.

### Salesforce Integration

* **PDFs from Related Albums**: Fixed an error when generating a PDF from explicitly selected images across multiple albums, such as Work Order Line Item photos included in a Work Order PDF.

### Core Platform

* [**Tag Filter Configuration**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/working-with-tags/filter-albums-by-tags-tag-filter#filtering-an-album-with-the-tag-filter-example): Removing tag-filter permissions no longer leaves empty settings that could cause unexpected behavior.

## Breaking Changes

### SharinPix Forms

* [**Hidden Field Submission**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/form-features-conditional-visibility#submit-answer-even-when-hidden): Conditionally hidden fields no longer submit previously entered values by default. Enable **Include hidden answer** when a hidden value should still be retained and submitted.
