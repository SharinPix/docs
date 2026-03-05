# SharinPix Form

## Overview

The **SharinPix Form** component allows users to access and fill out pre-built SharinPix Form Templates (created using the [Form Template Editor](../sharinpix-form/sharinpix-form-template-editor.md)) directly inside Salesforce.&#x20;

{% hint style="info" %}
**Information:**\
This feature is only available on Lightning. It can be used:

* On Community Builder
* On Page Builder
* On Desktop
* On Mobile
* In Flows (but not in Field Service Mobile Flow)
* In your own Lightning Component Development
{% endhint %}

{% hint style="warning" %}
**Prerequisites**

* **Permissions:**\
  Users must have the SharinPix Forms Admin or SharinPix Forms User permission set assigned. For more information on these two permission sets, check [_SharinPix Permission Sets_](../access-and-security/sharinpix-permission-sets.md)_._
* **Package Version:**\
  Ensure that the latest SharinPix Package Version is installed.&#x20;
* **Form Template**\
  A form template must be created beforehand using the [_SharinPix Form Template Editor._](../sharinpix-form/sharinpix-form-template-editor.md)
{% endhint %}

## Getting Started&#x20;

To use the **SharinPix Form** component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout.&#x20;

<figure><img src="../.gitbook/assets/Form Component .png" alt=""><figcaption></figcaption></figure>

## Lightning Web Component Parameters

<figure><img src="../.gitbook/assets/Form Component Parameters.png" alt=""><figcaption></figcaption></figure>

| Parameter               | Description                                                                                                                                                                                                                                                                                                                                                       | Default/Notes                                                                                  |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Main Form Template Name | Specifies the Main Form Template to launch. Enter the Main Form Template name directly, or enclose in braces the API name of a record field that contains it (for example, {Inspection\_Template\_\_c}). The template must exist in the [SharinPix Form Template Editor](https://docs.sharinpix.com/documentation/sharinpix-form/sharinpix-form-template-editor). | Must match an existing Main Form Template name. The component always opens the active version. |
| Name Field API Name     | Specifies the job name when displaying the Form in the **SharinPix Form** component. You can use any other fields in the record from which the component is being placed.                                                                                                                                                                                         | Default value: _Record name_                                                                   |
| Custom Paramters        | Used to specify additional user-defined parameters to be appended to the SharinPix Form. Example "userId=005Ec00000MAzP2MAI".                                                                                                                                                                                                                                     | Default value: _None_                                                                          |
| Height                  | Used to specify the component's height.                                                                                                                                                                                                                                                                                                                           | Default value: _500_                                                                           |

## Demo and Behavior

#### Example - Salesforce Record Page

The image below shows the **SharinPix Form** component in a Salesforce record page.&#x20;

<figure><img src="../.gitbook/assets/Form Component Doc .png" alt=""><figcaption></figcaption></figure>

The user can fill out the form and submit it as well. After submitting the form, a screen will appear with a message, "_Your form has been submitted."_ and two buttons, as shown in the image below:

<figure><img src="../.gitbook/assets/Form Submit Buttons.png" alt=""><figcaption></figcaption></figure>

| Button                   | Description                                                                              |
| ------------------------ | ---------------------------------------------------------------------------------------- |
| Review Submission        | When clicked, the submitted form response record page will open in a new tab.            |
| Submit Another Response  | When clicked, the component will refresh and allow the user to fill a new form response. |
