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

# SharinPix Map Use Cases

This article aims at demonstrating the common use cases of the [SharinPix Map](../lightning-web-component/sharinpix-map.md) component along with the corresponding configuration and examples.

In the following sections, you will learn:

* [How to get started with the SharinPix Map configuration on an object](sharinpix-map-use-cases.md#getting-started-with-the-sharinpix-map-configuration)
* [How to use the SharinPix Map component on parent and child objects](sharinpix-map-use-cases.md#using-the-sharinpix-map-on-parent-and-child-objects)

## Getting started with the SharinPix Map configuration

This section demonstrates how to get started with the configuration of the SharinPix Map component on the Account object. Here we will be using the three modes available in the component to configure it as follows:

1. [Load the map data into the component using the Geocode mode](sharinpix-map-use-cases.md#load-the-map-data-into-the-component-using-the-geocode-mode)
2. [Add polygons and markers to the map using the Edit mode](sharinpix-map-use-cases.md#add-polygons-and-markers-to-the-map-using-the-edit-mode)
3. [Display the result in the ReadOnly mode](sharinpix-map-use-cases.md#display-the-result-in-the-readonly-mode)

### Load the map data into the component using the Geocode mode

The **Geocode** mode is usually used to load your map data onto the component. To load the map, you can either make use of pre-defined map data available in a Salesforce field as explained in the following steps or by entering the required address on the map component itself.

To configure the component on a Salesforce object using the **Geocode** mode, follow the steps below:

* Using the object's Lightning Page Builder, drag and drop the SharinPix Map component onto the desired region.
* Next, configure the component as follows:

| Parameters                            | Description                                                                                                                                                                                                                                                                                | Is the Parameter Mandatory or Optional                                                                                        |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| <p>Mode<br></p>                       | <p>Choose <strong>Geocode</strong>.<br></p>                                                                                                                                                                                                                                                | <mark style="color:$danger;">Mandatory</mark>                                                                                 |
| Map Type                              | <p>The type of map to be displayed. Options are:<br>"roadmap", "satellite", "hybrid", or "terrain".<br></p>                                                                                                                                                                                | Optional                                                                                                                      |
| <p>Record Id Field API Name<br></p>   | <p>Enter <strong>Id</strong> as the value. This value refers to the current record Id.<br></p>                                                                                                                                                                                             | <p><mark style="color:$danger;">Mandatory</mark><br></p>                                                                      |
| <p>Address Field API Name<br></p>     | <p>Enter the <strong>API name</strong> of the field storing the address to be used to open the map when no value is available in the field used in the parameter, <strong>Map Data Field API Name</strong>, described just below.<br></p>                                                  | <p>Optional<br>(required only when no value has been provided for the parameter <strong>Map Data Field API Name)</strong></p> |
| <p>Map Data Field API Name<br></p>    | <p>The <strong>API name</strong> of the field in which the Google Map data will be stored. If map data are available in the field, the map will open to the same data stored. In this case, the value stored in the field <strong>Address Field API Name</strong> will be ignored.<br></p> | <p><mark style="color:$danger;">Mandatory</mark><br></p>                                                                      |
| <p>Default Zoom Level<br></p>         | The zoom level.                                                                                                                                                                                                                                                                            | <p>Optional<br></p>                                                                                                           |
| <p>45° tilt on Satellite view<br></p> | <p>To enable/disable the option to tilt the map at 45 degrees when switching to the Satellite view.<br></p>                                                                                                                                                                                | <p>Optional<br></p>                                                                                                           |
| <p>Height<br></p>                     | <p>The height of the Map component.<br></p>                                                                                                                                                                                                                                                | <p>Optional<br></p>                                                                                                           |

* Click the button **Save** when done.
* Then go onto a page record to check the rendering.

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.06.01-10_05_12 (1) (2).png>)

{% hint style="success" %}
**Tips:**

* If no data is available in both the **Map Data Field API Name** and **Address Field API Name** parameters, you can still enter your required address on the component itself.
* The changes applied to the map are automatically saved under the **Geocode** mode.
{% endhint %}

### Add polygons and markers to the map using the Edit mode

Now that the map data has been loaded onto the component, you can proceed with the addition of markers and polygons using the **Edit** mode.

To do so, follow the steps below:

* On the object's Lightning Page Builder, change the SharinPix Map component mode's from **Geocode** to **Edit**
* Next, configure the component as follows:

<table data-header-hidden><thead><tr><th></th><th width="249"></th><th></th></tr></thead><tbody><tr><td>Parameters</td><td>Description</td><td>Is the Parameter Mandatory or Optional<br></td></tr><tr><td>Mode<br></td><td>Choose <strong>Edit</strong>.<br></td><td><mark style="color:$danger;">Mandatory</mark><br></td></tr><tr><td>Map Type<br></td><td>The type of map to be displayed. Options are:<br>"roadmap", "satellite", "hybrid", or "terrain".<br></td><td>Optional<br></td></tr><tr><td>Record Id Field API Name<br></td><td>Enter <strong>Id</strong> as the value. This value refers to the current record Id.<br></td><td><mark style="color:$danger;">Mandatory</mark><br></td></tr><tr><td>Address Field API Name<br></td><td>Enter the API name of the field storing the address to be used to open the map when no value is available in the field used in the parameter, <strong>Map Data Field API Name</strong>, described just below.<br></td><td><p>Optional</p><p>(required only when no value has been provided for the parameter Map Data Field API Name)</p><p><br></p></td></tr><tr><td>Map Data Field API Name<br></td><td>The API name of the field in which the Google Map data will be stored. If map data are available in the field, the map will open to the same data stored. In this case, the value stored in the field <strong>Address Field API Name</strong> will be ignored.<br></td><td><mark style="color:$danger;">Mandatory</mark><br></td></tr><tr><td>Edit Record Id Field API Name<br></td><td>Enter <strong>Id</strong> as the value. This value refers to the current record Id.<br></td><td><mark style="color:$danger;">Mandatory</mark><br></td></tr><tr><td>Default Zoom Level<br></td><td>The zoom level.<br></td><td>Optional<br></td></tr><tr><td>45° tilt on Satellite view<br></td><td>To enable/disable the option to tilt the map at 45 degrees when switching to the Satellite view.<br></td><td>Optional<br></td></tr><tr><td>Height<br></td><td>The height of the Map component.<br></td><td>Optional<br></td></tr><tr><td><mark style="color:$danger;"><strong>Note:</strong></mark> <em><mark style="color:$danger;">The above steps correspond to the basic map configuration under the Edit mode. To use polygons and markers on the map, you will need to configure the parameters below.</mark></em></td><td></td><td></td></tr><tr><td>Polygon Label Field API Name<br></td><td>The field <strong>API name</strong> which contains label for the current polygon.<br></td><td><mark style="color:$danger;">Mandatory</mark><br>(Parameter must be populated and specified field should contain a value in order to draw polygons)<br></td></tr><tr><td>Polygon Area Field API Name<br></td><td>The field <strong>API name</strong> which will store the total area of the polygon(s) drawn. This field should be populated if polygons are added on the map.<br></td><td><mark style="color:$danger;">Mandatory</mark><br>(Parameter must be populated in order to save drawn polygons)<br></td></tr><tr><td>Polygon Options<br></td><td>Enter the polygon options in JSON object format. An example is given below:<br><br><mark style="color:$danger;"><code>{ "strokeColor": "Green", "strokeOpacity": 0.8, "strokeWeight": 2, "fillColor": "Yellow", "fillOpacity": 0.35, "labelColor": "Red" }</code></mark><br></td><td>Optional<br></td></tr><tr><td>Marker Label Field API Name<br></td><td>The field <strong>API name</strong> containing the current marker's label. To view the marker's label, simply hover over a marker.<br></td><td><mark style="color:$danger;">Mandatory</mark><br>(Parameter must be populated and specified field should contain a value in order to add markers)<br></td></tr><tr><td>Marker Size<br></td><td>The size of markers.<br></td><td>Optional<br></td></tr><tr><td>Marker Options</td><td><p>Enter the marker options in JSON object format. An example is given below:<br><br><mark style="color:$danger;"><code>{ "defaultColor": "#ff4646", "size": 5, "colorFieldApiName": "Color__c", "showLabel": true }</code></mark></p><p><br></p></td><td>Optional</td></tr></tbody></table>

* Click the button **Save** when done.
* Then go onto a page record to check the rendering. The example below depicts a SharinPix Map component in **Edit** mode with polygons and markers applied.

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.06.01-10_07_20 (1) (2).png>)

### Display the result in the ReadOnly mode

The **ReadOnly** mode allows users to view the component. No modifications are allowed under this mode.

In this section, we will demonstrate how to configure the map component under the **ReadOnly** mode:

* Using the object's Lightning Page Builder, change the SharinPix Map component mode's from **Edit** to **ReadOnly**.
* Next, configure the component as follows:

| <p>Parameters<br></p>                 | Description                                                                                                                                                                                                                                                                                       | <p>Is the Parameter Mandatory or Optional<br></p>                                                                          |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| <p>Mode<br></p>                       | <p>Choose <strong>ReadOnly</strong>.<br></p>                                                                                                                                                                                                                                                      | <p><mark style="color:$danger;">Mandatory</mark><br></p>                                                                   |
| <p>Record Id Field API Name<br></p>   | <p>Enter <strong>Id</strong> as the value. This value refers to the current record Id.<br></p>                                                                                                                                                                                                    | <p><mark style="color:$danger;">Mandatory</mark><br></p>                                                                   |
| <p>Map Type<br></p>                   | <p>The type of map to be displayed. Options are:<br>"roadmap", "satellite", "hybrid", or "terrain".<br></p>                                                                                                                                                                                       | <p>Optional<br></p>                                                                                                        |
| <p>Address Field API Name<br></p>     | <p>Enter the <strong>API name</strong> of the field storing the address to be used to open the map when no value is available in the field used in the parameter, <strong>Map Data Field API Name</strong>, described just below.<br></p>                                                         | <p>Optional</p><p>(required only when no value has been provided for the parameter Map Data Field API Name)</p><p><br></p> |
| <p>Map Data Field API Name<br></p>    | <p>The <strong>API name</strong> of the field in which the Google Map data will be stored. If map data are available in the field, the map will open to the same data stored. In this case, the value stored in the field <strong>Address Field API Name</strong> will be ignored.</p><p><br></p> | <p><mark style="color:$danger;">Mandatory</mark><br></p>                                                                   |
| <p>Default Zoom Level<br></p>         | The zoom level.                                                                                                                                                                                                                                                                                   | <p>Optional<br></p>                                                                                                        |
| <p>45° tilt on Satellite view<br></p> | To enable/disable the option to tilt the map at 45 degrees when switching to the Satellite view.                                                                                                                                                                                                  | <p>Optional<br></p>                                                                                                        |
| <p>Height<br></p>                     | <p>The height of the Map component.<br></p>                                                                                                                                                                                                                                                       | Optional                                                                                                                   |

* Click the button **Save** when done.
* Then go onto a page record to check the rendering. The example below depicts the map component in the **ReadOnly** mode. Here users can visualise the polygon and marker applied previously under the **Edit** mode.

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.06.01-10_18_41 (1) (2).png>)

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.06.01-10_21_21 (1) (2).png>)

## Using the SharinPix Map on parent and child objects

Modifications made to the SharinPix Map components of a child record can be reflected on the parent record.

This section demonstrates how to configure the map component on the Opportunity (child object) and Account (parent object) objects so that modifications made to the Opportunity's map are reflected on the Account's map. For this configuration, we will:

1. Load the map on the parent object with the desired map data using the **ReadOnly** mode.
2. Use the child's map to add polygons and markers using the **Edit** mode.

To do so, follow the steps below:

* Using the **Account** 's Lightning Page Builder, drag and drop the SharinPix Map component onto the desired region.
* Next, configure the component using the **ReadOnly** mode as explained [here](sharinpix-map-use-cases.md#display-the-result-in-the-readonly-mode). **Note:** _If the field used in Map Data Field API Name has no value, use the **Geocode** mode to load the map._
* Once the component added to the **Account** record page, go ahead and add the SharinPix Map component onto the **Opportunity** page record (child record) as follows:

| <p>Parameters<br></p>                    | <p>Description<br></p>                                                                                                                                                                                                                                                                                                                                                                                                                       | <p>Is the Parameter Mandatory or Optional<br></p>                                                                                                              |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>Mode<br></p>                          | <p>Choose <strong>Edit</strong>.<br></p>                                                                                                                                                                                                                                                                                                                                                                                                     | <p><mark style="color:$danger;">Mandatory</mark><br></p>                                                                                                       |
| <p>Map Type<br></p>                      | <p>The type of map to be displayed. Options are:<br>"roadmap", "satellite", "hybrid", or "terrain".<br></p>                                                                                                                                                                                                                                                                                                                                  | <p>Optional<br></p>                                                                                                                                            |
| <p>Record Id Field API Name<br></p>      | Enter the lookup field API name. In our case the value to be entered is **AccountId**.                                                                                                                                                                                                                                                                                                                                                       | <p><mark style="color:$danger;">Mandatory</mark><br></p>                                                                                                       |
| <p>Map Data Field API Name<br></p>       | <p>Enter the <strong>same</strong> <strong>API name</strong> of the field in which the Google Map data are stored on the <strong>Account</strong> (that is on the parent) object.<br>For example, if the value <strong>Map_data__c</strong> was entered in the <strong>Map Data Field API Name</strong> parameter of the <strong>parent's</strong> map component, the same value, <strong>Map_data__c</strong>, should be inserted here.</p> | <p><mark style="color:$danger;">Mandatory</mark><br></p>                                                                                                       |
| <p>Edit Record Id Field API Name<br></p> | <p>Enter <strong>Id</strong> as the value. This value refers to the current record Id (that is the child record Id).<br></p>                                                                                                                                                                                                                                                                                                                 | <p><mark style="color:$danger;">Mandatory</mark><br></p>                                                                                                       |
| <p>Polygon Label Field API Name<br></p>  | <p>The field API name which contains label for the current polygon.<br></p>                                                                                                                                                                                                                                                                                                                                                                  | <p><mark style="color:$danger;">Mandatory</mark><br>(Parameter must be populated and specified field should contain a value in order to draw polygons)<br></p> |
| <p>Polygon Area Field API Name<br></p>   | <p>The field API name which will store the total area of the polygon(s) drawn. This field should be populated if polygons are added to the map.<br></p>                                                                                                                                                                                                                                                                                      | <p><mark style="color:$danger;">Mandatory</mark><br></p>                                                                                                       |
| <p>Polygon Options<br></p>               | <p>Enter the polygon options in JSON object format. An example is given below:<br><mark style="color:$danger;"><code>{ "strokeColor": "Green", "strokeOpacity": 0.8, "strokeWeight": 2, "fillColor": "Yellow", "fillOpacity": 0.35, "labelColor": "Red" }</code></mark><br></p>                                                                                                                                                              | <p>Optional<br></p>                                                                                                                                            |
| <p>Marker Label Field API Name<br></p>   | <p>The field API name containing the current marker's label. To view the marker's label, simply hover over a marker.<br></p>                                                                                                                                                                                                                                                                                                                 | <p><mark style="color:$danger;">Mandatory</mark><br>(Parameter must be populated and specified field should contain a value in order to add markers)<br></p>   |
| <p>Marker Size<br></p>                   | The size of markers.                                                                                                                                                                                                                                                                                                                                                                                                                         | <p>Optional<br></p>                                                                                                                                            |
| Marker Options                           | <p>Enter the marker options in JSON object format. An example is given below:<br><br><mark style="color:$danger;"><code>{ "defaultColor": "#ff4646", "size": 5, "colorFieldApiName": "Color__c", "showLabel": true }</code></mark><br></p>                                                                                                                                                                                                   | <p>Optional<br></p>                                                                                                                                            |
| Show Current Record Overlay only         | Enable this option to display/hide overlays for the current record. If you want to display all overlays, keep this option unchecked.                                                                                                                                                                                                                                                                                                         | <p>Optional<br></p>                                                                                                                                            |
| Show Overlay Type                        | <p>The type of overlay to be displayed, that is either polygons or markers only or both. The values available for this field are <strong>polygon</strong> and <strong>marker</strong>.<br></p>                                                                                                                                                                                                                                               | <p>Optional<br></p>                                                                                                                                            |
| <p>Default Zoom Level<br></p>            | <p>The zoom level.<br></p>                                                                                                                                                                                                                                                                                                                                                                                                                   | <p>Optional<br></p>                                                                                                                                            |
| <p>45° tilt on Satellite view<br></p>    | <p>To enable/disable the option to tilt the map at 45 degrees when switching to the Satellite view.<br></p>                                                                                                                                                                                                                                                                                                                                  | <p>Optional<br></p>                                                                                                                                            |
| <p>Height<br></p>                        | <p>The height of the Map component.<br></p>                                                                                                                                                                                                                                                                                                                                                                                                  | Optional                                                                                                                                                       |

* Click the button **Save** when done.

You can now draw polygons and add markers on the Opportunity's map component. These modifications will be reflected on the Account's map component.

{% hint style="success" %}
**Useful Tips:**

* Polygons and markers can only be added under the **Edit** mode.
* The map component can be added in parent and child records.
* In some cases, users might want to modify the map data and add polygons/markers. To do so, you can add two map components onto your page layout, one in **Geocode** mode to allow map data modification and another one in **Edit** mode to allow addition of polygons and markers.
{% endhint %}
