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

# SFS Components Configuration (Roomplan, Document Scanner, Barcode Scanner, and Image and Annotate)

Salesforce delivers a very basic version of advanced feature integration with limited functionality. This documentation explains how to test it in your environment using the package we have provided, allowing you to compare the components included with those offered by SharinPix as part of its out-of-the-box solution.

{% hint style="warning" %}
**Prerequisite:**

* Salesforce Field Service Setup:
  * Before proceeding with the package installation, verify that Salesforce Field Service is already configured and set up in your Salesforce org.
* Install the package: [https://login.salesforce.com/packaging/installPackage.apexp?p0=04tVX000001HvkTYAS](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tVX000001HvkTYAS)
{% endhint %}

## Components Setup

## 1. Barcode Scanner

The **Salesforce Barcode Scanner** lets you scan barcodes into Salesforce using your phone's camera or a scanner. It works in the Salesforce app and helps with tasks like tracking inventory or managing field service. Learn more here: [Salesforce Barcode Scanner Documentation](https://developer.salesforce.com/docs/atlas.en-us.mobile_offline.meta/mobile_offline/use_barcodescanner_intro.htm).

![](<../.gitbook/assets/image (60) (4).png>)

**Using the Barcode Scanner on a Record Page and Salesforce Mobile App**

**Steps to add the component to a record page:**

* **Navigate to the Object Record Page** :
  * Go to the record page of the object where you want to place the barcode scanner (e.g., Case, Account, etc.).
* **Enter Edit Mode** :
  * Click the **Gear Icon** at the top right of the page.
  * Select **Edit Page** to open the Lightning App Builder.
* **Add the Barcode Scanner Component** :
  * In the Lightning App Builder, find the Barcode Scanner component in the list of available components.
  * Drag and drop the **Barcode Scanner Component** to the desired section on the page.
* **Save and Activate** :
  * Click **Save** to apply the changes.
  * If it hasn't been activated, click **Activation** and set it as the default page for desktop, mobile, or only mobile users, as needed.

**Using the Barcode Scanner as a Quick Action in Field Service**

Follow these steps to make the Barcode Scanner component available as a Quick Action within Salesforce Field Service:

* **Create a Quick Action for the Object** :
  * Go to **Setup** and navigate to **Object Manager**.
  * Select the object where you want to add the quick action (e.g., Work Order, Service Appointment).
* **Create a New Action** :
  * Click **Buttons, Links, and Actions** under the object.
  * Select **New Action**.
  * **Action Type** : Choose **Lightning Web Component**.
  * **Target Component** : Select the **Barcode Scanner Component**.
* **Name and Save** :
  * Give your action an appropriate name like "Scan Barcode."
  * Click **Save**.
* **Add the Quick Action to the Layout** :
  * Go to the **Page Layout** of the same object (Work Order, Service Appointment).
  * Drag the newly created quick action to the **Salesforce Mobile and Lightning Experience Actions** section of the layout.

## 2. Document Scanner

The **Salesforce Document Scanner** is a Lightning Web Component feature that scans documents using your device’s camera and Optical Character Recognition (OCR). It extracts text from printed or handwritten documents, returning either a simple text string or structured data aligned with the scanned image. Learn more here: [Salesforce Document Scanner Documentation](https://developer.salesforce.com/docs/atlas.en-us.250.0.mobile_offline.meta/mobile_offline/use_documentscanner.htm).

![](<../.gitbook/assets/image (61) (3).png>)

**Using the Document Scanner on a Record Page and Salesforce Mobile App**

* **Steps to add the component to a record page:**

1. **Navigate to the Object Record Page** :
   * Go to the record page of the object where you want to place the Document scanner (e.g., Case, Account, etc.).
2. **Enter Edit Mode** :
   * Click the **Gear Icon** at the top right of the page.
   * Select **Edit Page** to open the Lightning App Builder.
3. **Add the Document Scanner Component** :
   * In the Lightning App Builder, find the Document Scanner component in the list of available components.
   * Drag and drop the **Document Scanner Component** to the desired section on the page.
4. **Save and Activate** :
   * Click **Save** to apply the changes.
   * If it hasn't been activated, click **Activation** and set it as the default page for desktop, mobile, or only mobile users, as needed.

**Using the Document Scanner as a Quick Action in Field Service**

Follow these steps to make the Document Scanner component available as a Quick Action within Salesforce Field Service:

1. **Create a Quick Action for the Object** :
   * Go to **Setup** and navigate to **Object Manager**.
   * Select the object where you want to add the quick action (e.g., Work Order, Service Appointment).
2. **Create a New Action** :
   * Click **Buttons, Links, and Actions** under the object.
   * Select **New Action**.
   * **Action Type** : Choose **Lightning Web Component**.
   * **Target Component** : Select the **Document Scanner Component**.
3. **Name and Save** :
   * Give your action an appropriate name like "Scan Document."
   * Click **Save**.
4. **Add the Quick Action to the Layout** :
   * Go to the **Page Layout** of the same object (Work Order, Service Appointment).
   * Drag the newly created quick action to the **Salesforce Mobile and Lightning Experience Actions** section of the layout.

## 3. AR Capture

The **Salesforce AR SpaceCapture** lets you use your phone’s camera and augmented reality (AR) to create 3D models of physical spaces. This feature is useful for planning layouts, installations, or visualizing spaces. Learn more here: [Salesforce AR SpaceCapture Documentation](https://developer.salesforce.com/docs/atlas.en-us.field_service_dev.meta/field_service_dev/fsl_dev_mobile_lwc_space_capture_use.htm).

![](<../.gitbook/assets/image (62) (4).png>)

{% hint style="info" %}
**Note:**

This Component only works on iOS 14 that supports lidar capabilities and above and only on Salesforce Field Service.
{% endhint %}

**Using the AR capture component as a Quick Action in Field Service**

Follow these steps to make the AR Capture component available as a Quick Action within Salesforce Field Service:

1. **Create a Quick Action for the Object** :
   * Go to **Setup** and navigate to **Object Manager**.
   * Select the object where you want to add the quick action (e.g., Work Order, Service Appointment).
2. **Create a New Action** :
   * Click **Buttons, Links, and Actions** under the object.
   * Select **New Action**.
   * **Action Type** : Choose **Lightning Web Component**.
   * **Target Component** : Select the **AR capture Component**.
3. **Name and Save** :
   * Give your action an appropriate name like "Room Plan".
   * Click **Save**.
4. **Add the Quick Action to the Layout** :
   * Go to the **Page Layout** of the same object (Work Order, Service Appointment).
   * Drag the newly created quick action to the **Salesforce Mobile and Lightning Experience Actions** section of the layout.

## 4. Image and Annotate Component

The **Image and Annotate Component** lets users capture and annotate images directly in Lightning Web Components (LWCs). Field technicians can take photos, mark specific areas, and add notes to highlight issues or provide details. This makes it easier to document and communicate during service tasks. Learn more here: [Image and Annotate Documentation](https://help.salesforce.com/s/articleView?id=release-notes.rn_fieldservice_242_mobile_lwc_images.htm\&release=242\&type=5).

![](<../.gitbook/assets/image (63) (2).png>)

**Using the Image and Annotate as a Quick Action in Field Service**

Follow these steps to make the Image and Annotate component available as a Quick Action within Salesforce Field Service:\
**Create a Quick Action for the Object** :

* Go to **Setup** and navigate to **Object Manager**.
* Select the object where you want to add the quick action (e.g., Work Order, Service Appointment).

1. **Create a New Action** :
   * Click **Buttons, Links, and Actions** under the object.
   * Select **New Action**.
   * **Action Type** : Choose **Lightning Web Component**.
   * **Target Component** : Select the **image capture component**.
2. **Name and Save** :
   * Give your action an appropriate name, like "Capture Image".
   * Click **Save**.
3. **Add the Quick Action to the Layout** :
   * Go to the **Page Layout** of the same object (Work Order, Service Appointment).
   * Drag the newly created quick action to the **Salesforce Mobile and Lightning Experience Actions** section of the layout.
