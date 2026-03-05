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

# Release Notes - Q1 2025

Known Bug with correction

* SharinPix Mobile App: Unable to upload files greater than 30mb
* SharinPix Album: Filter by tags not working if a comma is present in the tags
* SharinPix Album: When playing a video, users were experiencing lag or delays when selecting a specific region within the video
* SharinPix Form: Not loading when re-opening it a second time on the Mobile App
* SharinPix Form: Images were not appearing on the Form if auto\_destroy\_after=0 is set up on an org (Images were being deleted)
* SharinPix Form: Fix Form element sorting
* SharinPix Form: Persistent Loading Animation present on Album
* SharinPix Form: Images not rendering (broken image icon) in PDFs

New Features

* SharinPix Mobile App: Option to switch between front and back camera
* SharinPix Album: Section by tag UI Improvement
* SharinPix Album: Enable Next and Previous buttons when viewing PDFs
* SharinPix Album: Paste on Empty Album
* [SharinPix Custom Upload Button](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-lwc-custom-upload-button-developer-oriented): Lightning web component version
* SharinPix Form: [Signature Input Element](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-template-editor#input-elements)
* SharinPix Form: [Capture Element](https://docs.sharinpix.com/m/documentation/l/1911114-sharinpix-form-template-editor#input-elements) (able to open camera, PDF, or template image on form)
* SharinPix Form: [Select and Multi-Select Question Elements](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-template-editor#input-elements)
* SharinPix Form: Rich Text Element
* SharinPix Form: [Formula Question Element](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-formula-functions-and-operators)
* SharinPix Form: Note available on Radio Question Element
* SharinPix Form: Enforce Media Capture for Radio Question Element
* SharinPix Form: Magic fill - Take a photo and analyse it using AI based on a prompt
* SharinPix Form: [Form Responses](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/overview-and-getting-started/sharinpix-forms)
* SharinPix Form: Read Only Mode (Preview on form response)
* SharinPix Form: Add Sections on PDF Print Preview
* [SharinPix Form Launcher](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-form-launcher)
* SharinPix Permission: Can now specify a [maximum file size](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/upload-images/upload-max-file-size) upon upload
* SharinPix Permission: New UI
* SharinPix Share: Activate or deactivate SharinPix Share link from Salesforce
* SharinPix Video: Allow Fullscreen
* Method for Automation Use (CreateContentDocumentAutomation): Automatically uploading a SharinPix Image to a Salesforce File using Flow
* Method for Automation Use (TagImageAutomation): Automatically adding a Tag to images using Flow

{% hint style="warning" %}
**Note:**

Latest Version containing the above Bug Fixes and New Features:

* SharinPix Mobile App: v2.6.59473
* SharinPix on Salesforce App Exchange: v.1.348
{% endhint %}
