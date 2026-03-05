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
  actions:
    visible: true
  anchors:
    visible: true
---

# Basic Setup - Step 1 - Configure the Salesforce usage of SharinPix



* Go to Salesforce Setup and type **Connected** in the Quick Find Box
  * Then click **Manage Connected Apps**

<figure><img src="../.gitbook/assets/image (3) (2).png" alt=""><figcaption></figcaption></figure>

* From the list, click **Edit** next to the **Albums** Connected App.

<figure><img src="../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

* Change the value of **Permitted Users** from **All users may self-authorize** to **Admin approved users are pre-authorized**

<figure><img src="../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

* Click on **Save** when done

## Alert ?

Just click on **OK**. You're about to give permission to the profiles that will be using this.

<figure><img src="../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

## Manage Profiles

* Go back to **Manage Connected Apps**, then click on **Albums.**

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

* Next, scroll down to **Profiles** and click on **Manage Profiles**.

![](<../.gitbook/assets/image (9).png>)

### Grant SharinPix Access to Profiles.

We will grant yourself access for now, therefore:

* Select **System Administration**

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

* Click **Save** when done

## Assign SharinPix Licenses to Salesforce Users

{% hint style="warning" %}
**Note**: This section does not apply to organisations using the SharinPix **Trial** version and on Sandboxes.
{% endhint %}

To assign SharinPix licenses to Salesforce users, follow the steps below:

* From **Setup**, enter **Installed Packages** in the **Quick Find** box, then select **Installed Packages**
* Click on **Manage Licenses** next to the package **ImageManagementBySharinPix**
* Add or remove the licenses corresponding to specific users

{% hint style="success" %}
**Tip:**

\
For more information about how to manage licenses for installed packages, you can refer to the following article:

[Managing Licenses for Installed Packages](https://help.salesforce.com/s/articleView?id=sf.distribution_managing_licenses.htm\&type=5)
{% endhint %}

{% hint style="info" %}
Now you just have to [Register Your Salesforce Organization to SharinPix](basic-setup-step-2-register-your-salesforce-organization-to-sharinpix.md) before you can set up SharinPix on [Classic](basic-setup-step-3a-for-classic-users-setup-sharinpix-for-salesforce-classic.md) / [Lightning](basic-setup-step-3b-for-lightning-users-setup-sharinpix-for-lightning-experience.md) / [Salesforce mobile App](basic-setup-step-3d-for-old-salesforce-mobile-app-users-setup-sharinpix-for-mobile-classic-implement.md)
{% endhint %}
