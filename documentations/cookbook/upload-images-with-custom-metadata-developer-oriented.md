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

# Upload Images with Custom Metadata (Developer-Oriented)

This documentation explains how to pass custom metadata to images uploaded using [SharinPix albums](../lightning-web-component/sharinpix-album-lwc.md).

Adding custom metadata to images may be useful when you need to filter or group the uploaded images by specific metadata. You can add custom metadata to the images you upload either via the web app or the SharinPix Mobile app.

To demonstrate how images can be uploaded with custom metadata, we will:

* [Create a custom token with the **upload\_metadata** parameter.](upload-images-with-custom-metadata-developer-oriented.md#generating-token-with-upload_metadata-parameter)
* [Use a custom token in a SharinPix Component.](upload-images-with-custom-metadata-developer-oriented.md#using-custom-token-with-upload_metadata-parameter-on-sharinpix-components)

## Generating Token with upload\_metadata parameter

To add custom metadata to images you upload, you must add the **upload\_metadata** to a token generated via code.

The code snippet below shows the **upload\_metadata** parameter `projectId => 15` as the value.

```apex
'upload_metadata'=> new Map<String,String> {'projectId'=> '15'}
```

{% hint style="warning" %}
**Note:**

The **upload\_metadata** parameter is of type **Map \<String,&#x20;**_**T**_**>** where _**T**_ is can be any other type.
{% endhint %}

### Upload metadata parameter in Album token

Adding the **upload\_metadata** parameter to an album token will add the custom metadata specified to images uploaded on that album.

The code snippet below shows the **upload\_metadata** parameter in a custom album token.

```apex
public String generateToken(Id recordID) {
 sharinpix.Client clientInstance = sharinpix.Client.getInstance();
 String token = clientInstance.token(
     new Map<String, Object> { 
         'upload_metadata' => new Map<String, String> { 'projectId' => '15' }
         'Id' => recordID,
         'path' => '/pagelayout/' + recordID,
         'abilities' => new Map<String, Object> {
             recordID => new Map<String, Object> {
                 'Access' => new Map<String, Boolean> {
                     'see' => true,
                     'image_list' => true,
                     'image_upload' => true
                 }
             }
         }
     }
 );
 return token;
```

{% hint style="info" %}
You can find other ways to generate album tokens in this article, which is called [Online Token Generation](../access-and-security/online-token-generation-methods.md).
{% endhint %}

{% hint style="success" %}
**Tip:**

If you have an existing [SharinPix Album Permission](../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md), follow the article [Generate token from SharinPix Permission with Apex](generate-token-from-sharinpix-permission-with-apex.md) to add the **upload\_metadata** parameter to that permission.
{% endhint %}

### Upload metadata parameter in Mobile token

Adding the **upload\_metadata** parameter to a mobile token will add the custom metadata to images uploaded using the SharinPix Mobile App.

The code snippet below shows the **upload\_metadata** parameter in a custom mobile token.

```apex
String token = sharinpix.Client.getInstance().token(
                new Map<String, Object> {
                    'user_id' => UserInfo.getUserId(),
                    'email' => UserInfo.getUserEmail(),
                    'album_id' => id,
                    'name' => '',
                    'exp' => 0,
                    'upload_metadata'=> new Map<String,String> {'projectId'=> '15'}
            );
            
// Save token value in Salesforce field
```

{% hint style="info" %}
You can find other ways to generate mobile tokens in the article [Mobile token generation](../mobile-app/mobile-token-generation-methods.md).
{% endhint %}

## Using custom token with upload\_metadata parameter on SharinPix Components

You can use your custom token containing the **upload\_metadata** parameter on the [SharinPix Album](../lightning-web-component/sharinpix-album-lwc.md) component or SharinPix mobile component such as the [SharinPix Mobile Launcher](../lightning-web-component/sharinpix-mobile-launcher.md) component. You can follow [this article](generate-token-from-sharinpix-permission-with-apex.md#get-token-parameter-inside-lightning-component) on how you can use your custom token in an Album component via code.

Once you have your custom token in one of the components, uploading images using either components will add your custom metadata to the images

### SharinPix Image Object with custom metadata

If you want to access the value given to the **upload\_metadata** parameter as part of a Salesforce field, you will need:

* [SharinPix Image Sync setup](../image-sync/setup-sharinpix-image-sync.md)
* [Image Sync for pictures uploaded via SharinPix Mobile App](../image-sync/image-sync-for-pictures-uploaded-via-sharinpix-mobile-app.md) (Optional)

{% hint style="info" %}
You can follow the article [Enable Image Sync for Lightning](../image-sync/enable-image-sync-for-lightning.md) on how to view SharinPix Image Records.
{% endhint %}

The value given to the **upload\_metadata** parameter is added to the **Metadatas** field of a SharinPix Image object, as shown in the screenshot below.

![](<../.gitbook/assets/sp image (1) (2).png>)
