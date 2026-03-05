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
---

# Why is my Form Response not properly created?

If you submitted a Form Response and it was not created on Salesforce, or it was created with missing related Form Answers, follow the steps below.

* Make sure that your API user has the "SharinPix Form" permission.

{% hint style="info" %}
The API user is the same user who granted SharinPix with full access to your Salesforce from the SharinPix Settings page.
{% endhint %}

* Check if there are any errors in the "Error Messages" field on the Form Response record if it was created.
* If nothing is present, check for errors in the SharinPix back office.
  * Go to the "SharinPix Settings" page.
  * Click on "Go to Administrative Dashboard".
  * Click on the "Form Responses" tab.
  * Click on the "Record Not Created" tab.
  * Click on the first Form Response and check for error messages in the "Message" row.

If the error does not appear to be an issue or requires no further action, click **Upsert on Salesforce** to retry.

<figure><img src=".gitbook/assets/Upsert on SF.png" alt=""><figcaption></figcaption></figure>

| Options                                                                   | Description                                                                                                                                                                                                                                                                                                          |
| ------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Resync the Salesforce record fields when upserting the form response.     | Select this option if you want your configured fields are synced with your response again.                                                                                                                                                                                                                           |
| Recreate the related Salesforce records when upserting the form response. | <p>Select this option if you want the child records to be recreated.<br></p><p><em><mark style="color:$warning;"><strong>Note:</strong></mark><mark style="color:$warning;"> </mark><mark style="color:$warning;">Recreating related Salesforce records duplicates any previously processed records.</mark></em></p> |

{% hint style="warning" %}
_The **Upsert operation in Salesforce** may not function properly if the associated Form Template Version is misconfigured. It can also be affected by other factors, such as outdated field mappings caused by changes you made to the Salesforce schema, or insufficient object and field permissions._\
\
_&#x46;or more information on Form Template Version, you can refer to this documentation:_\
[SharinPix Form Template Editor](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-elements/sharinpix-form-template-editor "mention")
{% endhint %}

To prevent future errors, ensure the Form Template mappings are updated whenever your Salesforce schema is modified and make sure the appropriate Form Template Version is activated. If the error persists, contact the SharinPix Support team at [**support@sharinpix.com**](mailto:support@sharinpix.com)**.**
