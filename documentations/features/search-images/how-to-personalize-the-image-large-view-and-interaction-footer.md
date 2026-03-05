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

# How to personalize the image large view and interaction (footer)

The present article will show how it is possible to open the parent Salesforce record of an image from the **Large View** mode.

We will make use of an Apex Class Controller to define the Salesforce record and a Visualforce Page to display the SharinPix Image Search.

## Demo in action

* An image is clicked upon.

<figure><img src="../../.gitbook/assets/Gradio Image (1).png" alt=""><figcaption></figcaption></figure>

* The **Large View** mode of the selected image is then activated.

<figure><img src="../../.gitbook/assets/Gradio Image (2).png" alt=""><figcaption></figcaption></figure>

* The defined **Salesforce record** can be opened by clicking on the icon as shown below.

<figure><img src="../../.gitbook/assets/Gradio Image (3).png" alt=""><figcaption></figcaption></figure>

* After clicking on the above icon, you will be redirected to the parent Salesforce record of the current image.

## Apex Class Controller

The code snippet below illustrates how the implementation of the Apex Class Controller.

```apex
  public class SharinPixSearchPage {
    public Map<String, Object> params;
    private sharinpix.Client clientInstance = sharinpix.Client.getInstance();
  
    public SharinPixSearchPage(ApexPages.StandardController controller) {
      Map<String, Object> query = new Map<String, Object> {
        'q' =>  '*'
      };
  
      params = new Map<String, Object> {
        'path' => 'search?search_bar=true&q='+clientInstance.token(query),
        'salesforceBaseUrl' => 'https://custom-domain.my.salesforce.com'
      };
    }
    
    public String getParameters() {
      return JSON.serialize(params);
    }
  }
```

* You need to set the **salesforceBaseUrl** key to the url that corresponds to your own Salesforce Organization domain.

```
'salesforceBaseUrl' => 'https://your-own-domain.my.salesforce.com'
```

## Visualforce Page

* The code snippet below illustrates the implementation of the Visualforce Page used in this article to display the SharinPix Image Search.

```html
  <apex:page docType="html-5.0" cache="false"
    showHeader="false"
    sidebar="false" 
    standardStylesheets="false"
    standardController="Account"
    extensions="SharinPixSearchPage"
    applyHtmlTag="false"
    applyBodyTag="false">
      
    <apex:canvasApp developerName="Albums" width="100%" height="500px" parameters="{! parameters }"/>
  </apex:page>
```
