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

# How to show the result

In this example, it is shown how the search results can be displayed on a Visualforce Page through the use of an Apex Class Controller.

* The code below demonstrates the implementation of the Visualforce Page used in this example.

```html
  <apex:page docType="html-5.0" cache="false"
    showHeader="false"
    sidebar="false"
    standardStylesheets="false"
    standardController="Account"
    extensions="SharinPixSearchPage"
    applyHtmlTag="false"
    applyBodyTag="false">
    <iframe src="{!searchUrl}" height="400px" width="100%" style="border: 0" > </iframe>
  </apex:page>
```

* The code below demonstrates the implementation of the Apex Class Controller used in this example.

```apex
  public class SharinPixSearchPage {
  	public String url { get; set; }
    	public String albumId { get; set; }
      public Map<String, Object> params;
      private sharinpix.Client clientInstance = sharinpix.Client.getInstance();
  
    	public SharinPixSearchPage(ApexPages.StandardController controller) {
        albumId = controller.getId();
        Map<String, Object> query = new Map<String, Object> {
          'q' =>  '*',
          'thumbnail_tags' => true,
          'thumbnail_filename' => true,
          'thumbnail_date' => 'L'
        };
        params = new Map<String, Object>{
          'path' => 'search?v=2&search_bar=false&q='+clientInstance.token(query)
        };
    	}
  
      public String getSearchUrl() {
        return clientInstance.getAppHost() + '?token=' + clientInstance.token(params);
      }
  }
```

* The snippet <mark style="color:red;">`'q' => '*'`</mark> represents the query fed to the search. The <mark style="color:red;">`*`</mark> symbol is used to return all the images from the corresponding album.

The screenshot below shows how the Visualforce Page appears when it is added to the record page of an Account object.

<figure><img src="../../.gitbook/assets/Gradio Image.png" alt=""><figcaption></figcaption></figure>
