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

# I got a Locker Service error message on SharinPix components. What should I do?

If you encounter an error message similar to the following when trying to access a SharinPix component, this may be related to the **Lightning Locker API Version** in your organization not being compatible with the SharinPix component's API version.

<mark style="color:$danger;">`Action failed: ltng:require$controller$init [$A.lockerService.isLockerNextEnabledForComponent is not a function. (In '$A.lockerService.isLockerNextEnabledForComponent(c)', '$A.lockerService.isLockerNextEnabledForComponent' is undefined)]`</mark>

<mark style="color:$danger;">`Please verify if SharinPix Sync Setting is active`</mark>

![](<.gitbook/assets/image (15).png>)

The workaround to avoid such mismatch is to, first, [upgrade your SharinPix package](how-to-update-sharinpix-package-from-the-appexchange.md).

If the new package does not resolve the issue then, another workaround is to temporarily change the **Lightning Locker API Version** to a previous version number.

To do so, follow the steps below:

1. From the **Setup** , search for **Session Settings**.
2. On the **Session Settings** page, look for **Lightning Locker API Version** and change the API version to the previous version number.

![](<.gitbook/assets/image (16).png>)

{% hint style="warning" %}
**Note:**

If the new SharinPix package does not resolve the issue, this means that we are still in the process of updating the API version of all our components. In such cases, you will have to temporarily change the **Lightning Locker API Version** to a previous version number.

If you wish to be notified once the API version of the SharinPix components is updated and when you can switch the **Lightning Locker API Version** back to the latest version, kindly [contact SharinPix Support](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/how-to-contact-support).
{% endhint %}
