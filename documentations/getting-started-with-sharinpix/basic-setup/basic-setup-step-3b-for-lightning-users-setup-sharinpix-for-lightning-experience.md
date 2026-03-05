# Basic Setup - Step 3b for Lightning Users - Setup SharinPix for Lightning Experience

What you have done for Classic will be available in Lightning and the mobile app on the detail tab.

BUT the way it works is not perfect; on any click on the Album, a new window will open.

To get the best implementation for Lightning, it's better to use our Lightning Component. Let's look at how to do that!

## 1. Get My Domain

**Note:**

To make any custom Lightning component, including SharinPix's components, visible to the user, you have to create a domain for your org. Use [this link to get step-by-step video instructions on how to set up My Domain.](http://salesforce.vidyard.com/watch/oFQ26FCXPVOA90xZaVDDjA)

When setting up the _My Domain_ , please note the following:

1. Choose the name of your domain wisely. It's forever!
2. Don't add hard-coded URLS across your Salesforce system.

## 2. Add a SharinPix component to a Lightning Page

To add a SharinPix component on your record page, proceed as follows:

* Go to a record page in Lightning.
* Edit the page as shown below.

![](<../../.gitbook/assets/4423d116-dcd7-4a71-a93c-ba74f09a3818 (1) (1).jpg>)

Some SharinPix Lightning components can display an error like: **"You do not have access to the Apex class named 'SharinPixLightningController'."**

This is due to the following Salesforce critical update: **Restrict Access to @AuraEnabled Apex Methods for Authenticated Users Based on User Profile**

To solve this, simply assign the permission set, **SharinPix Lightning Component** , to the user encountering this problem. The _SharinPix Lightning Component_ permission set gives access to SharinPix's Apex classes.

* Next, scroll down to the managed components.
* Choose the **SharinPix Album** component.

![](<../../.gitbook/assets/rsz_screenshot_2023-10-30_at_34935 pm (1) (1).png>)

* Drag and drop the component onto your page layout.

![](<../../.gitbook/assets/9e08cc65-e209-41f4-a5d0-40b7b3766a02 (1) (1).jpg>)

**Note:**

You can't put the component into the detail page because the detail page is itself a component.

* Save the page and activate it (if needed).

![](<../../.gitbook/assets/f29be533-03d9-4c60-bf10-8d05513b3340 (1) (1).jpg>)

**Tip:**

On the Activation page, you can set this as the organization-wide default, meaning the component shows up on all the pages for this object.

Go to "Learn more..." to explore the other options.

![](<../../.gitbook/assets/d59a71c9-30d8-40cd-b730-4a0c98989ce8 (1) (1).jpg>)

* Once saved and activated, go to the record page.
* Test the _SharinPix Album_ component by uploading an image.

![](<../../.gitbook/assets/916a1c2e-e198-4971-8db1-13903ebaf685 (1) (1).jpg>)

**Tip:**

The above image depicts a photo in the **Thumbnail View**.

For more information about the Thumbnail View and the options it provides, refer to the following article: [Thumbnail View](../../features/user-interface/thumbnail-view.md)

## 3. What's next?

Now you can:

* [Get SharinPix available for Salesforce Mobile App](basic-setup-step-3d-for-old-salesforce-mobile-app-users-setup-sharinpix-for-mobile-classic-implement.md)
* [Customize your SharinPix Album's permissions](../advanced-setup/advanced-configuration-customizing-your-sharinpix-components-with-sharinpix-permissions.md)
