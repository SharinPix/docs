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

# Open a specific image in Full View

The present example will show how it is possible to automatically make the **SharinPix Album** :

* [Show a specific image](open-a-specific-image-in-full-view.md#show-a-specific-image)
* [Activate the Edit mode](open-a-specific-image-in-full-view.md#activate-the-annotation-mode)

## Show a specific image

* This section will demonstrate how it is possible to open a specific image in large view when the SharinPix Album loads.

To specify which particular image is to be displayed when the SharinPix Album loads for the first time, you will need to replace the image's id assigned to the the following reference:

```apex
String imageId = '1b2efab9-ee60-4236-85ac-9e37dab7a0f8'; //replace with your own image id
```

The code snippet below shows the implementation of the Apex Controller Class which dictates what specific image is opened within the large view mode.

```apex
public class SharinPixActionDemoCtrl {
    public String parameters {get; set;}
    
    public SharinPixActionDemoCtrl(ApexPages.StandardController controller) {
        Id albumId = controller.getId();
        String imageId = '1b2efab9-ee60-4236-85ac-9e37dab7a0f8'; //replace with your own image id

        Map<String, Object> params = new Map<String, Object> {
            'Id' => albumId,
            'path' => 'pagelayout/' + albumId + '?image=' + imageId,
            'abilities' => new Map<String, Object> {
                albumId => new Map<String, Object> {
                    'Access' => new Map<String, Object> {
                        'see' => true,
                        'image_list' => true,
                        'image_upload' => true,
                        'image_delete' => true,
                        'image_annotate' => true
                    }
                }
            } 
        };
       	parameters = JSON.serialize(params);
    }
}
```

The code snippet below shows the implementation of the Visualforce Page whose sole purpose revolves around displaying the SharinPix Album.

```html
<apex:page StandardController="Account" extensions="SharinPixActionDemoCtrl">
    <sharinpix:sharinpix parameters="{! parameters }" height="500px"></sharinpix:sharinpix>
</apex:page>
```

## Activate the Annotation mode

* As well as opening a specific image automatically, it is also possible to open this same image within the **Edit** mode. To perform the latter, you will need to append an extra parameter as shown below:&#x20;

<mark style="color:red;">`'pagelayout/' + albumId + '?image=' + imageId + '&annotate=true'`</mark>

{% hint style="warning" %}
Note:

Not all image sync abilities are available for the fullscreen feature.
{% endhint %}
