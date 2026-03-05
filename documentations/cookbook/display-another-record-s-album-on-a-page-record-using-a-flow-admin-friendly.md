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

# Display another record's album on a page record using a Flow (Admin-friendly)

{% hint style="info" %}
This article demonstrates how to display another record's album on a page record of an object using Flow. To do so we will:

1. Setup the Lookup relationship between the required objects
2. Create the Flow
3. Add the Flow onto the desired page record
{% endhint %}

## Setup of the Lookup relationship

In order to add another record's album onto your page record, you need to access the other record's ID. This ID will then be used as the album ID inside the Flow.&#x20;

One easy way to obtain the related record's ID is to create a Lookup relationship field to the related record. For example, if you intend to display the album of **Object1** onto the page record of **Object2**, you can create a Lookup relation to **Object1** on **Object2** so as to obtain **Object1**'s record ID.

For simplicity of this demo, we will use the **Account** object and the **Opportunity** object as the Opportunity object already has a Lookup relation to the Account object by default.&#x20;

## Creation of the Flow

To create the Flow, follow the steps below:

* Go to Setup then type Flow in the Quick Find box. Under Process Automation, select **Flows**.
* Click on **New Flow**. You will be then directed to the Flow Designer.
* Click on **Screen** **Flow**, then **Create**.

![](<../.gitbook/assets/screenshot-innovation-innovation-3077-dev-ed.lightning.force.com-2020.05.21-13_57_37 (1).png>)

* Go on the **Manager** tab then click on New Resource. Fill the fields as indicated below:
  * **Resource Type:** Variable
  * **API Name:** recordId
  * **Data Type:** Text
  * **Availability Outside the Flow:** Available for input
* Click **Done**
* Next, go to the **Elements** tab then drag and drop the **Get Records** element found under the Data section onto the blank canvas. Fill the fields as indicated below:
  * **Label:** getOpportunityRecord
  * **Object:** Opportunity
  * Conditions: **Id** (Field) **Equals** (operator) **{!recordId}** (that is, the newly-created resource named recordId)
  * In the **How Many Records to Store**, check the **Only the first record** option
  * In the **How to Store Record Data**, check the **Automatically store all fields** option
  * Click on **Done**

![](<../.gitbook/assets/screenshot-innovation-innovation-3077-dev-ed.lightning.force.com-2020.05.21-14_11_45 (1).png>)

* Click **Done**.
* Go to the Elements tab and drag and drop a **Screen** element next to the **Get Records** element.
* For the Screen element, do the following configurations:
  * For the field **Label**, enter **Account Album**.
  * For this demo, we do not need to display the Flow's header and footer. Therefore, you can uncheck the checkboxes for **Show Header** and **Show Footer** under the section named **Configure Frame.**
  * Next, drag and drop the **SharinPix Album** component onto he screen canvas as demonstrated below:

![](<../.gitbook/assets/screenshot-innovation-innovation-3077-dev-ed.lightning.force.com-2020.05.21-14_22_14_(1) (1).png>)

* Next, click on the SharinPix Album component on the screen canvas to access it's property on the right-hand side panel.
* On the same panel, configure the SharinPix Album's properties as follows:
  * **API Name:** getAccountAlbum
  * **AlbumId:** {!getOpportunityRecord.Account.Id}&#x20;

**Note:** The value, _{!getOpportunityRecord.Account.Id}_, points to the Id of the related Account.

![](<../.gitbook/assets/screenshot-innovation-innovation-3077-dev-ed.lightning.force.com-2020.05.21-14_33_51 (1).png>)

* Click **Done**.
* Connect the elements as shown below.

![](<../.gitbook/assets/screenshot-innovation-innovation-3077-dev-ed.lightning.force.com-2020.05.21-14_36_17 (1).png>)

* Save the newly-created flow as **Account Album on Opportunity Record** then activate same.

## Addition of the Flow on the page record

This section demonstrates how to add the newly-created flow on the Opportunity page record. To do so, follow the steps below:

* Go to an Opportunity record, then open the **Lightning App Builder**.
* Drag and drop a **Flow** component onto the page layout where desired.
* On the Flow component's properties, select **Account Album** as value for the field named **Flow**.

![](<../.gitbook/assets/screenshot-innovation-innovation-3077-dev-ed.lightning.force.com-2020.05.21-14_43_48 (1).png>)

* Click on **Save** when done.

The related Account album is now available on the Opportunity page record!

![](<../.gitbook/assets/screenshot-innovation-innovation-3077-dev-ed.lightning.force.com-2020.05.21-14_51_54 (1).png>)
