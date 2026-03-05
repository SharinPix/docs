# Basic Setup - Step 3d for old Salesforce Mobile App Users - Setup SharinPix for Mobile (Classic Impl

If you have been through the [Basic Classic implementation](basic-setup-step-3a-for-classic-users-setup-sharinpix-for-salesforce-classic.md), you should already see the SharinPix album on the details tab. But it's not perfect and should be optimized by adding an action for SharinPix.

If you have been through both the Basic Classic Implementation and the [Basic Lightning configuration](basic-setup-step-3b-for-lightning-users-setup-sharinpix-for-lightning-experience.md) you will still have to do the following steps to see a SharinPix Album on your mobile phone.

## Create a "SharinPix Album" Lightning Action

To create a 'SharinPix Album' lightning action:

* Go to **Setup** , then **Object Manager**.
* Select the object on which you intend to add the custom action. In this case, it is the \*\*Account \*\*object.
* On the left-hand-side menu, select **Button, Links and Actions**.
* Click on the \*\*New Action \*\*button.

![](<../../.gitbook/assets/0f14690d-b924-4e9c-a39f-f0f68fa7e046 (1) (1).png>)

From the Action Type picklist, select**Lightning Component.**

![](<../../.gitbook/assets/f36b1e9c-ef8f-42e3-83dd-480ef9d04025 (1) (1).png>)

* For the field **Lightning Component** , select **< sharinpix>:SharinPixAlbum**
* For the field **Height** , enter **525px**
* For the field **Standard Label Type** , select **None**
* For the field **Label** , enter **SharinPix Album**
* The field \*\*Name \*\*will be auto-populated with the value **SharinPix\_Album**

![](<../../.gitbook/assets/4c87dba4-8646-4077-b341-e0f8a64cc054 (1) (1).png>)

* Click on **Save**

You can now add the newly-created action to the object's Page Layout.

## Make the "SharinPix Album" Action available on the Layout

In this section, we will add the newly-created custom action onto the Account Page Layout.

To do so:

* Head over to the Account Page Layout most relevant to your case.
* Click on the \*\*Mobile & Lightning Actions \*\*option.
* Drag and drop the \*\*SharinPix Album \*\*action onto the \*\*Salesforce Mobile and Lightning Experience Actions \*\*section.

![](<../../.gitbook/assets/7f966191-112e-40b6-a0fb-1c798be88467 (1) (1).png>)

* Click on **Save**.

## Test the "SharinPix Album" Lightning Action on your Desktop

If you access an Account record, the newly-created custom action should appear on the Page Layout as depicted below:

![](<../../.gitbook/assets/a079900d-4cfc-4a73-91a7-2d1fe72b10d5 (1) (1).png>)

Upon selecting the action, the \*\*SharinPix Album \*\*is launched as shown below:

![](<../../.gitbook/assets/b4765e9b-6ad0-4b49-b050-3db1b5ac103c (1) (1).png>)

## Test "SharinPix Album" Lightning Action on a Salesforce Mobile App

You'll also find the\*\* SharinPix Album\*\* custom action inside your Salesforce mobile application as depicted below:

![](<../../.gitbook/assets/6e164420-6aed-4ebb-a785-f63884db6eec (1) (1).png>)

The image above shows a photo in the **Thumbnail View**. For more information about the Thumbnail View and the options it provides, refer to the following article: [Thumbnail View](../../features/user-interface/thumbnail-view.md)

## What's Next?

Now it's time to check out the features you can enable from [SharinPix Global Settings](../advanced-setup/advanced-configuration-customizing-your-sharinpix-components-with-sharinpix-permissions.md)
