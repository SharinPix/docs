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

# Generate SharinPix Mobile URL

The following article will show how it is possible to generate a SharinPix Mobile URL that will launch the SharinPix Offline Mobile application.

The method package SharinPix comes along with a utility method named **generateMobileAppUrl** that takes as parameters:

* **albumId:** corresponds to the album where photos, shot by the SharinPix offline Mobile application, are uploaded to.
* **options:** refers to a Map data structure that contains the name of the Job (**name**) and the **expiration** value, in seconds, of the SharinPix Mobile URL (**linkExpiration**). It also includes other mobile parameters using the key (**claims**) with a Map of keys that should be present in the token.

The code snippet below shows how this method is used to generate the url:

```apex
String albumId = 'insert_your_album_id';
String name = 'job1';
Integer linkExpiration = 100;

Map<String, Object> options = new Map<String, Object> {
    'name' => name,
    'linkExpiration' => linkExpiration
};

sharinpix.Utils util = new sharinpix.Utils();
String mobileAppURL = util.generateMobileAppUrl(albumId, options);
```

If tokens should not contain a userId, the parameter '**anonymousUser** ' should be added to claims section, as demonstrated below to remove any user association.

```apex
Map<String, Object> options = new Map<String, Object> {
    'name' => name,
    'linkExpiration' => linkExpiration,
    'claims' => new Map<String, Object> {
        'anonymousUser' => true //this removes any user association
    }
};
```
