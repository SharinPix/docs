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

# SharinPix Code Generator

The SharinPix Code Generator provides an interface allowing users to manually add, remove or modify SharinPix Album abilities and features before generating the corresponding code.

In this article, we will demonstrate how to:

1. Access the SharinPix Code Generator
2. Manually set a SharinPix album's abilities/features
3. Locate the corresponding code generated

## Access the SharinPix Code Generator

To access the Code Generator from your Organisation:

* Click on the **App Launcher**
* Enter SharinPix Settings in the search bar and select **SharinPix Settings**
* On the SharinPix Settings page, click on the **Go to administration dashboard** button as indicated below:

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2020.09.21-11_15_50 (1) (1).png>)

Upon clicking on the button, the SharinPix Administration will open in a new tab.

* Next, from the top menu bar, click on **Code Generator**. The Code Generator's interface is as shown below:

![](<../.gitbook/assets/screenshot-app.sharinpix.com-2020.09.21-11_19_49 (1) (1).png>)

## Set the SharinPix Album's abilities and features

Now that you know how to access the SharinPix Code Generator, go ahead and add some album abilities and features by checking the different options available:

![](<../.gitbook/assets/screenshot-app.sharinpix.com-2020.09.21-11_29_50 (1) (1).png>)

You can also test the abilities and features enabled by adding an image onto the test album available in the **Preview** section:

![](<../.gitbook/assets/screenshot-app.sharinpix.com-2020.09.21-11_36_37 (1) (1).png>)

## Locate the corresponding code generated

Once you are satisfied with the abilities and features added to the album, take a look at the code generated. The code genarated comes in the following formats:

1. SharinPix Canvas App
2. SharinPix Visualforce Component
3. SharinPix Visualforce Component embedded in a Visualforce page along with the corresponding Apex Controller
4. Lightning Component embedding the SharinPix Visualforce Component
5. Raw Permissions

![](<../.gitbook/assets/screenshot-app.sharinpix.com-2020.09.21-11_44_57 (1) (1).png>)

To access the code generated, simply click on the arrow located on the right-hand side, then click on the **Copy Code** button.

![](<../.gitbook/assets/screenshot-app.sharinpix.com-2020.09.21-11_49_00 (1) (1).png>)

You can now integrate the same code generated in your own implementation.

{% hint style="warning" %}
**Note**:

You should ensure that you are using the correct album ID format when using the generated code in your own implementation.

The SharinPix Code Generator allows users to either use the **Salesforce Record Id** directly or a **Slaesforce field** that stores the album ID to retrieve the correct album ID by making use of the **Album Id** field in the **Information** section as shown below:
{% endhint %}

![](<../.gitbook/assets/rsz_1screenshot_from_2020-09-21_12-00-36 (1) (1).png>)
