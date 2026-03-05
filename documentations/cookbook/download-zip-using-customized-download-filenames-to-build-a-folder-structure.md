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

# Download Zip - Using Customized Download Filenames to Build a Folder Structure

This article demonstrates how to build a folder structure when downloading a SharinPix zip file using a customized filename by means of:

* [A SharinPix Permission record.](download-zip-using-customized-download-filenames-to-build-a-folder-structure.md#using-customized-filename-in-sharinpix-permission-record-to-build-a-folder-structure-when-downloadin)
* [An Apex class.](download-zip-using-customized-download-filenames-to-build-a-folder-structure.md#using-customized-filename-in-an-apex-class-to-build-a-folder-structure-when-downloading-a-sharinpix)

## Example: Building a Folder Structure Using Customized Filename Inside a Zip File

Let's suppose we have a list of grocery store branches registered as Account records. Each grocery store has multiple store locations registered as Location records.

Using a [SharinPix Search component](../lightning-web-component/sharinpix-search.md), we are retrieving all images from all stores irrespective of the branch and location and identifying each image using a [SharinPix custom label](../features/user-interface/thumbnail-view-display-infos.md) displaying the branch name and the location as follows: **branchName/storeLocation**

![](<../.gitbook/assets/test (91).png>)

{% hint style="info" %}
**Information:**

The above SharinPix custom label has been configured using the following Formula field of type text on the **SharinPix Image object** : <mark style="color:$danger;">`IF( ISNULL(Store__c), 'N/A', Store__r.Account__r.Name &'/'& Store__r.Name)`</mark>

For more information on how to configure SharinPix custom labels, refer to this article: [Thumbnail View - Display Infos](../features/user-interface/thumbnail-view-display-infos.md)
{% endhint %}

By using the same custom label as the download filenames in the downloaded zip, we achieve the following folder structure:

![](<../.gitbook/assets/test (92).png>)

![](<../.gitbook/assets/test (93).png>)

The following sections demonstrate how to customize the filename to achieve the above folder structure when downloading the zip.

## Using Customized Filename in SharinPix Permission Record to Build a Folder Structure When Downloading a SharinPix Zip

To build a folder structure using a SharinPix Permission record, proceed as follows:

1. Create a text field on the SharinPix Image object that will store the path, delimiting each folder and file by slash (/). For example: _ObjectA/ObjectB/ImageFilename_. _Tip: Formula fields of type text can be used for this purpose._
2. Copy the field API name of the field storing the path.
3. Create/Edit the SharinPix Permission and paste the field API name in the **Salesforce field on sObject SharinPixImage\_\_c with custom image filename for zip download** parameter as demonstrated below.

![](<../.gitbook/assets/test (94).png>)

4\. Ensure that the other zip abilities (_Download Zip_ and _Zip file name_ , for instance) are properly configured. For more information on the zip abilities, refer to this article: [Multiple Images download (ZIP) - Out of the box](../features/download-images/multiple-images-download-zip-out-of-the-box.md)

5\. Configure the other SharinPix Permission abilities as desired and click on **Save** when done.

6\. Assign the SharinPix Permission to the desired SharinPix component.

{% hint style="success" %}
**Tip:**

For more information on how to create, edit, and assign a SharinPix Permission, refer to this article: [SharinPix Permission object - How to create and assign custom permission?](../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md)
{% endhint %}

7\. Go to the SharinPix component and download the zip file. The defined path will be applied to the unzipped folder.

## Using Customized Filename in an Apex Class to Build a Folder Structure When Downloading a SharinPix Zip

To build a folder structure in an Apex method, proceed as follows:

1. Create a text field on the SharinPix Image object that will store the path delimiting each folder and file by slash (/). For example: _ObjectA/ObjectB/ImageFilename_. _Tip: Formula fields of type text can be used for this purpose._
2. Copy the field API name of the field storing the path.
3. In your Apex method, use the field API name as the value for the **download\_custom\_filename** parameter. _Tip: Do not forget to configure the zip filename using the **download\_filename** parameter._

The two examples below demonstrate how the _**download\_filename** and_ **download\_custom\_filename** are configured in a custom Search and album component.

### Code Snippet for Search Component

```apex
params = new Map<String, Object> {
    'path' => '/search?search_bar=false&q=' + clientInstance.token(query),
    'download' => true,
    'download_filename' => 'Store Search',
    'download_custom_filename' => 'CustomFilename__c'
 };
```

### Code Snippet for Album Component

```apex
Map<String, Object> params = new Map<String, Object> { 
    'download' => true,
    'download_filename' => 'Store Search',
    'download_custom_filename' => 'Store_Path__c'
    'abilities' =>  new Map<String, Object> { 
        'download' => true,
        albumId =>  new Map<String, Object> { 
            'Access' =>  new Map<String, Object> { 
                'see' => true,
                'image_download' => true,
                'image_list' => true,
                'image_upload' => true,
            }
        }
    },
    'Id' => albumId
};
```

{% hint style="success" %}
**Tip:**

For more information on how to customize download filenames, refer to this article:

[Multiple Image download (ZIP) - How to personalize the download filenames](../features/download-images/multiple-image-download-zip-how-to-personalize-the-download-filenames.md)
{% endhint %}
