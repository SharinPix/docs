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

# Basic Setup - Step 3d for old Salesforce Mobile App Users - Setup SharinPix for Mobile (Classic Implementation)

{% hint style="warning" %}
If you have been through the [Basic Classic implementation](basic-setup-step-3a-for-classic-users-setup-sharinpix-for-salesforce-classic.md), you should already see the SharinPix album on the details tab. But it's not perfect and should be optimized by adding an action for SharinPix.

If you have been through both the Basic Classic Implementation and the [Basic Lightning configuration](basic-setup-step-3b-for-lightning-users-setup-sharinpix-for-lightning-experience.md) you will still have to do the following steps to see a SharinPix Album on your mobile phone.
{% endhint %}

## Create a "SharinPix Album" Lightning Action

To create a 'SharinPix Album' lightning action:

* Go to **Setup** , then **Object Manager**.
* Select the object on which you intend to add the custom action. In this case, it is the **Account** object.
* On the left-hand-side menu, select **Button, Links and Actions**.
* Click on the **New Action** button.

![](<../.gitbook/assets/image (12).png>)

From the Action Type picklist, select **Lightning Component.**

![](<../.gitbook/assets/image (13).png>)

* For the field **Lightning Component**, select **\<sharinpix>:SharinPixAlbum**
* For the field **Height** , enter **525px**
* For the field **Standard Label Type** , select **None**
* For the field **Label** , enter **SharinPix Album**
* The field **Name** will be auto-populated with the value **SharinPix\_Album**

![](<../.gitbook/assets/image (14).png>)

* Click on **Save**

You can now add the newly-created action to the object's Page Layout.

## Make the "SharinPix Album" Action available on the Layout

In this section, we will add the newly-created custom action onto the Account Page Layout.

To do so:

* Head over to the Account Page Layout most relevant to your case.
* Click on the **Mobile & Lightning Actions** option.
* Drag and drop the **SharinPix Album** action onto the **Salesforce Mobile and Lightning Experience Actions** section.

![](<../.gitbook/assets/image (15).png>)

* Click on **Save**.

## Test the "SharinPix Album" Lightning Action on your Desktop

If you access an Account record, the newly-created custom action should appear on the Page Layout as depicted below:

![](<../.gitbook/assets/image (16).png>)

Upon selecting the action, the **SharinPix Album** is launched as shown below:

![](<../.gitbook/assets/image (17).png>)

## Test "SharinPix Album" Lightning Action on a Salesforce Mobile App

You'll also find the **SharinPix Album** custom action inside your Salesforce mobile application as depicted below:

![](<../.gitbook/assets/image (18).png>)

{% hint style="success" %}
The image above shows a photo in the **Thumbnail View**. For more information about the Thumbnail View and the options it provides, refer to the following article: [Thumbnail View](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/user-interface/thumbnail-view)
{% endhint %}

## What's Next?

{% hint style="info" %}
Now it's time to check out the features you can enable from [SharinPix Global Settings](../advanced-configuration-customizing-your-sharinpix-components-with-sharinpix-permissions.md)
{% endhint %}
