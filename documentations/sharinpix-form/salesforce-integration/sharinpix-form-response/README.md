---
description: >-
  Understand what the Form Response object stores and what each core field is
  used for.
---

# SharinPix Form Response

## Overview

**SharinPix Form Response** stores each SharinPix Form submission in Salesforce.

You can use this object to review submitted data, access generated files such as PDFs, associate the response with a Salesforce record, and use the response in Salesforce automation.

Typical use cases include:

* [Reopening a previously submitted form to review or modify it.](../reopen-a-previously-submitted-sharinpix-form.md)
* [Comparing a new submission with a previous one.](../../advanced-form-configuration/form-features-initial-follow-up-form-responses-comparative-form.md)
* [Exporting the response as a PDF](../../form-pdf-configuration/import-form-pdf-to-album-using-flow-admin-oriented.md).

{% hint style="warning" %}
**Prerequisites**

* Make sure you have the **latest** version of the SharinPix package installed. Refer to [_this documentation_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to update your package.
* To access **SharinPix Form Response**, users must have the **SharinPix Forms Admin** or **SharinPix Forms User** permission set assigned. For more information, see [SharinPix Permission Sets](https://docs.sharinpix.com/documentation/access-and-security/sharinpix-permission-sets).
{% endhint %}

## Fields & Relationships

The following fields and relationships are the main ones used on **SharinPix Form Response**.

<table><thead><tr><th width="186.78515625">Field Name</th><th>Details</th></tr></thead><tbody><tr><td>Form Response Number</td><td><ul><li><strong>API Name:</strong> <code>Name</code></li><li><strong>Type:</strong> Auto Number</li><li><strong>Description:</strong> The Form Response number assigned to this particular SharinPix Form Response. (System-generated ID assigned during creation).</li></ul></td></tr><tr><td>Public ID</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__PublicId__c</code></li><li><strong>Type:</strong> Text(255) (External ID) (Unique Case Sensitive)</li><li><strong>Description:</strong> Unique external identifier used to reference a SharinPix Form Response.</li></ul></td></tr><tr><td>Parent Record ID</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__ParentRecordId__c</code></li><li><strong>Type:</strong> Text</li><li><strong>Description:</strong> Stores the Salesforce record ID from which the SharinPix Form was launched.</li></ul></td></tr><tr><td>Parent Record</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__ParentRecord__c</code></li><li><strong>Type:</strong> Formula (Text)</li><li><strong>Description:</strong> Links to the Salesforce record associated with the SharinPix Form Response.</li></ul></td></tr><tr><td>Form Response Data URL</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__FormResponseDataURL__c</code></li><li><strong>Type:</strong> URL(255)</li><li><strong>Description:</strong> Stores the submitted form response data, including images.</li></ul></td></tr><tr><td>PDF URL</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__PdfUrl__c</code></li><li><strong>Type:</strong> URL(255)</li><li><strong>Description:</strong> URL of the generated PDF version of the submitted form.</li></ul></td></tr><tr><td>Comparative PDF URL</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__ComparativePdfUrl__c</code></li><li><strong>Type:</strong> URL(255)</li><li><strong>Description:</strong> Stores the URL of the comparative PDF generated to compare the current Form Response with the previously submitted response.</li></ul></td></tr><tr><td>Records Created At</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__RecordsCreatedAt__c</code></li><li><strong>Type:</strong> Date/Time</li><li><strong>Description:</strong> Stores the date and time when all child records associated with the form response were created.</li></ul></td></tr><tr><td>Fields Synced At</td><td><p></p><ul><li><strong>API Name:</strong> <code>sharinpix__FieldsSyncedAt__c</code></li><li><strong>Type:</strong> Date/Time</li><li><strong>Description:</strong> Stores the date and time when the fields configured for Salesforce synchronization were synced.<br>This helps confirm that the form data has been fully synced to Salesforce.</li></ul></td></tr><tr><td>Started At</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__StartedAt__c</code></li><li><strong>Type:</strong> Date/Time</li><li><strong>Description:</strong> Stores the date and time when the user started filling out the SharinPix Form.</li></ul></td></tr><tr><td>Submitted At</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__SubmittedAt__c</code></li><li><strong>Type:</strong> Date/Time</li><li><strong>Description:</strong> Stores the date and time when the user submitted the SharinPix Form.</li></ul></td></tr><tr><td>Image Synced At</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__ImageSyncedAt__c</code></li><li><strong>Type:</strong> Date/Time</li><li><strong>Description:</strong> Stores the date and time when all images attached to the form response were uploaded to SharinPix and synced to Salesforce.</li></ul></td></tr><tr><td>ProcessedAt</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__ProcessedAt__c</code></li><li><strong>Type:</strong> Date/Time</li><li><strong>Description:</strong> Stores the date and time when all answers for the SharinPix Form Response were created.</li></ul></td></tr><tr><td>User</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__User__c</code></li><li><strong>Type:</strong> Lookup(User)</li><li><strong>Description:</strong> The ID of the Salesforce user who created the SharinPix Form template from which this response was submitted.</li></ul></td></tr><tr><td>Submitted By</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__SubmittedBy__c</code></li><li><strong>Type:</strong> Lookup(User)</li><li><strong>Description:</strong> The ID of the Salesforce user who submitted the SharinPix Form Response, based on the user ID included in the SharinPix Form URL.</li></ul></td></tr><tr><td>Sharinpix Form Template</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__FormTemplate__c</code></li><li><strong>Type:</strong> Lookup(SharinPix Form Template)</li><li><strong>Description:</strong> The Active Form Template Version used to create the current SharinPix Form Response.</li></ul></td></tr><tr><td>Form Template Main</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__FormTemplateMain__c</code></li><li><strong>Type:</strong> Lookup(SharinPix Form Template)</li><li><strong>Description:</strong> The Main Form Template associated with the Form Version Template used to create the response.</li></ul></td></tr><tr><td>Previous Form Response</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__PreviousFormResponse__c</code></li><li><strong>Type:</strong> Lookup(SharinPix Form Response)</li><li><strong>Description:</strong> ID of the previously submitted SharinPix Form Response that was reopened or reused to create the current response.</li></ul></td></tr><tr><td>Error Messages</td><td><ul><li><strong>API Name:</strong> <code>sharinpix__ErrorMessages__c</code></li><li><strong>Type:</strong> Long Text Area(32768)</li><li><strong>Description:</strong> Stores errors that occurred while processing the SharinPix Form Response.</li></ul></td></tr></tbody></table>

## Custom fields and relationships

You can add your own lookup fields on **SharinPix Form Response** to link responses to a parent object, such as an Account, Case, or a custom object. This setup is useful when you want to show related responses on a parent record.

See [Setup Custom Lookup For SharinPix Form Response](setup-custom-lookup-for-sharinpix-form-response.md) for setup steps.

## Related documentation

* [Reopen A Previously Submitted SharinPix Form](../reopen-a-previously-submitted-sharinpix-form.md)
* [Form Features - Initial/Follow-up Form Responses (Comparative Form)](../../advanced-form-configuration/form-features-initial-follow-up-form-responses-comparative-form.md)
* [Import Images from Form Response to Parent Object (Admin-Oriented)](../import-images-from-form-response-to-parent-object-admin-oriented.md)
* [Import Form PDF as Content Document using Flow (Admin-Oriented)](../../form-pdf-configuration/import-form-pdf-as-content-document-using-flow-admin-oriented.md)
* [Import Form PDF to Album using Flow (Admin-Oriented)](../../form-pdf-configuration/import-form-pdf-to-album-using-flow-admin-oriented.md)

