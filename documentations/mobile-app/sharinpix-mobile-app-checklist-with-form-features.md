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

# SharinPix Mobile App: Checklist with Form Features

The SharinPix **Checklist with Form Features** (also referred to as "**Form Checklist**") is an extension of the [SharinPix Checklist](sharinpix-mobile-app-checklist.md) feature. **Form fields** can be specified alongside the list of tags which users can fill and submit. Submission of such checklist will result in the **creation** or **modification** of a record in the **SharinPix Checklist Result** object on Salesforce.

In the following sections, you will learn:

* [Opening a Checklist with Form Features on the SharinPix Mobile App](sharinpix-mobile-app-checklist-with-form-features.md#opening-a-checklist-with-form-features-on-the-sharinpix-mobile-app)
* [SharinPix Checklist Result Object](sharinpix-mobile-app-checklist-with-form-features.md#sharinpix-checklist-result-object)
* [Errors that may be encountered with the SharinPix Checklist with Form Features and the reasons for these errors](sharinpix-mobile-app-checklist-with-form-features.md#errors)

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist with Form Features - 1.png" alt=""><figcaption></figcaption></figure>

## Prerequisite

**SharinPix Checklist Result Permission**

Assign the **SharinPix Checklist Result Permission** to the users. This permission set gives basic access to the SharinPix Checklist Result feature. Check out [SharinPix Permission Sets](../access-and-security/sharinpix-permission-sets.md) for more information.

## Opening a Checklist with Form Features on the SharinPix Mobile App

In order to open a checklist with form features on the SharinPix mobile app, a [deeplink or universal link](navigation-with-sharinpix-deep-link-and-universal-link.md) can be used with the **checklist\_ref** parameter. The value for this parameter should be configured on the Org's mobile app global configuration.

When opening a checklist on the SharinPix mobile app with the **checklist\_ref** parameter, the application will try to find a **key** , in the mobile app global configuration's **checklists** object, matching the **checklist\_ref** value specified to load the checklist with the appropriate tags and form fields.

Example of a deeplink:

<mark style="color:red;">`sharinpix://upload?token=<Your Token>&checklist_ref=building-inspection`</mark>

Here, the application will try to find the "building-inspection" key in the checklists object.

{% hint style="warning" %}
Note:

* Matching of the **checklist\_ref** parameter value with the **checklists** object **keys** is **case sensitive**.
* If no matching key is found, an **error** page will be displayed. See [Errors](sharinpix-mobile-app-checklist-with-form-features.md#errors) section.
* If you are using the [SharinPix Mobile Launcher](../lightning-web-component/sharinpix-mobile-launcher.md), add the **checklist\_ref** parameter in the **Custom parameters** of the Lightning component.
{% endhint %}

### Mobile App Global Configuration

In your Org's [mobile app global configuration](sharinpix-mobile-app-global-configuration.md):

Add a "**checklists"** key. The value for this key is an object. The keys for this object are the values that can be used for the **checklist\_ref** parameter in deeplinks or universal links. Any number of keys can be added.

#### Example:

```json
{
  "checklists": {
    "building-inspection": { ... },
    "field-equipments": { ... }
  }
}
```

The value for any key in the **checklists** object is another **object** with the following entries:

* **tags** : An array of strings where each string represents a tag. A **minimum count** of images can be specified for each tag by adding **"\*\*\<MIN\_COUNT>**" at the end of the tag name. If no minimum count is specified, the default will be **one**.\
  Example:\
  <mark style="color:red;">`"tags": ["Fire Extinguisher", "Exit Doors**5", "Electrical Setup**0"]`</mark> Here three tags are specified. The tag **"Fire Extinguisher"** will have a minimum count of **one** since it was not specified, **"Exit Doors"** will have a minimum count of **five,** and **"Electrical Setup"** will have a minimum count of **zero** therefore optional.
* **form:** An array of Form-Field objects.

{% hint style="warning" %}
Note:

* The **tags** key is **optional** if the [**checklist**](sharinpix-mobile-app-deeplink-syntax.md#checklist) parameter is used to launch SharinPix mobile app.
* The **minimum count** for a tag is the minimum number of images a user should take for that tag when filling the checklist. Failing to reach this count will trigger a **warning message** when submitting the checklist. However, the submission is **not blocked** and the user can confirm the submission. To **prevent** submission, the [enforce\_min\_count](sharinpix-mobile-app-deeplink-syntax.md#enforce_min_count) parameter can be used.
* The **form** key is **optional** and if omitted, the checklist will be equivalent to a [**normal checklist**](sharinpix-mobile-app-checklist.md) without form features and Checklist Result records on Salesforce are **not** **created** if the configured checklist have **no form fields** or no **form key**.
{% endhint %}

The **Form-Field** object has the following entries:

* **type** : The form field type. Available options are: **select** and **textarea**.
* **value** : The name of the form field.
* **optional** : Boolean indicating whether the field is optional (**not required**) or not.
* **options** : An array of strings where each string represents an option **if** the type is **select**.
* **default\_option** : A default **pre-selected** option **if** the type is **select**.
* **label** : The label for the form field

{% hint style="warning" %}
Note:

* The **optional** key can be omitted. When omitted, it is **equivalent** to setting **optional** to **false** <mark style="color:red;">`"optional": false`</mark>.
* Failing to fill any **required** fields will trigger a **warning message** when submitting the checklist. However the submission is **not blocked** and the user can confirm the submission. The **status** of the checklist will also be **incomplete**. See the [SharinPix Checklist Result Object](sharinpix-mobile-app-checklist-with-form-features.md#sharinpix-checklist-result-object) section below for more information on the checklist **status**.
{% endhint %}

#### Example:

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
      ],
      "form": [
        {
          "type": "select",
          "value": "status",
          "optional": false, 
          "options": [
            "OK",
            "KO",
            "NA"
          ],
          "default_option": "",
          "label": "Status"
        },
        {
            "type": "textarea",
            "value": "comments",
            "label": "Comments"
        }
      ]
    }
  }
}
```

In this example, only **one** checklist is defined. The **building-inspection** checklist has **five** tags namely, **Fire Extinguisher** with a default minimum count of **one** , **Exit Doors** with a minimum count of **five**, **Electrical Setup** with a minimum count of **zero** , **Electrical Panel** with a minimum count of **ten** and **Charging Station** with a default minimum count of **one**. The checklist has **two** form-fields. The first one is of type **select**. The name of the field is **status** and it is **required** as **optional** is **false**. The **status** field has **three** options namely **OK**, **KO**, **NA** and it does not have a default option. The label is **Status**. The second one is of type **textarea.** The name of the field is **comments** and the label is **Comments**. The field is **required** by default as the **optional** key is omitted.

### Additional Configurations

When a checklist is submitted without the minimum number of images specified for any tag, or without filling any required form-fields, a **warning message** is shown to the user. These messages can be configured on the Org's mobile app global config.

Two messages can be configured:

* **incomplete\_checklist\_alert\_text:** This is the message shown when there are less images than the minimum count specified.
* **incomplete\_form\_alert\_text:** This is the message shown when there are unfilled required fields.

{% hint style="success" %}
Tip:

Two placeholders can be used with these messages namely the "**\<COUNT>**" placeholder and the "**< LIST\_INCOMPLETE>**" placeholder.

* The "**< COUNT>**" placeholder will be replaced by **either** the **number of tags** with less images than the **minimum count** specified for the tag(when used in **incomplete\_checklist\_alert\_text**) **or** the **number of tags** with **unfilled** **required** **form-fields**(when used in **incomplete\_form\_alert\_text**) depending in which message it is used.
* The "**\<LIST\_INCOMPLETE>**" placeholder will be replaced by a list of tags which has **either** less images than the minimum count specified for the tag **or** an unfilled required field for the tag.
{% endhint %}

Example:

```json
{
  "incomplete_checklist_alert_text": "The following <COUNT> items are incomplete. <LIST_INCOMPLETE>",
  "incomplete_form_alert_text": "<COUNT> form fields have not been filled.",
  "checklists": {
    "building-inspection": {
      "tags": [
        "Fire Extinguisher",
        "Exit Doors**5",
        "Electrical Setup**0",
        "Electrical Panel**10",
        "Charging Station"
      ],
      "form": [
        {
          "type": "select",
          "value": "status",
          "optional": false,
          "options": [
            "OK",
            "KO",
            "NA"
          ],
          "default_option": ""
          "label": "Status"
        },
        {
          "type": "textarea",
          "value": "comments",
          "label": "Comments"
        }
      ]
    }
  }
}
```

{% hint style="info" %}
Info:\
**Default** warning messages will be used if these messages are not present on the Org's mobile app global config.
{% endhint %}

### Additional Parameters

Additional parameters can be used to access **additional features** or modify some **default behaviors** when using a checklist with form features. The parameters that can used are:

* [**enforce\_min\_count**](sharinpix-mobile-app-deeplink-syntax.md#enforce_min_count),
* [**checklist\_order**](sharinpix-mobile-app-deeplink-syntax.md#checklist_order),
* [**checklist\_reload**](sharinpix-mobile-app-deeplink-syntax.md#checklist_reload),
* [**await\_upload**](sharinpix-mobile-app-deeplink-syntax.md#await_upload)
* [**checklist**](sharinpix-mobile-app-deeplink-syntax.md#checklist)
* [**form\_\<form-field-name>**](sharinpix-mobile-app-deeplink-syntax.md#form_-lt-form-field-name-gt)

## SharinPix Checklist Result Object

When a user submits a checklist with form features, a record is either **created** or **modified** in the **SharinPix Checklist Result** object on Salesforce.

A record is **created** for every **unique** combination of the **token** and **checklist\_ref** used. Otherwise the record is just updated.

Example:

<mark style="color:red;">`sharinpix://upload?token=A&checklist_ref=building-inspection`</mark>

When using the above deeplink for the first time, submission of this checklist will result in the **creation** of a **SharinPix Checklist Result** record. If the **same link** is used and the checklist is submitted **again** , the record will only be **updated**. However if a different **token** or **checklist\_ref** is used, a **new** record will be **created**.

Among many others, the **Payload (JSON)** and **Images Mapping (JSON)** are two fields of the **SharinPix Checklist Result** object.

### Payload (JSON) field

The **Payload (JSON)** field is a JSON representation of the checklist submitted. The JSON contains an **items** entry which is an **array** of **objects**. Each object in the array represents a **checklist item**. There is an item for each tag in the checklist i.e if there are **five** tags, there will be **five** items.

Each **item** object contains the following entries:

* **name** : The name of the tag.
* **image\_count** : The count of images taken for this tag.
* **image\_minimum\_count** : The minimum count of images specified for this tag.
* **form\_data** : An object mapping form-field names to their submitted values.

The JSON also contains other entries such as:

* **status** : The overall status of the checklist. **complete** if the number of images taken for each tag is **greater or equal to** the minimum count specified for the tag and all required fields are filled. **incomplete** otherwise
* **image\_count** : The total number of images taken
* **items\_filled** : The number of items where the item's **image\_count** is **greater or equal to** it's **image\_minimum\_count**
* **items\_total** : The total number of items

Example:

```json
{
  .....
  "status": "incomplete",
  "image_count": 1,
  "items_filled": 0,
  "items_total": 1,
  "items": [
    {
      "name": "Fire Extinguisher",
      "image_count": 1,
      "image_minimum_count": 2,
      "form_data": {
        "status": "OK",
        "comments": "All good"
      }
    }
  ]
  .....
}
```

In this example, the checklist has a **single** item for the **Fire Extinguisher** tag. A minimum count of **two** images was specified for the tag. A **single** image was taken for the tag and the **status** form-field value was set to "**OK"**. The **comments** form-field value was set to "**All good**".The overall **status** of the checklist is **incomplete** since a **single** image was taken while the minimum count specified was **two** for the tag.

{% hint style="warning" %}
Note:

* The **Payload (JSON)** contains other entries **not** mentioned and shown in this example.
* Checklist Result records are **not** **created** if the configured checklist have **no form fields** or no **form key**.
{% endhint %}

### Images Mapping (JSON) field

The **Images Mapping (JSON)** field is a JSON that maps **Checklist Result Item names** to their **image IDs**.

Example:

```json
 {
  "Fire Extinguisher": ["a2fafcb6-f4c5-48b7-948e-29985db3fb36"]
 }
```

In this example, the checklist has a single **Fire Extinguisher** tag and a single image was for this tag.

Below is a screenshot of how it looks on Saleforce:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist with Form Features - 2.png" alt=""><figcaption></figcaption></figure>

## Demo

Now that you know how to configure a **Checklist with Form Features**, let's see how it looks like on the SharinPix mobile app.

For this demo, we are using the example configuration from the [Configuration for the Checklist with Form Features](sharinpix-mobile-app-checklist-with-form-features.md#mobile-app-global-configuration) section in a SharinPix deeplink: <mark style="color:red;">`sharinpix://upload?token=...&checklist_ref=building-inspection`</mark>

Here is the result on the SharinPix mobile app after opening the deeplink:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist with Form Features - 3.png" alt=""><figcaption></figcaption></figure>

From here, you can upload images and fill the form-fields.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist with Form Features - 4.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Info:

* The **number of images** **taken** and **minimum count** specified is indicated next to dropdown. It's colour will change from **orange** to **green** when the number of images taken is **greater or equal to** the minimum count specified.
* The button in the **top right** is for **re-ordering** the checklist items based on its completeness. An item is considered complete when the number of images taken reached the **minimum count AND** when required form-fields are **filled**. A completed item will move down on re-ordering and incomplete ones will remain at the top.
* The **badge** on the button indicates the **number of tags** that will be **re-ordered** when it is clicked. The button is **only visible** if [**checklist\_order**](sharinpix-mobile-app-deeplink-syntax.md#checklist_order) is set to **auto** and [checklist\_reload](sharinpix-mobile-app-deeplink-syntax.md#checklist_reload) is **not** set to **auto**.
{% endhint %}

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist with Form Features - 5.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist with Form Features - 6.png" alt=""><figcaption></figcaption></figure>

Warning message displayed when user tries to submit an **incomplete** checklist. User can confirm submission by clicking **Continue**.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist with Form Features - 7.png" alt=""><figcaption></figcaption></figure>

When the checklist is **completed**, the "**Done"** button becomes **green**.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist with Form Features - 8.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Tips:

Since this feature is relatively new, we recommend:

* Using a **maximum** of two form fields per checklist
* Avoid changing the list of **tags** for a checklist if it has already been used and submitted.

The checklist page will always show all the images with the same tag from the **same Job** even from previous sessions. This can affect the image count for a tag in the checklist result submitted. For example if a normal checklist was used before then a checklist with form features is used with some common tags.
{% endhint %}

## Errors

**Checklist reference not found**

This error occurs when the **checklist\_ref** value specified in the deeplink or universal link is not defined on the Org's mobile app global configuration.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist with Form Features - 9.png" alt=""><figcaption></figcaption></figure>

**Bad checklist configuration**

This error occurs when the **checklist\_ref** being used is not properly configured on the Org's mobile app global configuration.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Checklist with Form Features - 10.png" alt=""><figcaption></figcaption></figure>
