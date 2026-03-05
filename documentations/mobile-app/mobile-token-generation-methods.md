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

# Mobile token generation methods

SharinPix mobile upload tokens are used to securely upload photos and PDF forms from the SharinPix mobile app to Salesforce. Such tokens can be used by users to perform the upload without being connected to Salesforce.

This article outlines the methods to generate mobile upload tokens without being connected to the internet (**Excluding Salesforce**).

{% hint style="success" %}
**Tip:**

For more information on SharinPix tokens, refer to this article: [Working with SharinPix Tokens](../best-practices/working-with-sharinpix-tokens.md)
{% endhint %}

Mobile upload tokens can be configured and generated using the following methods:

1. [Using Salesforce Flows.](mobile-token-generation-methods.md#id-1.-using-salesforce-flows) (Admin-Friendly)
2. [Using Apex methods.](mobile-token-generation-methods.md#id-2.-token-generation-using-apex-methods-developer-oriented) (Developer-Oriented)
3. [Using Apex Triggers.](mobile-token-generation-methods.md#id-3.-token-generation-using-apex-triggers-developer-oriented) (Developer-Oriented)

## 1. Using Salesforce Flows

The SharinPix package includes the **TokenGeneration** Apex class which can be invoked from a Salesforce Flow to generate and store the mobile **upload** tokens in Salesforce fields.

For more information on how to create and configure such automation, refer to this article: [SharinPix automatic mobile upload token generation (Admin Friendly)](sharinpix-automatic-mobile-upload-token-generation-admin-friendly.md)

## 2. Token generation using Apex methods (Developer-oriented)

The SharinPix package includes the **Utils** Apex class which consists of handy Apex methods that clients can easily integrate in their custom code.

The same Apex class includes the **generateMobileAppUrl** method which is used to generate a URL to the SharinPix mobile app. _The same URL already embeds a mobile upload token enabling photo uploads on the SharinPix app._

For more information about the **generateMobileAppUrl** Apex method, refer to this link: [Utils - generateMobileAppUrl](../cookbook/utils-methods.md)

## 3. Token generation using Apex Triggers (Developer-oriented)

You also implement an automatic mobile upload token generation using an Apex Trigger and store the generated token in a Salesforce field.

```apex
String token = sharinpix.Client.getInstance().token(
                new Map<String, Object> {
                    'user_id' => UserInfo.getUserId(),
                    'email' => UserInfo.getUserEmail(),
                    'album_id' => id,
                    'name' => '',
                    'exp' => 0 //the value 0 means non expiring token
                }
            );
            
// Save token value in Salesforce field
```
