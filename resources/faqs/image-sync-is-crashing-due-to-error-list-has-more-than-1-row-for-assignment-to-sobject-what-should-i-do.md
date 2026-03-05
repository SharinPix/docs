# Image Sync is crashing due to error 'List has more than 1 row for assignment to SObject'. What should I do?

If your Image Sync is crashing due to the error message **List has more than 1 row for assignment to SObject** , here is what you can do:

1. Verify if you have SharinPix Image Sync settings for the same Salesforce object. If that's the case, delete the extra setting as SharinPix _requires only one_ Image Sync setting per object.
2. Verify if any two or more SharinPix Image Sync settings have the same object API name in the _Parent Object Name_ field. If that is the case, this means that the such Image Sync settings belong to the same object. Delete the extra settings as SharinPix _requires only one_ Image Sync setting per object.

{% hint style="warning" %}
**Note:**

* SharinPix Image Sync settings are available on the Salesforce **Custom Metadata Types** page. For more information on how to access the Image Sync settings, refer to the following article: [Setup SharinPix Image Sync](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/setup-sharinpix-image-sync)
* For any other SharinPix Image Sync issue, refer to the following article: [Troubleshoot Common Image Sync Issues](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/troubleshoot-common-image-sync-issues)
{% endhint %}

