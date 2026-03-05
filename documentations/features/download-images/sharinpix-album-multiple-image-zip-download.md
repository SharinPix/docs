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

# SharinPix Album: Multiple Image ZIP Download

This article demonstrates how to download selected images from a SharinPix album as a ZIP. By default, downloads are in **Original** (unchanged formats), but you can also enable **Current** (edited JPG) or have both.

{% hint style="warning" %}
**Prerequisite:**

Activate ZIP downloads by enabling the **Download ZIP** option. This can be configured via:

* [SharinPix Global Settings](sharinpix-album-multiple-image-zip-download.md#sharinpix-global-settings)
* [SharinPix Permission Record](sharinpix-album-multiple-image-zip-download.md#sharinpix-permission-record)
* [Visualforce Implementation](sharinpix-album-multiple-image-zip-download.md#visualforce-implementation)
{% endhint %}

## Download Options

Depending on which download options are enabled, images can be downloaded in their original format, the edited JPG format, or both.

| Download Options Enabled          | Download Zip Image Formats                                |
| --------------------------------- | --------------------------------------------------------- |
| Download zip                      | Original unedited image                                   |
| Download zip + Original           | Original unedited image                                   |
| Download zip + Current            | Image with current edits/transformations converted to JPG |
| Download zip + Original + Current | Both Original and Current image formats                   |

### SharinPix Global Settings

![](<../../.gitbook/assets/SharinPix Global Settings Multiple Download.png>)

{% hint style="info" %}
**Info:**

For more information on how to access and configure the _SharinPix Global Settings_, please refer to:

[How to use the SharinPix Global Settings](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/advanced-configuration-customizing-your-sharinpix-components-with-sharinpix-permissions)
{% endhint %}

### SharinPix Permission Record

In the **Download Types** field, enter **original**, **current**, or both separated by a semicolon **(original; current)**. Refer to the [Download Options](sharinpix-album-multiple-image-zip-download.md#download-options) table above.

![](<../../.gitbook/assets/SharinPix Permission Multiple Download.png>)

{% hint style="info" %}
**Info:**

For information on how to access and configure a _SharinPix Permission record_, please refer to:

[How to create and use the SharinPix Permission record](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md)
{% endhint %}

### Visualforce Implementation

You can have more controls on the download formats with '**download\_types': \['original', 'current']** or just enable download zip with **'download': true**. Refer to the [Download Option](sharinpix-album-multiple-image-zip-download.md#download-options)s table above.

```
<apex:page standardController="Opportunity"> 
 <sharinpix:SharinPix height="500px" 
	parameters="{
     'Id': '{!CASESAFEID($CurrentPage.parameters.Id)}', 
     'download': true,
     'download_types': ['original', 'current'],
     'abilities':{'{!CASESAFEID($CurrentPage.parameters.Id)}':
         	{'Access': {
            'image_tag':true,
            'paste':true,
            'image_copy':true,
            'image_download':true,
            'image_rotate':true,
            'image_crop':true,
            'image_delete':true,
            'image_upload':true,
            'image_list':true,
            'see':true 
            }
			   }
	   }
	}" 
	/> 
</apex:page>
```

{% hint style="info" %}
**Info:**

For more information on how to configure your _VisualForce page_, please refer to:

[Learn more on Visualforce Implementation](multiple-image-download-zip-how-to-add-download-true-to-a-visualforce-page.md)
{% endhint %}

## Demo

The example below demonstrates how to download selected images as a ZIP file.

1\. Select some images from the album by clicking on the **selection icons.**

![](<../../.gitbook/assets/Image Selection.png>)

2\. Once the images are selected, click on the **selection dropdown.**

![](<../../.gitbook/assets/Selection Dropdown.png>)

3\. Next, click on the **Download** option.

![](<../../.gitbook/assets/Download Option.png>)

4\. Depending on which options were enabled as described in the [Download Types](sharinpix-album-multiple-image-zip-download.md#download-options) table, you will see one or more download zip buttons. The zip file will begin downloading once one of the available download zip buttons is clicked.

* A single **Download ZIP** button is available when enabled with **Download Zip** alone, or combined with **Original only**, or with **Current only**.

![](<../../.gitbook/assets/Download Zip.png>)

* Two **Download ZIP** buttons are available when **Download ZIP** , **Original** , and **Current** options are all enabled.

![](<../../.gitbook/assets/Multiple Download Zip.png>)

{% hint style="success" %}
**Tips:**

SharinPix also allows you to personalize the download filenames. For more information on how to configure the filenames, refer to the article below:

[Multiple Image download (ZIP) - How to personalize the download filenames](multiple-image-download-zip-how-to-personalize-the-download-filenames.md)
{% endhint %}
