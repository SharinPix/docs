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

# SharinPix Related Record Albums is not working for my custom object. How do I fix this?

If you have added the [SharinPix Related Record Albums](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-related-record-albums) component on a custom object’s page layout and the child records are not showing, one possible cause could be a naming conflict: a custom object may exist in your organization that has the same name as a packaged custom object within SharinPix. Examples of possibly conflicting object names include Visit and Share. As the custom object and the SharinPix managed object share the same name, Salesforce limits us from using the custom object and defaults to using the managed custom object. To resolve this conflict, please use the workaround provided below:

**Steps to Fix SharinPix Related Record Albums Not Displaying Records for your Custom Object:**

**1. Install the Unlocked Package**

* Click the link to install the unlocked package in your org:\
  [Install Package](https://login.salesforce.com/packaging/installPackage.apexp?p0=04tVX000001SubNYAS)

![](<.gitbook/assets/image (28).png>)

**2. Update the SharinPix Managed Package**

* Ensure your SharinPix managed package is updated to **version 1.324 or above**.
  * Here is the [documentation](how-to-update-sharinpix-package-from-the-appexchange.md) to update the package

**3. Assign the SharinPix Bridge Permission Set**

* Assign the **SharinPix Bridge** permission set to all users requiring access to the Related Record Albums.

**5. Verify the Configuration**

* Open a parent record where the **SharinPix Related Record Albums** has been set up.
* Confirm that the related albums and images are now displayed correctly.

![](<.gitbook/assets/image (29).png>)
