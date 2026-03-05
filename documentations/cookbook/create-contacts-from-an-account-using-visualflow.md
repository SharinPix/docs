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

# Create Contacts from an Account using VisualFlow

In this demo, we will see how it is possible to create one or multiple **Contact** records from a particular **Account** record and upload a profile picture corresponding to **SharinPix Album** for each newly-created **Contact** record.

[1. Overview](create-contacts-from-an-account-using-visualflow.md#id-1.-overview)

[2. Creating the Flow](create-contacts-from-an-account-using-visualflow.md#id-2.-creating-the-flow)

[3. Implementing the Visualforce Page](create-contacts-from-an-account-using-visualflow.md#id-3.-implementing-the-visualforce-page)

[4. Implementing the Apex Controller](create-contacts-from-an-account-using-visualflow.md#id-4.-implementing-the-apex-controller)

[5. Implementing the custom action](create-contacts-from-an-account-using-visualflow.md#id-5.-implementing-the-custom-action)

[6. The Flow in action](create-contacts-from-an-account-using-visualflow.md#id-6.-the-flow-in-action)

## 1. Overview

To implement the present demo, we will reference a **Visual Flow** inside a **Visualforce Page**.  Before we dive into its technical implementation, the following steps provide a high-level overview of the objective we want to achieve in this demo:

**Visual Flow:**

1. Look up the **Id** of Account Record from which the Screen Flow was launched.
2. Display the input fields to so as to create the **Contact** record(s) while using the **Account Id** (collected in the previous step) in order to create a **LookUp** **relationship** between the **Account** and the recently-created **Contact** record(s).
3. Display the **SharinPix Album** for the user to upload the profile picture of the newly-created **Contact(s).**

**Visualforce Page:**

4\. Reference the newly-created **Flow** inside a **Visualforce Page.**

**Account Page-Layout:**

5\. Create a **custom action** to launch the **Visualforce Page** created in the previous step.

6\. Add the custom action to the Account's **page-layout.**&#x20;

## 2. Creating the Flow

* Navigate to **Setup**. In the **Quick Find** box, type **flows.**
* Under **Process Automation**,  click on **Flows**.
* Click on the **New Flow** button.
* Inside the **Flow Designer**, under section **DATA,** of the **Palette** tab, drag the **Fast Lookup** element onto the canvas.

<figure><img src="../.gitbook/assets/test (46).png" alt=""><figcaption></figcaption></figure>

In the **Fast Lookup** modal (as shown in the screenshot below), enter values for these input fields:

* &#x20;**Name:** a name of your choice (in this case it is **Account Lookup**)
* **Look up**: the parent object from which to lookup the **Id** (in this case it is **Account**).
* **Variable:** the name of the SObject variable. (You need to create a **SObject variable** first).

<figure><img src="../.gitbook/assets/test (47).png" alt=""><figcaption></figcaption></figure>

* **Fields:** the field value of the object we want to store in the **SObject variable** we created.(In this case, its **Id**)

<figure><img src="../.gitbook/assets/test (48).png" alt=""><figcaption></figcaption></figure>

We will use a **screen,** to display the input fields for a Contact's **First Name** and **Last Name.**

* Under section **USER INTERFACE,** drag a **screen** element onto the canvas.

Fill in the following values for the newly-created **screen** element:

* **Name:** Name of the screen element (in this case it is **Display SharinPix Screen**)

<figure><img src="../.gitbook/assets/test (49).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/test (50).png" alt=""><figcaption></figcaption></figure>

* Add a **Textbox** field to collect the **First Name** of the **Contact**. (in this case labelled **First Name**)

<figure><img src="../.gitbook/assets/test (51).png" alt=""><figcaption></figcaption></figure>

* Add a **Textbox** field to collect the **Last Name** of the **Contact** (in this case labelled **Last Name**)

![](<../.gitbook/assets/test (52).png>)

* Connect the **Fast Lookup** to the newly-created **screen** element as shown below. Make sure the **Fast Lookup** element is **set as the start element** by clicking on the **downward-facing green arrow icon**.

![](<../.gitbook/assets/test (53).png>)

* Under section **DATA**, drag the **Record Create** element onto the canvas.

![](<../.gitbook/assets/test (54).png>)

Fill in the values for the **Record Create** element as shown below. The role of the **Record Create** element is to create a **Contact** by specifying its first and last name as well the Account Id so as to establish a lookup relationship between the newly-created Contact record and the Account record from which the **Flow** was launched.

* **Name:** The **Name** of the Record Create element. (in this case it is **CreateContact**)
* **Assignments:**
  * **Create:** The **SObject Type** to create. (in this case it **Contact**)**.**
  * **Fields**:
    * **AccountId** with **value: {! Id },** which corresponds to the variable obtained by the previously-created **Fast Lookup element.**
    * **FirstName** with **value: {! First\_Name }** which corresponds to the input Textbox element found in the previously-created **screen element**.
    * **LastName** with **value: {! Last\_Name }** which corresponds to the input Textbox element found in the previously-created **screen element.**

In the last area, after the creation of the **Contact** record, the Id of the newly-created record, needs to be stored inside a variable so that it can be easily referenced within the flow. In the present context, a variable named **AlbumId** has been created and assigned the Id of the newly-created Contact as shown below.

<figure><img src="../.gitbook/assets/test (55).png" alt=""><figcaption></figcaption></figure>

Click on **OK** when you're done.

Under the **LOGIC** section, drag and drop the **Assignment** element onto the canvas. This element is meant to be used as a flag that will enable or disable the rendering of the **SharinPix Visualforce Component** present on the Visualforce Page implemented in the [next section](create-contacts-from-an-account-using-visualflow.md#id-3.-implementing-the-visualforce-page).

Before we proceed, we need to create a **Boolean variable**.

* Go to the **Resources tab**.
* Under section **Create New**.
* Click on the **Variable** item.
* Fill in the values as presented in the next screenshot.

<figure><img src="../.gitbook/assets/test (56).png" alt=""><figcaption></figcaption></figure>

The variable is set to **False** by default and is only assigned the **True** value only when the SharinPix Visualforce Component needs to be rendered.

Now we will use the **Assignment element,** to change the value of the above variabl&#x65;**.**

![](<../.gitbook/assets/test (57).png>)

Fill in the values for the **Assignment element** as described in the next steps:

For the following fields:

* **Name**:  the name of the assignment element. (In this case, it is **Assign Render Value**)
* Assignments:
  * Variable **RenderAlbum** is assigned the value **True**.

![](<../.gitbook/assets/test (58).png>)

The next screen implemented below will only display a label. At this stage, once the variable **RenderAlbum** is assigned the value **True**, the SharinPix Album present on the Visualforce Page will display.

The screen below will display the label **Upload Profile Picture** however you can use any label that fits your context.

![](<../.gitbook/assets/test (59).png>)

At this stage, we will assign the **false** value to the variable **RenderAlbum**, which will hide the SharinPix Album from the Visualforce Page.

The screenshot below shows how to re-assign its value.

![](<../.gitbook/assets/test (60).png>)

In the next stage, we will prompt the user whether he/she wants to create another **Contact** record.

The following steps below will create a screen to ask the question with the following **Field Settings**:

![](<../.gitbook/assets/test (61).png>)

The choices **Yes** and **No** capture the user input and will be used by the next **decision element**.

Inside the **decision element**, we will create 2 possible outcomes:

* **Continue**
* **Not continue**

If the choice **Yes** has been selected, the outcome will be **Continue**.

![](<../.gitbook/assets/test (62).png>)

If the choice **No** has been selected, the outcome will be **Not Continue**.

![](<../.gitbook/assets/test (63).png>)

If the choice **Yes** has been made, the outcome **Continue** will lead the flow towards the first screen we implemented and the cycle for the creation of a **Contact** will start all over again.

![](<../.gitbook/assets/test (64).png>)

On the other hand, if the choice **No** has been made, the outcome **Not Continue** will lead the screen flow towards an end screen as implemented below.

![](<../.gitbook/assets/test (65).png>)

When you are all done with the above steps, click on **Save** then **Close**. The flow also needs to be **activated** for the changes to be effective.

## 3. Implementing the Visualforce Page

The following Visualforce Implementation will reference:

* The flow created above.
* The SharinPix Visualforce Component.

```apex
<apex:page StandardController="Account" extensions="FlowController">
    <flow:interview name="SharinPix_Account_Contacts" interview="{! sp_flow }" finishLocation="/{!$CurrentPage.parameters.Id}"></flow:interview>
    <sharinpix:SharinPix height="400px" rendered="{! sp_flow.RenderAlbum == true }" parameters="{'Id': '{! sp_flow.ContactId }', 'abilities':{'{! sp_flow.ContactId }':{'Access': {'image_upload':true,'image_list':true,'see':true,'image_delete':true}}}}" />	
</apex:page>
```

The code snippet below references the VisualFlow we implemented above.

```html
<flow:interview name="SharinPix_Account_Contacts" interview="{! sp_flow }" finishLocation="/{!$CurrentPage.parameters.Id}"></flow:interview>
```

* As it can bee seen above, the flow element has the following properties:
  * **Name:**  the name of the flow created in the previous section
  * **Interview:** a reference to the flow interview as declared in the Apex Controller of the current Visualforce Page. This reference will allow us to access the variables found in the flow.

The code snippet below references the SharinPix Visualforce Component.

```html
<sharinpix:SharinPix height="400px" rendered="{! sp_flow.RenderAlbum == true }" parameters="{'Id': '{! sp_flow.ContactId }', 'abilities':{'{! sp_flow.ContactId }':{'Access': {'image_upload':true,'image_list':true,'see':true,'image_delete':true}}}}" />	
```

As it can be seen in the above code snippet, the SharinPix Visualforce Component has the properties:

* **height:** corresponds to the height of the SharinPix Album as rendered inside the SharinPix Visualforce Component.
* **rendered:** corresponds to the Boolean flag  that dictates whether the SharinPix Visualforce Component is to be rendered, hence displayed on the Visualforce Page.
* **parameters:** corresponds to the set of SharinPix Abilities enabled/disabled on the SharinPix Album.

## 4. Implementing the Apex Controller

The code snippet below shows the implementation of the Apex Class used as the controller for the Visualforce Page implemented above.

```apex
public class FlowController {
    public Flow.Interview.SharinPix_Account_Contacts sp_flow { get; set; }
    public FlowController (ApexPages.StandardController controller) {}
}
```

The declared variable **sp\_flow** represents the reference for the Flow as implemented [above](create-contacts-from-an-account-using-visualflow.md#id-2.-creating-the-flow). It will allow us to access the variables present within the flow.

For example, within the **SharinPix Visualforce Component** referenced inside the Visualforce Page implemented in the previous [section](create-contacts-from-an-account-using-visualflow.md#id-3.-implementing-the-visualforce-page), uses the Flow reference to access the following variables:

* **sp\_flow.RenderAlbum:** The **RenderAlbum** variable is used to dictate whether the SharinPix Visualforce Component is to be displayed or not on the Visualforce Page.
* **sp\_flow.ContactId:** The **ContactId** variable is used to associate the SharinPix Album to the relevant Contact Record.

## 5. Implementing the custom action

The objective of this section is to create a custom action that will launch the Visualforce Page as implemented above. The custom action will be associated to the Account Object, and used to create Contacts and upload their profile pictures on the SharinPix Album.

Follow the next steps to create the custom action:

* Ensure that the Visualforce Page implemented above is **Available for Lightning Experience, Lightning Communities, and the mobile app**.&#x20;
* Go to **Setup,**  select **Object Manager**, then click on the **Account Object.**
* On the left-hand-side panel, select **Buttons, Links and Actions**.

![](<../.gitbook/assets/test (66).png>)

Click on **New Action.**

![](<../.gitbook/assets/test (67).png>)

You will then be prompted to fill values for the custom action.

![](<../.gitbook/assets/test (68).png>)

Enter the following values for the corresponding fields:

* **Action Type:** Select **Custom Component.**
* **Visualforce Page:** select the name of the Visualforce Page implemented in the previous section.
* **Height:** enter a minimum value of 600px. (the px unit refers to the amount of pixels)
* **Standard Label Type:** Select a Type that matches your current context, if applicable.
* **Label:** Enter a relevant Label value. In this context, it is **Take Profile Pictures**.
* **Icon:** select **ActionSharinPixAlbum** which comes along with the SharinPix package when installed.

![](<../.gitbook/assets/test (69).png>)

Now the remaining step consists of adding the newly-created custom action the page-layout of the **Account Object.**

On the left-hand-side panel, select **Page Layouts.** Then select the layout most relevant to your context.

Upon selecting the layout, you will then be directed to the Page-Layout Editor. In the Left-hand-side panel, select **Mobile & Lightning Actions.**  Drag and Drop the **Take Profile Pictures element** from the elements group onto the section designated **Salesforce Mobile and Lightning Experience Actions.**

Click on **Save** when you're don&#x65;**.**

## 6. The Flow in action

In this section, we will demonstrate how our implementation of our VisualFlow operates.

* Navigate to the record of an **Account Object**.
* The custom action **Take Profile Pictures** should be displayed on the page-layout of the record.

![](<../.gitbook/assets/test (70).png>)

* Click on **Take Profile Pictures.**
* Enter the **First name** and **Last name** of the Contact you intend you create.

![](<../.gitbook/assets/test (71).png>)

* Click on **Next.** The Contact record will be created, then another screen will show up, displaying the SharinPix Album.  You will then be able to upload the Profile Picture of the newly-created Contact record.

![](<../.gitbook/assets/test (72).png>)

![](<../.gitbook/assets/test (73).png>)

After you uploaded, the picture, click on **Next.**

The next screen will prompt you whether to create new contacts or end the flow.

![](<../.gitbook/assets/test (74).png>)

If you choose to continue. select **Yes** and click **Next.** You will then be directed to the first screen and the cycle will start all over again.

![](<../.gitbook/assets/test (75).png>)

However, if you select **No,**  you will be directed to the end screen.

![](<../.gitbook/assets/test (76).png>)

The Flow will then exit once you click on **Finish.**
