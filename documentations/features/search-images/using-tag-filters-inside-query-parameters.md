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

# Using tag filters inside query parameters

The present article will show how it is possible to search for specific images by defining tags inside the query parameters.

We will make use of an Apex Controller to define the tags and a Visualforce Page to display the SharinPix Image Search:

* [Apex Class Controller](using-tag-filters-inside-query-parameters.md#apex-class-controller)
* [Visualforce Page](using-tag-filters-inside-query-parameters.md#visualforce-page)

## Apex Class Controller

The codes snippet below shows the implementation of the Apex Class Controller.

```apex
public class SharinPixSearchPage {
  public Map<String, Object> params;
  private sharinpix.Client clientInstance = sharinpix.Client.getInstance();

  public SharinPixSearchPage(ApexPages.StandardController controller) {
    Map<String, Object> query = new Map<String, Object> {
      'q' =>  '"tag1" "tag2" "tag3"'
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

The key <mark style="color:red;">`q`</mark> defines the set of tags that must be present on the image search results. In the above example, the query parameter contains:

```
'q' =>  '"tag1" "tag2" "tag3"'
```

This indicates that only images with both tags, irrespective of which album they belong to, are to be displayed on the search results.

The key <mark style="color:red;">`q`</mark> can take other values that can broaden or narrow the scope of the search results. The examples below show how this can be made possible.

### View images from all albums

* To view images from all 3 albums, the query should be:

<mark style="color:red;">`'q' => '"album1" "album2" "new album"'`</mark>

{% hint style="success" %}
Note that double quotes are used for text with spaces. They are optional if no spaces are contained.
{% endhint %}

### View images with either tags

* To view images from 2 albums and with both of the 2 tags:

<mark style="color:red;">`'q' => 'tags:(+("album1" "album2") +("tag1" AND "tag 2"))'`</mark>

### Only view images with both tags

* To view images from 2 albums and with either of the 2 tags:

<mark style="color:red;">`'q' => 'tags:(+("album1" "album2") +("tag1" OR "tag 2"))'`</mark>

### View images from multiple albums

* To view images with both of the tags, irrespective of the albums they are in:

<mark style="color:red;">`'q' => '"tag1" "tag 2"'`</mark>

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
