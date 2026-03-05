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

# Image methods

## Image methods

The SharinPix package provides the Apex class, **Image**, which includes methods that can be applied when manipulating images on Salesforce.

Methods:

* [moveImages](image-methods.md#moveimages)
* [exportAsContentDocument](image-methods.md#exportascontentdocument)
* [downloadImages](image-methods.md#downloadimages)
* [fetchAsBase64](image-methods.md#fetch-as-base64-1)
* [restoreImage](image-methods.md#restore-image-1)

### Image Method Example <a href="#image-method-example" id="image-method-example"></a>

#### moveImages <a href="#moveimages" id="moveimages"></a>

_global static List\<Object> **moveImages**(List\<String> lstImageIds, String destinationAlbumId)_

* Moves one or more images to another album. Note: This method can be used to move a maximun of 50 images at once. Example:

```apex
sharinpix.Image.moveImages(new List<String> { 'imageId1', 'imageId2' }, 'destinationAlbumId');
```

#### exportAsContentDocument <a href="#exportascontentdocument" id="exportascontentdocument"></a>

_global void **exportAsContentDocument**()_

* Exports a SharinPix Image to Salesforce as a Content Document. Example:

```apex
(new sharinpix.Image('public_id')).exportAsContentDocument();
```

#### downloadImages <a href="#downloadimages" id="downloadimages"></a>

_global static String **downloadImages**(List\<String> imageIds)_

* Get a URL that opens a zip including the images. Example:

```apex
sharinpix.Utils u = new Sharinpix.Utils(); 
sharinpix.Image.downloadImages(u.getAlbumImageIds(albumId));
```

#### fetchAsBase64 <a href="#fetch-as-base64-1" id="fetch-as-base64-1"></a>

_global static String **fetchAsBase64**(String url)_

* Converts an image to base64. Example:

```apex
sharinpix.Image.fetchAsBase64('https://app.sharinpix.com/image.png');
```

#### restoreImage <a href="#restore-image-1" id="restore-image-1"></a>

_global static String **restoreImage**(String imageId)_

* Restores a trashed SharinPix Image. Example:

```apex
sharinpix.Image.restoreImage('imageId');
```

{% hint style="success" %}
**Tip:**

The SharinPix package also includes the **Utils** class, which provides useful methods that can be used for image, album, tag management, and a lot more. For more information about the **Utils** method, please refer to the article below:

[Utils methods](utils-methods.md)
{% endhint %}
