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

# SharinPix Sketcher

The **SharinPix Sketcher** component enables users to annotate sketches. Common annotation features provided by this component include the addition of polygons, lines, shapes, text, and many more. [This functionality is also available for offline use in Salesforce Field Service (SFS).](sharinpix-sketch-components-for-salesforce-field-service-usage.md)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
* Field Service Mobile (accessible both online and offline)
{% endhint %}

## Getting Started

To use the SharinPix Sketcher component, simply need to drag and drop the component from the Lightning App Builder onto your page layout.

![](<../.gitbook/assets/1_1 (1) (1).png>)

## SharinPix Sketcher Setting

To use SharinPix Sketch on both desktop and mobile, you should ensure the following for the SharinPix Sketch component:

* Assign the permission set, **SharinPix Sketch Permission** , to the users.
* Follow the steps below to set up a SharinPix Sketch Template and use of SharinPix Sketcher:
  1. Go to the App Launcher and find the **Sketch Template**.
  2. Create a new template and insert the **SVG** of an image into the **template** field.
  3. Go to the object where you will add the SharinPix Sketcher and edit the record page to add the component.
  4. In the SharinPix Sketcher component, select the Sketch Template.
  5. Begin adding annotation and text to the Sketch as needed.

## Demo

The diagram below depicts the creation of a sketch template with the SVG metadata of an image integrated into the template.

![](<../.gitbook/assets/Screenshot from 2024-04-02 23-14-32 (1) (1) (1).png>)

The screenshot below depicts the Sketcher Component with a sketch template.

![](<../.gitbook/assets/sketchera (1) (1) (1).png>)

The diagram below shows the SharinPix Sketcher with Sketch Template created above.

![](<../.gitbook/assets/Screenshot from 2024-04-10 15-06-21 (1) (1) (1).png>)

The picture below shows sketches that has been annotated and saved in SharinPix Sketcher.

![](<../.gitbook/assets/Screenshot from 2024-04-10 16-03-45 (1) (1) (1).png>)
