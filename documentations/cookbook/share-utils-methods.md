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

# Share Utils Methods

The SharinPix package provides the Apex class, **ShareUtils** , which includes methods that can be applied when sharing albums or images from Salesforce.

{% hint style="warning" %}
**Note:**

* Sharing is currently available on the Album component.
* Ensure that the user performing the Share has been assigned the [SharinPix Share Permission](../access-and-security/sharinpix-permission-sets.md).
{% endhint %}

### Share Utils Example <a href="#share-utils-example" id="share-utils-example"></a>

#### generateUrl <a href="#generateurl" id="generateurl"></a>

_global static String **generateUrl**(String recordId, String permissionIdOrName)_

* This method can be used to share a complete album with specific abilities.
* In the below code, “permission” is the name or ID of a SharinPix Permission.

```apex
String url = sharinpix.ShareUtils.generateUrl('0018a00001rL2scAAC', 'permission');
System.debug('shareable url: ' + url);
```

_**Note:** For more information on how to create/edit the custom permission, refer to this article:_ [_SharinPix Permission object - How to create and assign custom permission?_](../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md)

#### generateUrl <a href="#generateurl_1" id="generateurl_1"></a>

_global static String **generateUrl**(String recordId, String permissionIdOrName, List\<ShareImageInfos> imageInfos, Map\<String, Object> params)_

* This method can be used to share certain images of an album with specific abilities.&#x20;

```java
String url = sharinpix.ShareUtils.generateUrl('0018a00001rL2scAAC', 'permission', _imageInfos_ , _params_);
System.debug('shareable url: ' + url);
```

**Note:** _imageInfos and params are explained below._

#### Parameters

**imageInfos**

* imageInfos should be in the format below:

List\<sharinpix.ShareImageInfos> imageInfos = new List\<sharinpix.ShareImageInfos> { new sharinpix.ShareImageInfos('**imageId**', **index**)};

```java
List<sharinpix.ShareImageInfos> imageInfos = new List<sharinpix.ShareImageInfos> {
    new sharinpix.ShareImageInfos(
        '3a253a91-705c-4023-ad10-1206e93087d4', 
        0
    ),
    new sharinpix.ShareImageInfos(
        '8e83c16a-bb32-46d2-ae8b-60077bf2af2b', 
        1
    )
};
```

The **index** should be set only if the order of the images displayed is to be predefined. In addition to **index**, the params key **orderByIndex** should be set to true as explained below.

**params**

* The params value should be an Apex Map. The possible keys in it are:
  * **orderByIndex** (Boolean): set to true to maintain the order of the images according to their “index” values. If set to true, any sort field or direction on the SharinPix Permission is overridden. If set to false, the behaviour will default to the SharinPix Permission’s sort field or the application default.

```javascript
Map<String, Object> params = new Map<String, Object> {'orderByIndex' => true};
```

{% hint style="danger" %}
**Note:**

We advise caution when configuring a SharinPix Permission. If upload, edit or delete permissions are present, the viewers of the shared URL will be able to make changes to your images that will reflect on your Salesforce.
{% endhint %}
