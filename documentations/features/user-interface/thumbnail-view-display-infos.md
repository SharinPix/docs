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

# Thumbnail View - Display infos

Relevant information can be displayed on image thumbnails in SharinPix albums. The options that can be displayed are:

* **Filename**
* **Tags**
* **Title**
* **Date**
* **Custom label**

![](<../../.gitbook/assets/image (49).png>)

<table><thead><tr><th>Abiltity</th><th>Value</th><th width="249.87890625">Description</th></tr></thead><tbody><tr><td>Filename</td><td>Boolean</td><td>Displays the filename of the image.</td></tr><tr><td>Tags</td><td>Boolean</td><td>Displays the tags applied on the image. To see how to tag images, click <a href="../working-with-tags/">here</a>.</td></tr><tr><td>Title</td><td>Boolean</td><td>Displays the image's title. This value can be set either by making use of the <a href="../../access-and-security/sharinpix-abilities.md#id-13.-image_caption">image_caption</a> ability or on the SharinPix mobile app.</td></tr><tr><td>Date</td><td>String</td><td>Displays the date on which the image has been created. Date formats can be found <a href="/broken/spaces/VeS2KFLWXcoY15x9kHdt/pages/bPkucKIzfNREoczL4gdX">here</a>. For example, <code>date: 'L'</code></td></tr><tr><td>Custom label</td><td>String</td><td>This parameter allows the display of a custom label. The value of the custom label should be stored in a Salesforce field on the sObject <strong>SharinPixImage__c</strong>. The <strong>Salesforce field API name</strong> should then be used as the value for the parameter <strong>custom_label</strong> , for example: <code>custom_label: 'CustomFilename__c'</code>, where <em>CustomFilename__c</em> refers to the API name of the Salesforce field storing the value for the custom label.</td></tr></tbody></table>

## SharinPix Permission

SharinPix Permissions can be used to activate the abilities corresponding to the above mentioned options.

![](<../../.gitbook/assets/image (50).png>)

## Apex Class & VF Page Implementations

The display parameters can be used as shown in the following code snippets.

```apex
public class ThumbnailInfos {
    private Map<String, Object> params;

    public test(ApexPages.StandardController stdCtrl) {
        String albumId = (Id)stdCtrl.getId();
        params = new Map<String, Object>{
            'path' => '/pagelayout/' + albumId,
            'abilities' => new Map<String, Object> {
                albumId => New Map<String, Object> {
                    'Access' => new Map<String, Object> {
                        'see' => true,
                        'image_list' => true,
                        'image_upload' => true
                    },
                    'Display' => new Map<String, Object> {
                      'tags' => true,
                      'title' => true,
                      'date' => 'L'
                    }
            	}
            },
            'download' => true,
            'custom_label' => 'sharinpix__FileName__c'
    	};
    }

    public String getParameters() {
        return JSON.serialize(params); 
    }
}
```

```apex
<apex:page docType="html-5.0" cache="false"
  showHeader="false"
  sidebar="false"
  standardStylesheets="false"
  standardController="Account"
  extensions="ThumbnailInfos"
  applyHtmlTag="false"
  applyBodyTag="false">
  <sharinpix:sharinpix id="iframe" parameters="{!parameters}" ></sharinpix:sharinpix>
  <sharinpix:CustomData componentId="iframe"></sharinpix:CustomData>
</apex:page>
```

{% hint style="success" %}
**Tip:**

SharinPix also provides download parameters that can be used to personalize the download filenames. For more information about these parameters and how to configure them, refer to the following article:

[Multiple Image download (ZIP) - How to personalize the download filenames](../download-images/multiple-image-download-zip-how-to-personalize-the-download-filenames.md)
{% endhint %}
