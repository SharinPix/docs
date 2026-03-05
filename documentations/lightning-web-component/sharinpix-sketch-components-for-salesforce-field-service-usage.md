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

# SharinPix Sketch Components for Salesforce Field Service Usage

The **SharinPix Sketch Components** enable users to annotate sketches. These components provide common annotation features, including the addition of polygons, lines, shapes, text, and more. The functionality is also available for offline use in Salesforce Field Service (SFS).

In the following sections, you will learn:

* [How to set up SharinPix Sketch components for Salesforce Field Service.](sharinpix-sketch-components-for-salesforce-field-service-usage.md#setting-up-sharinpix-sketch-components-for-salesforce-field-service)
* [How to set up Briefcase Builder for using SharinPix Sketch components in Offline mode.](sharinpix-sketch-components-for-salesforce-field-service-usage.md#set-up-briefcase-builder-for-offline-use)

{% hint style="warning" %}
**Prerequisite:**

Before setting up SharinPix Sketch Components to be used in Salesforce Field Service, you should ensure that users can access Sketch Objects. If that's not already the case, you can refer to the following article to provide access: [assign permission to users](sharinpix-sketcher.md#sharinpix-sketcher-setting)
{% endhint %}

{% hint style="success" %}
**Note:**

For more information on the SharinPix Sketch Components, please refer to the below articles:

* [SharinPix Sketcher](sharinpix-sketcher.md)
* [SharinPix Sketch Plan](sharinpix-sketch-plan.md)
{% endhint %}

## Setting Up SharinPix Sketch Components for Salesforce Field Service

Create a new permission set as indicated below and assign it to the users:

1. Go to Salesforce Setup
2. Search and open _Permission Sets_ and create a new permission set, with the label for example _**Field Service - LWC Access**._
3. For the **License** , select **Field Service Mobile**.

![](<../.gitbook/assets/1_1 (2).png>)

4\. In the _Find Settings_ search box, enter and click on _Access Lightning Web Components in Field Service Mobile_ , then edit the page to select the **Access Lightning Web Components in Field Service Mobile** checkbox.

![](<../.gitbook/assets/2_2 (2).png>)

5\. Assign this permission set _**Field Service - LWC Access**_ to the user.

![](<../.gitbook/assets/3_3 (2).png>)

6\. To use the SharinPix Sketch components on the Salesforce Field Service mobile app, you must create a Lightning web component (LWC) action, which is similar to creating a regular quick action, and assign it to your Salesforce Field Service (SFS) layout.

To distinguish between the SharinPix Sketcher and Sketch Plan components, use the specific LWC in the quick action. Use "sharinpix:sketcher" for the SharinPix Sketcher component and "sharinpix:sketchPlan" for the SharinPix Sketch Plan component as depicted in the diagrams below.

![](<../.gitbook/assets/4_4 (1).png>)

![](<../.gitbook/assets/image (127).png>)

## Set Up Briefcase Builder for offline use

To use the SharinPix Sketch Components offline, you must set up a briefcase on Salesforce. A _briefcase_ is a set of rules and filters that select records to prime for offline use. Briefcase Builder supports up to 50,000 records that can be retrieved offline. Follow the steps below to set up a briefcase:

1. Go to Salesforce Setup and search for **Briefcase** **Builder**.
2. Click on the **New Briefcase** button.
3. Enter a unique briefcase name and an optional description.
4. Click **Next**.
5. Add one or more objects and any related objects (in our case, Sketches, Sketch Templates, SharinPix Plan Items, and objects you are using, e.g., Work Order) to the briefcase for the business process, task, or event that you want to make available offline in the briefcase.
6. Apply the relevant filters and logic.
7. Assign relevant users to the briefcase.
8. Select the connected apps you want to associate with this briefcase, then to activate the briefcase for assigned users and groups, click **Activate.**

{% hint style="info" %}
**Information:**

To learn more about the Briefcase Builder, check out the information available on the following website: [https://help.salesforce.com/s/articleView?id=sf.briefcase\_builder\_overview.htm\&type=5](https://help.salesforce.com/s/articleView?id=sf.briefcase_builder_overview.htm\&type=5).
{% endhint %}

## SharinPix Sketch Components in SFS Mobile App Demo

The diagram below shows the SharinPix Sketch Component quick action on the SFS (Salesforce Field Service) mobile app.

![](<../.gitbook/assets/sketcher 2 (1) (1) (1).png>)

The image below displays annotated sketches within the **SharinPix Sketcher** Component.

![](<../.gitbook/assets/SI-34844 (1) (1) (1).png>)

The image below shows annotated sketches (**Markers**) within the **SharinPix Sketch Plan** Component.

![](<../.gitbook/assets/sketchPlan2 (1) (2).png>)

The picture below shows sketches annotated and saved in the SharinPix Sketch Component on Salesforce Field Service.

![](<../.gitbook/assets/sketcher (1) (1) (1).png>)
