# SharinPix Forms

## Overview

{% hint style="info" %}
SharinPix Forms are a powerful way to capture, organize, and manage data within Salesforce, even when offline. By leveraging intuitive, customizable forms, organizations can streamline data collection processes, improve record management, and enhance visual documentation. These forms are designed to work seamlessly with any Salesforce objects and can also integrate media such as images, videos, scanned documents, 3D Twin, personalised sketches, signatures and much more to enrich the captured data.
{% endhint %}

## SharinPix Forms Salesforce Data Model

![](<../.gitbook/assets/Form - Copy of ERD as of 17 Sept 2025 - Plus Propre (1) (1).jpg>)

The key objects that make up the form structure include:

* **Parent Object/Record:**\
  This is the Salesforce Record where the [SharinPix Form Launcher](/broken/spaces/Hhhsz8OAg6xcF0k0DJhg/pages/Nt8NRMnhV6xJ29Cqi1dY) is configured, for example, an Account Record where the Form will be launched from.
* **Form Template:**\
  This is the primary step to define the overall layout and metadata for a form. It is created using the [SharinPix Form Template Editor](sharinpix-form-template-editor.md) and contains essential information like the form's name, description, list of questions and actions as well as configuration settings.\
  A Form Template is compound by a list of [Form Elements](sharinpix-form-template-editor.md). This Elements can be either a decoration (Title, Description, guidance), a question (with a specific UI to enter values) or an action (which open a camera to take pictures, permits to sketch a specific context, to scan documents, ...).
* **Form Response:**\
  Once a form is deployed and filled out, each submission is captured as a form response. This object not only stores the respondent's answers but also the questions presented, ensuring that both questions and answers are retained for future reference and reporting. It offers as well a quick access to the global form information through either a visual representation, a generated PDF or a list of related Answers records.
* **Form In Progress:**\
  When a form is saved, it will create a [SharinPix Form In Progress](sharinpix-form-in-progress.md) object on Salesforce. This object does not create Form Answer records because it is not a form that has been submitted. The Form In Progress Record contains the SharinPix Form In Progress LWC that allows the user to continue filling, saving and submitting the form. Once the form is submitted, the Form In Progress Record is converted into a Form Response Record.
* **Form Answer:**\
  When a form is submitted, a SharinPix Form Answer record is created for each Form Question and it is associated with the appropriate SharinPix Form Response object. It contains the answer metadata and value which can be used in any custom implementation afterwards.

## Key Benefits

* **Built for Salesforce:** SharinPix Forms is designed to work natively within Salesforce.
* **External Access:** SharinPix Forms can also be accessed outside Salesforce using a link.
* **Admin Friendly:** Enables Salesforce admins to create and manage forms easily using standard Salesforce features.
* **Seamless Media Integration:** Combines images and other media directly within forms for richer data capture.
* **Native Data Handling:** Forms, responses, and media are stored as native Salesforce objects.
* **Enhanced workflows:** Supports standard Salesforce automation, reporting, and workflows.
* **Visual And Data Synergy:** Allows visual documentation to complement traditional form data collection.
