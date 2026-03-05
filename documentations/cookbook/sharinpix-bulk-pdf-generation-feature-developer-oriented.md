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

# SharinPix Bulk PDF Generation Feature (Developer-oriented)

## Overview

{% hint style="info" %}
The _SharinPix Bulk PDF Generation_ feature efficiently generates PDFs using SharinPix for multiple records in Salesforce. This process is carried out in the background using a Batch Apex process, ensuring scalability and minimal impact on Salesforce performance during execution. It requires developer skills to trigger the code and specify the configuration in Apex.
{% endhint %}

## How It Works

{% hint style="success" %}
To use this feature, developers must write APEX code that sets up a list of records using the <mark style="color:red;">`sharinpix.SharinPixCacheBuilder.Params`</mark> class. Once this list is prepared, the <mark style="color:red;">`sharinpix.SharinPixCacheBuilder.render()`</mark> method is called to trigger the PDF generation process. This initiates a Batch Apex job that processes the records and generates PDFs in the background.
{% endhint %}

## Sample Code

Below is a sample code snippet demonstrating the implementation of the bulk PDF generation feature in Apex:

```apex
// Initialize a list to hold the parameters for PDF generation
List<sharinpix.SharinPixCacheBuilder.Params> paramsList = new List<sharinpix.SharinPixCacheBuilder.Params>();

// Query all Account records (this can be customized based on your use case)
for (Account acc : [SELECT Id FROM Account]) {
    // Create a new Params instance for each record
    sharinpix.SharinPixCacheBuilder.Params params = new sharinpix.SharinPixCacheBuilder.Params();
    params.recordId = acc.Id; // Set the record Id
    params.filenameFieldApiName = 'Name'; // Specify the field to be used as the filename of the PDF
    params.firstPageFieldApiName = null; // Specify the field for the first page content (if any)
    params.imageUrlFieldApiName = 'sharinpix__ImageURLThumbnail__c'; // Set the field for image URLs
    params.preDescriptionFieldApiName = 'Description'; // Set the field for a description before the content

    // Add the Params instance to the list
    paramsList.add(params);
}

// Call the render method to start the Batch Apex process for PDF generation
list<Id> pdfIds = sharinpix.SharinPixCacheBuilder.render(paramsList);
```

## Parameters

The Params class contains several parameters that can be configured to customize the PDF generation process. Below is a detailed list of the available parameters:

* **recordId (Id, Required)** : The ID of the record for which the PDF is being generated.
* **imageUrlFieldApiName (String, Required)** : The API name of the field that stores the image URL to be included in the PDF.
* **imageIds (List)** : A list of SharinPix Image Public IDs (field sharinpix\_\_ImagePublicId\_\_c on SharinPix Image object) for images to be included in the PDF. If no Ids was given, it will take all images for the given record.
* **columns (Integer)** : The number of columns to be included in the PDF. The value must be between 1 and 12. If an invalid value is provided, it defaults to 2.
* **imageCaptionText (String)** : The API name of the field containing the text to be displayed alongside the image. Defaults to ‘None’.
* **firstPageFieldApiName (String)** : The API name of the Rich Text field containing the content for the first page of the PDF.
* **lastPageFieldApiName (String)** : The API name of the Rich Text field containing the content for the last page of the PDF.
* **preDescriptionFieldApiName (String)** : The API name of the Rich Text field containing the pre-description of images.
* **postDescriptionFieldApiName (String)** : The API name of the Rich Text field containing the post-description of images.
* **orientation (String)** : The PDF page orientation (e.g., ‘Portrait’, ‘Landscape’).
* **singleImagePerPage (Boolean)** : If set to true, each page of the PDF will contain only a single image. Defaults to false.
* **footer (String)** : The format of the footer in the PDF. You can use merge fields like {pagenumber} for the current page and {pagecount} for the total pages.
* **filenameFieldApiName (String)** : The API name of the field that will be used as the filename for the generated PDF.

## Execution

Once the render method is invoked with the list of Params, a Batch Apex job is triggered to process each record in the list and generate the corresponding PDFs. The PDFs will be available for download or further processing as per your requirements.

The method will return a list of Ids corresponding to an object called, <mark style="color:red;">`sharinpix__SharinPixCache__c`</mark><mark style="color:red;">.</mark>

To know if the PDFs have been generated, the following sample code can be used:

```java
public static boolean checkCacheStatus(list<Id> cacheIds) {
    List<sharinpix__SharinPixCache__c> lstCache = [SELECT Id, sharinpix__Status__c 
                              FROM sharinpix__SharinPixCache__c 
                              WHERE (sharinpix__Status__c = 'Completed' 
                              OR sharinpix__Status__c = 'Failed') AND Id IN :cacheIds ];

    if (cacheIds.size() == lstCache.size()) { return true; }
    return false;
}
```

{% hint style="info" %}
Should you require any assistance on using this feature, do not hesitate to send a mail to [support@sharinpix.com](mailto:support@sharinpix.com)
{% endhint %}
