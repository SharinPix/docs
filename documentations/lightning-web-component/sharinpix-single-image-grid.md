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

# SharinPix Single Image Grid

The SharinPix Single Image Grid component can embed multiple [Single Image Grid](sharinpix-single-image.md) components to render a grid of SharinPix Single Image component.

![](<../.gitbook/assets/SingleGridBuilderRecord (1) (1) (1).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
* On Mobile
* In your own Lightning Component development
* On Community Builder
{% endhint %}

{% hint style="success" %}
**Tips:**

When using the Single Image Grid component in Salesforce Community, you will need to specify the record ID. To use the current record ID, the **Record Id** parameter should be filled with the expression, **{!recordId}**, as depicted in the image below.

The other parameters can be populated as described in the [Lightning Component Parameters](sharinpix-single-image-grid.md#lightning-component-parameters) section.
{% endhint %}

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed--sitestudio.na73.force.com-2021.01.09-12_39_39 (1) (1) (1).png>)

## Getting Started

To use the SharinPix Single Image Grid component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

![](<../.gitbook/assets/11 (1) (1) (2).png>)

## Lightning Component Parameters

![](<../.gitbook/assets/SingleGridBuilder (1) (1) (1).png>)

* **Number of Columns:** Used to specify the number of columns. Rows will be deduced from the number of tags entered.
* **Individual Component Height:** Used to specify the height in px for an individual Single Image component in the grid.
* **Tag Names (JSON):** Used to specify the tags for every Single Image component. First tag will be used on the top left component. The value entered should be **an array in JSON format**. Example: \["Top", "Right"]
* **Record Id:** Used to specify the Id of the record or album. To use current record Id, leave this field blank.
* **Placeholder URL:** Used to specify the URL of the image to use as placeholder. Leave blank to use default placeholder. This will override the value set by the SharinPix Permission if a permission ID is already defined.
* **Custom Permission ID or Name:** Used to specify the Name or ID of a SharinPix Permission record **of type Single Image**. This permission is mainly used to disable the delete option on the individual Single Image components.

{% hint style="success" %}
**Tip:**

To enable/disable the delete ability, you will need to create a SharinPix Permission record and set **Delete images** accordingly (that is, true or false) as shown in the example below. Then, add the name or ID of the SharinPix Permission record created to the **Custom Permission ID or Name** parameter.
{% endhint %}

![](<../.gitbook/assets/SingleGridPermission (1) (1) (1).png>)

* **Enable Image Sync:** Used to enable/disable Image Sync.
* **Enable Action:** Used to enable/disable Tag Action.
* **Crop After Upload:** Used to enable/disable the cropping option on the uploaded image. This will override the value set by the SharinPix Permission if a permission ID is already defined.
* **Auto Refresh View:** Used to enable/disable the option to reload the view. This is used with the Image Sync and Tag Action feature.
* **Custom Image Click Event:** Used to specify the custom event name to emit when clicking on image. The values available are **open-album** and **open-album-image**. On image click, **open-album** will open the complete album if selected, while **open-album-image** will open the image in full album view.
* **Custom Permission ID or Name for Album:** Id or Name of the SharinPix Permission record **of type Album** to be used for opening the images' album, if Custom Image Click Event is open-album or open-album-image.
* **Advanced Configuration (JSON):** Refers to an object in JSON format specifying layout and options for each Single Image component and corresponding album, if relevant. This value will override all other relevant parameters.

## Demo

The example below shows the SharinPix Single Image Grid component on a record page. Here, the number of columns has been set to 2 and the number of tags provided is 4.

![](<../.gitbook/assets/SingleGridBuilderrec (1) (1) (1).png>)

{% hint style="success" %}
**Tip:**

The number of rows is deduced from the number of tags entered. For instance, if the number of columns is set to 2 and the number of tags provided is 3 ( for example: \["first","second","third"] ), the component will be as follows:
{% endhint %}

![](<../.gitbook/assets/SingleGrid3Photo (1) (1) (1).png>)

### Demo: open-album

In this scenario, the **Custom Image Click Event** parameter has been set to **open-album**.

Here, when the user clicks on an image available on the Single Image Grid component, a SharinPix album will be displayed as shown in the example below:

![](<../.gitbook/assets/SingleGridAlbum (1) (1) (1).png>)

### Demo: open-album-image

In this scenario, the **Custom Image Click Event** parameter has been set to **open-album-image**.

Here, when the user clicks on an image available on the Single Image Grid component, the image will be opened in **Large View** mode as shown below:

![](<../.gitbook/assets/SingleGridFull (1) (1) (1).png>)

{% hint style="success" %}
**Tip:**

You can refer to the following link for more details on the features available for the Large View mode:

[Elements of the Large View](../features/user-interface/large-view.md#elements-of-the-large-view)
{% endhint %}

### Demo: Advanced Parameters (Developer-Oriented)

The Single Image Grid component permits you to use your own parameters for more control of the grid behaviour. Using your own parameters, you can set the number of rows and columns as well as enable the desired options for each cell, that is, each individual Single Image component.

The options available for the cells are:

* **recordId**
* **placeholderUrl**
* **tag**
* **enableImageSync**
* **enableAction**
* **enableCrop**
* **refreshView**
* **height:** Used to specify the height in px.
* **permissionId:** Used to specify the SharinPix permission of type Single Image. This is mainly used to enable or disable the delete option on the individual Single Image component.
* **style:** Used to modify the css. Specifying the style will override the default css of the individual Single Image component.

{% hint style="warning" %}
**Note:**

Make sure to specify the **width** if you’re overriding the css **style** attribute. Overriding this property can break the grid. Here is an example of a custom css style attribute:

"style": "width: 50%; transform: translateX(50%);"
{% endhint %}

To make use of customized parameters, you should enter the same in the **Advanced Configuration (JSON)** parameter in the App Builder.

The value entered in the **Advanced Configuration (JSON)** parameter should be a 2D array in JSON format. The first dimension will refer to the rows and the second dimension to the cells. You can also specify the height of the SharinPix album if required:

```
{
    "grid": [
        [
            {
                "style": "",
                "recordId": "",
                "placeholderUrl": "",
                "componentId": "",
                "tag": "",
                "height": "",
                "enableImageSync": "",
                "enableAction": "",
                "enableCrop": "",
                "refreshView": "",
                "permissionId": ""
            }
        ]
    ],
    "album": {
        "height": 800
    }
}
```

Here is an example:

```
  {
    "grid": [
      [
        {
        	"style": "width: 50%;",
          "tag": "first",
          "height": "300",
          "placeholderUrl": "<Enter your URL here>",
          "permissionId": "album-trash-false"
        },
        {
          "tag": "second",
          "height": "300",
          "placeholderUrl": "<Enter your URL here>"
        }
      ],
      [
        {
          "tag": "forth",
          "height": "350",
          "placeholderUrl": "<Enter your URL here>"
        }
      ]
    ],
    "album": {
      "height": 800
    }
  }
```
