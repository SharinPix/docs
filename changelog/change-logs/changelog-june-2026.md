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

# Changelog - June 2026

## New Features

### SharinPix Forms <a href="#sharinpix-forms" id="sharinpix-forms"></a>

* **Voice-to-Form Input**: Users can now fill out complex form fields simply by speaking, using advanced speech-to-text intelligence.
* **Bulk Element Editing**: The [SharinPix Form Template Editor](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-template-editor) now allows administrators to cut, copy, and delete multiple form elements at once, vastly speeding up form design.
* **Upgraded Rich-Text Toolbar**: The [Rich Text Area ](https://docs.sharinpix.com/forms/form-elements/sharinpix-form-sections-and-repeated-sections-1)now includes a cleaner, more intuitive formatting toolbar for an improved writing experience.
* **Repeated Section Relaunches**: [Follow-up or relaunched forms](https://docs.sharinpix.com/forms/advanced-form-configuration/form-features-initial-follow-up-form-responses-comparative-form) can now carry over and display values from the repeated sections of the original form submission.

### Core Platform <a href="#core-platform.4" id="core-platform.4"></a>

* **Secure Proxy Access**: Secure proxy URLs are now available for supported customer environments, complete with advanced security protections and expiration controls.

### Salesforce Integration <a href="#salesforce-integration" id="salesforce-integration"></a>

* **Flow Screen Relauncher LWC**: The [SharinPix Form Relauncher Lightning Web Component](https://docs.sharinpix.com/forms/salesforce-integration/reopen-a-previously-submitted-sharinpix-form#reopen-a-previously-submitted-sharinpix-form-using-lwc-in-digital-experience) is now natively available to embed directly inside Salesforce Flow screens.

## 📈 Enhancements

### SharinPix Forms <a href="#sharinpix-forms.1" id="sharinpix-forms.1"></a>

* **Offline Template Reliability**: Offline file handling for form templates has been reinforced to perform more consistently across diverse Salesforce environments.
* **Accurate Form Initializations**: Forms now initialize more reliably when loading elements that depend on heavy external resources, preventing premature "ready" states and layout flashes.
* **Data & Link Synchronization**: [SharinPix Form Responses](https://docs.sharinpix.com/forms/salesforce-integration/sharinpix-form-response) now save and sync with higher structural reliability, eliminating instances of missing image links or incomplete payload updates.
* **Clearer Sync Errors**: [SharinPix Form Response](https://docs.sharinpix.com/forms/salesforce-integration/sharinpix-form-response) records now surface highly descriptive error messages when backend Salesforce updates cannot be completed, speeding up troubleshooting.

### Core Platform <a href="#core-platform.5" id="core-platform.5"></a>

* **Proactive Token Refreshes**: Salesforce connections are now proactively refreshed by the system to reduce sync dropouts caused by expired OAuth tokens in inactive organizations.
* **Static IP Token Requests**: Salesforce OAuth token refresh requests can now support static outbound IP configurations for customers utilizing strict, IP-restricted Connected Apps.

## 🛠️ Bug Fixes

### SharinPix Forms <a href="#sharinpix-forms.2" id="sharinpix-forms.2"></a>

* **Voice to Form**: Fixed an issue in voice inputs to ensure the last spoken words are captured accurately when a user stops the microphone.

### Salesforce Integration <a href="#salesforce-integration.1" id="salesforce-integration.1"></a>

* **Data Override Protection**: Added a new custom field (`FieldsSyncedAt__c`) on the [SharinPix Form Response objec](https://docs.sharinpix.com/forms/salesforce-integration/sharinpix-form-response#fields-and-relationships)t to track exactly when Salesforce fields were last updated via pushback, safely preventing subsequent form responses from accidentally overwriting manual user modifications.

## ⚠️ Breaking Changes

### Salesforce Integration <a href="#salesforce-integration.2" id="salesforce-integration.2"></a>

* **Einstein Feature Deprecation**: All Einstein-related functionality has been formally removed from the Salesforce package. Customers currently utilizing legacy Einstein-based features must review their workflows and alternative setups before applying this upgrade.

{% include ".gitbook/includes/this-has-been-generated-wit....md" %}
