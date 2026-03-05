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

# SharinPix Map To Album

{% hint style="warning" %}
**Note:**

* This component is dependent on the SharinPix Map component.
* Click [here](sharinpix-map.md) for more information on the SharinPix Map component.
{% endhint %}

The **SharinPix Map To Album** component extracts a Map as an image from the SharinPix Map component and saves it in a specific SharinPix album.

<figure><img src="../.gitbook/assets/image (11) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used on:

* On Page Builder
* On Desktop
* In Flows (but not in Field Service Mobile Flow)
* In Salesforce Community
* In your own Lightning Component development
{% endhint %}

## Getting Started

To use the SharinPix Map To Album component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

![](<../.gitbook/assets/ssMapToAlbum (1) (1) (1).png>)

## Lightning Component Parameters

![](<../.gitbook/assets/map_album (1) (1) (1).png>)

* **Generate Map Button Label:** Used to specify the button's label. The default value is **Export Map to Album**.
* **Map Record Id Field API Name:** API name of the field containing the record ID of the object from which the map data will be retrieved. Leave blank to use the current object record's ID.
* **Map Data Field API Name:** Map Data Field API name used to store Google Maps data. The map will be generated with data saved in this field if it is available. The value entered in this field should be the same as the SharinPix Map's Map Data Field API Name.
* **Map Type:** The type of map to be exported (roadmap, satellite, hybrid, terrain).
* **Album ID:** Used to specify the album ID to which images will be saved. To use the current record ID, leave this field blank.
* **Polygon Options:** Options to apply to polygon objects. Value should be in JSON object format. Leave blank for none. Example:

<mark style="color:red;">`{ "strokeColor": "Green", "strokeOpacity": 0.8, "strokeWeight": 2, "fillColor": "Yellow", "fillOpacity": 0.35, "labelColor": "Red", "fontSize": "20px" }`</mark>

* **Marker Options:** The marker's appearance. The value entered in this field should be in a JSON format as demonstrated in the example below:\
  <mark style="color:red;">`{ "size": 5, "showLabel": true, "defaultColor": "#ff4646" }`</mark>
  * **Note:** The marker label is configured only in the **Marker Options (JSON)** parameter. Here, the actual marker label name is retrieved from the map data.
* **Tag:** The tag to be applied to all images generated from the SharinPix Map to Album component. For no tag application, leave this field blank.
* **Component ID:** Component ID to be matched by SharinPix components on the page. This is any text that will be common between this component and the **SharinPix Album** component. It allows for matching components to communicate in case some components need to be repeated on the same record page. Example: Set 'sharinpix-1' as Target Component ID here and also on **SharinPix Album** component's Component ID field.

{% hint style="warning" %}
**Note:**

* For a map image to be inserted in the **SharinPix Album** automatically, you need to make sure that the **ComponentId** of this component and that of **SharinPix Album** have the same value.
* For the [SharinPix Image Sync](../image-sync/what-is-sharinpix-image-sync.md) feature to be activated on the destination album when the image is exported from the Map to Album component, you should specify a value for the **Component ID** parameter on the **Map to Album** component and use the same value for the **SharinPix Album's Component ID** parameter.
{% endhint %}

## Demo

The picture below shows a map in the SharinPix Map component.

![](<../.gitbook/assets/Screenshot_from_2021-04-16_15-35-52 (1) (1) (1).png>)

The picture below shows the target album on an Account record **before** using the SharinPix Map To Album component:

![](<../.gitbook/assets/Screenshot_from_2021-04-16_15-44-24 (1) (1) (1).png>)

To export an image from a map to the target album, click on the button **Export Map to Album**.

The picture below shows the result in the target album **after** using the SharinPix Map To Album component:

![](<../.gitbook/assets/Screenshot_from_2021-04-16_15-40-23 (1) (1) (1).png>)
