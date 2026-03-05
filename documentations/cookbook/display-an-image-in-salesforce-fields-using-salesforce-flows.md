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

# Display an image in Salesforce fields using Salesforce Flows

{% hint style="info" %}
This article demonstrates how to display the latest image uploaded onto a SharinPix Album in Salesforce fields.

This can be performed by:

* [Adding an image to a Rich Text field using a Salesforce Flow and the SharinPix Image Sync feature.](display-an-image-in-salesforce-fields-using-salesforce-flows.md#using-a-flow-to-add-an-image-to-a-rich-text-field)
* [Using a Salesforce Flow along with the SharinPix Image Sync feature to display an image in a Formula field.](display-an-image-in-salesforce-fields-using-salesforce-flows.md#using-flow-to-display-an-image-in-a-formula-field)
{% endhint %}

{% hint style="warning" %}
**Note:**

In both cases, the **SharinPix Image Sync** feature should be enabled for the object you intend to use.

You can refer to the following article for detailed information about how to set up the Image Sync for an object:

[Setup SharinPix Image Sync](../image-sync/setup-sharinpix-image-sync.md)
{% endhint %}

{% hint style="info" %}
**Information:**

For this demo, we will use the Account object since the SharinPix package includes an Image Sync setup for the Account object by default.&#x20;

However, you should make sure that the **Enable Image Sync** parameter is checked on the SharinPix Album component added to the Account record page.
{% endhint %}

## Using a Flow to add an image to a Rich Text field

### Creation of the Rich Text field

Before creating the Flow, we need to create a field that will display the image. Therefore, go to the Account object and create a new field as follows:

* Data type: **Text Area (Rich)**
* Field Label: **Image**

### Creation of the Flow

Once the Image Sync is enabled and the Rich Text field is created, go ahead and create a new Salesforce Flow as follows:

* Go to Setup. In the Quick Find Box, type **Flows**.
* Under **Process Automation** , select **Flows**.
* Click on the **New Flow** button.
* Select the option **Record-Triggered Flow** , and click on the **Create** button.

<figure><img src="../.gitbook/assets/test (17).png" alt=""><figcaption></figcaption></figure>

* After clicking on _Create_, the _Configure Start_ modal will be displayed. Fill in the modal as indicated below:
  * **Select Object**: SharinPix Image
  * **Configure Trigger**: A record is created
  * For the **Set Entry Conditions**, select **All Conditions Are Met (AND)**&#x61;nd fill in the details as follows:
    1. &#x20;**Field:** sharinpix\_\_Account\_\_c
    2. &#x20;**Operator:** IsNull
    3. &#x20;**Value:** Select **{!$GlobalConstant.False}**
  * **Optimize the Flow for**: Actions and Related Records
* Click on **Done** to save the configurations.

![](<../.gitbook/assets/image (43) (3).png>)

* Next, add an **Update Triggering Record** element.

<figure><img src="../.gitbook/assets/test (18).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/test (19).png" alt=""><figcaption></figcaption></figure>

* On the _Update Triggering Record_ modal, enter the following information:
  * **Label:** Update Parent Account Record
  * **How to Find Records to Update and Set Their Values:** Specify conditions to identify records, and set fields individually
  * **Object:** Account
  * In the **Field Account Records** section:
    * **Condition Requirements to Update Record:** All Conditions Are Met (AND)
    * **Field:** Id
    * **Operator:** Equals
    * **Value:** {!$Record.sharinpix\_\_Account\_\_c}
  * In the **Set Field Values for the Account Records** section:
    * For the **Field**, select the **Image** field available on the parent Account record.
    * For the **Value**, click on **New Resource** and enter the following information
      1. &#x20;**Resource Type:** Variable
      2. &#x20;**API Name:** richTextValue
      3. &#x20;**Description:** Optional
      4. **Default Value:**&#x20;

<mark style="color:red;">`<img src={!$Record.sharinpix__ImageURLThumbnail__c}/>`</mark>

![](<../.gitbook/assets/image (42) (3).png>)

* Save the newly-created resource.
* Click on **Done** to save the _formula_ and the \_Update Triggering Record \_element.

![](<../.gitbook/assets/image (41) (3).png>)

* Save the Flow and activate it.

## Demo

To test this new implementation:

* Go to an Account record
* Upload an image to the SharinPix album
* Check if the field, **Image** displays the image accordingly

<figure><img src="../.gitbook/assets/test (20).png" alt=""><figcaption></figcaption></figure>

## Using Flow to display an image in a Formula field

This section covers the following:

* [Creation of a Salesforce field to store the image URL](display-an-image-in-salesforce-fields-using-salesforce-flows.md#creation-of-the-salesforce-fields)
* [Creation of a Formula field to display the image](display-an-image-in-salesforce-fields-using-salesforce-flows.md#creation-of-the-salesforce-fields)
* [Creation of a Flow to update the URL field whenever an image is uploaded](display-an-image-in-salesforce-fields-using-salesforce-flows.md#creation-of-the-flow-1)

### Creation of the Salesforce fields

Create the fields as follows:

1. A field of type **URL** to store the image URL generated:
   * Data Type: **URL**
   * Field Label: **First Image URL**
2. A **Formula** field that will use the image URL stored in the field created above (that is **First Image URL)** to display the image. For the formula field:
   * Date Type: **Formula**
   * Field Label: **First** **Image**
   * Formula Return Type: **Text**
   * Formula:

<mark style="color:red;">`IF( ISBLANK( First_Image_URL ), "Image Not Found", IMAGE( First_Image_URL, "" ) )`</mark>

### Creation of the Flow

Once the fields created, go ahead and create a new Salesforce Flow as follows:

* Go to Setup. In the Quick Find Box, type **Flows**.
* Under **Process Automation** , select **Flows**.
* Click on the **New Flow** button.
* Select the option **Record-Triggered Flow** , and click on the **Create** button

![](<../.gitbook/assets/image (40) (3).png>)

* After clicking on _Create_, the _Configure Start_ modal will be displayed. Fill in the modal as indicated below:
  * **Select Object**: SharinPix Image
  * **Configure Trigger**: A record is created
  * For the **Set Entry Conditions**, select **All Conditions Are Met (AND)**&#x61;nd fill in the details as follows:
    1. &#x20;**Field:** sharinpix\_\_Account\_\_c
    2. &#x20;**Operator:** IsNull
    3. &#x20;**Value:** Select **{!$GlobalConstant.False}**
  * **Optimize the Flow for**: Actions and Related Records
* Click on **Done** to save the configurations.

![](<../.gitbook/assets/image (39) (3).png>)

* Next, add an **Update Triggering Record** element.

<figure><img src="../.gitbook/assets/test (21).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/test (22).png" alt=""><figcaption></figcaption></figure>

* On the _Update Triggering Record_ modal, enter the following information:
  * **Label:** Update Parent Account Record
  * **How to Find Records to Update and Set Their Values:** Specify conditions to identify records, and set fields individually
  * **Object:** Account
  * In the **Field Account Records** section:
    * **Condition Requirements to Update Record:** All Conditions Are Met (AND)
    * **Field:** Id
    * **Operator:** Equals
    * **Value:** {!$Record.sharinpix\_\_Account\_\_c}
  * In the **Set Field Values for the Account Records** section:
    * For the **Field**, select the **First Image URL** field available on the parent Account record.
    * For the **Value**, select **{!$Record.sharinpix\_\_ImageURLThumbnail\_\_c}**

![](<../.gitbook/assets/image (38) (3).png>)

* Click on **Done** to save the _formula_ and the _Update Triggering Record_ element.
* Save and activate the Flow.

### **Demo**

To test this new implementation:

* Go to an Account record
* Upload an image to the SharinPix album
* Check if the **Image** and **First Image URL** fields have been populated correctly as demonstrated below:

![](<../.gitbook/assets/image (37) (3).png>)

{% hint style="success" %}
**Tip:**

The methods mentioned above have a limitation, they cannot be used to display multiple images in one field.

However, SharinPix  provides a component (the **SharinPix To Rich Text Area** component) that perform the same process and which can be used to add multiple images in one field.

The SharinPix To Rich Text Area component allows users to select and send one or more images from a SharinPix album to a **Rich Text** field. This method is easier to configure and provides more flexibility.

For more information about this component, please refer to the following article:

[SharinPix To Rich Text Area](../lightning-web-component/sharinpix-to-rich-text-area.md)
{% endhint %}

## DEPRECATED: Using Process Builder to add an image to a Rich Text field

{% hint style="warning" %}
**Note:**

This section is deprecated and is only used for Process Builder maintenance.
{% endhint %}

### Create the Process Builder <a href="#create-the-process-builder" id="create-the-process-builder"></a>

Follow the steps below to create the Process Builder:

* Go to Setup. In the Quick Find Box, type **Process Builder**
* Under **Process Automation**, select **Process Builder**
* Click on New
* For the newly-created Process Builder:
  1. For the field, **Process Name** enter **Add Image to Rich Text Field on Account**
  2. Enter a description for the process. (This step is optional)
  3. For the field, **The process starts when** select **A record changes**
  4. Click **Save**

Once on the Process Builder editor:

* Click on **Add Object**
  1. For the field **Object**, select **SharinPix Image**
  2. For the field **Start the process**, choose **when a record is created**
  3. Click on **Save**
* Click on **Add Criteria**
  1. For the field **Criteria Name**, enter **No Criteria**
  2. For the field **Criteria for Executing Actions**, choose **No criteria—just execute the actions!**
  3. Click on **Save**
*   Click on **Add Action**

    1. For the **Action Type** field, choose **Update Records**
    2. For the **Action Name**, enter **Update Account Record**
    3. For the **Record Type**, select **Select a record related to the sharinpix\_\_SharinPixImage\_\_c**. Then from the dropdown menu, select **Account**
    4. Click on **Choose**

    <figure><img src="../.gitbook/assets/test (23).png" alt=""><figcaption></figcaption></figure>


* Leave **Criteria for Updating Records** on **No criteria—just update the records!**
* Inside the **Set new field values for the records you update** section:
  1. For the **Field**, select the Rich Text field created previously, that is **Image**
  2. For the **Type**, select **Formula**
  3. For the **Value**, click on **Build a formula**&#x20;
  4. Inside the formula builder, use the following formula:

**" \<img src="" & \[sharinpix\_\_SharinPixImage\_\_c].sharinpix\_\_ImageURLThumbnail\_\_c & "" />"**

<figure><img src="../.gitbook/assets/test (24).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The above formula makes use of the field **\[sharinpix\_\_SharinPixImage\_\_c].sharinpix\_\_ImageURLThumbnail\_\_c** which stores the image's URL in a thumbnail format on the SharinPix Image object.
{% endhint %}

5\. Click on **Use this Formula**

* Click on **Save** when done

You can now activate the Process Builder.

## DEPRECATED: Using Process Builder to display an image in a Formula field

{% hint style="warning" %}
**Note:**

This section is deprecated and is only used for Process Builder maintenance.
{% endhint %}

#### Create the Process Builder <a href="#create-the-process-builder_1" id="create-the-process-builder_1"></a>

Follow the steps below to create the Process Builder:

* Go to Setup. In the Quick Find Box, type **Process Builder**
* Under **Process Automation**, select **Process Builder**
* Click on New
* For the newly-created Process Builder:
  1. For the field, **Process Name** enter **Add an Image to Field on Account**
  2. Enter a description for the process. (This step is optional)
  3. For the field, **The process starts when** select **A record changes**
  4. Click **Save**

Once on the Process Builder editor:

* Click on **Add Object**
  1. For the field **Object**, select **SharinPix Image**
  2. For the field **Start the process**, choose **when a record is created**
  3. Click on **Save**
* Click on **Add Criteria**
  1. For the field **Criteria Name**, enter **No Criteria**
  2. For the field **Criteria for Executing Actions**, choose **No criteria—just execute the actions!**
  3. Click on **Save**
*   Click on **Add Action**

    1. For the **Action Type** field, choose **Update Records**
    2. For the **Action Name**, enter **Update Account Record**
    3. For the **Record Type**, select **Select a record related to the sharinpix\_\_SharinPixImage\_\_c**. Then from the dropdown menu, select **Account**
    4. Click on **Choose**

    <figure><img src="../.gitbook/assets/test (25).png" alt=""><figcaption></figcaption></figure>


* Leave **Criteria for Updating Records** on **No criteria—just update the records!**
* Inside the **Set new field values for the records you update** section:
  1. For the **Field**, select the URL field created previously, that is **First Image URL**
  2. For the **Type**, select **Field Reference**
  3. For the **Value**, choose **Image URL Thumbnail**
* Click **Save** when done

You can now activate the Process Builder.
