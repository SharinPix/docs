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

# SharinPix Mobile App: Checklist

The SharinPix **checklist** feature provides a list of tags ready to be filled with images uploaded by users. When using this feature, if a tag is applied to the minimum number of images required, the associated tag entry turns from red to green on the checklist.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist - 1.png" alt=""><figcaption></figcaption></figure>

## Opening the checklist on the SharinPix mobile app

In order to access the checklist feature on the SharinPix mobile app, a deeplink can be used.

SharinPix uses deeplinks to launch the SharinPix app from other mobile apps such as the Salesforce mobile app or Salesforce Field Service (FSL) app.

{% hint style="info" %}
For more information about the deeplink syntax, you can refer to the following article:

[_SharinPix mobile App : Deeplink syntax_](sharinpix-mobile-app-deeplink-syntax.md)
{% endhint %}

### Checklist configuration

To configure the checklist feature in a deeplink, the parameter [**checklist**](sharinpix-mobile-app-deeplink-syntax.md#checklist) should be used. The value will then correspond to each tag entry, separated by the semicolon symbol (that is, by **;**).

The example below demonstrates the checklist parameter with five tags (Kitchen, Bedroom, Living-Space, Balcony, and Outdoor):

```
checklist=Kitchen;Bedroom;Living-Space;Balcony;Outdoor
```

Using the above example, users are required to upload at least one image for each tag to complete the checklist.

### Checklist configuration to indicate the minimum number of images to be uploaded

The checklist feature allows you to set a minimum number of images to be uploaded under each tag. The syntax here is two asterisk symbols (that is, \*\*) followed by the minimum number of images, as demonstrated below:

```
checklist=Kitchen**3
```

Using the above checklist configuration, the users are required to upload **at least three images** under the tag, **Kitchen**.

```
checklist=Kitchen**3;Bedroom**2
```

Using the above example, users are required to upload at least three images tagged with Front, at least two images tagged with Side, and at least one image tagged with _Bedroom_ in order to complete the checklist.

{% hint style="warning" %}
**Note:**

You can still submit the captured images even if the checklist is not completed. The checklist feature is mainly used as a status and does not block submissions when incomplete.
{% endhint %}

### Configuring a checklist on the Mobile App Global Configuration

Alternatively, you can use the **checklist\_ref** parameter to access the checklist feature. The value for this parameter should be configured on your Org's [mobile app global configuration](sharinpix-mobile-app-global-configuration.md).

When opening a checklist on the SharinPix mobile app with the **checklist\_ref** parameter, the application will try to find a **key** , in the mobile app global configuration's **checklists** object, matching the **checklist\_ref** value specified to load the checklist with the appropriate tags.

Example:

```
checklist_ref=building-inspection
```

Here, the application will try to find the "building-inspection" key in the checklists object.

{% hint style="warning" %}
Note:

* Matching of the **checklist\_ref** parameter value with the **checklists** object **keys** is **case sensitive**.
* If no matching key is found, an **error** page will be displayed.
* If you are using the [SharinPix Mobile Launcher](../lightning-web-component/sharinpix-mobile-launcher.md), add the **checklist\_ref** parameter in the **Custom parameters** of the Lightning component.
{% endhint %}

**Mobile App Global Configuration**

In your Org's [mobile app global configuration](sharinpix-mobile-app-global-configuration.md):

* Add a "**checklists"** key. The value for this key is an object. The keys for this object are the values that can be used for the **checklist\_ref** parameter in deeplinks or universal links. Any number of keys can be added.

The value for any key in the **checklists** object is another **object** with the following entries:

* **tags** : An array of strings where each string represents a tag. A **minimum count** of images can be specified for each tag by adding **"\*\*\<MIN\_COUNT>**" at the end of the tag name. If no minimum count is specified, the default will be **one**.

Example:

<mark style="color:red;">`"tags": ["Fire Extinguisher", "Exit Doors**5", "Electrical Setup**0"]`</mark>

Here three tags are specified. The tag **"Fire Extinguisher"** will have a minimum count of **one** since it was not specified, **"Exit Doors"** will have a minimum count of **five,** and **"Electrical Setup"** will have a minimum count of **zero** therefore optional.

{% hint style="info" %}
Info:

Another **form** key can be used to extend the basic checklist feature to a [Checklist with Form Features](sharinpix-mobile-app-checklist-with-form-features.md).
{% endhint %}

Example:-

```json
{
  "checklists": {
    "building-inspection": {
      "tags": [
        "Fire Extinguisher",
        "Exit Doors**5",
        "Electrical Setup**0",
        "Electrical Panel**10",
        "Charging Station"
      ]
    },
    "house": {
      "tags": [
        "Doors",
        "Windows",
        "Bedrooms"
      ]
    }
  }
}
```

{% hint style="warning" %}
Note:

If you are using the [SharinPix Mobile Launcher](../lightning-web-component/sharinpix-mobile-launcher.md), add the **checklist\_ref** parameter in the **Custom parameters** of the Lightning component.
{% endhint %}

## Demo

Now that you know how to configure the checklist parameter, let's see how it looks like on the SharinPix mobile app.

For this demo, we will use the following checklist configuration in our deeplink:

<mark style="color:red;">`checklist=Kitchen**3;Bedroom**2;Living Space**2;Balcony**2;Outdoor**3`</mark>

Once you select the deeplink, the SharinPix mobile app is launched and the checklist feature is displayed as follows:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist - 2.png" alt=""><figcaption></figcaption></figure>

Next, we will upload the required number of images for the _Kitchen_ tag:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist - 3.png" alt=""><figcaption></figcaption></figure>

Once all images have been captured, you should tap on the check button located at the bottom right corner to validate the checklist and submit the images.

{% hint style="success" %}
**Tips:**

* If you attempt to submit the images before the completion of the checklist, you will be prompted with a message asking if you wish to exit despite the missing tasks. This message can be personalized using the [incomplete\_checklist\_alert\_text parameter](sharinpix-mobile-app-global-configuration.md#configure-the-incomplete_checklist_alert_text-parameter). To **prevent** submission, the [**enforce\_min\_count**](sharinpix-mobile-app-deeplink-syntax.md#enforce_min_count) parameter can be used.
* The tag entries on the checklist can be parameterized in such a way so that once the required number of images has been uploaded for a tag (that is, when the tag entry color changes from red to green), the corresponding row is sent to the bottom of the list. For such configurations, you can make use of the [checklist\_order parameter](sharinpix-mobile-app-global-configuration.md#configure-the-checklist_order-parameter).
* The checklist page displays all images captured for each tag in the same job. So, you will still be able to see the existing images from previous sessions. Also, if you have added tags to some images before coming to the checklist page, those images will also appear if the tag is also present in the checklist. An example is provided below.
  1. The SharinPix mobile app is opened with <mark style="color:red;">`auto_tag=Outdoor`</mark>.
  2. Some images are captured with the <mark style="color:red;">`Outdoor`</mark> tag.
  3. The SharinPix mobile app is then opened again, but this time with <mark style="color:red;">`checklist=Kitchen**3;Bedroom**2;Living Space**2;Balcony**2;Outdoor**3`</mark>. Here, you will notice that all images captured previously with the auto tag <mark style="color:red;">`Outdoor`</mark> are available in the checklist by default as depicted below:
{% endhint %}

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist - 4.png" alt=""><figcaption></figcaption></figure>
