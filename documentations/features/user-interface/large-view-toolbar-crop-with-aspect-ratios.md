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

# Large View: Toolbar - Crop with Aspect Ratios

SharinPix allows you to crop an image from an album to a specified aspect ratio.

In this article, we will show you how to specify aspect ratios using:

1. [SharinPix Permission Object](large-view-toolbar-crop-with-aspect-ratios.md#specify-aspect-ratios-using-sharinpix-permission-admin-oriented) (This method is suitable for admins)
2. [SharinPix Parameters](large-view-toolbar-crop-with-aspect-ratios.md#specify-aspect-ratios-using-sharinpix-parameters-developer-oriented)

To crop an image to a specified aspect ratio, you first need to access the crop Editing mode by:

1\. Clicking on the image to access the large view:

![](<../../.gitbook/assets/image (8) (2).png>)

2\. Selecting the **crop** option to activate the Editing mode:

![](<../../.gitbook/assets/image (9) (2).png>)

3\. Accessing the **Aspect Ratio** feature from the Editing mode:

![](<../../.gitbook/assets/image (10) (3).png>)

{% hint style="success" %}
**Tip:**

For more information about the crop option or the features available in the Editing mode, refer to the previous article or click on the following link: [Large View: Toolbar – Crop](large-view-toolbar-crop.md)
{% endhint %}

{% hint style="warning" %}
**Note:**

The crop option can only be configured by either using a **SharinPix Permission record** or by **code implementation**.
{% endhint %}

## Specify Aspect Ratios Using SharinPix Permission (Admin-Oriented)

Aspect ratios can be easily specified using the SharinPix Permission object (an object allowing users to configure the features to be added or omitted from a SharinPix album).

{% hint style="success" %}
**Tip:**

For more information about the SharinPix Permission object, refer to the following article:

[SharinPix Permission object](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md)
{% endhint %}

To specify aspect ratios using SharinPix Permission:

* Create or edit a SharinPix Permission record
* In the **Toolbar** section, check the option **Crop images**. Then, enter the aspect ratios you intend to use in the **Crop ratio** section as demonstrated in the example below:

![](<../../.gitbook/assets/image (11) (3).png>)

{% hint style="warning" %}
**Note:**

* The aspect ratios specified in the **Crop ratio** section should be separated by a semi-colon
* The aspect ratios are displayed in the same order as entered in the **Crop ratio** section
* The first value specified in the list will be applied by default when accessing the Aspect Ratio feature from the crop Editing mode
{% endhint %}

* Check the other features you want to apply to the SharinPix album and click save when done

{% hint style="info" %}
In the example above, the aspect ratios specified are **4:3** , **1:1** , **16:9** and **free**.

While the values **4:3**, **1:1** and **16:9** are self-explanatory, the '**free**' value looks foreign. This is because the 'free' value is predefined in SharinPix and it allows users to adjust the crop frame as desired.
{% endhint %}

You can also display labels in the **Aspect Ratio list** available from the **Editing mode** instead of the actual values.

To do so, simply use the following format in the **Crop ratio** section in your **SharinPix Permission r**ecord:

<p align="center"> <mark style="color:$danger;"><code>4:3|Banner;1:1|Square;16:9|Landscape;free|Free</code></mark></p>

![](<../../.gitbook/assets/image (12) (3).png>)

The result is depicted in the example below:

![](<../../.gitbook/assets/image (13) (3).png>)

## Specify Aspect Ratios Using SharinPix Parameters (Developer-Oriented)

Aspect ratios can also be specified using SharinPix Parameters and subsequently used in a SharinPix album wrapped within a Visualforce Page.

To specify aspect ratios using SharinPix parameters:

* Create an Apex Controller that will define the SharinPix album's parameters (including the part on aspect ratios specification) using the code snippet below:

```apex
public class SharinPixAlbumController {
	public String parameters {get; set;}
    public SharinPixAlbumController(ApexPages.StandardController stdCtrl) {
        Id albumId = stdCtrl.getId();
        
        Map<String, Object> params = new Map<String, Object> { 
            'abilities' =>  new Map<String, Object> { 
                albumId =>  new Map<String, Object> { 
                    'Access' =>  new Map<String, Object> { 
                        'see' => true,
                        'image_list' => true,
                        'image_upload' => true,
                        'image_delete' => true
                    }
                }
            },
            'Id' => albumId,
            'crop_ratio' => new List<String>{'4:3','1:1','16.9','free'}
		};
        parameters = JSON.serialize(params);
    }
}
```

{% hint style="warning" %}
**Note:**

* The crop ratio should be added at the **root**
* The aspect ratios should be specified in the following format:

<p align="center"> <mark style="color:$danger;"><code>'crop_ratio' => new List{'4:3','1:1','16:9','free'}</code></mark></p>
{% endhint %}

* Next, implement the Visualforce Page embedding the SharinPix album with the applied parameters using the code snippet below:

{% code fullWidth="false" %}
```apex
    <apex:page StandardController="Account" extensions="SharinPixAlbumController">
    	<sharinpix:SharinPix parameters="{! parameters }" height="500px" />
    </apex:page>
```
{% endcode %}

* Finally, add the Visualforce Page to the **Account** record layout so as to test the aspect ratios

![](<../../.gitbook/assets/image (14) (2).png>)
