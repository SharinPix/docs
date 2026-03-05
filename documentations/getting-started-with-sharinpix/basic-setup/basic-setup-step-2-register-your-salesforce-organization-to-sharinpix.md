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

# Basic Setup - Step 2 - Register your Salesforce organization to SharinPix

## First of all, go to the SharinPix Settings Tab

### If you are in Classic: Behind the + in the tab line (All Tabs) - SharinPix Settings

<figure><img src="../.gitbook/assets/image (2) (2).png" alt=""><figcaption></figcaption></figure>

### If you are in Lightning: AppLauncher - SharinPix Settings

In Lightning, click the waffle (The App Launcher - 9 Dots button under the Salesforce logo - (1) in the picture).

You can type Settings in the Search Bar (2) or find SharinPix Settings in the All Items list (3) at the bottom of the page by scrolling down.

<figure><img src="../.gitbook/assets/image (3) (3).png" alt=""><figcaption></figcaption></figure>

## Connect to SharinPix for the first time / Grant API access / Go to Admin Dashboard.

This screen manages the connection between Salesforce and SharinPix.

The first line should be green; if not, click on the **Reset** button next to it. At this time, your Salesforce organization is registered with SharinPix.

SharinPix needs the second line to turn green to have the right to update your Salesforce data on your behalf. To grant access to Salesforce, click on the **Grant** button next to " **Sharinpix - > Salesforce full API access**".

{% hint style="warning" %}
**Please note the following before granting the API access:**

* This action should be performed by a **System Admin**.
* In case you're a third-party user having a temporary account, ensure that the grant access to Salesforce is performed by one of the client's active System Admin and not by a third-party user.
* If the user who previously granted access to Salesforce is deactivated, this second line will be automatically deactivated, and the API calls will not go through anymore. In this case, another active admin user should grant access to Salesforce by clicking the **Grant** button.
{% endhint %}

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080.png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
**Note:**

* If the SharinPix Setting Page keeps loading:
  * Verify on Session Settings if the **Visualforce Cross-Origin Security Headers** checkboxes are disabled. To do so:
  1. _Go to Setup - > Session Settings -> Tab **Visualforce Cross-Origin Security Headers** -> Uncheck both checkboxes._
  2. Then reload the SharinPix Setting Page.
  3. The checkboxes can be re-checked after all configurations from the SharinPix Setting page are completed.
{% endhint %}

<figure><img src="../.gitbook/assets/image (5) (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
Tip:

The **Go to administration dashboard** button provides access to advanced SharinPix settings.

For more information about the SharinPix Administration Dashboard, refer to the following article: [Overview of the SharinPix Administration Dashboard](../overview-of-the-sharinpix-administration-dashboard.md)
{% endhint %}

Now you are ready to set up SharinPix in:

* [Salesforce Classic](basic-setup-step-3a-for-classic-users-setup-sharinpix-for-salesforce-classic.md)
* [Salesforce Lightning Experience](basic-setup-step-3b-for-lightning-users-setup-sharinpix-for-lightning-experience.md)
* [Salesforce mobile App](basic-setup-step-3d-for-old-salesforce-mobile-app-users-setup-sharinpix-for-mobile-classic-implement.md)
