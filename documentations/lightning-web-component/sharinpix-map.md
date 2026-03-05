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

# SharinPix Map

{% hint style="danger" %}
This component is only available in the SharinPix **Enterprise license plan**. For more info, please contact [support@sharinpix.com](mailto:support@sharinpix.com)
{% endhint %}

{% hint style="info" %}
The **SharinPix Map** component permits to display, modify the position/zoom level and save the Google Maps' display configuration on a record. Additionally, this component allows users to annotate the map by drawing polygons on it.
{% endhint %}

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2020.06.03-14_13_25 (1) (1) (1).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
* On Mobile
* In Flows (but not in Field Service Mobile Flow)
* In Salesforce Community
* In your own Lightning Component development
{% endhint %}

## Getting Started

In order to use the SharinPix Map component, you will first need a **Google API Key**.

Once your Google API key is ready, you will have to set the key in SharinPix.

To do so:

* Go to the **SharinPix Settings** tab
* Then enter your Google API key inside the **Google API key** text box

![](<../.gitbook/assets/image (5) (3).png>)

* Click **Save** when done

To use the SharinPix Map component on record pages, simply drag and drop the component from the Lightning App Builder onto your page layout.

![](<../.gitbook/assets/image (1) (1) (1) (1).png>)

## Lightning Component Parameters

![](<../.gitbook/assets/image (2) (1) (1).png>)

![](<../.gitbook/assets/image (3) (1) (1).png>)

* **Mode:** The mode of the Map component. The values available are **ReadOnly**, **Geocode**, and **Edit**.
  * The **ReadOnly** mode allows users to display the map. The map cannot be edited using this option. However, it can be explored by zooming in/out or moving around.
  * The **Geocode** mode allows users to edit the map configuration. The modifications made while using this mode are saved automatically. It includes position, zoom and all other display mode
  * The **Edit** mode allows users to annotate the map by drawing polygons on it. When using this mode, values in fields **Edit Record Id Field API Name** and **Polygon Label Field API Name** are required to specify which polygons the user is editing/creating.
* **Map Type:** The type of map to be displayed.
* **Record Id Field API Name:** The record Id field API name of the parent object. The default value is **Id**.
* **Address Field API Name:** The API name of the field containing the **address** to be used to open the map when the **Map Data Field** value is not yet available. It is ignored otherwise. Note: _For the address to be taken into account and applied to the map, the map should be set to the **Geocode** mode and the **Map Data Field API Name** should be empty._
* **Map Data Field API Name:** The API name of the field in which the Google Maps data will be stored. If map data is available in the field, the map will open to the same data stored. In this case, the value stored in the field **Address Field API Name** will be ignored.
* **Edit Record Id Field API Name:** The record Id field API name of the child object. This becomes handy when using different records (Buildings as an example), each having its own polygon. This parameter is only used when in **Edit** mode.
* **Polygon Label Field API Name:** The field API name which contains label for the current polygon. This parameter is only used when in **Edit** mode.
* **Polygon Area Field API Name:** The field API name which will store the total area of the polygon(s) drawn. Note:
  * This field should be populated if polygons are added on the map
  * The area stored is computed in square meters
* **Polygon Options:** The polygon's appearance. The value entered in this field should be in a JSON format as demonstrated in the example below:\
  `{ "strokeColor": "Green", "strokeOpacity": 0.8, "strokeWeight": 2, "fillColor": "Yellow", "fillOpacity": 0.35, "labelColor": "Red", "fontSize": "14px" }`

{% hint style="warning" %}
**Note:**

* We can include the **badgeOptions** within the JSON structure, which makes polygon labels stand out more on the SharinPix map. The badge size is adjusted according to the font size you set in the JSON. An example demonstrating the use of the 'badgeOptions' feature within the JSON is provided below:\
  `{ "strokeColor": "Green", "strokeOpacity": 0.8, "strokeWeight": 2, "fillColor": "Yellow", "fillOpacity": 0.35, "labelColor": "Red", "fontSize": "14px", "badgeOptions": {"color":"blue"} }`
* Using labels longer than 4 characters for the badge option are not advisable.
{% endhint %}

* **Marker Label Field API Name:** The field API name containing the current marker's label. To view the marker's label, simply hover over a marker.
* **Marker Size:** The size of markers. The default value is 'Small'.
* **Marker Options:** The marker's appearance. The value entered in this field should be in a JSON format as demonstrated in the example below:\
  `{ "defaultColor": "#ff4646", "size": 5, "colorFieldApiName": "Color__c", "showLabel": true }`\
  **Note:** When the **size** key is added the value specified in the JSON, the **Marker Size** parameter is not taken into consideration.
* **Show Current Record Overlay only:** Option to display/hide overlays for the current record. If you want to display all overlays, keep this option unchecked.
* **Show Overlay Type:** The type of overlay to be displayed, that is either polygons or markers only or both. The values available for this field are **polygon** and **marker**.
  * If you want to display only polygons, enter **polygon** as value for the field
  * If you want to display only markers, enter **marker**
  * To display both polygon and marker overlays, enter **polygon, marker**

Please note that under the **Edit** mode, all overlays are displayed by default. Therefore, the value entered in the field **Show Overlay Type** will be ignored.

* **Default Zoom Level:** The zoom level. The values available range from 1 to 20. It is only used at the first load and ignored when Map Data are saved.
* **45° tilt on Satellite view:** Used to enable/disable the option to tilt the map at 45 degrees when switching to the Satellite view.
* **Height:** The height of the Map component.

{% hint style="warning" %}
**Note:**

* The fields **Read-only Mode** and **Label** are deprecated and should therefore be ignored.
* The Google Maps API provides map tiles at various zoom levels for different map type imagery. Most roadmap imagery is available from zoom levels 0 to 18, for example. Satellite imagery varies more widely as this imagery is not generated, but directly photographed.
{% endhint %}

{% hint style="success" %}
**Tip:**

For detailed steps on how to configure the SharinPix Map component under the **Geocode** , **Edit** or **ReadOnly** mode as well as how to use it Map on parent and child records, refer to the following article: [SharinPix Map Use Cases](../cookbook/sharinpix-map-use-cases.md)
{% endhint %}

## Demo

The image below depicts the SharinPix Map component on a record page:

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2020.06.03-13_47_56 (1) (1) (1).png>)

The image below shows polygons drawn on the SharinPix Map component:

![](<../.gitbook/assets/screenshot-sharinpixwinter19-dev-ed.lightning.force.com-2020.06.03-14_05_10 (1) (1) (1).png>)

The image below shows polygons drawn on the SharinPix Map component having the badge options:

![](<../.gitbook/assets/Screenshot from 2024-04-01 17-07-46 (1) (1) (1).png>)

## Google Maps Prerequisites

Prior to using the SharinPix Map component, you should ensure that you have your [Google Cloud Platform](https://cloud.google.com/) project already set up and that the following APIs have been activated:

* Geocoding API
* Maps JavaScript API
* Places API

If you have not created a project yet, you can do so by following the steps below:

* Log into [**Google Cloud Platform**](https://cloud.google.com/)
* Create a new project by entering the keywords **Create a Project** in the search bar
* Click on **Create a Project** and enter your project details:

![](<../.gitbook/assets/image (4) (1) (1).png>)

* Click on **Create** when done
* Next, open the newly-created project by using the down arrow located on the top left corner:

![](<../.gitbook/assets/image (5) (1) (1).png>)

* This action will open a modal listing all your projects. Select the desired project and click on **OPEN**:

![](<../.gitbook/assets/image (6) (4).png>)

Once you are on the right project, set up your **API key** by following the steps below:

* From the left menu bar, click on **Credentials**
* Then click on **+ CREATE CREDENTIALS** followed by **API key**:

![](<../.gitbook/assets/image (7) (4).png>)

* Enter your API key and click on **CLOSE** when done:

![](<../.gitbook/assets/image (9) (3).png>)

{% hint style="warning" %}
**Note:**

The added API key should should correspond to the **Google API key** added on the **SharinPix Settings** page of your organization as described in the **Getting Started** section at the beginning of this article.
{% endhint %}

Once your project has been created, go ahead and activate the 3 required APIs.

To activate the APIs, follow the steps below:

* Using the search bar, look for **Geocoding API**. Then, click on **ENABLE** as demonstrated below:

![](<../.gitbook/assets/image (10) (4).png>)

* Repeat the above for the APIs **Maps JavaScript API** and **Places API:**

![](<../.gitbook/assets/image (13) (1) (1).png>)

![](<../.gitbook/assets/image (11) (5).png>)

## Google Maps Pricing

{% hint style="warning" %}
**Note:**

Please refer to the following link for more information about the Google Maps Pricing:

[https://cloud.google.com/maps-platform/pricing](https://cloud.google.com/maps-platform/pricing)
{% endhint %}

SharinPix makes use of the APIs listed below:

* **Maps JavaScript API** (under the **Maps** section)\
  An API call is made for the Maps JavaScript API each time a map is displayed/modified.

![](<../.gitbook/assets/image (14) (1) (1).png>)

* **Geocoding** and **Autocomplete** APIs (under the **Places** section)\
  API calls are made for these each time an address is typed in the Map in **Geocode** mode.

![](<../.gitbook/assets/image (15) (1) (1).png>)
