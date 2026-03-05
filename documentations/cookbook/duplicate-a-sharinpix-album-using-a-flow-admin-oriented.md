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

# Duplicate a SharinPix album using a Flow (Admin-Oriented)

{% hint style="info" %}
This article demonstrates how to duplicate a SharinPix album using a Salesforce Flow.
{% endhint %}

For this demo, we will use the **Lead** and **Opportunity** objects.

The setup will be in such a way that when a Lead record is converted into an Opportunity, the Lead's album is duplicated to the Opportunity record.

{% hint style="info" %}
The SharinPix package includes the Apex class **DuplicateAlbum** which is used to duplicate SharinPix albums.
{% endhint %}

## Creation of the Flow

This section demonstrates how to create a Flow that invokes the Apex class, **DuplicateAlbum** to duplicate Lead albums onto converted Opportunity records.

To do so, follow the steps below:

* Go to Setup. In the Quick Find Box, type **Flows**.
* Under **Process Automation**, select **Flows**.
* Click on the **New Flow** button.
* Select the option **Record-Triggered Flow**, and click on the **Create** button.

<figure><img src="../.gitbook/assets/test (17).jpg" alt=""><figcaption></figcaption></figure>

* After clicking on _Create_, the _Configure Start_ modal will be displayed. Fill in the modal as indicated below:
  * **Select Object**: Lead
  * **Configure Trigger**: A record is created or updated
  * For the **Set Entry Conditions** section:
    1. &#x20;Select **All Conditions Are Met (AND)**
    2. For the **Field**, select **ConvertedOpportunityId**
    3. Select **Is Changed** for the **Equals** parameter
    4. Select **{!$GlobalConstant.True}** for the Value parameter
  * **When to Run the Flow for Updated Records**: Every time a record is updated and meets the condition requirements
  * **Optimize the Flow for**: Actions and Related Records
* Click on **Done** to save the configurations

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.12.30-12_59_01 (1).png>)

* Next, add an **Action** element.

{% hint style="danger" %}
**Warning:**

Starting with the Salesforce **Winter’26 release**, Apex Actions can no longer be executed directly in the **Run Immediately** path of a record-triggered flow. Instead, they must be placed in an **asynchronous path**, as the synchronous execution option is no longer supported.

For more details, please refer to the documentation here:\
[Unable to save a flow with an Apex Action after the Salesforce Winter ’26 release – What should I do?](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/i-am-unable-to-save-a-flow-with-an-apex-action-after-the-salesforce-winter-26-release-what-should-i)
{% endhint %}

<figure><img src="../.gitbook/assets/test (8).jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/test (9).jpg" alt=""><figcaption></figcaption></figure>

* On the _Action_ modal, use the search bar to find the **sharinpix\_\_DuplicateAlbum** Apex class.
* Click on **sharinpix\_\_DuplicateAlbum**.

<figure><img src="../.gitbook/assets/test (10).jpg" alt=""><figcaption></figcaption></figure>

* On the _Action_ modal for _sharinpix\_\_DuplicateAlbum_, populate the fields as indicated below:
  * **Label:** Duplicate Lead album
  * **Description:** Enter a description (optional)
  * **Destination Album ID**: {!$Record.ConvertedOpportunityId}
    * _Note: This is a mandatory field and refers to the converted Opportunity ID._
  * **Source Album ID**: {!$Record.Id}
    * _Note: This is a mandatory field and refers to the current Lead ID._
  *   **Include tags** (Optional): {!$GlobalConstant.True}

      * _Note: This is an additional variable that, when set to true, enables duplication of tags applied to the album's images as well. **To activate the same in the Flow, select the Include toggle first, then set the value of the 'Include tags' parameter to True as indicated below.**_

      <figure><img src="../.gitbook/assets/test (11).jpg" alt=""><figcaption></figcaption></figure>


* Click **Done** to save the _Action_ configurations.  &#x20;
* Save the Flow and activate it.

## Demo

To test the Flow:

* Go on a Lead record and upload some images to its corresponding SharinPix album
* Then, convert the Lead
* Go to the converted Opportunity record. The images previously uploaded on the Lead are now available on the converted Opportunity album

## DEPRECATED: Creation of the Process Builder

This section demonstrates how to create a Process Builder that invokes the Apex class **DuplicateAlbum** to rename an album.

To do so, follow the steps below:

* Go to Setup. In the Quick Find Box, type **Process Builder**
* Under **Process Automation**, select **Process Builder**
* Click on **New**
*   For the newly-created Process Builder:

    1. For the field, **Process Name** enter **SharinPix Duplicate Lead To Opportunity Album**
    2. Enter a description for the process (This step is optional)
    3. For the field, **The process starts when**, select **A record changes**
    4. Click **Save**

    <figure><img src="../.gitbook/assets/test (12).jpg" alt=""><figcaption></figcaption></figure>

Once on the Process Builder editor:

*   Click on **Add Object**

    1. For the field **Object** , select **Lead**
    2. For the field **Start the process** , choose **when a record is created or edited**
    3. Click on **Save**

    <figure><img src="../.gitbook/assets/test (13).jpg" alt=""><figcaption></figcaption></figure>
* Next, click on **Add Criteria**
  1. For the field **Criteria Name**, enter **On Lead to Opportunity conversion**
  2. For the field **Criteria for Executing Actions**, select **Conditions are met**
* Inside the **Set Conditions** section
  1. Choose **Converted Opportunity ID** as the field
  2. Then, select **Is Changed** as the operator, **Boolean** as the type, and **True** as the value
* Leave the field **Conditions** as **All of the conditions are met (AND)**

<figure><img src="../.gitbook/assets/test (14).jpg" alt=""><figcaption></figcaption></figure>

* Next, click on **Add Action**
  1. For the **Action Type**, choose **Apex**
  2. For the **Action Name**, enter **Duplicate Opportunity album**
  3. For the **Apex Class**, select **sharinpix\_\_DuplicateAlbum**
* Inside the **Set Apex Variables**:
  1. For the field **Destination Album ID**, choose **Field Reference** as the type. For the value, choose **Converted Opportunity ID**
  2. For the field **Source Album ID**, choose **Field Reference** as the type and **Lead ID** as the value

<figure><img src="../.gitbook/assets/test (15).jpg" alt=""><figcaption></figcaption></figure>

There is one additional variable available in the **Set Apex Variables** , namely, **Include tags** which, when set to true, enables duplication of tags applied to the album's images as well.

This variable is optional and can be accessed by clicking on the **Add Row** link inside the **Set Apex Variables** section.

<figure><img src="../.gitbook/assets/test (16).jpg" alt=""><figcaption></figcaption></figure>

* Click **Save** when done

You can now activate the Process Builder.

{% hint style="danger" %}
**Note:**

* The variables **Source Album ID** and **Destination Album ID** are compulsory and should therefore be filled in.
* The variable **Include tags** is optional and can therefore be ignored when not required.
{% endhint %}
