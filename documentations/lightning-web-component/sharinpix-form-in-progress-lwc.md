# SharinPix Form In Progress LWC

## Overview

The **SharinPix Form In Progress** component allows users to access Form responses that have been saved as drafts in Salesforce. Users can reopen a draft response, update its content and submit the form when it is ready.

To allow users to save a Form as a draft, enable the **Save as Draft** button. For configuration instructions, refer to [SharinPix Form In Progress](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/salesforce-integration/sharinpix-form-in-progress "mention").

{% hint style="info" %}
**Information**

This feature is only available on Lightning. It can be used:

* On Experience Builder
* On Lightning App Builder
* On Desktop
* On Mobile

⚠️ This component cannot be used in Flows.\
⚠️ This component is only available on the object `sharinpix__FormInProgress__c` record page.
{% endhint %}

{% hint style="warning" %}
**Prerequisites**

* **Permissions:** Users must have the SharinPix Forms Admin or SharinPix Forms User permission set assigned. For more information on these two permission sets, check [_SharinPix Permission Sets_](https://docs.sharinpix.com/documentation/access-and-security/sharinpix-permission-sets)_._
* **Package Version:** Ensure that the latest SharinPix Package Version is installed.
{% endhint %}

## Getting Started

To use the **SharinPix Form In Progress** component:

1. Open the **Lightning App Builder**.
2. Drag and drop the **SharinPix Form In Progress** component onto the **Form In Progress record page**.
3. Configure the component parameters as described below.
4. Save and activate the page.

<figure><img src="../.gitbook/assets/SPX FIP.png" alt=""><figcaption></figcaption></figure>

## Lightning Component Parameters

<table><thead><tr><th>Parameter</th><th width="261.33203125">Description</th><th>Default/Notes</th></tr></thead><tbody><tr><td>Custom Parameters</td><td>Used to specify additional user-defined parameters to be appended to the SharinPix Form.<br><br>Example:<br><code>userId=&#x3C;Salesforce_User_Id></code></td><td>Default value: <em>None</em></td></tr><tr><td>Height</td><td>Used to specify the component's height.</td><td>Default value: <code>500px</code></td></tr></tbody></table>

## Demo and Behavior

### Example - Salesforce Record Page

The image below shows the **SharinPix Form In Progress** component in a Salesforce record page.

<figure><img src="../.gitbook/assets/SPX Form In Progress.png" alt=""><figcaption></figcaption></figure>

From here, the Form can be completed, saved, and submitted. Upon submitting the Form, the Form In Progress Record is deleted, and its corresponding Form Response Record is created. The PDF URL of the partially filled Form is also available from here.

<figure><img src="../.gitbook/assets/FIP Submit Screen.png" alt=""><figcaption></figcaption></figure>

After you submit the form, a confirmation screen displays "**Your form has been submitted"**. Use either button to continue:

| Button                | Description                                                        |
| --------------------- | ------------------------------------------------------------------ |
| **Review Submission** | Opens the submitted form response record in a new tab.             |
| **Return to Record**  | Opens the parent record where you completed the form in a new tab. |
