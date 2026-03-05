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

# Using Sort inside query parameters

In the present article, we will see how it is possible to define in which **order** and based on which criteria the images in the search results should appear.

We will make use of an Apex Class Controller and a **canvasApp** on a Visualforce Page so as to define the sort order inside the query parameters.

* [Apex Controller](using-sort-inside-query-parameters.md#apex-controller)
* [Visualforce Page](using-sort-inside-query-parameters.md#visualforce-page)

## Apex Controller

The code snippet below shows the implementation of the Apex Class Controller.

```apex
public class SharinPixSearchController {
  public Map<String, Object> params;
  private sharinpix.Client clientInstance = sharinpix.Client.getInstance();

  public SharinPixSearchController(ApexPages.StandardController controller) {
    Map<String, Object> query = new Map<String, Object> {
      'q' =>  '*',
      'abilities' => new Map<String, Object> {             
        'Sort' => new Map<String, Object> {
          'field' => 'created_at',
          'order' => 'desc'
        }
      }
    };

    params = new Map<String, Object> {
      'path' => 'search?search_bar=true&q='+clientInstance.token(query)
    };
  }

  public String getParameters() {
    return JSON.serialize(params);
  }
}
```

By referring to the above code,

The <mark style="color:red;">`Sort`</mark> Map structure contains two keys:

* <mark style="color:red;">`field`</mark> - corresponds to the date used to sort the images of the search results. It takes two values:
  * <mark style="color:red;">`created_at`</mark> - It is the date on which the image has been uploaded to SharinPix.
  * <mark style="color:red;">`date_taken`</mark> - It is the date on which the photo has been captured by a device.
* <mark style="color:red;">`order`</mark> - corresponds to the order in which the images appear in the search results. it takes these values:
  * <mark style="color:red;">`asc`</mark> - The images appear from the least recent to the most recent(based on the date defined in <mark style="color:red;">`field`</mark>)
  * <mark style="color:red;">`desc`</mark> - The images appear from the most recent to the least recent(based on the date defined in <mark style="color:red;">`field`</mark>)

## Visualforce Page

The code snippet below illustrates the implementation of the Visualforce Page used to display the SharinPix Image Search.

```html
<apex:page docType="html-5.0" cache="false"
  showHeader="false"
  sidebar="false"
  standardStylesheets="false"
  standardController="Account"
  extensions="SharinPixSearchController"
  applyHtmlTag="false"
  applyBodyTag="false">
  <apex:canvasApp developerName="Albums" width="100%" height="500px" parameters="{! parameters }"/>
</apex:page>
```
