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

# Multiple Image download (ZIP) - How to personalize the download filenames

## Download inside SharinPix Search

The screenshot below demonstrates the **SharinPix Search** component fetching and displaying all the images present on every Service Appointment records which are associated to the current Work Order object.

![](../../.gitbook/assets/screenshot.png)

The SharinPix Search can be used to download selected images into a zip folder. You also have the possibility to define custom names to assign to the zip folder as well as define names of the individual image files inside the zip folder.

{% hint style="warning" %}
**Note:**

In order to use custom download filenames, you should ensure that the SharinPix Permission Set named, **SharinPix Lightning Components**, has been assigned to all users requiring this functionality.
{% endhint %}

## Download Parameters

In any case, to be able to download images, you have to set the **download** parameter to **true**:

`download: true`

To define the name of the zipped/unzipped folder, use the **download\_filename** parameter. The value should be of type String, for example: `download_filename: 'my_zip_filename'`

To define the individual names of the image files inside the zip folder, either of the 2 parameters below can be used:

* **download\_filenames**: The value should be of type String, for example: `download_filenames: 'inside_the_zip-00001'`. The names of the individual files will be in the following format:\
  `inside_the_zip-00001,`` `_`inside_the_zip-00002`_`, inside_the_zip-00003` and so on.
* **download\_custom\_filename**: This parameter allows us to download the image with a custom filename. The value of the custom filename should be stored in a Salesforce field on the **SharinPixImage\_\_c** sObject. The **Salesforce field API name** should then be used as the value for the parameter **download\_custom\_filename** , for example: `download_custom_filename: 'CustomFilename__c'`, where _CustomFilename\_\_c_ refers to the API name of the Salesforce field storing the value for the custom filename.

### Using Download Parameters in SharinPix Search

In a SharinPix Search context, the **download parameters** can be used as shown in the following code snippet.

```
params = new Map<String, Object> {
    'path' => '/search?search_bar=false&q=' + clientInstance.token(query),
    'download' => true,
    'download_filename' => 'my_zip_filename',
    **'download_filenames' = > 'inside_the_zip-00001'**
 };
```

When using the above code snippet, the SharinPix Search Component will name the zipped folder as **my\_zip\_filename** while the names of the individual files will be in the format: **inside\_the\_zip-00001**, **inside\_the\_zip-00002**, **inside\_the\_zip-00003** etc..

The following code snippet includes the usage of the **download\_custom\_filename** parameter in the SharinPix Search.

```
params = new Map<String, Object> {
    'path' => '/search?search_bar=false&q=' + clientInstance.token(query),
    'download' => true,
    'download_filename' => 'my_zip_filename',
    **'download_custom_filename' = > 'CustomFilename__c'**
 };
```

Using the above code snippet, the SharinPix Search Component will name the zipped folder as **my\_zip\_filename** and use the value stored in the field labelled as **CustomFilename\_\_c** to name the individual files.

{% hint style="success" %}
**Tips:**

* For more information about how to implement a personalized SharinPix Search, refer to the following article:

[Using your personalized Search](../search-images/using-your-personalized-search.md)

* SharinPix also has parameters such as custom labels, date or tags that can be used to display more details on the image thumbnails in the search. For more information on these parameters and how they are configured, refer to the following article:

[Display Thumbnail Infos](../search-images/display-thumbnail-infos.md)
{% endhint %}

#### DEMO: Custom Download in SharinPix Search

![](../../.gitbook/assets/screenshot.png)

**Images are selected**

![](../../.gitbook/assets/screenshot_1.png)

**Images are downloaded**

![](../../.gitbook/assets/screenshot_2.png)

**Zipped Folder**

![](../../.gitbook/assets/zipped.png)

**Unzipped Folder**

![](../../.gitbook/assets/unzipped_folder.png)

**Individual Files inside unzipped Folder**

![](../../.gitbook/assets/screenshot_3.png)

### Using Download Parameters in SharinPix Album

For SharinPix albums, the **download\_filename** and **download\_filenames** parameters can be defined using in album parameters of an Apex controller, as demonstrated in the code snippet below:

```
Map<String, Object> params = new Map<String, Object> { 
    'download' => true,
    'download_filename' => 'sample_folder',
    'download_filenames' => 'inside_the_zip-00001',
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

The **download\_custom\_filename** parameter on the other hand can be configured in 3 ways:

1. Using the SharinPix Global Settings
2. Using a SharinPix Permission record
3. Using an Apex controller

The following code snippet includes the usage of the **download\_custom\_filename** parameter in the Apex controller.

#### Configuring the download\_custom\_filename parameter in the SharinPix Global Settings

The **download\_custom\_filename** parameter can be configured using the SharinPix Global Settings record by populating the **Salesforce field on sObject SharinPixImage\_\_c with custom image filename for zip download** field in the **Miscellaneous** section as shown below:

![](../../.gitbook/assets/screenshot-app.sharinpix.com-2021.01.29-17_25_44.png)

To access the SharinPix Global Settings:

* From App Launcher, search for **SharinPix Settings**
* Once on the SharinPix Settings tab, click on the **Go to administration dashboard** button. This action will open the global settings
* Next, from the global settings, click on the **Settings** option from the top menu bar
* Then click on the **Edit Organization** button and scroll down to the **Miscellaneous** section to configure the **download\_custom\_filename** parameter as demonstrated in the above image

#### Configuring the download\_custom\_filename parameter using a SharinPix Permission record

The download\_custom\_filename can be configured using the SharinPix Permission record by populating the **Salesforce field on sObject SharinPixImage\_\_c with custom image filename for zip download** field in the **Miscellaneous** section as shown below:

![](../../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.01.29-17_14_06.png)

In the above example, the value stored in the field **sharinpix\_\_Filename\_\_c** **(**&#x77;hich refers to the filename in this case) is used to name the individual files.

{% hint style="warning" %}
**Note:**

When configuring the **download\_custom\_filename** via a SharinPix Permission record, you should ensure that the **Download zip** parameter is checked in order to allow the download feature on the album.
{% endhint %}

#### Configuring the download\_custom\_filename parameter using an Apex controller

For SharinPix albums, the **download\_filename** and **download\_custom\_filename** parameters can be defined using in album parameters of an Apex controller as demonstrated in the code snippet below:

```
Map<String, Object> params = new Map<String, Object> { 
    'download' => true,
    'download_filename' => 'sample_folder',
    'download_custom_filename' => 'sharinpix__FileName__c'
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
**Tips:**

1. The download filenames can also be configured as a folder path to construct a folder structure when downloading the zip file. For more information on how to achieve this, refer to this article: [Using Customized Downloaded Zip's Filename to Build a Folder Structure](../../cookbook/download-zip-using-customized-download-filenames-to-build-a-folder-structure.md)
2. SharinPix also provides more parameters such as custom labels, dates, or titles that can be used on the image thumbnails to provide more information about the images. For more information about these parameters and how to configure them, refer to the following article:\
   [Thumbnail View - Display Infos](../user-interface/thumbnail-view-display-infos.md)
{% endhint %}
