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

# SharinPix Import Files

The **SharinPix Import Files** component allows users to import Salesforce files onto a SharinPix album.

<figure><img src="../.gitbook/assets/image (9) (2) (1).png" alt=""><figcaption></figcaption></figure>

![](<../.gitbook/assets/Screenshot_from_2022-03-10_13-28-37 (1) (1) (1).png>)

{% hint style="info" %}
**Information:**

This feature is only available on Lightning. It can be used:

* On Page Builder
* On Desktop
{% endhint %}

## Getting Started

To use the **SharinPix Import Files** component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.

<figure><img src="../.gitbook/assets/image (10) (2) (1).png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.03.10-13_31_18 (1) (1) (1).png>)

* **Button Label:** Used to specify the button label.
* **Include Attachments:** Used to enable/disable attachment imports. _**Note:** This will consume API requests._

## Demo

The picture below depicts the **SharinPix Import Files** component and an empty **SharinPix Album**:

![](<../.gitbook/assets/Screenshot_from_2022-03-10_13-35-53 (1) (1) (1).png>)

The picture below shows the import file modal upon clicking on the **Import Salesforce Files into SharinPix Album** button:

![](<../.gitbook/assets/Screenshot_from_2022-03-10_13-28-37 (1) (1) (1).png>)

The picture below shows the import file modal with the selected files. Click on the **Import Selection** button to import the files.

![](<../.gitbook/assets/Screenshot_from_2022-03-10_13-38-37 (1) (1) (1).png>)

The picture below depicts the imported files on the SharinPix Album component.

![](<../.gitbook/assets/Screenshot_from_2022-03-10_13-39-49 (1) (1) (1).png>)

{% hint style="warning" %}
**Note:**

For the **SharinPix Import Files component** to work, the **ImportFilesController** Apex class needs to be assigned to the users.
{% endhint %}
