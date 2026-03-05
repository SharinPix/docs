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

# Display Images in Service Report (Salesforce Field Service / FSL)

This article demonstrates how to display a SharinPix Image record in a Service Report. This can be performed by either storing the image in a **SharinPix Image field** of type [Formula](display-images-in-service-report-salesforce-field-service-fsl.md#using-formula-fields-to-display-images-in-a-service-report) or [Rich Text](display-images-in-service-report-salesforce-field-service-fsl.md#using-rich-text-fields-to-display-images-in-a-service-report).

{% hint style="warning" %}
**Note:**

In order to display images in a Service Report, SharinPix Image Sync should be set up for the object you intend to use.

For this demo, we will be using the Work Order object. Therefore, Image Sync should be enabled for this object. You should also make sure that the option \*\*Enable Image Sync \*\*is checked for the SharinPix Album component added to the Work Order object.

You can refer to the following article for more details on how to set up Image Sync for an object: [Setup SharinPix Image Sync](../../image-sync/setup-sharinpix-image-sync.md)
{% endhint %}

## Using Formula fields to display images in a Service Report

In this section, we will:

1. Make use of Formula fields on the SharinPix Image object to store the image
2. Add the Formula field to the required Service Report Template

### Use of the Formula field

The SharinPix package already includes some Formula fields that store images with different dimensions on the **SharinPix Image** object. These fields are:

* **Image Original:** corresponds to the original size
* **Image Mini:** corresponds to a size of **100 x 100** pixels
* **Image Thumbnail:** corresponds to a size of **200 x 200** pixels
* **Image Full:** corresponds to a size of **1920 x 1280** pixels

You can either use the above Formula fields in your Service Report template or use custom Formula fields to store the images. The custom Formula fields should be in the following format:

`IMAGE(<Image_URL>, <Alternate_Text>, Height, Width)`

{% hint style="success" %}
**Tips:**

* The height and width in the Formula field are optional.
* You can use the SharinPix Transformation feature to customize the image size for better results. SharinPix Transformation allows automatic resizing of your images.

Using this feature, you can easily play with the height and width until the desired image display is obtained. You can find more information on SharinPix Transformation here: [SharinPix Transformation - get your images automatically resized!](../../image-sync/sharinpix-transformation-get-your-images-watermarked.md)

The best practices when it comes to the usage of the SharinPix Transformation are:

* Firstly, add a SharinPix Transformation on a custom URL field. For example, a custom field named  **PDF\_Image\_version\_URL\_\_c**.
* Then, make the transformation fit your needs in terms of resolution.
* Finally, use the transformation URL field in a Formula field without setting the formula's height and width as demonstrated below:

`IF (ISBLANK(PDF_Image_version_URL__c), "", IMAGE(PDF_Image_version_URL__c, ""))`

**Note:** The IF(ISBLANK()) part is used as an alternate in cases where the URL field (PDF\_Image\_version\_URL\_\_c in this scenario) is blank. This will ensure that no broken image links are displayed.
{% endhint %}

### Addition of the Formula field to the Service Report template

Now that your Formula field is ready, go ahead and add the **SharinPix Images related list** on the Service Report Template by following the steps below:

* From Setup, search and select **Service Report Template**
* Click on the **Edit** link, next to the required template
* From the left menu, click on **Work Order**
* Drag and drop the **List** element onto the template

<figure><img src="../../.gitbook/assets/image (1) (6).png" alt=""><figcaption></figcaption></figure>

* On the **List Properties** modal:
  * Enter **SharinPix Images** as the **Title**
  * Select **SharinPix Images** as the **Object**
  * From the **Available Fields** list, search and add the required Formula field. For example, **Image Thumbnail**

<figure><img src="../../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

* Click **OK** when done
* Then, click on **Save**

Your Service Report template is now ready!

## Using Rich Text fields to display images in a Service Report

In this section, we will:

1. [Create a Rich Text field on the SharinPix Image object to store the image](display-images-in-service-report-salesforce-field-service-fsl.md#creation-of-the-rich-text-field)
2. [Create a Flow that will populate the Rich Text field](display-images-in-service-report-salesforce-field-service-fsl.md#creation-of-the-flow)
3. [Add the Rich Text field to the required Service Report Template](display-images-in-service-report-salesforce-field-service-fsl.md#addition-of-the-rich-text-field-to-the-service-report-template)

### Creation of the Rich Text field

Before creating the Flow, we need to create a field that will display the image. To do so, follow the steps below:

* Go on **Setup**, then click on **Object Manager**
* Search and select **SharinPix Image**
* Next, create a Rich Text field as follows:
  * Data type: **Text Area (Rich)**
  * Field Label: **Display** **Image**

### Creation of the Flow

To create the Flow,

* Go to Setup. In the Quick Find Box, type **Flows**.
* Under **Process Automation** , select **Flows**.
* Click on the **New Flow** button.
* Select the option **Record-Triggered Flow** , and click on the **Create** button.

<figure><img src="../../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>

* After clicking on _Create_ , the \_Configure Start \_modal will be displayed. Fill in the modal as indicated below:
  * **Select Object** : SharinPix Image
  * **Configure Trigger** : A record is created or updated
  * **Set Entry Conditions** : None
  * **Optimize the Flow for** : Actions and Related Records
* Click on **Done** to save the configurations.

<figure><img src="../../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

* Next, add an **Update Triggering Records** element.

<figure><img src="../../.gitbook/assets/image (1) (7).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

* On the _Update Triggering Record_ modal, enter the following information:
  * **Label**: Update SharinPix Image Record
  * **How to Find Records to Update and Set Their Values:** Use the sharinpix image record that triggered the flow
  * **Condition Requirements to Update Record:** None - Always Update Record
  *   In the Set Field Values for the Account Records section:

      * For the **Field** , select the Display **Image** field.
      * For the **Value** , click on **New Resource** and enter the following information
        1. **Resource Type**: Variable
        2. **API Name**: retrieveImageURL
        3. **Description:** Optional
        4. **Default Value:**

      `<img src={!$Record__Prior.sharinpix__ImageURLThumbnail__c}/>`

<figure><img src="../../.gitbook/assets/image (120).png" alt=""><figcaption></figcaption></figure>

* Save the newly-created resource and the \_Update Triggering Record \_element.

<figure><img src="../../.gitbook/assets/image (121).png" alt=""><figcaption></figcaption></figure>

* Next, save the Flow and activate it.

### Addition of the Rich Text field to the Service Report template

Now that your Flow is ready, go ahead and add the **SharinPix Images related list** on the Service Report Template by following the steps below:

* From Setup, search and select **Service Report Template**
* Click on the **Edit** link, next to the required template
* From the left menu, click on **Work Order**
* Drag and drop the **List** element onto the template

<figure><img src="../../.gitbook/assets/image (122).png" alt=""><figcaption></figcaption></figure>

* On the **List Properties** modal:
  * Enter **SharinPix Images** as the **Title**
  * Select **SharinPix Images** as the **Object**
  * From the **Available Fields** list, search and add the Formula field labeled as **Display Image Formula**

<figure><img src="../../.gitbook/assets/image (123).png" alt=""><figcaption></figcaption></figure>

* Click **OK** when done
* Then, click on **Save**

Your Service Report template is now ready!

### DEPRECATED: Creation of the Process Builder

This section is deprecated and is only used for Process Builder maintenance.

* Go to **Setup**. In the Quick Find Box, type **Process Builder**
* Under **Process Automation** , select **Process Builder**
* Click on New
* For the newly-created Process Builder:
  1. For the field, **Process Name** enter **Add Image to Rich Text Field on SharinPix Image**
  2. Enter a description of the process. (This step is optional)
  3. For the field, **The process starts when** select **A record changes**
  4. Click **Save**

Once on the Process Builder editor:

* Click on **Add Object**
  1. For the field **Object** , select **SharinPix Image**
  2. For the field **Start the process** , choose **when a record is created or edited**
  3. Click on **Save**
* Click on **Add Criteria**
  1. For the field **Criteria Name** , enter **No Criteria**
  2. For the field **Criteria for Executing Actions** , choose **No criteria—just execute the actions!**
  3. Click on **Save**
* Click on **Add Action**
  1. For the **Action Type** field, choose **Update Records**
  2. For the **Action Name** , enter **Update SharinPix Image Record**
  3. For the **Record Type** , select **Select the sharinpix\_\_SharinPixImage\_\_c record that started your process**
  4. Click on **Choose**

<figure><img src="../../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>

* Leave **Criteria for Updating Records** on **No criteria—just update the records!**
* Inside the **Set new field values for the records you update** section:

1. For the **Field** , select the Rich Text field created previously, that is **Display** **Image**
2. For the **Type** , select **Formula**
3. For the **Value** , click on **Build a formula**
4. Inside the formula builder, use the following formula:

**`<img src="" & [sharinpix__SharinPixImage__c].sharinpix__ImageURLThumbnail__c & "" />`**

<figure><img src="../../.gitbook/assets/image (125).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The above formula makes use of the field **\[sharinpix\_\_SharinPixImage\_\_c].sharinpix\_\_ImageURLThumbnail\_\_c** which stores the image's URL in a thumbnail format on the SharinPix Image object.
{% endhint %}

5\. Click on **Use this Formula**

* Click on **Save** when done.
