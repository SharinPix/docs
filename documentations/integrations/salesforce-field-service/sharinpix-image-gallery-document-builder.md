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

# SharinPix Image Gallery (Document Builder)

The **SharinPix Image Gallery** component works with Salesforce Field Service to help create professional PDF service documents, including images. Using the Document Builder, you can easily make documents with images to fit your business needs.

{% hint style="info" %}
**Prerequisites**

Before using the **SharinPix Image Gallery**, make sure that you:

1. Activate Document Builder in your org
2. Give users access to Document Builder
3. Assign Document Builder to Dispatchers and Mobile Workers
4. Install the SharinPix Field Service package
5. Have the SharinPix package version 1.308 or above installed on your org (**note:** [How to upgrade SharinPix package](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange))
{% endhint %}

## 1. Activating the Document Builder feature

1. From _Setup_, enter and select **Field Service Settings** in the _Quick Find_ box.
2. Select **Enable Document Builder**.

A notification will inform you that Salesforce is registering your org. You will receive an email notification a few minutes later letting you know when you are registered. After you’ve registered, you can start [creating Service Document templates](sharinpix-image-gallery-document-builder.md#create-a-service-document-template).

{% hint style="warning" %}
**Note:** Only Salesforce admins with access to the Setup menu, can access the builder experience and build Service Document templates.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (73) (2).png" alt=""><figcaption></figcaption></figure>

## 2. Give Users Access to Document Builder

1. From _Setup_, enter Users, and then select **Permission Sets**, in the _Quick Find_ box.
2. Find and assign the following permission sets to Field Service technicians, dispatchers, and admins:
   * **Field Service Document Builder Dispatcher**,&#x20;
   * **Field Service Document Builder Mobile**, and
   * **Field Service Document Builder Standard**
3. To assign the permission sets to users, select **Manage Assignments**.

<figure><img src="../../.gitbook/assets/image (74) (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

Users who have been assigned the above permission sets no longer have access to Service Reports, and the Create Service Report button.
{% endhint %}

### 3. Assign Document Builder to Dispatchers and Mobile Workers <a href="#assign-document-builder-to-dispatchers-and-mobile-workers" id="assign-document-builder-to-dispatchers-and-mobile-workers"></a>

1. From _Setup_, enter and select **Permission Sets**, in the _Quick Find_ box
2. Create a permission set by clicking on the **New** button.
3. Give it a name, for example, _Field Service Document Builder_.
4. Leave the License picklist field blank, and then save your changes.
5. Scroll down to the **System** section and click **System Permissions**.
6. Click **Edit**, select **Document Builder**, and **Access Lightning Web Components for Field Service Mobile**, then save your changes.
7. Assign this permission set to users by clicking **Manage Assignments**.

## 4. Installing the SharinPix Field Service Package

Use the following link to install the SharinPix Field Service package if it's not installed already: [SharinPix Field Service package install link](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tVX000001NLMXYA4)

## Create a Service Document Template

Once the Document Builder is activated and relevant permission sets are assigned to your users, you can create Service Document templates as explained below.

* From _Setup_, enter and select **Document Builder**, in the Quick Find box

<figure><img src="../../.gitbook/assets/image (75) (2).png" alt=""><figcaption></figcaption></figure>

* To create a template, click **New Template**.
* Add a label to indicate the type of Service Document you’re creating, for example, _Service Appointment Debrief_.
* Select any object from the dropdown list: **Work Order**, **Work Order Line Item**, or **Service Appointment**. Your selection dictates which object the template is created from and which fields and related lists appear in Document Builder.&#x20;
* Click Next.
* Choose between a blank template and a standard default template. **Note:** A standard template gives you a starting point with added fields and related lists.

You are now ready to start building your Service Document!

## Configuring the SharinPix Image Gallery Component.

{% hint style="danger" %}
**Prerequisite:**\
Make sure you have images on the records for which you are creating the Service Document and that [SharinPix Image Sync](../../image-sync/setup-sharinpix-image-sync.md) is activated for your object. Please note that no images will be available for the report without the _SharinPix Image Sync_ feature being activated.
{% endhint %}

To add and configure the _SharinPix Image Gallery_ component on the Document Builder, proceed as follows:

* On the Document Builder page, search for **SharinPix Image Gallery** and drag and drop the component onto the Service Document where desired.

<figure><img src="../../.gitbook/assets/image (76) (2).png" alt=""><figcaption></figcaption></figure>

### Component Parameters & Configurations

<figure><img src="../../.gitbook/assets/image (77) (2).png" alt=""><figcaption></figcaption></figure>

Configure the component's parameter as follows:

* **Number of Columns**: Choose the number of columns to be included in your document.
* **Image URL field**: Select the desired image size using the **Image URL field** parameter. The parameter's values are:
  * **Image Original:** corresponds to the original size.
  * **Image Mini:** corresponds to a size of 100 x 100 pixels.
  * **Image Thumbnail:** corresponds to a size of 200 x 200 pixels.
  * **Image Full:** corresponds to a size of 1920 x 1280 pixels.
* **Filter Tags**: Add tags separated by the semicolon(;) character. Images will be displayed in the SharinPix Image Gallery based on your input tags. Leave the field blank to display all images.
* **Sections by Tags:** Use this to organize images into sections based on their tags. Enter multiple tags separated by a semicolon (e.g., Tag1;Tag2;Tag3). Each tag will create a separate section displaying images with that tag. If left blank, all images will appear together without any grouping.

{% hint style="success" %}
**Tip:**

You can also customize and generate image URLs with the desired image size using the _SharinPix Transformation_ feature. For detailed steps on how to do so, please see: [SharinPix Transformation - get your images automatically resized!](https://docs.sharinpix.com/m/documentation/l/1045753-sharinpix-transformation-get-your-images-automatically-resized)
{% endhint %}

## Generating a Service Document

To generate the PDFs from the desktop site:

* **Create Service Document:**
  * Go to the Quick Action section in your record and find the **Create Service Document** action.
  * Click **Create Service Document**.
* **Create PDF:**
  * Click **Create PDF**. You will get a popup message indicating that your request is queued.
  * When your PDF is ready, you will receive a notification under the Global Notifications bell.
* **Access PDFs:**
  * To access the PDFs you create, including an archive of your PDFs, navigate to the work order and click the **Related** tab.
  * Scroll down to **Service Reports**.
* **View PDF:**
  * To view your PDF, click a service report name in the list view.

<figure><img src="../../.gitbook/assets/image (78) (2).png" alt=""><figcaption></figcaption></figure>

To use Document Builder on the Field Service mobile app, enable push notifications on your device. Push notifications will inform you when your PDF is ready or if there are any errors.

1. **Open a Work Order:** Go to a work order, work order line item, or service appointment. In this example, we use a work order.
2. **Create Service Document:** Click the Actions launcher and select **Create Service Document**.
3. **Preview and Collect Signature:** You will be redirected to a preview of the Work Summary template. This template shows customer details and the work completed, and prompts you to collect a customer signature.
   * Collect the customer signature by having them type and sign their name.
   * If you can’t collect the signature, click **Can’t Collect Signature** and provide a reason, such as the representative not being present.
4. **Save and Generate Document:** Click **Save**, then click **Generate Document** on the following window.
   * A popup will notify you when the document generation is complete. If you don’t see a popup and the process is taking a long time, pull down to refresh the page. If you’re offline, your document will be added to a queue.
5. **View the PDF:** Click the notification to return to the Field Service mobile app, where you can see the final PDF of the work summary. This PDF is accessible from the **Overview** tab on the given work order.

## Demo: See the generated report with SharinPix images in action!

<figure><img src="../../.gitbook/assets/image (79) (2).png" alt=""><figcaption></figcaption></figure>

## Demo: Sections By Tags

<figure><img src="../../.gitbook/assets/image (80) (2).png" alt=""><figcaption></figcaption></figure>
