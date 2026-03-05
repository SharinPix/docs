# User receiving error message 'You do not have access to the Apex class named 'SharinPixLightningController' when trying to access a SharinPix component. What should I do?

![](<.gitbook/assets/image - 2026-01-28T164723.513.png>)

Error messages such as '**You do not have access to the Apex class named 'SharinPixLightningController'** ' (or another class name: '_You do not have access to Apex class name \[ApexClassName]_ ') mostly occur when a non-admin user try to access a SharinPix component.

This is due to the following Salesforce critical update: **Restrict Access to @AuraEnabled Apex Methods for Authenticated Users Based on User Profile**

To resolve this, simply assign the permission set named **SharinPix Lightning Components** to the user encountering this error message. The SharinPix Lightning Component permission set gives access to SharinPix's Apex classes.

{% hint style="success" %}
This will be automatically activated in August 2020 unless otherwise stated by Salesforce.
{% endhint %}

{% hint style="warning" %}
**Note:**

If the permission set **SharinPix Lightning Components** is not available, kindly update your SharinPix package. You can refer to the following article for more information about how to update the SharinPix package:

[How to update SharinPix package from the AppExchange?](how-to-update-sharinpix-package-from-the-appexchange.md)
{% endhint %}
