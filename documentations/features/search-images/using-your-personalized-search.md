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

# Using your personalized Search

* In this article, we will see how it is possible to personalize the search when using the SharinPix Image Search.
* You can rely on that entry in our Github account to deploy and play with this sample on any of your Salesforce orgs: [https://github.com/SharinPix/demo-apex/tree/account\_contacts\_search](https://github.com/SharinPix/demo-apex/tree/account_contacts_search)

{% hint style="success" %}
**Tip:**

The SharinPix Image Search query is a simple Elasticsearch query. You can find more information about Elasticsearch query by clicking [here](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-simple-query-string-query.html).
{% endhint %}

The following sections demonstrate how to use the SharinPix Album to perform a personalized search and display all the images present on the **Contact** records that are related to a particular **Account** record. This can be done by either using a **SharinPix Canvas App** or by embedding the SharinPix component inside an **Iframe**.

Therefore, you will need:

1. an [Apex Class Controller](using-your-personalized-search.md#apex-class-controller) that will build the query and generate the token.
2. a [Visualforce Page](using-your-personalized-search.md#visualforce-page) that will embed the Canvas App or the Iframe.

## Apex Class Controller

* The implementation for the Apex Class Controller can be found below.

```apex
public class SharinPixDemoAccountContactsSearchCtrl {
    private Map<String, Object> params;
    private sharinpix.Client clientInstance = sharinpix.Client.getInstance();

    public SharinPixDemoAccountContactsSearchCtrl(ApexPages.StandardController stdCtrl) {
        Id accountId = stdCtrl.getId();
        List<Contact> contacts = [SELECT Id FROM Contact WHERE AccountId = :accountId];
        String queryStr = '';
        for (Contact contact : contacts) {
            queryStr += '"' + contact.Id + '" ';
        }

        params = new Map<String, Object> {
            'path' => '/search?search_bar=false',
            'q' => queryStr,
            'download' => true,
            'download_filename' => 'my_zip_filename',
            'download_filenames' => 'inside_the_zip-00001'
        };
    }

    public String getParameters() {
        return JSON.serialize(params);
    }

    public String getSearchUrl() {
        return clientInstance.token(params);
    }
}
```

* A **query** is constructed by concatenating several **Contact** record Ids, separated by a single white-space. This query is meant to search for all Contact Objects that are related to the corresponding Account object.
* The code snippet below shows how the query is represented in code.

```apex
String queryStr = '';
for (Contact contact : contacts) {
	queryStr += '"' + contact.Id + '" ';
}
```

### Search Refinement

There are multiple ways to refine the search by modifying the parameter **q**. This permits you to:

* Search for images in one or more specific albums
* Search for images having specific tags
* Search for images taken on specific dates.

The following examples demonstrate how to refine the search:

* **Search for images found in specific albums**
  * Suppose we have albums with IDs **albumID** , **albumID 1** and **albumID 2** and we want to search for images found only in **albumID** and **albumID 1**. To do so, we have to modify the parameter **q** as shown below:

```apex
Map<String, Object> query = new Map<String, Object>();
query.put('q', queryStr);

params = new Map<String, Object> {
    'path' => '/search?search_bar=false',
    'q' => '"albumID" "albumID 1"',
    'download' => true,
    'download_filename' => 'my_zip_filename',
    'download_filenames' => 'inside_the_zip-00001'
};
```

{% hint style="warning" %}
**Note:**

Double quotes are used for text with spaces. They are optional if no spaces are contained.

For example:

<mark style="color:red;">`'q' => '"albumID" "albumID 1"',`</mark> could have been written as <mark style="color:red;">`'q' => 'albumID "albumID 1"',`</mark>
{% endhint %}

* **Search for images having specific tags**
  * Suppose we want to search only for images with tags names **Tag1** , we have to modify the parameter **q** in the code as shown below:

```apex
params = new Map<String, Object> {
    'path' => '/search?search_bar=false',
    'q' => 'tags:(+('+queryStr+') +("Tag1"))',
    'download' => true,
    'download_filename' => 'my_zip_filename',
    'download_filenames' => 'inside_the_zip-00001'
};
```

* Suppose we want to search only for images with tags names **Tag1&#x20;**<mark style="color:red;">**and**</mark>**&#x20;Tag 2**, we have to modify the parameter **q** in the code as shown below:

```apex
params = new Map<String, Object> {
    'path' => '/search?search_bar=false',
    'q' => 'tags:(+('+queryStr+') +("Tag1" AND "Tag 2"))',
    'download' => true,
    'download_filename' => 'my_zip_filename',
    'download_filenames' => 'inside_the_zip-00001'
};
```

* You can also search for images with either **Tag1** <mark style="color:red;">**or**</mark> **Tag2** using the code snippet below:

```apex
params = new Map<String, Object> {
    'path' => '/search?search_bar=false',
    'q' => 'tags:(+('+queryStr+') +("Tag1" OR "Tag 2"))',
    'download' => true,
    'download_filename' => 'my_zip_filename',
    'download_filenames' => 'inside_the_zip-00001'
};
```

* **Search for tagged images found in specific albums**
  * The example below shows how you can refine the search in order to search for images having tag **Tag1** in albums with IDs **albumID** **and** **albumID** **1** only.

```apex
Map<String, Object> query = new Map<String, Object>();
query.put('q', queryStr);

params = new Map<String, Object> {
    'path' => '/search?search_bar=false',
    'q' => 'tags:(+("albumID" "albumID 1") +("Tag1"))',
    'download' => true,
    'download_filename' => 'my_zip_filename',
    'download_filenames' => 'inside_the_zip-00001'
};
```

* **Search for images taken on specific dates from specific albums**
  * The following example demonstrates how you can enhance the search criteria to specifically look for images taken on certain dates from 'Jan 01, 2024' to 'Feb 01, 2024' within albums with IDs **albumID 1** and **albumID 2** only.

```apex
List<String> ids = ['albumID 1', 'albumID 2'];
String queryStr = '("albumID 1" "albumID 2") 
AND taken_at:[2024-01-01 TO 2024-02-01]';

params = new Map<String, Object> {    
    'path' => '/search?search_bar=false',    
    'q' => queryStr,
    'download' => true,
    'download_filename' => 'my_zip_filename',
    'download_filenames' => 'inside_the_zip-00001'
};
```

### Enable download and zipping

It is possible to download the search image results into a zipped folder through the use of the following parameters.

* <mark style="color:red;">`download`</mark> - (true or false ) enable or disable the download feature.
* <mark style="color:red;">`download_filename`</mark> - specify the name of the downloaded image file (only 1 image)
* <mark style="color:red;">`download_filenames`</mark> - specify the name format of the downloaded image files (multiple images)

{% hint style="success" %}
**Tip:**

For more information about how to personalize the download filenames, refer to the following article:

[Multiple Image download (ZIP) - How to personalize the download filenames](../download-images/multiple-image-download-zip-how-to-personalize-the-download-filenames.md)
{% endhint %}

```apex
params = new Map<String, Object> {
    'path' => '/search?search_bar=false'
    'q' => queryStr,
    'download' => true,
    'download_filename' => 'my_zip_filename',
    'download_filenames' => 'inside_the_zip-00001'
};
```

## Visualforce Page

* The code snippet below shows the implementation of the Visualforce Page used to display the search results on a SharinPix Album.

```html
<apex:page standardController="Account" extensions="SharinPixDemoAccountContactsSearchCtrl"
        showHeader="false" sidebar="false">
 <!-- Use either -->
 <apex:canvasApp developerName="Albums" width="100%" height="500px" parameters="{! parameters }"/>
 
 <!-- or -->
 <iframe id="iframeId" width="100%" height="500px" style="border: 0;" src="https://app.sharinpix.com/post_message"></iframe>
 <script>
     document.getElementById('iframeId').onload = function() {
         this.contentWindow.postMessage({ token: "{! searchUrl }" }, 'https://app.sharinpix.com');
     }
 </script>
</apex:page>
```

{% hint style="success" %}
In the code snippet above, SharinPix makes a reference to the **postMessage** method when using an Iframe.

For more information about the postMessage method and how SharinPix uses it, you can refer to the following article:

[Using a SharinPix component in an Iframe (Developer-oriented)](../main-integration/using-a-sharinpix-component-in-an-iframe-developer-oriented.md)
{% endhint %}
