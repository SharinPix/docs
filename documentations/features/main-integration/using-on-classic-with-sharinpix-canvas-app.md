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

# Using on Classic with SharinPix Canvas App

This article demonstrates how to add the SharinPix Canvas app onto an object's page-layout by:

1. Firstly, setting up SharinPix on your Org
2. Secondly, adding the Canvas app onto the page-layout

{% hint style="warning" %}
**Note:**

Canvas apps have some limitations. For example, they only allow 5,000 calls per day per user within 24-hour.

Therefore the usage of the SharinPix Canvas App is not recommended for implementations. In such cases, we recommend the usage of the **SharinPix Visualforce Component** instead. The SharinPix Canvas App, however, can still be used for testing purposes.

For more information about Canvas app limitations, please refer to the following link:

[https://developer.salesforce.com/docs/atlas.en-us.platform\_connect.meta/platform\_connect/canvas\_framework\_limits.htm](https://developer.salesforce.com/docs/atlas.en-us.platform_connect.meta/platform_connect/canvas_framework_limits.htm)

For more information about the SharinPix Visualforce Component and how it is used, kindly refer to the following [link](using-on-classic-with-a-visualforce-page-without-an-apex-controller-admin-friendly-version.md#sharinpix-visualforce-component).
{% endhint %}

## 1. Set up SharinPix in your Org <a href="#add-the-canvas-app-to-the-page-layout-of-an-object" id="add-the-canvas-app-to-the-page-layout-of-an-object"></a>

1\. Go to Setup.

2\. In the **Quick Find Box**, type **Installed Packages.**

3\. Under the **Build** section, select **Installed Packages**.

<figure><img src="../../.gitbook/assets/image (45) (1).png" alt=""><figcaption></figcaption></figure>

4\. Select the **SharinPix Package** known as **ImagesManagementBySharinPix.**

![](<../../.gitbook/assets/image (46) (1).png>)

5\. Click on **View components**.

![](<../../.gitbook/assets/image (47) (1).png>)

6\. Click on **Albums**.

![](<../../.gitbook/assets/image (48) (1).png>)

7\. Click on **Edit Policies.**

![](<../../.gitbook/assets/image (49) (1).png>)

Next to the field **Permitted Users,** select **All users may self-authorize** from the picklist.

![](<../../.gitbook/assets/image (50) (1).png>)

Click on **Save** when you are done.

## 2. Add Canvas App to a Page Layout

Access the object upon which you intend to add the canvas app on the page-layout. In this case, it is the object Account. Select a record of type Account.

9\. Click on **Edit Layout**.

![](<../../.gitbook/assets/image (55) (1) (1).png>)

10\. Select the **Canvas App** category from the types of components list as shown below.

![](<../../.gitbook/assets/image (54) (1).png>)

11\. Drag and drop the **Albums** canvas app on the page-layout on the area you desire.

![](<../../.gitbook/assets/image (53) (1).png>)

12\. Adjust the **Height** of the **SharinPix Album** to **500px**.

![](<../../.gitbook/assets/image (52) (1).png>)

Click on **Save** when you are done.

The **SharinPix Canvas App** should now appear on the page-layout of the record as presented in the screenshot below.

![](<../../.gitbook/assets/image (51) (1).png>)
