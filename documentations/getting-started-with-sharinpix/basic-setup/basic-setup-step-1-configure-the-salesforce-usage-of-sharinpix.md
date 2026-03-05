# Basic Setup - Step 1 - Configure the Salesforce usage of SharinPix

* Go to Salesforce Setup and type **Connected** in the Quick Find Box
  * Then click **Manage Connected Apps**

![](<../../.gitbook/assets/5aabce98-5aec-455a-9943-3077a7bac143 (1) (1).jpg>)

* From the list, click **Edit** next to the **Albums** Connected App

![](<../../.gitbook/assets/6cbc5d25-2a1a-4082-96d6-ef0d55119c77 (1) (1).jpg>)

* Change value of\*\* Permitted Users\*\* from **All users may self authorize** to **Admin approved users are pre-authorized**

![](<../../.gitbook/assets/49d23b65-fdaa-4b03-af48-41a58807f32e (1) (1).jpg>)

* Click on \*\*Save \*\*when done

## Alert?

Just click on **OK**. You're about to give permission to the profiles that will be using this.

![](<../../.gitbook/assets/4ec1dfd2-033b-4fb7-9c66-2ed4ddfea796 (1) (1).jpg>)

## Manage Profiles

* Go back to **Manage Connected Apps** , then click on **Albums**

![](<../../.gitbook/assets/alb (1) (1).png>)

* Next, scroll down to **Profiles** and click on **Manage Profiles**.

![](<../../.gitbook/assets/alb (1) (1).png>)

### Grant SharinPix Access to Profiles.

We will grant yourself access for now, therefore:

* select **System Administration**

![](<../../.gitbook/assets/ce428235-3f05-4c18-a905-44340a561e3c (1) (1).jpg>)

* Click \*\*Save \*\*when done

## Assign SharinPix Licenses to Salesforce Users

\*\*Note: \*\*This section is not applicable for organisations using the SharinPix **Trial** version and on Sandboxes.

To assign SharinPix licenses to Salesforce users, follow the steps below:

* From **Setup** , enter **Installed Packages** in the **Quick Find** box, then select **Installed Packages**
* Click on \*\*Manage Licenses \*\*next to the package **ImageManagementBySharinPix**
* Add or remove the licenses corresponding to specific users

**Tip:**

For more information about how to manage licenses for installed packages, you can refer to the following article:

[Managing Licenses for Installed Packages](https://help.salesforce.com/s/articleView?id=sf.distribution_managing_licenses.htm\&type=5)

Now you just have to [Register Your Salesforce Organization to SharinPix](basic-setup-step-2-register-your-salesforce-organization-to-sharinpix.md) before you can set up SharinPix on [Classic](basic-setup-step-3a-for-classic-users-setup-sharinpix-for-salesforce-classic.md) / [Lightning](basic-setup-step-3b-for-lightning-users-setup-sharinpix-for-lightning-experience.md) / [Salesforce mobile App](basic-setup-step-3d-for-old-salesforce-mobile-app-users-setup-sharinpix-for-mobile-classic-implement.md)
