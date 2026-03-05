# SharinPix Form In Progress

## Overview

**SharinPix Form In Progress** allows users to start filling a form in web mode and save the current state of the form. After saving the form, a Form In Progress Record is created on Salesforce where the user can either complete the form and submit or continue filling the form and save. Upon submission, the Form In Progress Record is converted into a Form Response Record.

{% hint style="warning" %}
**Prerequisites**

Before using the **SharinPix Form In Progress** , ensure the following:

* Check **Create Form In Progress On Salesforce** in Organization Settings. [Contact SharinPix Support](../getting-started-with-sharinpix/how-to-contact-support.md) to enable this feature.
* Users must have the **SharinPix Forms** **Admin** or **SharinPix Forms User** permission set assigned. For more information on these two permission sets, check [SharinPix Permission Sets](../access-and-security/sharinpix-permission-sets.md).
* You have the **latest** **SharinPix Package Version** Installed. Refer to [_this documentation_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to update your package.
{% endhint %}

## Getting Started

### Demo

Once a form is opened in Web mode, the users can either save their current progress or submit it as shown below:

<figure><img src="../.gitbook/assets/formimg1.png" alt=""><figcaption></figcaption></figure>

Upon Save, a Form In Progress Record is created on Salesforce and be accessed as follows:

<figure><img src="../.gitbook/assets/formimg2.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Info**

If the tab is closed without pressing the Save button, all progress will be lost. The SharinPix Form should be saved or submitted.
{% endhint %}

The Form In Progress Record can be accessed from the Form Template Related List or from the Record Page where a custom lookup has been [setup](setup-custom-lookup-for-sharinpix-form-in-progress.md). From here, the form can be completed, saved, and submitted. Upon submitting the Form, the Form In Progress Record is deleted, and its corresponding Form Response Record is created. The PDF URL of the partially filled form is also available from here.

<figure><img src="../.gitbook/assets/form img3.png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
**Alert**

The SharinPix Form In Progress LWC shown in the above screenshot is only available on the SharinPix Form In Progress lightning\_\_RecordPage. To use it on a Digital Experience Page, the LWC should be added manually on the Site Page.
{% endhint %}
