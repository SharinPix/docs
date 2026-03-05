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

# Generate SharinPix PDFs Automatically

{% hint style="info" %}
This article demonstrates how to generate a PDF using a Salesforce Flow or an Apex Batch.
{% endhint %}

{% hint style="warning" %}
**Pre-requirements:**

* For this demo, you should ensure that the SharinPix Image Sync feature is activated for the object you intend to use. For more information on how to set up the Image Sync, you can refer to the following article: [Setup SharinPix Image Sync](../image-sync/setup-sharinpix-image-sync.md)
* You should also ensure that the SharinPix Permission Set named, **SharinPix Lightning Components**, has been assigned to all users intending to use the configurations described in this article to generate PDFs.
{% endhint %}

In the following sections, we will use the **Account** object to generate a PDF whenever an Account record's type is changed to a specific value using the SharinPix Apex class, **SharinPixToPdfAutomation**, in [a Salesforce Flow](generate-sharinpix-pdfs-automatically.md#creation-of-the-flow) (Admin-Oriented).

We will also cover how to generate PDF files on multiple records using [Apex Batch](generate-sharinpix-pdfs-automatically.md#apex-batch-implementation-developer-oriented) (Developer-Oriented).

The Apex class, **SharinPixToPdfAutomation**, provides several fields that can be used to parametrize the PDF template. The table below provides more details for each field:

| Field Name               | Description                                                                                                                                                                                                                                                                                                                                                                                                          | Is Field Value Mandatory? |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| Record ID                | The current record ID.                                                                                                                                                                                                                                                                                                                                                                                               | **Yes**                   |
| Image URL Field API Name | <p>The <strong>API name</strong> of the image URL field.<br>Some available values are:<br><strong>sharinpix__ImageURLFull__c</strong>, <br><strong>sharinpix__ImageURLOriginal__c</strong>,<br><strong>sharinpix__ImageURLThumbnail__c</strong>,<br><strong>sharinpix__ImageURLMini__c</strong><br>You can also create a custom image URL field on the <strong>SharinPix Image</strong> <strong>object</strong>.</p> | **Yes**                   |
| List of Image Public IDs | <p>The list of <strong>image public IDs</strong> of images to be included in the PDF.<br>If no value is provided for this field, all images available on the record's album will be included in the PDF.</p>                                                                                                                                                                                                         | No                        |
| Number of Columns        | <p>The number of columns to be included in the PDF.<br>The default column value is <strong>2</strong> and the accepted value ranges from <strong>1</strong> to <strong>12</strong> columns.</p>                                                                                                                                                                                                                      | No                        |
| Image Caption Text       | <p>The <strong>API name</strong> of the field containing the text to be displayed alongside the image.<br>Some accepted values here are any <strong>API name</strong> of <strong>Text</strong> fields <strong>available for the SharinPix Image object</strong> such as <strong>Name</strong>, <strong>sharinpix__Title__c</strong> or <strong>Title &#x26; Description</strong>.</p>                                | No                        |
| First Page Content       | The **API name(s)** of the **Rich Text** field(s) containing the first-page content. The Rich Text fields should be delimited by semi-colons.                                                                                                                                                                                                                                                                        | No                        |
| Last Page Content        | The **API name(s)** of the **Rich Text** field(s) containing the last page content. The Rich Text fields should be delimited by semi-colons.                                                                                                                                                                                                                                                                         | No                        |
| Images' Pre-description  | The **API name(s)** of **Rich Text** field(s) containing the pre-description of images. The Rich Text fields should be delimited by semi-colons.                                                                                                                                                                                                                                                                     | No                        |
| Images' Post-description | The **API name(s)** of **Rich Text** field(s) containing the post-description of images. The Rich Text fields should be delimited by semi-colons.                                                                                                                                                                                                                                                                    | No                        |
| Page Orientation         | <p>The PDF page orientation.<br>The default value is <strong>portrait</strong> and the accepted values are <strong>portrait</strong> and <strong>landscape</strong>.</p>                                                                                                                                                                                                                                             |                           |
| Single Image Per Page    | The option specifies whether the PDF must contain a **single image per page**.                                                                                                                                                                                                                                                                                                                                       | No                        |
| Footer Format            | <p>The footer's format. The following merged fields can be used to specify the page numbering as follows, current page: {pagenumber} and total pages: {pagecount}.<br>One example is <strong>Page {pagenumber} of {pagecount}</strong> which translates to something like <strong>Page 1 of 12</strong>.</p>                                                                                                         | No                        |
| Filename Field           | The API name of the field which will contain the filename to be used for the generated PDF.                                                                                                                                                                                                                                                                                                                          | No                        |

{% hint style="info" %}
The SharinPix package includes the Apex class **SharinPixToPdfAutomation** which is used in Flows to generate PDFs.

Please note that this class is available in package version **1.193** and above. If your SharinPix package has an older version, refer to the following article to update the same:

[How to update SharinPix package from the AppExchange?](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)
{% endhint %}

### Creation of the Salesforce Flow <a href="#creation-of-the-flow" id="creation-of-the-flow"></a>

This section demonstrates how to create a **Flow** that invokes the Apex class **SharinPixToPdfAutomation** to generate a PDF.

To do so, follow the steps below:

* Go to Setup. In the Quick Find Box, type **Flow**
* Under **Process Automation**, select **Flows**
* Click on the button **New Flow** located on the top right corner
* Select **Record-Triggered Flow** as the Flow type
* Once on the Flow builder, click on the **Edit** link located in the **Start** element

<figure><img src="../.gitbook/assets/test (31).png" alt=""><figcaption></figcaption></figure>

* For the, **Trigger the Flow When** , section, select **A record is updated**
* For the, **Run the Flow section** , select **After the record is saved**

<figure><img src="../.gitbook/assets/image (29) (4).png" alt=""><figcaption></figcaption></figure>

* Next, click on the **Choose Object** button located on the **Start** element, then
  1. Choose **Account** as the object
  2. Leave the **Condition Requirements** section as **After the record is saved**
  3. Next, choose **Type** as the **field**, **Equals** as the **operator** and **Customer - Channel** as the **value**
  4. For the **When to Run the Flow for Updated Records** section, select **Only when a record is updated to meet the condition requirements**
  5. Click on **Done** to apply the changes
*   Then, go to the **Manager** tab and click on the **New Resource** button to create a variable as follows:

    1. For the variable, select **Variable** as the **Resource Type**
    2. Enter **recordId** as the **API Name**
    3. Select **Text** as the **Data Type**
    4. For the **Availability Outside the Flow** section, select **Available for input**
    5. Click **Done** to save

    <figure><img src="../.gitbook/assets/test (32).png" alt=""><figcaption></figcaption></figure>


*   Next, drag and drop an **Assignment** element onto the canvas. For this element, enter the following details:

    1. Enter **Assign Record ID** as the label
    2. In the **Set Variable Values** section, enter recordId as the Variable, Equals as the operator and for the value, click on **$Record\_\_Prior** followed by **Id**
    3. Click on **Done** to save

    <figure><img src="../.gitbook/assets/test (33).png" alt=""><figcaption></figcaption></figure>


* Connect the **Assignment** element to the **Start** element
* Next, drag and drop an **Action** element
* In the **Action** search bar, search for **sharinpix\_\_SharinPixToPdfAutomation**&#x20;
* Enter **PDF Generation** for the label
*   In the **Set Input Values**, configure the fields as follows:

    1. For the field **Image URL Field API Name**, enter the desired image URL field's API name. For this example, the field **sharinpix\_\_ImageURLThumbnail\_\_c** was used
    2. For the field **Record ID**, choose the variable **recordId**



    <figure><img src="../.gitbook/assets/test (34).png" alt=""><figcaption></figcaption></figure>

The fields **Image URL Field API Name** and **Record ID** are mandatory and therefore, should always be provided with a value.

There are 11 additional **non-mandatory** fields which are also provided by the **SharinPixToPdfAutomation** Apex class. You will find more information regarding these fields in the table available at the beginning of this article.

Let's add some of them by selecting the **Include** button and entering the required values as follows:

* For the field **Footer Format**, enter **Page {pagenumber} of {pagecount}** as value
* For the **Image Caption Text** field, enter **Name**
* For the field, **Number of Columns**, enter the value **3**
* For the **Page Orientation**, enter **landscape**
* Click **Done** to save

<figure><img src="../.gitbook/assets/test (35).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tips:**

* In the above example, we did not specify a list of pre-defined images to be added to the PDF. In this case, all images uploaded onto the record's album will be included in the PDF by default.
* If you want to filter the images to be included in the PDF, for instance, including only images of type **png**, you can set up the Flow in such a way as to store these images in a **Collection Variable** and pass the same variable as the value for the **List of Image Public IDs** field
{% endhint %}

* Connect the **Action** element to the **Assignment** element before saving and activating your Flow



<figure><img src="../.gitbook/assets/test (36).png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
**Warning:**\
Starting with the Salesforce **Winter ’26 release**, Apex Actions can no longer be executed directly in the **Run Immediately** path of a record-triggered flow. Instead, they must be placed in an **asynchronous path**, as the synchronous execution option is no longer supported.

For more details, please refer to the documentation here:\
[Unable to save a flow with an Apex Action after the Salesforce Winter ’26 release – What should I do?](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/i-am-unable-to-save-a-flow-with-an-apex-action-after-the-salesforce-winter-26-release-what-should-i)&#x20;
{% endhint %}

#### Demo <a href="#demo_1" id="demo_1"></a>

To test the Flow:

* Go on an Account record
* In the record's **Details** section, change of the value of the field **Type** to **Customer - Channel** to trigger the PDF generation using the Flow
* To view the generated PDF, go to the **Notes & Attachments** section found in the record's **Related** section:&#x20;

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.03.29-12_56_46 (1) (1).png>)

![](<../.gitbook/assets/image (30) (3).png>)

{% hint style="warning" %}
**Notes:**

* Generating a PDF with many images may take several minutes before completion.
* In some cases, you are required to refresh your page to access the PDF in the **Notes & Attachment** section.
{% endhint %}

## Apex Batch Implementation (Developer-Oriented)

The **SharinPixToPdfAutomation** class includes the method **performAsync** (available in versions 1.205 and above)  which can be used to generate PDF files on multiple records.

The **performAsync** method takes as parameter, variables from an inner class named **Params** as demonstrated in the code snippet below:

```apex
sharinpix.SharinPixToPdfAutomation.Params params = new sharinpix.SharinPixToPdfAutomation.Params();
    
params.recordId = acc.Id;
params.imageUrlFieldApiName = 'sharinpix__ImageURLThumbnail__c';
                
SharinPixToPdfAutomation.performAsync(params);
```

The variables available in the **Params** inner class are as follows:

| Variable API Name                                                                              | Description                                                                                                                                                                                                                                                                                                                                                                                                          |
| ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>recordId</p><p><mark style="color:red;">(This variable is mandatory)</mark></p>             | The record ID.                                                                                                                                                                                                                                                                                                                                                                                                       |
| <p>imageUrlFieldApiName</p><p><mark style="color:red;">(This variable is mandatory)</mark></p> | <p>The <strong>API name</strong> of the image URL field.<br>Some available values are:<br><strong>sharinpix__ImageURLFull__c</strong>, <br><strong>sharinpix__ImageURLOriginal__c</strong>,<br><strong>sharinpix__ImageURLThumbnail__c</strong>,<br><strong>sharinpix__ImageURLMini__c</strong><br>You can also create a custom image URL field on the <strong>SharinPix Image</strong> <strong>object</strong>.</p> |
| imageIds                                                                                       | The list of image public IDs of images to be included in the PDF.If no value is provided for this field, all images available on the record's album will be included in the PDF.                                                                                                                                                                                                                                     |
| columns                                                                                        | The number of columns to be included in the PDF. The default column value is 2 and the accepted value ranges from 1 to 12 columns.                                                                                                                                                                                                                                                                                   |
| imageCaptionText                                                                               | <p>The <strong>API name</strong> of the field containing the text to be displayed alongside the image.<br>Some accepted values here are any <strong>API name</strong> of <strong>Text</strong> fields <strong>available for the SharinPix Image object</strong> such as <strong>Name</strong>, <strong>sharinpix__Title__c</strong> or <strong>Title &#x26; Description</strong>.</p>                                |
| firstPageFieldApiName                                                                          | The API name(s) of the Rich Text field(s) containing the first-page content. The Rich Text fields should be delimited by semi-colons.                                                                                                                                                                                                                                                                                |
| lastPageFieldApiName                                                                           | The API name(s) of the Rich Text field(s) containing the last page content. The Rich Text fields should be delimited by semi-colons.                                                                                                                                                                                                                                                                                 |
| preDescriptionFieldApiName                                                                     | The API name(s) of the Rich Text field(s) containing the pre-description of images. The Rich Text fields should be delimited by semi-colons.                                                                                                                                                                                                                                                                         |
| postDescriptionFieldApiName                                                                    | The API name(s) of the Rich Text field(s) containing the post-description of images. The Rich Text fields should be delimited by semi-colons.                                                                                                                                                                                                                                                                        |
| orientation                                                                                    | The PDF page orientation. The default value is **portrait** and the accepted values are **portrait** and **landscape**.                                                                                                                                                                                                                                                                                              |
| singleImagePerPage                                                                             | This option specifies whether the PDF must contain a single image per page.                                                                                                                                                                                                                                                                                                                                          |
| footer                                                                                         | The footer's format. The following merged fields can be used to specify the page numbering as follows, current page: {pagenumber} and total pages: {pagecount}. One example is Page {pagenumber} of {pagecount} which translates to something like Page 1 of 12.                                                                                                                                                     |
| filenameFieldApiName                                                                           | The API name of the field containing the filename to be used for the generated PDF.                                                                                                                                                                                                                                                                                                                                  |

The example below demonstrates how the **performAsync** method can be used in a Batch to generate PDFs on multiple Account records:

```apex
public class myBatch implements Database.Batchable<sObject>, Database.AllowsCallouts {
	public Database.QueryLocator start(Database.BatchableContext bc) {
        return Database.getQueryLocator('SELECT Id FROM Account WHERE NumberOfEmployees > 100');
    }

    public void execute(Database.BatchableContext bc, List<Account> scope){
        sharinpix.SharinPixToPdfAutomation.Params params = new sharinpix.SharinPixToPdfAutomation.Params();
        for(Account acc : scope) {
            params.recordId = acc.Id;
            params.imageUrlFieldApiName = 'sharinpix__ImageURLThumbnail__c';
            sharinpix.SharinPixToPdfAutomation.performAsync(params);
        }
    }

    public void finish(Database.BatchableContext bc){
    }
}
```

{% hint style="danger" %}
When running the batch, the number of records to be passed in the Database.executeBatch method should be limited to **one**: `Database.executeBatch(new myBatch(), 1);`
{% endhint %}

{% hint style="warning" %}
**Notes:**

* Generating a PDF with many images may take several minutes before completion.
* In some cases, you are required to refresh your page to access the PDF in the **Notes & Attachment** section.
{% endhint %}

{% hint style="danger" %}
Salesforce is retiring Process Builders at the end of 2022. More information here: [Go with the Flow: What’s Happening with Workflow Rules and Process Builder?](https://admin.salesforce.com/blog/2021/go-with-the-flow-whats-happening-with-workflow-rules-and-process-builder)

For **maintenance** of previous configurations of SharinPix PDF in Process Builders, kindly refer to the following section.
{% endhint %}

## DEPRECATED: Creation of the Process Builder

This section demonstrates how to create a Process Builder that invokes the Apex class **SharinPixToPdfAutomation** to generate a PDF.

To do so, follow the steps below:

* Go to Setup. In the Quick Find Box, type **Process Builder**
* Under **Process Automation**, select **Process Builder**
* Click on **New**
*   For the newly-created Process Builder:

    1. For the field, **Process Name**, enter **SharinPix Automated PDF Generation**
    2. Enter a description for the process (This step is optional)
    3. For the field **The process starts when**, select **A record changes**
    4. Click **Save**

    <figure><img src="../.gitbook/assets/test (38).png" alt=""><figcaption></figcaption></figure>

Once on the Process Builder editor:

*   Click on **Add Object**

    1. For the field **Object** , select **Account**
    2. For the field **Start the process** , choose **when a record is created or edited**
    3. Click on **Save**

    <figure><img src="../.gitbook/assets/test (39).png" alt=""><figcaption></figcaption></figure>


* Next, click on **Add Criteria**
  1. For the field **Criteria Name**, enter **Account Type is Prospect**
  2. For the field **Criteria for Executing Actions**, select **Conditions are met**
* Inside the **Set Conditions** section
  1. Choose **Account Type** as the field
  2. Then, select **Equals** as the operator, **Picklist** as the type and **Prospect** as the value
* Leave the field **Conditions** as **All of the conditions are met (AND)**
* Click on **Save** when done

<figure><img src="../.gitbook/assets/test (40).png" alt=""><figcaption></figcaption></figure>

* Next, click on **Add Action**
  1. For the **Action Type**, choose **Apex**
  2. For the **Action Name**, enter **Generate PDF**
  3. For the **Apex Class**, select **sharinpix\_\_SharinPixToPdfAutomation**
*   Inside the **Set Apex Variables**:

    1. For the field **Image URL Field API Name**, enter the desired image URL field's API name. For this example, the field **sharinpix\_\_ImageURLThumbnail\_\_c** was used. **Note:** Notice here that the type remains **String**. You only need to insert the field's API name
    2. For the field **Record ID**, choose **Field Reference** as the type and **Account ID** as the value

    <figure><img src="../.gitbook/assets/test (41).png" alt=""><figcaption></figcaption></figure>

The fields **Image URL Field API Name** and **Record ID** are mandatory and therefore, should always be provided with a value.

There are 11 additional **non-mandatory** fields which are also provided by the **SharinPixToPdfAutomation** Apex class. You will find more information regarding these fields in the table available at the beginning of this article.&#x20;

Let's configure some of these parameters in our Process Builder:

* To access the parameters, click on the **+ Add Row** link within the **Set Apex Variables** section
  1. Add the field, **Image Caption Text** and enter **Name** as the value. **Note:** Notice here that the type remains **String**. You only need to insert the field's API name
  2. For this demo, we will add a list of pre-defined images to the PDF. Therefore, add the field **List of Image Public IDs** and enter the **image public IDs** of the desired images as follows: \["\<First image's Public ID>","\<Second image's Public ID>","\<Third image's Public ID>","\<Forth image's Public ID>"]

Here is an example:

\["cb3cac5e-17fa-480c-b85f-085c78b8a3ec","cb3cac5e-17fa-480c-b85f-085c78b8a2ee","cb3cac5e-17fa-480c-b85f-085c78b8a4ff","cb3cac5e-17fa-480c-b85f-085c78b8a6gt"]

&#x20;  3\.  Add the field, **Footer Format** and **Page {pagenumber} of {pagecount}** enter the as the value

* Click on **Save** when done

<figure><img src="../.gitbook/assets/test (43).png" alt=""><figcaption></figcaption></figure>
