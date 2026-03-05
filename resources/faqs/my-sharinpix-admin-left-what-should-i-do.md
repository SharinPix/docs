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

# My SharinPix Admin left. What should I do?

This article will provide all the steps to update the new SharinPix Admin after the previous SharinPix Admin left or is no more available for this role.

This documentation will ensure:

* Continuity to all the SharinPix features.
* That the new SharinPix Admin has proper access to SharinPix features.

{% hint style="warning" %}
A user seeking full SharinPix access needs to have the System Administrator profile.
{% endhint %}

To ensure that SharinPix is fully configured for a new Admin, the below steps should be completed:

1. **Profile**\
   The user must have a System Administrator profile and that the profile has well been added to the Managed Connected Apps. Click [here](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/basic-setup/basic-setup-step-1-configure-the-salesforce-usage-of-sharinpix#manage-profiles) to see how to add your profile in Manage Connected Apps.
2. **SharinPix License**\
   The user should be added to the **Installed Packages.** Click [here](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/basic-setup/basic-setup-step-1-configure-the-salesforce-usage-of-sharinpix#assign-sharinpix-licenses-to-salesforce-users) to see how to add a user to Installed Packages
3. **Grant API Access**\
   The user should grant **Salesforce full API access.** Click [here](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/basic-setup/basic-setup-step-2-register-your-salesforce-organization-to-sharinpix) to how to grant Salesforce full API access.

## Other settings to verify

{% hint style="warning" %}
* If the user is a **System Administrator** profile and image sync is not working, hence the permission set "**SharinPix Image Sync Permission**" should be assigned to the user.
* If the user is **not** a **System Administrator**, the user will not be able to access the main SharinPix Components. Hence the user should be given the permission set "**SharinPix Lightning Component".**\
  \
  For more info on permission, you can refer to the documentation [**SharinPix Permission**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/sharinpix-permission-sets)**.**
{% endhint %}
