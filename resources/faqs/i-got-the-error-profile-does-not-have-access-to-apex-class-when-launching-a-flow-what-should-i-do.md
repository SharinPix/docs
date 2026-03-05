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

# I got the error 'Profile does not have access to: \[Apex class]' when launching a Flow. What should I do ?

If you got an error such as **Profile does not have access to: sharinpix\_\_RenameAlbum** while attempting to launch a Flow (or a Process Builder) that makes use of SharinPix classes or when using custom Apex classes that include SharinPix features, this is due to missing access to the mentioned class for the user that launched the automation.

To correct such errors, you should assign the Apex class to the user or profile attempting to launch the automation as follows:

* If you are using the Apex class included in the SharinPix package, you can simply assign the permission set named **SharinPix Lightning Components** to the user. \
  \
  **Note:** Such classes start with the namespace **sharinpix**, for example, **sharinpix\_\_TokenGeneration**
* If you are using a custom Apex class, you should then assign the specified class to the user profile. For more details on how to assign an Apex class to a profile, click [here](https://help.salesforce.com/articleView?id=sf.users_profiles_apex_access.htm\&type=5).

{% hint style="warning" %}
**Note:**

Detailed error messages relating to Salesforce Flow failures are sent by email. These messages are useful to identify the cause of the error as well as the user with the missing access to the Apex class.

You can control who receives process error emails. For more information on how this is done, click [here](https://help.salesforce.com/articleView?id=sf.flow_troubleshoot_error_email.htm\&type=5).
{% endhint %}
