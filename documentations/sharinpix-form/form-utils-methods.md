# Form Utils Methods

## Overview

The SharinPix package provides the Apex class, **FormUtils**, which are utility methods for use for the [Form Feature](sharinpix-forms.md).

**The Form Utils methods include:**

* [generateToken: Generate form token](form-utils-methods.md#generatetoken)
* [generateUrl / generateOnlineUrl: Generate form URL](form-utils-methods.md#generateurl-generateonlineurl)
* [exportFormResponseAsContentDocument](form-utils-methods.md#exportformresponseascontentdocument)
* [exportFormResponseAsContentDocument (with options)](form-utils-methods.md#exportformresponseascontentdocument-with-options)

{% hint style="warning" %}
**Prerequisites:**

Before using any of the above methods, ensure the following:

* You have the latest **SharinPix Package** installed. This feature requires version **1.375** or higher. You can follow [this guide](https://docs-uat.sharinpix.com/faqs/how-to-update-sharinpix-package-from-the-appexchange) to upgrade your SharinPix Managed Package to the newest version.
* Users must have the **SharinPix Forms** **Admin** or **SharinPix Forms User** permission set assigned. For more information on these two permission sets, check [SharinPix Permission Sets](https://docs-uat.sharinpix.com/documentation/access-and-security/sharinpix-permission-sets).
{% endhint %}

## Form Utils Methods Example

### generateToken

_global static String **generateToken**(String **recordId** , String **templateId** , Map\<String, Object> **options**)_

* This method generates a SharinPix Form Token with specific abilities. Below is a detailed description of each parameter:
  * **recordId (String)**\
    The unique identifier of the record associated with the form. This parameter specifies which record the generated token will be linked to. For example, if the form pertains to a specific account or case, you would pass that record's ID here.
  * **templateId (String)**\
    The identifier of the form template to be used for token generation. Ensure the templateId corresponds to the desired form template in your system.
  * **options (Map \<String, Object>)**\
    A key-value map that provides additional configuration options to customize the form's behavior. This parameter is optional and allows flexibility in defining extra settings. Common examples include:
    * **nameFieldApiName**: Specifies the API name of the field used to display a recognizable name for the form (e.g., a contact’s name or an opportunity title).
    * **formExpiry**: Defines the expiration date or duration for the form's validity. The formExpiry takes a number as value indicating the number of days after which the form will expire.

```
Map<string, object> options = new Map<string, object> {
    'nameFieldApiName' => 'WorkOrderNumber',
    'formExpiry' => 8
};

String token = sharinpix.FormUtils.generateToken('0018a00001rL2scAAC', 'a0Ral000007iSvpEAE', options);
```

### generateUrl / generateOnlineUrl

_global static String **generateUrl**(String **recordId** , String **templateId** , Map\<String, Object> **options**)_

_global static String **generateOnlineUrl**(String **recordId** , String **templateId** , Map\<String, Object> **options**)_

These methods generate a SharinPix Form URL (Universal Link) for a specific form template. Both methods work the same way, with only one difference:

| _**generateUrl**_       | Opens the form in the **SharinPix Mobile App** |
| ----------------------- | ---------------------------------------------- |
| _**generateOnlineUrl**_ | Opens the form in a **Web Browser**            |

Below is a detailed description of each parameter:

* **recordId (String)**\
  The unique identifier of the record associated with the form. This parameter specifies which record the generated token will be linked to. For example, if the form pertains to a specific account or case, you would pass that record's ID here.
* **templateId (String)**\
  The identifier of the form template to be used for token generation. Ensure the templateId corresponds to the desired form template in your system.
* **options (Map \<String, Object>)**\
  A key-value map that provides additional configuration options to customize the form's behavior. This parameter is optional and allows flexibility in defining extra settings. Common examples include:
  * **nameFieldApiName**: Specifies the API name of the field used to display a recognizable name for the form (e.g., a contact’s name or an opportunity title).
  * **formExpiry**: Defines the expiration date or duration for the form's validity. The formExpiry takes a number as value indicating the number of days after which the form will expire.

```
Map<String, Object> options = new Map<String, Object>{
    'nameFieldApiName' => 'WorkOrderNumber',
    'formExpiry' => 8
};

String mobileUrl = sharinpix.FormUtils.generateUrl('0018a00001rL2scAAC', 'a0Ral000007iSvpEAE', options);
String browserUrl = sharinpix.FormUtils.generateOnlineUrl('0018a00001rL2scAAC', 'a0Ral000007iSvpEAE', options);
```

### exportFormResponseAsContentDocument

_global static void **exportFormResponseAsContentDocument**(String **formResponsePublicId** , String **recordId**)_

This method exports a SharinPix Form Response PDF as a Salesforce **ContentDocument**, attaching it to a specified record.

Parameters:

* **formResponsePublicId (String)**\
  The public identifier of the SharinPix Form Response to export.
* **recordId (String)**\
  The Salesforce record ID to which the generated ContentDocument will be linked. This is typically the record (e.g., an Account, Case, or Work Order) that the form response pertains to.

```
sharinpix.FormUtils.exportFormResponseAsContentDocument(
    '01995896-6708-74dd-9d0d-cd962ba16a8df',
    '0018a00001rL2scAAC'
);
```

### exportFormResponseAsContentDocument (with options)

_global static void **exportFormResponseAsContentDocument**(String **formResponsePublicId** , String **recordId,** Map\<String, Object> **options**)_

This method works like the previous one, but allows additional **export configuration options** , such as specifying a filename for the exported PDF. It still exports the SharinPix Form Response as a Salesforce **ContentDocument** and links it to the specified record.

**Parameters**

* **formResponsePublicId (String)**\
  The public identifier of the SharinPix Form Response to export.
* **recordId (String)**\
  The Salesforce record ID to which the generated ContentDocument will be linked.
* **options (Map \<String, Object>)**\
  A key-value map allowing you to customize the export behavior.

```
Map<String, Object> options = new Map<String, Object>{
    'filename' => 'FR0001'
};

sharinpix.FormUtils.exportFormResponseAsContentDocument(
    '01995896-6708-74dd-9d0d-cd962ba16a8df',
    '0018a00001rL2scAAC',
     options
);
```
