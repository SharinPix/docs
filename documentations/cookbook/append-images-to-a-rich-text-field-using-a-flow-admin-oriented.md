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

# Append images to a Rich Text field using a Flow (Admin-Oriented)

This article demonstrates how to append images to a Rich Text field using a Flow.

{% hint style="warning" %}
**Pre-requirements:**

For this demo, you should ensure that the SharinPix Image Sync feature is activated for the object you intend to use. For more information on how to set up the Image Sync, you can refer to the following article: [Setup SharinPix Image Sync](../image-sync/setup-sharinpix-image-sync.md)
{% endhint %}

In the following sections, we will use the **Account** object and configure an automation that will append images to a Rich Text whenever an Account record's type is changed to a specific value using the SharinPix Apex class, **SharinPixToRichTextAutomation**. To do so, we will use a [Salesforce Flow](append-images-to-a-rich-text-field-using-a-flow-admin-oriented.md#creation-of-the-flow)

The Apex class, **SharinPixToRichTextAutomation**, provides several fields that can be used to parameterize the Rich Text. The table below provides more details for each field:

| Field Name                     | Description                                                                                                                                                                                                                                                                                                                                                                                                         | Is Field Value Mandatory? |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| Record ID                      | The current record ID.                                                                                                                                                                                                                                                                                                                                                                                              | **Yes**                   |
| Rich Text Field API Name       | The **API name** of the target Rich Text field.                                                                                                                                                                                                                                                                                                                                                                     | **Yes**                   |
| Image URL Field API Name       | <p>The <strong>API name</strong> of the image URL field.<br>Some available values are:<br><strong>sharinpix__ImageURLFull__c</strong>,<br><strong>sharinpix__ImageURLOriginal__c</strong>,<br><strong>sharinpix__ImageURLThumbnail__c</strong>,<br><strong>sharinpix__ImageURLMini__c</strong><br>You can also create a custom image URL field on the <strong>SharinPix Image</strong> <strong>object</strong>.</p> | **Yes**                   |
| List of Image Public IDs       | <p>The list of <strong>public IDs</strong> of images to be included in the Rich Text field.<br>If no value is provided for this field, all images available on the record's album will be included in the Rich Text field.</p>                                                                                                                                                                                      | No                        |
| Replace Rich Text Area Content | When the value is set to **true**, the existing content of the target Rich Text Area will be replaced.                                                                                                                                                                                                                                                                                                              | No                        |
| Image Caption Text             | <p>The <strong>API name</strong> of the field containing the text to be displayed alongside the image.<br>Some accepted values here are any <strong>API name</strong> of <strong>Text</strong> fields <strong>available for the SharinPix Image object</strong> such as <strong>Name</strong>, <strong>sharinpix__Title__c</strong>, or <strong>Title &#x26; Description</strong>.</p>                              | No                        |
| Number of Columns              | <p>The number of columns to be included in the Rich Text field.<br>The default column value is <strong>1</strong> and the accepted value ranges from <strong>1</strong> to <strong>10</strong> columns.</p>                                                                                                                                                                                                         | No                        |

{% hint style="info" %}
The SharinPix package includes the Apex class **SharinPixToRichTextAutomation** which is used in Flows to append images to a Rich Text field.

Please note that this class is available in package version **1.194** and above. If your SharinPix package has an older version, you can refer to the following article to update it:

[How to update SharinPix package from the AppExchange?](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)
{% endhint %}

## Creation of the Flow

This section demonstrates how to create a **Flow** that invokes the Apex class **SharinPixToRichTextAutomation** to append images to a specific Rich Text field.

To do so, follow the steps below:

* On the **Account** object, create a new **Rich Text field** named **Images** (You can skip this step if you have already created the field in the previous section)
* Go to Setup. In the Quick Find Box, type **Flow**
* Under **Process Automation**, select **Flows**
* Click on the button **New Flow** located in the top right corner
* Select **Record-Triggered Flow** as the Flow type
* Once on the Flow builder, click on the **Edit** link located in the **Start** element

![](<../.gitbook/assets/test (77).png>)

* For the, **Trigger the Flow When**, section, select **A record is updated**
* For the, **Run the Flow section**, select **After the record is saved**

![](<../.gitbook/assets/test (78).png>)

* Next, click on the **Choose Object** button located on the **Start** element, then
  1. Choose **Account** as the object
  2. Leave the **Condition Requirements** section as **After the record is saved**
  3. Next, choose **Type** as the **field**, **Equals** as the **operator** and **Customer - Channel** as the **value**
  4. For the **When to Run the Flow for Updated Records** section, select **Only when a record is updated to meet the condition requirements**
  5. Click on **Done** to apply the changes
* Then, go to the **Manager** tab and click on the **New Resource** button to create a variable as follows:
  1. For the variable, select **Variable** as the **Resource Type**
  2. Enter **recordId** as the **API Name**
  3. Select **Text** as the **Data Type**
  4. For the **Availability Outside the Flow** section, select **Available for input**
  5. Click **Done** to save

![](<../.gitbook/assets/test (79).png>)

Next, drag and drop an **Assignment** element onto the canvas. For this element, enter the following details:

1. Enter **Assign Record ID** as the label
2. In the **Set Variable Values** section, enter recordId as the Variable, Equals as the operator and for the value, click o&#x6E;**$Record\_\_Prior** followed by **Id.**
3. Click on **Done** to save

![](<../.gitbook/assets/flow4 (1) (2).png>)

* Connect the **Assignment** element to the **Start** element
* Next, drag and drop an **Action** element
* In the **Action** search bar, search for **sharinpix\_\_SharinPixToRichTextAutomation**
* Enter **Append images to Rich Text** for the label
* In the **Set Input Values**, configure the fields as follows:
  1. For the field **Image URL Field API Name**, enter the desired image URL field's API name. For this example, the field **sharinpix\_\_ImageURLThumbnail\_\_c** was used
  2. For the field **Record** **ID**, choose the variable **recordId**
  3. For the field **Rich Text Field API Name**, enter the desired Rich Text field API name. In this case it is **Images\_\_c.**

![](<../.gitbook/assets/test (80).png>)

The fields **Image URL Field API Name**, Rich Text Field API Name, and Record ID are mandatory and must therefore always be provided with a value.

There are 4 additional **non-mandatory** fields that are also provided by the SharinPixToRichTextAutomation Apex class. You will find more information regarding these fields in the table available at the beginning of this article.

Let's add some of them by selecting the **Include** button and entering the required values as follows:

* For the **Image Caption Text** field, enter **Name**
* For the field, **Number of Columns**, enter the value **2**
* For the **Replace Rich Text Area Content**, select **{!$GlobalConstant.True}**
* Click **Done** to save

![](<../.gitbook/assets/test (81).png>)

{% hint style="success" %}
**Tips:**

* In the above example, we did not specify a predefined list of images to append to the Rich text. In this case, all images uploaded onto the record's album will be appended to the Rich Text by default.
* Contrary to Process Builders, Salesforce Flows also allow you to filter the images you want to add to the Rich Text. For example, if you only want SharinPix images having the **png** format to be appended, you can set up the Flow in such a way to store these images in a **Collection Variable** and pass the same variable as the value for the **List of Image Public IDs** field
{% endhint %}

* Connect the **Action** element to the **Assignment** element before saving and activating your Flow

![](<../.gitbook/assets/test (82).png>)

{% hint style="danger" %}
**Warning:**

Starting with the Salesforce **Winter’26 release**, Apex Actions can no longer be executed directly in the **Run Immediately** path of a record-triggered flow. Instead, they must be placed in an **asynchronous path**, as the synchronous execution option is no longer supported.

For more details, please refer to the documentation here:\
[Unable to save a flow with an Apex Action after the Salesforce Winter ’26 release – What should I do?](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/i-am-unable-to-save-a-flow-with-an-apex-action-after-the-salesforce-winter-26-release-what-should-i)
{% endhint %}

### Demo

To test the Flow:

* Go to an Account record
* In the record's **Details** section, change the value of the field **Type** to **Customer - Channel** to append the images to the Rich Text field.
* Check if the Rich Text field, **Images**, has been populated accordingly:

<figure><img src="../.gitbook/assets/test (83).png" alt=""><figcaption></figcaption></figure>

### DEPRECATED: Creation of the Process Builder <a href="#creation-of-the-process-builder" id="creation-of-the-process-builder"></a>

This section demonstrates how to create a Process Builder that invokes the Apex class **SharinPixToRichTextAutomation** to append images to a specific Rich Text field.

To do so, follow the steps below:

* On the **Account** object, create a new **Rich Text field** named **Images**&#x20;
* Go to Setup. In the Quick Find Box, type **Process Builder**
* Under **Process Automation**, select **Process Builder**
* Click on **New**
*   For the newly-created Process Builder:

    1. For the field, **Process Name**, enter **SharinPix - Append images to Rich Text field**
    2. Enter a description for the process (This step is optional)
    3. For the field, **The process starts when**, select **A record changes**
    4. Click **Save**

    <figure><img src="../.gitbook/assets/test (84).png" alt=""><figcaption></figcaption></figure>



Once on the Process Builder editor:

* Click on **Add Object**
  1. For the field **Object**, select **Account**
  2. For the field **Start the process**, choose **when a record is created or edited**
  3. Click on **Save**

<figure><img src="../.gitbook/assets/test (85).png" alt=""><figcaption></figcaption></figure>

* Next, click on **Add Criteria**
  1. For the field **Criteria Name**, enter **Account Type is Prospect**
  2. For the field **Criteria for Executing Actions**, select **Conditions are met**
* Inside the **Set Conditions** section
  1. Choose **Account Type** as the field
  2. Then, select **Equals** as the operator, **Picklist** as the type, and **Prospect** as the value
* Leave the field **Conditions** as **All of the conditions are met (AND)**
* Click on **Save** when done

<figure><img src="../.gitbook/assets/test (86).png" alt=""><figcaption></figcaption></figure>

* Next, click on **Add Action**
  1. For the **Action Type**, choose **Apex**
  2. For the **Action Name**, enter **Append images to Rich Text**
  3. For the **Apex Class**, select **sharinpix\_\_SharinPixToRichTextAutomation**
*   Inside the **Set Apex Variables**:

    1. For the field **Image URL Field API Name**, enter the desired image URL field's API name. For this example, the field **sharinpix\_\_ImageURLThumbnail\_\_c** was used. **Note:** Notice here that the type remains **String**. You only need to insert the field's API name
    2. For the field, **Rich Text Field API Name**, enter the desired Rich Text field API name. In this case, it is **Images\_\_c**. **Note:** Notice here that the type remains **String**. You only need to insert the field's API name
    3. For the field **Record ID**, choose **Field Reference** as the type and **Account ID** as the value<br>

    <figure><img src="../.gitbook/assets/test (87).png" alt=""><figcaption></figcaption></figure>

The fields **Image URL Field API Name**, **Rich Text Field API Name**, and **Record ID** are mandatory and therefore, should always be provided with a value.

There are 4 additional **non-mandatory** fields which are also provided by the **SharinPixToRichTextAutomation** Apex class. You will find more information regarding these fields in the table available at the beginning of this article.&#x20;

Let's configure some of these parameters in our Process Builder:

* To access the parameters, click on the **+ Add Row** link within the **Set Apex Variables** section
  1. Add the field, **Image Caption Text**, and enter **Name** as the value. **Note:** Notice here that the type remains **String**. You only need to insert the field's API name
  2. Add the field **Replace Rich Text Area Content** and enter **True** as the value
  3.  For this demo, we will add a list of pre-defined images to the PDF. Therefore, add the field **List of Image Public IDs** and enter the image public IDs of the desired images as follows: \["\<First image's Public ID>","\<Second image's Public ID>","\<Third image's Public ID>","\<Forth image's Public ID>"]

      Here is an example:

      \["cb3cac5e-17fa-480c-b85f-085c78b8a3ec","cb3cac5e-17fa-480c-b85f-085c78b8a2ee","cb3cac5e-17fa-480c-b85f-085c78b8a4ff","cb3cac5e-17fa-480c-b85f-085c78b8a6gt"]
* Click on **Save** when done

<figure><img src="../.gitbook/assets/test (88).png" alt=""><figcaption></figcaption></figure>

You can now activate the Process Builder.<br>
