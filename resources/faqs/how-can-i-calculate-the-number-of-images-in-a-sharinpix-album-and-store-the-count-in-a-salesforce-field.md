# How can I calculate the number of images in a SharinPix Album and store the count in a Salesforce field?

This section demonstrates how to keep track of the number of images added to a SharinPix album and store the count in a Salesforce field automatically.

For such implementation, we will leverage the SharinPix Image Sync feature to track the image count.

When Image Sync is activated on an object, a related **SharinPix Image** record is created whenever an image is uploaded to the object's SharinPix album. The number SharinPix Image records created can then be used to count the number of images uploaded to the album.

There are two ways to track the number of images uploaded to a SharinPix album:

1. [By using a Rollup Helper from the AppExchange.](how-can-i-calculate-the-number-of-images-in-a-sharinpix-album-and-store-the-count-in-a-salesforce-field.md#using-a-rollup-helper)
2. [Or by using a Salesforce Flow to update the count and the Salesforce field.](how-can-i-calculate-the-number-of-images-in-a-sharinpix-album-and-store-the-count-in-a-salesforce-field.md#using-a-flow)

{% hint style="warning" %}
**Note:**

In both cases, Image Sync should be set up for the object on which you intend to keep an image count.

You can refer to the following article for detailed information about how to set up Image Sync for an object: [Setup SharinPix Image Sync](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/setup-sharinpix-image-sync)
{% endhint %}

For this demo, we will use the Account object as the SharinPix package already activate SharinPix Image Sync on the Account object by default.

However, kindly ensure that the option **Enable Image Sync** is checked for the SharinPix album added to the Account record page.

## Using a Rollup Helper

Rollup Helpers are available on the AppExhange. They usually provide an interface to easily create new rollups without any coding.

With a Rollup helper, we can therefore create data rollups by using the **Account** object and the **SharinPix Image** object. In this case, the Account object will act as the parent object on which the rollup results (that is, the image count) will be made available in a Salesforce field and the SharinPix Image will act as the child object from which the data for the image count will be obtained.

{% hint style="success" %}
**Tip:**

For more information about Rollup Helpers and how they can be used to create data rollups, refer to the following article:

[https://www.passagetechnology.com/rollup-helper-admin-guide](https://www.passagetechnology.com/rollup-helper-admin-guide)
{% endhint %}

## Using a Flow

Before creating the Flow, you will need to create a field that will store the count. Therefore, go on the Account object and create a new field with:

* The **Number** data type
* **Image Count** as label
* A default value of **0**

### Create a Flow to update count on record creation

Next, follow the steps below to create the Flow.

* Go to Setup. In the Quick Find Box, type **Flows**.
* Under **Process Automation** , select **Flows**.
* Click on the **New Flow** button.
* Select the option **Record-Triggered Flow** , and click on the **Create** button.

![](<.gitbook/assets/image - 2026-01-29T090023.964.png>)

* After clicking on _Create_ , the \_Configure Start \_modal will be displayed. Fill in the modal as indicated below:
  * **Select Object** : SharinPix Image
  * **Configure Trigger** : A record is created
  * For the **Set Entry Conditions** , select **All Conditions Are Met (AND)** and fill in the details as follows:
    1. **Field:** sharinpix\_\_Account\_\_c
    2. **Operator:** IsNull
    3. **Value**: Select **{!$GlobalConstant.False}**
  * **Optimize the Flow for** : Actions and Related Records
* Click on **Done** to save the configurations.

![](<.gitbook/assets/image - 2026-01-29T090406.360.png>)

* Next, add an **Update Triggering Record** element.

![](<.gitbook/assets/image - 2026-01-29T090454.277.png>)

![](<.gitbook/assets/image - 2026-01-29T090530.144.png>)

* On the \_Update Triggering Record \_modal, enter the following information:
  * **Label**: Update image count on Account Record
  * **How to Find Records to Update and Set Their Values:** Specify conditions to identify records, and set fields individually
  * **Object**: Account
  * In the **Field Account Records** section:
    * **Condition Requirements to Update Record:** All Conditions Are Met (AND)
    * **Field**: Id
    * **Operator:** Equals
    * **Value**: {!$Record.sharinpix\_\_Account\_\_c}
  * In the Set Field Values for the Account Records section:
    * For the **Field** , select the **Image Count** field available on the parent Account record.
    * For the **Value** , click on **New Resource** \_ \_ and enter the following information
      1. **Resource Type:** Formula
      2. **API Name**: imageCount
      3. Description: Optional
      4. **Date Type:** Number
      5. **Decimal Places:** 0
      6. **Formula**: `{!$Record.sharinpix__Account__r.Image_Count__c} + 1`

![](<.gitbook/assets/image - 2026-01-29T090629.676.png>)

* Save the newly-created resource.
* Click **Done** to save the _formula_ and the \_Update Triggering Record \_element.

![](<.gitbook/assets/image - 2026-01-29T090802.813.png>)

* Save the Flow and activate it.

### Create a Flow to update count on record deletion

* Create a new _Record-Triggered Flow_ that triggers on SharinPix Image record deletion.

![](<.gitbook/assets/image - 2026-01-29T090951.402.png>)

* Next, add and configure an **Update Triggering Record** element as explained in the section _Create a Flow to update count on record creation_.
* Change the **imageCount** formula to:

`{!$Record.sharinpix__Account__r.Image_Count__c}-1`

![](<.gitbook/assets/image - 2026-01-29T091228.106.png>)

* Save and activate the Flow.

## Demo

To test this new implementation:

* Go to an Account record
* Upload an image to the SharinPix album
* Check if the field **Image Count** has been updated accordingly

## DEPRECATED: Using a Process Builder

{% hint style="warning" %}
**Note:**

This is a deprecated section and is only used for Process Builder maintenance.
{% endhint %}

To create the Process Builder, follow the steps below:

* Go to Setup. In the Quick Find Box, type **Process Builder**
* Under **Process Automation** , select **Process Builder**
* Click on New
* For the newly-created Process Builder:
  1. For the field, **Process Name** enter **SharinPix Album Image Count on Account Object**
  2. Enter a description of the process. (This step is optional)
  3. For the field, **The process starts when** select **A record changes**
  4. Click **Save**

Once on the Process Builder editor:

* Click on **Add Object**
  1. For the field **Object**, select **SharinPix Image**
  2. For the field **Start the process**, choose **only when a record is created**
  3. Click on **Save**

![](<.gitbook/assets/image - 2026-01-29T093413.989.png>)

* Click on **Add Criteria**
  1. For the field **Criteria Name** , enter **No Criteria**
  2. For the field **Criteria for Executing Actions** , choose **No criteria—just execute the actions!**
  3. Click on **Save**

![](<.gitbook/assets/image - 2026-01-29T093506.550.png>)

* Click on **Add Action**
  1. For the **Action Type** field, choose **Update Records**
  2. For the **Action Name** , enter **Update Image Count**
  3. For the **Record Type** , select **Select a record related to the sharinpix\_\_SharinPixImage\_\_c**. Then from the dropdown menu, select **Account**
  4. Click on **Choose**

![](<.gitbook/assets/image - 2026-01-29T093601.595.png>)

* Leave **Criteria for Updating Records** on **No criteria—just update the records!**
* Inside the **Set new field values for the records you update** section:
  1. For the **Field** , select **Image Count**
  2. For the **Type** , select **Formula**
  3. For the **Value** , click on **Build a formula**
  4. Inside the formula builder, use the following formula:

`[sharinpix__SharinPixImage__c].sharinpix__Account__r.Image_Count__c + 1`

![](<.gitbook/assets/image - 2026-01-29T093637.095.png>)

5. Click on **Use this Formula**

![](<.gitbook/assets/image - 2026-01-29T093706.294.png>)

* Click on **Save** when done

You can now activate the Process Builder.
