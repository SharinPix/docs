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

# Display Thumbnail Infos

* [Implementation of Apex Class](display-thumbnail-infos.md#implementation-of-apex-class)
* [Implementation of Visualforce Page](display-thumbnail-infos.md#implementation-of-visualforce-page)
* [How it appears](display-thumbnail-infos.md#how-it-appears)

The present article demonstrates how it is possible to display these details on an image's thumbnail:

* **Date**
* **Tags**
* **Original filename**
* **Custom label**

## Implementation of Apex Class

The code snippet below shows the implementation of the Apex Class used to display thumbnail details.

```apex
public class SharinPixSearchPage {
    private Map<String, Object> params;
    private sharinpix.Client clientInstance = sharinpix.Client.getInstance();

    public SharinPixSearchPage(ApexPages.StandardController stdCtrl) {
        params = new Map<String, Object>{ 
            'path' => 'search?v=2&search_bar=false', 
            'q' => '*',
            'thumbnail_tags' => true,
            'thumbnail_filename' => true,
            'thumbnail_date' => 'L',
            'custom_label' => 'CustomLabel__c'
        };
    }

    public String getParameters() {
        return JSON.serialize(params); 
    }

    public String getSearchUrl() { 
        return clientInstance.getAppHost() + '?token=' + clientInstance.token(params); 
    }
}
```

<table><thead><tr><th>Parameter</th><th>Value</th><th width="406.98046875">Description</th></tr></thead><tbody><tr><td>thumbnail_tags<br></td><td>Boolean</td><td>Display tags applied on image in thumbnail.</td></tr><tr><td>thumbnail_filename</td><td>Boolean</td><td>Display image's original filename in thumbnail.</td></tr><tr><td>thumbnail_date</td><td>String</td><td>Display the date on which the image was uploaded in a specified format. For example: 'd MMM YY' yields <mark style="color:red;"><code>4 Nov 18</code></mark>.<br>More information about date formats can be found <a href="/broken/spaces/VeS2KFLWXcoY15x9kHdt/pages/bPkucKIzfNREoczL4gdX">here</a>.</td></tr><tr><td>custom_label</td><td>String</td><td>This parameter allows the display of a custom label. The value of the custom label should be stored in a Salesforce field on the sObject <strong>SharinPixImage__c</strong>. The <strong>Salesforce field API name</strong> should then be used as the value for the parameter <strong>custom_label</strong>, for example: <mark style="color:red;"><code>custom_label: 'CustomLabel__c'</code></mark>, where <em>CustomLabel__c</em> refers to the API name of the Salesforce field storing the value for the custom label.</td></tr></tbody></table>

## Implementation of Visualforce Page

The code snippet below shows the implementation of the Visualforce Page used in this demo.

```html
<apex:page docType="html-5.0" cache="false"
  showHeader="false"
  sidebar="false"
  standardStylesheets="false"
  standardController="Account"
  extensions="SharinPixSearchPage"
  applyHtmlTag="false"
  applyBodyTag="false">
  <iframe src="{!searchUrl}" height="400px" width="100%" style="border: 0" ></iframe>
</apex:page>
```

## How it appears

The screenshot below shows how the **filename** and **date** are displayed on the thumbnail of an imag&#x65;**.**

<figure><img src="../../.gitbook/assets/Gradio Image (4).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tip:**

SharinPix also provides download parameters that can be used to personalize the download filenames. For more information about these parameters and how to configure them in a custom search, refer to the following article:

[Multiple Image download (ZIP) - How to personalize the download filenames](../download-images/multiple-image-download-zip-how-to-personalize-the-download-filenames.md)
{% endhint %}
