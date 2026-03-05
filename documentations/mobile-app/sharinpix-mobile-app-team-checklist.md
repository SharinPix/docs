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

# SharinPix Mobile App: Team Checklist

This article presents the SharinPix **Team Checklist** feature which enables users to view photos uploaded to an album via a [checklist](sharinpix-mobile-app-checklist.md).

The team checklist ensures that users can view live photos uploaded to a checklist by other users.

{% hint style="success" %}
**Tip:**

For more information on the checklist feature and how it is configured, refer to this article: [SharinPix Mobile App: Checklist](sharinpix-mobile-app-checklist.md)
{% endhint %}

<figure><img src="../.gitbook/assets/Gradio Image (15).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

* The Team Checklist only works **online** to fetch the photos.
* To use the Team Checklist feature, you should configure the token abilities as explained in the section [Configure Team Checklist Abilities on Token](sharinpix-mobile-app-team-checklist.md#configure-team-checklist-abilities-on-token) below.
{% endhint %}

{% hint style="success" %}
**Tips:**

* For more information on how to enable the team checklist feature on all devices by default, refer to this link: [Configure Team Checklist parameter on the Global Settings](sharinpix-mobile-app-global-configuration.md#configure-the-team-parameter)
* For more information on how to configure the team checklist parameter in SharinPix deeplinks, refer to the following link: [Team Checklist parameter](sharinpix-mobile-app-deeplink-syntax.md#team)
{% endhint %}

{% hint style="danger" %}
Once a user logs out of SharinPix, all tokens generated with his/her user ID in them are invalidated. This is a security mechanism. If ever those users have to access the team checklist feature on the mobile app with their old tokens, the feature will not be functional. To circumvent this, you can enable the flag labelled "**Allow bypassing user logout security check**" to whitelist the tokens. The flag is available on your organization’s SharinPix admin dashboard (see image below).

This addresses specific scenarios where the tokens being used are linked to the users who generated them (by a user\_id parameter). This feature is not intended for general mobile app use but is needed for instances where Team Checklist is implemented, and tokens linked to users need to persist beyond logout. To avoid meddling with the security in place, we recommend using the [Mobile Launcher](../lightning-web-component/sharinpix-mobile-launcher.md) component instead of activating the flag.
{% endhint %}

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Team Checklist - 2.png" alt=""><figcaption></figcaption></figure>

## Configure Team Checklist Abilities on Token

The Team Checklist token abilities can be configured either:

1. [Using the SharinPix Mobile Launcher with a SharinPix Permission.](sharinpix-mobile-app-team-checklist.md#using-the-sharinpix-mobile-launcher-with-a-sharinpix-permission)
2. [Using an Apex method.](sharinpix-mobile-app-team-checklist.md#using-apex-method)

### Using the SharinPix Mobile Launcher with a SharinPix Permission

The easiest way of configuring the Team Checklist is using the [SharinPix Mobile Launcher](../lightning-web-component/sharinpix-mobile-launcher.md) component with [SharinPix Permission](../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md). Such SharinPix Permission is depicted below - all component abilities for the Mobile Launcher component should be checked to configure the Team Checklist token:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Team Checklist - 4.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Tip:

For detailed information on how to configure a Team Checklist token for the Mobile Launcher component using a SharinPix Permission, refer to this article: [SharinPix Permission for SharinPix Mobile Launcher Component](../access-and-security/sharinpix-permission-for-sharinpix-mobile-launcher-component.md)
{% endhint %}

### Using Apex method

The Team Checklist token abilities can be programmatically configured using a code snippet as below:

```apex
String token = sharinpix.Client.getInstance().token(
    new Map<String, Object> {
        'album_id' => id,
        'name' => 'Job name',
        'image_list' => true,
        'album_view' => true,
        'tag_read' => true,
        'user_id' => UserInfo.getUserId(), // token linked to this user
        'email' => UserInfo.getUserEmail(), // token linked to this user
        'exp' => 0 //the value 0 means non expiring token
    }
);
// Save token value in Salesforce field
```

{% hint style="success" %}
**Tip:**

For some custom components, you can directly pass a SharinPix Permission ID to provide the correct Team Checklist token abilities.
{% endhint %}

### Demo: Team Checklist

In the diagram below, some images display a cloud icon, indicating they were uploaded by other users, while those without the cloud icon were uploaded by the current user of the mobile app. Pressing the 'refresh' button fetches new images uploaded by other users.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Team Checklist - 3.png" alt=""><figcaption></figcaption></figure>
