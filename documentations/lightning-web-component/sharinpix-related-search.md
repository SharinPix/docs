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

# SharinPix Related Search

The **SharinPix Related Search** component permits to search for images that were uploaded on a related child object.

![](<../.gitbook/assets/screenshot-enterprise-computing-8320-dev-ed.lightning.force.com-2020.05.14-15_47_14 (1) (1) (1).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Community Builder (**Note:** _For more information on how to configure the component in Salesforce community, click_ [_here_](sharinpix-related-search.md#configure-the-sharinpix-related-search-in-salesforce-community)_)_
* On Page Builder
* On Desktop
* On Mobile
* In Flows (but not in Field Service Mobile Flow)
* In your own Lightning Component development
{% endhint %}

## Getting Started

To use the SharinPix Related search component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/Image from Gradio (10).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

![](<../.gitbook/assets/screenshot-fun-page-2589-dev-ed.lightning.force.com-2021.06.09-16_40_31 (1) (1) (1).png>)

* **Child Object:** Used to specify the child object from which to retrieve images. The "All Visible Child Objects" option retrieves images from all child objects that show as Related Lists on the record's page layout; this option is meant to work only on record pages.\
  **Note:** _This parameter is configured differently within Salesforce Community. Click_ [_here_](sharinpix-related-search.md#configure-the-sharinpix-related-search-in-salesforce-community) _for more details on how to configure the same within Community._
* **Tag Operator:** Used to filter the search by tags. The values available are **OR** and **AND**. Using **OR** , the search result will contain images having any of the tags specified whereas using **AND** will return the images with all specified tags.
* **Tag Names (JSON):** Used to specify the tags to be used to filter the search. The value inserted in this field should be an array in JSON format.
* **Affixes (JSON):** Used to specify prefixes and suffixes to be added to the Object IDs returned by the report. The value inserted in this field should be an array in JSON format.
* **Height:** Used to specify the component's height. The default value is **600**(px).
* **Include images from current record:** When checked, this option enables inclusion of the current record's images in the search results.
* **Use Fullscreen Image Viewer:** This option is used to view the image in fullscreen in the related search.
* **Custom Permission ID or Name:** Used to specify the Id or Name of a custom permission.

## Demo

The example below shows the images uploaded on the child object:

![](<../.gitbook/assets/screenshot-enterprise-computing-8320-dev-ed.lightning.force.com-2020.05.14-16_14_36 (1) (1) (1).png>)

The picture below depicts the SharinPix Related Search component on the parent object's page record. The component shows the same images uploaded on the child object:

![](<../.gitbook/assets/screenshot-enterprise-computing-8320-dev-ed.lightning.force.com-2020.05.14-16_17_54 (1) (1) (1).png>)

## Configure the SharinPix Related Search in Salesforce Community

This section demonstrates how to configure the **SharinPix Related Search** within Salesforce Communities.

For such configuration, you should proceed as follows:

* On the Community Builder, drag and drop the **SharinPix Related Search** component from the **Components** section onto the canvas:

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed--sitestudio.na73.force.com-2021.07.19-10_27_34 (1) (1) (1).png>)

* Next, make sure that the **Record ID** and **Child Relationship Name** parameters are configured as follows:
  * **Record ID:** To use the current record ID, ensure that this value is set to **{!recordId}**. If you want to use another record ID, then enter the desired ID
  * **Child Relationship Name:** This parameter stores the child relationship API name on which to search the images and is configured differently in Community. To know the exact value to be entered for the **Child Relationship Name** parameter when used within Community:

1\. Firstly, add the **SharinPix Related Search** component on the same object **on Salesforce itself using the Lightning App Builder**. _Note: This part is performed only to obtain the correct parameter value, you do not need to save the page_

2\. Still using the Lightning App Builder, select the desired value for the component's **Child Object** parameter using the dropdown:

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.07.19-12_29_45 (1) (1) (1).png>)

3\. Next, copy the value in between the parentheses. In the above example, the value to be copied is **Contacts**

4\. Next, use the copied value for the for the **Child Relationship Name** parameter **within the Salesforce Community** by pasting the value in the corresponding textbox on the Community builder:

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed--sitestudio.na73.force.com-2021.07.19-12_42_12 (1) (1) (1).png>)

* Once the Record ID and Child Relationship Name parameters have been configured as explained above, go ahead and configure the other parameters as desired.
