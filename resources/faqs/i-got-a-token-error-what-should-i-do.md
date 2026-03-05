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

# I got a token Error, what should i do?

When you come across a token error while trying to display a SharinPix album (or any SharinPix tab) it may be due to a configuration problem.

<figure><img src=".gitbook/assets/ got a token Error, what should i do.png" alt=""><figcaption></figcaption></figure>

To resolve the token error, you should verify:

* [That SharinPix has been properly configured on your Org](i-got-a-token-error-what-should-i-do.md#verify-that-sharinpix-has-been-properly-configured)
* [That the current user's profile has been added to the Albums connected app](i-got-a-token-error-what-should-i-do.md#verify-that-users-profile-has-been-added-to-the-albums-connected-app)
* [That SharinPix licenses have been assigned to the current user (this is not necessary for the trial)](i-got-a-token-error-what-should-i-do.md#verify-that-the-sharinpix-licenses-has-been-assigned-to-the-user)

## Verify that SharinPix has been properly configured

The steps below outlines the checks to be performed to ensure that SharinPix has been properly configured:

* Go to **Setup** (1), find and select **Manage Connected Apps** (2) using the **Quick FInd** search bar
* On Manage Connected Apps, click on **Edit** (3) next to **Albums**

![](.gitbook/assets/screenshot-docs.sharinpix.com-2020.07.16-14_04_46.png)

* Next, for the section, **OAuth Policies**, ensure that the chosen value for **Permitted Users** is set to **Admin approved users are pre-authorized**. If it is not the case, go ahead and set the value to **Admin approved users are pre-authorized**
* Click **Save** when done

![](.gitbook/assets/screenshot-spx-fsl-summer20-dev-ed.lightning.force.com-2020.07.16-14_09_36.png)

* Next, from the App Launcher find and select **SharinPix Settings**
* Once the SharinPix Settings tab is opened, verify if the second line, that is **Sharinpix -> Salesforce full API access**, is highlighted in green
* If not the case, click on the **Grant** button as shown below to grant access

![](.gitbook/assets/screenshot-docs.sharinpix.com-2020.07.16-14_35_51.png)

* You will then be directed to the following prompt. Click on **Allow**

![](.gitbook/assets/screenshot-docs.sharinpix.com-2020.07.16-14_39_06.png)

* Then, refresh the page on which the token error was initially showing up. You should see that the SharinPix Album (or any SharinPix tab) is now available

## Verify that user's profile has been added to the Albums connected app

You should also ensure that the current user's profile has been added to the **Album** connected app. To verify this, follow the steps below:

* From **Manage Connected App**, open **Albums**
* Once inside Albums, scroll down to **Profiles** and check if the profile of the user encountering the token error is present
* If not the case, click on **Manage Profiles** and add the user's profile
* Then, go back the page on which the token error was initially showing up. You should see that the SharinPix Album (or any SharinPix tab) is now available

## Verify that the SharinPix licenses has been assigned to the user

For this part, follow the steps below:

* From **Setup**, find and select **Installed Packages** using the **Quick Find** box
* Then, click **Manage Licenses** next to the SharinPix package labeled as **ImageManagementBySharinPix**
* Next, add or remove the licenses corresponding to specific users

{% hint style="info" %}
For details about the solutions provided in this article, you can check the following resources:

* SharinPix usage configuration on Salesforce : [Basic Setup](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/basic-setup/basic-setup-step-1-configure-the-salesforce-usage-of-sharinpix)
* Add user profiles to Album connected app: [Manage Profiles](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/basic-setup/basic-setup-step-1-configure-the-salesforce-usage-of-sharinpix#manage-profiles)
* Assign SharinPix licenses to user: [Assign SharinPix Licenses](how-to-assign-sharinpix-licenses.md)

Still having the error? Contact us by clicking [here](https://www.sharinpix.com/#contact)!
{% endhint %}
