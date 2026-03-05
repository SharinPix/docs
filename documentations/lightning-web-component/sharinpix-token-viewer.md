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

# SharinPix Token Viewer

{% hint style="info" %}
The **SharinPix Token Viewer** component permits the user to open any component using a token.
{% endhint %}

{% hint style="warning" %}
**Note:**

The SharinPix Token Viewer component works **only** with the [SharinPix Online Tokens](../best-practices/working-with-sharinpix-tokens.md#sharinpix-online-token).

For more information on the type of SharinPix Tokens, refer to the following article: [Working with SharinPix Tokens](../best-practices/working-with-sharinpix-tokens.md)
{% endhint %}

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
* On Mobile
* On Community Builder
{% endhint %}

## Getting Started

To use the SharinPix Token Viewer component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/image (18) (2).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

<figure><img src="../.gitbook/assets/image (19) (3).png" alt=""><figcaption></figcaption></figure>

* **Token Field API Name:** The API name of the field containing the SharinPix token.
* **SharinPix Secured Token Name:** The name of the 'SharinPix Secured Token' Custom Metadata configured for the token viewer component. More information on how to configure the SharinPix Secured Token below.
* **Height:** Used to specify the component's height. The default height is **500** (px).

{% hint style="warning" %}
**Note:**

If the **SharinPix Secured Token Name** is set, the **Token Field API Name** is ignored.
{% endhint %}

### SharinPix Secured Token Setting

The SharinPix Secured Token will be used to create a token that expires. The expired token will be used on the token viewer component. Using the SharinPix Secured Token, the Token Viewer component will not use the token stored in the Salesforce field directly; instead, it will generate a new token that expires. This adds a layer of security as the token stored on Salesforce, which may be non-expiring, is not exposed in the user's browser.

Steps to configure the SharinPix Secured Token:

1. Go to Salesforce Setup
2. Open Custom Metadata Types
3. Click on Manage Records for **SharinPix Secured Token** Custom metadata type
4. Insert a label and name
5. For the **Object name** parameter, insert the object API name on which the SharinPix Token Viewer component has been added.
6. For the **Field name** parameter, insert the field API name of the field containing the token to be expired.
7. In the **Expiration** parameter, enter the number of minutes the token will live. The maximum allowed is 100.
8. Check the **Active** checkbox to activate the setting.

![](<../.gitbook/assets/SecuredToken (1) (1) (1).png>)

## Demo

A token of the SharinPix Album has been generated and inserted in the field 'token' as shown below:

{% hint style="success" %}
**Tip:**

Learn how to [generate tokens](../cookbook/generate-token-from-sharinpix-permission-with-apex.md) automatically.
{% endhint %}

![](<../.gitbook/assets/to (1) (1) (1).png>)

The picture below depicts a _SharinPix Album_ in the _SharinPix Token Viewer_ component:

![](<../.gitbook/assets/tokenViewer3 (1) (1) (1).png>)
