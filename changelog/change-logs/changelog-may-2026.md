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

# Changelog - May 2026

## New Features & Enhancements

### SharinPix Forms

* **Next-Gen Voice AI**: Upgraded Voice-to-Form technology from GPT Realtime 1.5 to GPT Realtime 2, leveraging OpenAI's latest models to provide faster, more accurate AI-assisted form filling.
* **Dynamic Rich-Text Images**: Improved the [Rich Text Area](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-sections-and-repeated-sections-1) component so image URLs can be parsed clearly, enabling formula-driven or dynamically generated image references within your text content.
* **Streamlined Section Mapping**: Refined the [Form Template Editor](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-template-editor) interface by automatically hiding invalid configuration UI for repeated sections and exposing correct, contextual section-level controls.
* **Global Theme Scaling**: Extended system themes to natively support both light and dark button contrasts (`btn-light` and `btn-dark`), ensuring clean component rendering across custom or mixed-theme environments.
* **Custom Brand Styling**: Added a dedicated [primary color](https://docs.sharinpix.com/forms/form-elements/form-features-theme-customization#how-to-configure-the-primary-color) property (`theme.primaryColor`) directly to the form template schema, allowing administrators to match form interfaces to specific customer brand colors.
* **Orphaned Response Protection**: Enforced strict rules keeping form responses permanently linked to their master templates, eliminating orphaned records and ensuring continuous auditability and rendering context.

### Core Architecture <a href="#core-architecture" id="core-architecture"></a>

* **Visual Tag Identification**: Applied client-defined custom colors to image tags for designated Salesforce organizations, allowing field teams to identify media statuses at a glance.
* **Instant Automation Imports**: Added an asynchronous trigger option for Tag Actions during data imports, ensuring backend automation and workflows fire immediately when images are imported and tagged.
* **Connection Observability**: Introduced follow-up logging and live ping checks around API-user authentication failures following the PKCE migration, allowing faster troubleshooting of Salesforce connectivity issues.
* **Direct Sticker Configuration**: Added Album Sticker configuration to the settings page, exposing sticker-related album controls directly in the administration UI.

### Mobile App <a href="#mobile-app" id="mobile-app"></a>

* **Flexible GPS Enforcement**: Updated mobile behavior so the GPS-required flag can be overridden when needed, avoiding blocked captures in flows where GPS enforcement should not apply.

### Salesforce Integration <a href="#salesforce-integration" id="salesforce-integration"></a>

* **Rich Text Field Syncing**: Added a dedicated Salesforce Rich Text Area field onto the Form Answer object to cleanly map data from the form's Rich Text element while safely handling Salesforce field size limits.
* **Extended URL Capacities**: Increased the character capacity for the redirect URL field on [SharinPix Share](https://docs.sharinpix.com/documentation/lightning-web-component/sharinpix-share#activate-deactivate-a-sharinpix-share) records, preventing database insert failures when handling exceptionally long automation-generated links.
* [**Reopen Previously Submitted Form History**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/salesforce-integration/reopen-a-previously-submitted-sharinpix-form): Created a self-lookup relationship `sharinpix__PreviousFormResponse__c` on the [SharinPix Form Response object](https://docs.sharinpix.com/forms/salesforce-integration/sharinpix-form-response#fields-and-relationships), allowing newly relaunched forms to seamlessly reference their original parent response record.
* **Embedded Documentation Assistant**: Integrated the SharinPix Documentation Assistant directly inside the Salesforce Support tab, giving administrators instant, contextual help without leaving the package.

## 🛠️ Bug Fixes

### SharinPix Forms <a href="#sharinpix-forms.1" id="sharinpix-forms.1"></a>

* **Date Shortcut Populations**: Fixed the Date question controls where the "Set to current date" option and the quick "Today" shortcut failed to populate fields correctly.
* **iOS Submission Freezes**: Resolved an issue where submitted forms occasionally became stuck in a permanent processing loop on iOS devices instead of completing their server-side workflows.
* **Null Payload Prevention**: Fixed a synchronization bug where mobile-originated form responses were occasionally created with empty answer data, ensuring downstream Salesforce records populate reliably.
* **PDF Download Stabilizations**: Improved PDF generation reliability to prevent timeout errors (HTTP 503) on initial download attempts, securing the pipeline that automatically saves PDFs to Salesforce Content Documents.

### Core Architecture <a href="#core-architecture.1" id="core-architecture.1"></a>

* **Smart Bulk Selection**: Corrected the gallery bulk selection shortcut (`Cmd+A`) to ensure it only selects images visible under the active tag filter, preventing hidden media from being accidentally edited or deleted.
* **Multi-Page PDF Selection**: Fixed the "Select All" behavior for grouped PDF documents so every page in the document is highlighted rather than just the active page being viewed.

### Mobile App <a href="#mobile-app.1" id="mobile-app.1"></a>

* **Camera Lifecycle Stability**: Fixed repeated mobile camera failures reported as `OperationCanceledException: Camera is not active`, improving capture stability when the camera lifecycle is interrupted or canceled.

### Salesforce Integration <a href="#salesforce-integration.1" id="salesforce-integration.1"></a>

* **Screen Flow Component Defaults**: Fixed parameter handling inside Salesforce Screen Flows to ensure the Album LWC respects active package defaults—such as fullscreen image viewer, actions, and image sync settings—instead of reverting to old cached inputs.

{% include ".gitbook/includes/this-has-been-generated-wit....md" %}
