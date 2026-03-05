---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: false
  outline:
    visible: true
  pagination:
    visible: false
  metadata:
    visible: false
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Integrate SharinPix with an External Application

## Overview

SharinPix can be used from an external web or mobile application. A web application can display SharinPix components in an iframe, while a mobile application can launch the SharinPix Mobile App through a universal link.

This article explains the architecture, album mapping, and token-generation steps needed for these integrations. It is intended for developers implementing an external application.

In this article, we will cover:

* [When to use this integration](integrate-sharinpix-with-an-external-application.md#when-to-use-this-integration)
* [Choose the integration approach](integrate-sharinpix-with-an-external-application.md#choose-the-integration-approach)
* [Understand the host organization, album ID, and token](integrate-sharinpix-with-an-external-application.md#understand-the-host-organization-album-id-and-token)
  * [Host Salesforce organization](integrate-sharinpix-with-an-external-application.md#host-salesforce-organization)
  * [Album and record mapping](integrate-sharinpix-with-an-external-application.md#album-and-record-mapping)
  * [Secret, issuer, and token](integrate-sharinpix-with-an-external-application.md#secret-issuer-and-token)
* [Display an album in a web application](integrate-sharinpix-with-an-external-application.md#display-an-album-in-a-web-application)
* [Launch the SharinPix Mobile App from your application](integrate-sharinpix-with-an-external-application.md#launch-the-sharinpix-mobile-app-from-your-application)
* [Test the integration and prepare an organization change](integrate-sharinpix-with-an-external-application.md#test-the-integration-and-prepare-an-organization-change)
* [Before going live](integrate-sharinpix-with-an-external-application.md#before-going-live)
* [If you need a custom upload integration](integrate-sharinpix-with-an-external-application.md#if-you-need-a-custom-upload-integration)

## When to use this integration

* You use Salesforce alongside an external system or a custom web or mobile application and want to access the same SharinPix files from that application.
* You are moving your business application away from Salesforce and want to maintain access to your existing SharinPix files. Contact [our Support team](../../getting-started-with-sharinpix/how-to-contact-support.md) before changing the Salesforce organization associated with SharinPix.

## Choose the integration approach

* **Web application:** [embed a SharinPix Album in an iframe](integrate-sharinpix-album-on-your-website-developer-oriented.md) and supply a server-generated online token.
* **Mobile application:** launch the [SharinPix Mobile App](../../mobile-app/sharinpix-mobile-app-how-it-works.md) using a [universal link or deep link](../../mobile-app/sharinpix-mobile-app-deeplink-syntax.md) containing a mobile upload token.

<figure><img src="../../.gitbook/assets/REST API screenshot 1.png" alt=""><figcaption></figcaption></figure>

## Understand the host organization, album ID, and token

### Host Salesforce organization

The host organization is the Salesforce organization associated with your SharinPix account. It provides access to SharinPix configuration and administration. The external application can provide the business interface without requiring users to work in the Salesforce interface.

Before configuring the integration, [register your Salesforce organization to SharinPix](../../getting-started-with-sharinpix/basic-setup/basic-setup-step-2-register-your-salesforce-organization-to-sharinpix.md). If you are testing with a Salesforce Developer organization, SharinPix can later change the associated Salesforce organization so the same SharinPix files remain available through the new organization. Coordinate that change with [our Support team](../../getting-started-with-sharinpix/how-to-contact-support.md) to confirm the album mapping and preserve access to existing files.

### Album and record mapping

The album ID identifies the SharinPix album that the application should display or upload to. In a Salesforce integration, this is the Salesforce record ID. Your external application must maintain a stable mapping between its business record and the corresponding SharinPix album ID.

For existing files, preserve the existing album IDs in this mapping. Do not assume that the ID of a new external record identifies the existing SharinPix album. The [SharinPix Code Generator](../../cookbook/sharinpix-code-generator.md) explains how to use a Salesforce record ID or a field containing an album ID.

### Secret, issuer, and token

The issuer identifies the organization owning the album and files. The SharinPix secret is used on a trusted server to sign a JSON Web Token (JWT). The token identifies the target album and grants the permissions needed for the operation.

Follow the secret-creation and server-side signing instructions in [Integrate SharinPix Album on Your Website](integrate-sharinpix-album-on-your-website-developer-oriented.md). For token types, permissions, and lifecycle considerations, see [Working with SharinPix Tokens](../../best-practices/working-with-sharinpix-tokens.md).

{% hint style="danger" %}
**Security:** Never include the SharinPix secret in browser code, a mobile application, a URL, or a distributed client. Generate and sign tokens on a trusted server, authorize the user and target album before issuing a token, and grant only the permissions required.
{% endhint %}

<figure><img src="../../.gitbook/assets/REST API screenshot 2.png" alt=""><figcaption></figcaption></figure>

## Display an album in a web application

1. Authenticate the user in your application and determine which business records they may access.
2. Resolve that record to the correct SharinPix album ID on your backend.
3. Generate an online token on the server. Use the [online token generation methods](../../access-and-security/online-token-generation-methods.md) for Apex examples, or the [website integration example](integrate-sharinpix-album-on-your-website-developer-oriented.md) for JWT generation outside Salesforce.
4. Return the token to the authorized application and use the iframe example in the website integration guide to display the album.
5. Test both allowed and denied operations with the permissions required by your users.

{% hint style="success" %}
**Tip**\
\
To build the permissions used by the token, open the [SharinPix Code Generator](../../cookbook/sharinpix-code-generator.md), select the required abilities, test them in the preview, and review the generated Raw Permissions or Apex example. Confirm the album ID before using the generated code in your implementation.
{% endhint %}

## Launch the SharinPix Mobile App from your application

The [SharinPix Mobile App](../../mobile-app/sharinpix-mobile-app-how-it-works.md) provides capture and upload functionality, including offline capture. Your application obtains an appropriate token and opens a link to hand off the capture workflow.

{% hint style="warning" %}
**Warning**\
\
For external integrations, preferably generate the mobile upload token without an associated user (anonymous). When using `generateMobileAppUrl`, set `anonymousUser` to `true` inside the `claims` map in the `options` parameter to remove the user association. See [Generate SharinPix Mobile URL](../../cookbook/generate-sharinpix-mobile-url.md) for the URL-generation example and anonymous-user configuration.
{% endhint %}

Your backend should still authorize access to the target album before providing the token or URL.

1. Generate a [mobile upload token](../../mobile-app/mobile-token-generation-methods.md) for the target album using a [Salesforce Flow](../../mobile-app/sharinpix-automatic-mobile-upload-token-generation-admin-friendly.md), [Apex method](../../mobile-app/mobile-token-generation-methods.md#id-2.-token-generation-using-apex-methods-developer-oriented), or [Apex trigger](../../mobile-app/mobile-token-generation-methods.md#id-3.-token-generation-using-apex-triggers-developer-oriented).
2. Provide the token to the authorized external application through your authenticated backend. Do not expose the signing secret.
3. Construct a [universal link or deep link](../../mobile-app/sharinpix-mobile-app-deeplink-syntax.md) with the token and the required parameters.
4. Open the link from your application. SharinPix uploads the captured media to the album identified by the token.
5. Configure a return URL, when needed, using the supported parameters in the deeplink syntax documentation.

Universal-link example (replace the placeholder with a URL-encoded mobile upload token):

{% code collapsedlinecount="10" %}
```
https://app.sharinpix.com/native_app/upload?token=<mobile-upload-token>
```
{% endcode %}

Deep-link equivalent:

{% code collapsedlinecount="10" %}
```
sharinpix://upload?token=<mobile-upload-token>
```
{% endcode %}

See the [parameters for capture mode, tags, checklist, confirmation behavior, and return navigation](../../mobile-app/sharinpix-mobile-app-deeplink-syntax.md). **URL-encode dynamic values** and test the complete handoff on your target devices.

## Test the integration and prepare an organization change

If you need an environment to test the implementation, create a Salesforce Developer organization, install SharinPix, and [register the organization](../../getting-started-with-sharinpix/basic-setup/basic-setup-step-2-register-your-salesforce-organization-to-sharinpix.md). You can then obtain a secret through the SharinPix Administration Dashboard and test token generation, album access, and mobile handoff using the linked guides above.

When you are ready to move to another organization, SharinPix can change the associated Salesforce organization. Contact [our Support team](../../getting-started-with-sharinpix/how-to-contact-support.md) to confirm the target setup, licensing, existing album mapping, and cutover steps.

{% hint style="danger" %}
**Important:** The Salesforce Developer organization described here is for testing the implementation. Do not uninstall SharinPix or deactivate any Salesforce organization until our Support team has confirmed how access to existing files will be maintained.
{% endhint %}

## Before going live

* Verify that each authorized external record opens the correct album, including records with existing files.
* Keep secrets server-side and restrict token permissions and lifetime to the workflow.
* Test unauthorized access, expired tokens, mobile handoff, and offline capture, followed by upload.
* Confirm the complete integration architecture with [our Support team](../../getting-started-with-sharinpix/how-to-contact-support.md) before production use or an organizational change.

## If you need a custom upload integration

Custom REST upload integrations are strongly discouraged because they require additional implementation and ongoing maintenance. If your application must control the upload interface or call upload endpoints, [contact our Support team](../../getting-started-with-sharinpix/how-to-contact-support.md) and explain your use case and requirements. Support can review the approach and share the relevant technical details if a custom integration is appropriate.
