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
  actions:
    visible: true
---

# Troubleshoot SharinPix Mobile App Common Issues

This article outlines:

1. [The common SharinPix mobile app issues.](troubleshoot-sharinpix-mobile-app-common-issues.md#common-sharinpix-mobile-app-issues)
2. [How to debug SharinPix mobile app issues?](troubleshoot-sharinpix-mobile-app-common-issues.md#common-sharinpix-mobile-app-issues)
3. [How to report errors/bugs on the SharinPix mobile app?](troubleshoot-sharinpix-mobile-app-common-issues.md#id-3.-how-to-report-errors-bugs-on-the-sharinpix-mobile-app)

## Common SharinPix Mobile App Issues

The most common SharinPix mobile app issues are:

1. [Photos captured on the app are not available on the Salesforce record.](troubleshoot-sharinpix-mobile-app-common-issues.md#id-1.-photos-captured-on-the-app-are-not-available-on-salesforce)
2. [Upload tokens used are invalid or wrongly configured.](troubleshoot-sharinpix-mobile-app-common-issues.md#id-2.-upload-tokens-used-are-invalid-or-wrongly-configured)

The subsections below explain the above in more detail.

### 1. Photos captured on the app are not available on Salesforce

If you cannot find the photos captured on the SharinPix mobile app on the Salesforce record, it can be due to one of the following:

* The upload token used is invalid or does not contain the right data. For more information on how to debug such tokens, please refer to the section - [Upload tokens used are invalid or wrongly configured.](troubleshoot-sharinpix-mobile-app-common-issues.md#id-2.-upload-tokens-used-are-invalid-or-wrongly-configured)
* The photo upload is still pending on the mobile app.

The SharinPix mobile app allows users to capture photos offline. In such cases, the photos are uploaded to Salesforce once an internet connection is available.

For more information on how to check the upload status on the mobile app and the actions to be taken, please refer to this article: [I don't find images uploaded through SharinPix Mobile App on my Salesforce!](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/i-don-t-find-images-uploaded-through-sharinpix-mobile-app-on-my-salesforce)

{% hint style="warning" %}
**Note**:

* Opening the SharinPix mobile app once internet connectivity is available on the device will force the completion of pending uploads.
* If uploads are still pending when an internet connection is available, a notification can be sent instructing the user to open the SharinPix mobile app to complete pending uploads.
{% endhint %}

### 2. Upload tokens used are invalid or wrongly configured

SharinPix makes use of JSON Web Tokens to securely transmit information from its components and mobile app to Salesforce.

SharinPix tokens are categorized as follows:

1. **SharinPix Online Tokens** - Used to display SharinPix components online in your Salesforce organization or on the SharinPix mobile app.
2. **SharinPix Mobile Upload Tokens** - Used to upload photos using the SharinPix mobile app.

{% hint style="success" %}
**Tips:**

* For more information on SharinPix Tokens and how they work, refer to this article: [Working with SharinPix Tokens](../best-practices/working-with-sharinpix-tokens.md)
* For more information on how to differentiate between online and mobile upload tokens, refer to this link: [How to easily differentiate between online and mobile upload tokens?](../best-practices/working-with-sharinpix-tokens.md#how-to-easily-differentiate-between-online-and-mobile-upload-tokens)
{% endhint %}

This section covers the following problems:

1. [An **Invalid Token Error** message is displayed on the screen.](troubleshoot-sharinpix-mobile-app-common-issues.md#id-2.a.-an-invalid-token-error-message-is-displayed-on-the-screen)
2. [The photos are not uploaded to the expected record on Salesforce.](troubleshoot-sharinpix-mobile-app-common-issues.md#id-2.b.-photos-are-not-uploaded-to-the-expected-record-on-salesforce)
3. [The SharinPix mobile app does not open on the expected screen - no upload screen or album displayed as expected for instance.](troubleshoot-sharinpix-mobile-app-common-issues.md#id-2.c.-the-sharinpix-mobile-app-does-not-open-on-the-expected-screen)

#### 2.a. An 'Invalid Token Error' message is displayed on the screen.

<figure><img src="../.gitbook/assets/Troubleshoot SharinPix Mobile App Common Issues - 1 (1).jpg" alt=""><figcaption></figcaption></figure>

If you are encountering an **Invalid Token Error** , as demonstrated above, you should:

* If you are saving the token value in a Salesforce field, ensure that the user has at least **read** access to the field and that the field API name has been properly typed in the deeplink or URL.
* If you are directly passing the token value to the deeplink or URL, ensure that the token value is complete and has been properly added to the deeplink or URL. To cross-check this quickly, you can make use of the [jwt.io](https://jwt.io/) website to verify the validity of the token as demonstrated below:

Here's how a valid token value is presented on the [jwt.io](https://jwt.io/) website:

<figure><img src="../.gitbook/assets/Troubleshoot SharinPix Mobile App Common Issues - 2.png" alt=""><figcaption></figcaption></figure>

Here's how an invalid token value is presented on the [jwt.io](https://jwt.io/) website:

<figure><img src="../.gitbook/assets/Troubleshoot SharinPix Mobile App Common Issues - 3.png" alt=""><figcaption></figcaption></figure>

#### 2.b. Photos are not uploaded to the expected record on Salesforce

If you cannot see the uploaded photo on the Salesforce record, you should verify if the token has been configured properly and is uploading to the right record.

To verify this for mobile upload tokens, proceed as follows:

* Open the [jwt.io](https://jwt.io/) website.
* Copy the token value and paste it into the **Encoded** section.
* In the _payload_ section under **Decoded**, verify if:
  * The **album\_id** value corresponds to the expected Salesforce record ID.
  * Ensure that the token has not expired.
  * Verify that the secret key corresponds to your SharinPix's secret key.

{% hint style="warning" %}
**Note:**

For more details on how to verify the album ID, token expiration, and secret key, refer to this link: [SharinPix Mobile Upload Token](../best-practices/working-with-sharinpix-tokens.md#sharinpix-mobile-upload-token)
{% endhint %}

<figure><img src="../.gitbook/assets/Troubleshoot SharinPix Mobile App Common Issues - 4.png" alt=""><figcaption></figcaption></figure>

To verify this for online mode tokens, proceed as follows:

* Open the [jwt.io](https://jwt.io/) website.
* Copy the token value and paste it into the **Encoded** section.
* In the _payload_ section under **Decoded** , verify if:
  * The Salesforce record ID is correct.
  * Ensure that the token has not expired.
  * Verify that the secret key corresponds to your SharinPix's secret key.

{% hint style="warning" %}
**Note:**

For more details on how to verify the album ID, token expiration, and secret key, refer to this link: [SharinPix Online Token](../best-practices/working-with-sharinpix-tokens.md#sharinpix-online-token)
{% endhint %}

<figure><img src="../.gitbook/assets/Troubleshoot SharinPix Mobile App Common Issues - 5.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

* In case your token has wrongly been configured, you should review the token generation used on your Salesforce organization.
* When using the online mode token, if the album available on the SharinPix mobile app keeps on loading, ensure that the token generation method has the **anonymousUser** parameter set to **true** as demonstrated here: [Online Mode Use Case Examples](sharinpix-mobile-app-online-mode.md#online-mode-use-case-examples)
{% endhint %}

#### 2.c. The SharinPix mobile app does not open on the expected screen

SharinPix makes use of two types of tokens - **SharinPix Online Tokens** and **SharinPix Mobile Upload Tokens**.

To upload photos, you should ensure that a **SharinPix Mobile Upload Tokens** is being used in the mobile app URL or deeplink.

If you want to access online features such as SharinPix images, albums, and search within the SharinPix mobile app, ensure that a **SharinPix Online Tokens** is used.

For more information on how to differentiate between online and mobile upload tokens, click [here](../best-practices/working-with-sharinpix-tokens.md#how-to-easily-differentiate-between-online-and-mobile-upload-tokens).

### 3. How to report errors/bugs on the SharinPix mobile app?

If sections 1 & 2 didn't resolve, refer to this article for more information on how to report the issue: [How to report a bug on the SharinPix mobile app?](https://github.com/SharinPix/documentation/blob/main/FAQ/l/987938-how-to-report-a-bug-on-the-sharinpix-mobile-app/README.md)
