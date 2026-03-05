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

# Rename a SharinPix album using a Flow (Admin-Oriented)

This article demonstrates how to rename a SharinPix album using a Salesforce Flow.

For this demo, we will use the **Lead** and **Opportunity** objects.

The setup will be in such a way that when a Lead record is converted into an Opportunity, the Lead's album is copied to the Opportunity record.

{% hint style="info" %}
The SharinPix package includes the Apex class **RenameAlbum** which is used to rename SharinPix albums.
{% endhint %}

## Creation of the Flow

This section demonstrates how to create a Flow that invokes the Apex class, **RenameAlbum** in order to rename albums on Lead records and copy them to the converted Opportunity record.

To do so, follow the steps below:

* Go to Setup. In the Quick Find Box, type **Flows**.
* Under **Process Automation**, select **Flows**.
* Click on the **New Flow** button.
* Select the option **Record-Triggered Flow**, and click on the **Create** button.

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

* After clicking on _Create_, the _Configure Start_ modal will be displayed. Fill in the modal as indicated below:
  * **Select Object**: Lead
  * **Configure Trigger**: A record is created or updated
  * For the **Set Entry Conditions** section:
    1. &#x20;Select **All Conditions Are Met (AND)**
    2. For the **Field**, select **ConvertedOpportunityId**
    3. Select **Is Changed** for the **Equals** parameter
    4. Select **{!$GlobalConstant.True}** for the Value parameter
  * **When to Run the Flow for Updated Records**: Every time a record is updated and meets the condition requirements<br>
  * **Optimize the Flow for**: Actions and Related Records
* Click on **Done** to save the configurations.

![](<../.gitbook/assets/image (47) (3).png>)

* Next, add an **Action** element.

{% hint style="danger" %}
**Warning:**

Starting with the Salesforce **Winter’26 release** , Apex Actions can no longer be executed directly in the **Run Immediately** path of a record-triggered flow. Instead, they must be placed in an **asynchronous path** , as the synchronous execution option is no longer supported.

For more details, please refer to the documentation here:\
[_Unable to save a flow with an Apex Action after the Salesforce Winter ’26 release – What should I do?_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/i-am-unable-to-save-a-flow-with-an-apex-action-after-the-salesforce-winter-26-release-what-should-i)
{% endhint %}

![](<../.gitbook/assets/image (45) (3).png>)

![](<../.gitbook/assets/image (48) (3).png>)

* On the \_Action \_modal, use the search bar to find the **sharinpix\_\_RenameAlbum**\*\* \*\* Apex class.
* Click on **sharinpix\_\_RenameAlbum**.

![](<../.gitbook/assets/image (49) (3).png>)

* On the _Action_ modal for _sharinpix\_\_RenameAlbum_, populate the fields as indicated below:
  * **Label:** Rename Lead album
  * **Description:** Enter a description (optional)
  * **Current Album ID**: {!$Record.Id}
    * _Note: This is a mandatory field and refers to the current Lead ID._
  * **New Album ID**: {!$Record.ConvertedOpportunityId}
    * _Note: This is a mandatory field and refers to the converted Opportunity ID._

![](<../.gitbook/assets/image (50) (3).png>)

* Click **Done** to save the _Action_ configurations.  &#x20;
* Save the Flow and activate it.

## Demo

To test the Flow:

* Go on a Lead record and upload some images to its corresponding SharinPix album.
* Then, convert the Lead.
* Go to the converted Opportunity record. The images previously uploaded on the Lead are now available on the converted Opportunity album.

{% hint style="success" %}
**Tip:**

This implementation can also be used when attempting to copy a SharinPix Album integrated on a website to a Salesforce record.

For example, suppose you want to copy the album from the website to a Lead record, here you will need to capture the ID of the album found on the website and store the same as a temporary ID in a Salesforce field on the Lead object. Then, create a Flow that invokes the method **RenameAlbum** to perform the renaming. In this case, the **Current Album ID** will be the temporary ID and the **New Album ID** will be the Lead record's ID.
{% endhint %}

## DEPRECATED: Creation of the Process Builder

This section demonstrates how to create a Process Builder that invokes the Apex class **RenameAlbum** to rename an album.

To do so, follow the steps below:

* Go to Setup. In the Quick Find Box, type **Process Builder**
* Under **Process Automation**, select **Process Builder**
* Click on **New**
* For the newly-created Process Builder:
  1. For the field, **Process Name** enter **SharinPix Rename Lead To Opportunity Album**
  2. Enter a description for the process (This step is optional)
  3. For the field **The process starts when**, select **A record changes**
  4. Click **Save**

![](<../.gitbook/assets/screenshot-spooncomp-dev-ed.lightning.force.com-2020.06.19-11_50_29 (1).png>)

Once on the Process Builder editor:

* Click on **Add Object**
  1. For the field **Object**, select **Lead**
  2. For the field **Start the process**, choose **when a record is created or edited**
  3. Click on **Save**

![](<../.gitbook/assets/image (51) (3).png>)

* Next, click on **Add Criteria**
  1. For the field **Criteria Name**, enter **On Lead to Opportunity conversion**
  2. For the field **Criteria for Executing Actions**, select **Conditions are met**
* Inside the **Set Conditions** section
  1. Choose **Converted Opportunity ID** as the field
  2. Then, select **Is Changed** as the operator, **Boolean** as the type and **True** as the value
* Leave the field **Conditions** as **All of the conditions are met (AND)**

![](<../.gitbook/assets/image (52) (3).png>)

* Next, click on **Add Action**
  1. For the **Action Type**, choose **Apex**
  2. For the **Action Name**, enter **Rename Opportunity album**
  3. For the **Apex Class**, select **sharinpix\_\_RenameAlbum**
* Inside the **Set Apex Variables**:
  1. For the field **New Album ID**, choose **Field Reference** as the type. For the value, choose **Converted Opportunity ID**
  2. For the field **Current Album ID**, choose **Field Reference** as the type and **Lead ID** as the value

<figure><img src="../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

* Click **Save** when done

You can now activate the Process Builder.
