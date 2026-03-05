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

# SharinPix component not working in Salesforce Site. What should I do?I don't see my SharinPix Lightn

<figure><img src=".gitbook/assets/test (2).png" alt=""><figcaption></figcaption></figure>

If you are having the above error or an error such as '**List has no rows for assignment to SObject**' while attempting to launch a Salesforce Site embedding SharinPix components such as SharinPix Album or SharinPix Webform component, here are some points that are worth checking:

* First of all you should check if the issue is coming from the SharinPix component. To do so, comment the section containing the component in your Visualforce page, then, check if the error still persists on your Salesforce Site. If the error is still there, this means that the issue is not from the SharinPix component.
* Secondly, you should check if the Site user (Guest user) has proper access to the SharinPix Apex classes associated with the SharinPix components. To ensure this, you simply need to assign the SharinPix permission set named **SharinPix Lightning Components** to the Site user.&#x20;
* You should also verify that the Site user has proper access to the SharinPx objects (such as SharinPix Image or SharinPix Permission objects) used in your Salesforce Site. To do so,  follow the steps below ( Note: we will use the **SharinPix Image** object as an example here):
  * From the Site details page, click on **Public Access Settings**
  * Then, in the **Custom Field-Level Security** section, click on **View** located next to the entry for **SharinPix Image** as shown below:

![](.gitbook/assets/screenshot-harktampa4238--sharinpix.lightning.force.com-2021.03.18-10_28_08_\(1\).png)

* Next, click on **Edit** and give access to SharinPix Image fields:

![](.gitbook/assets/screenshot-harktampa4238--sharinpix.lightning.force.com-2021.03.18-10_30_12_\(1\).png)

* Click **Save** when done

You should also, ensure that the Site user has basic read and create access right to the SharinPix Image object. This can be verified in the **Custom Object Permissions** section of the **Public Access Settings** page itself as depicted below:

![](.gitbook/assets/screenshot-harktampa4238--sharinpix.lightning.force.com-2021.03.18-10_33_21_\(1\).png)

* If the above points still do not resolve your issue, you can then give access to SharinPix objects to your Site users via the **Salesforce Sharing Settings**. This will give your Site users access to all SharinPix records (even the one they did not create) being used on your Salesforce site.

To give access to SharinPix objects using **Sharing Settings** , follow the steps below ( Note: we will use the SharinPix Permission object as an example here):

* From **Setup** , search for **Sharing Settings**
* From **Sharing Settings** , in the **Organization-Wide Defaults** , ensure that the following accesses are given to the SharinPix Permission object:

![](.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.03.17-12_35_15.png)

* Next, in the **Sharing Rules** section, look for **SharinPix Permission Sharing Rules**
* Click on **New**

![](.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.03.17-12_38_43.png)

* Then, enter the required details as shown below:

![](.gitbook/assets/screenshot-harktampa4238--sharinpix.lightning.force.com-2021.03.15-17_48_16_\(1\).png)

{% hint style="warning" %}
**Note:**

In the above example, we used **Name not equal as null** as the criteria. As all SharinPix Permission records have a name, by doing so, the Guest user will have access to all SharinPix Permission records.
{% endhint %}

* Click on **Save** when done

{% hint style="info" %}
If you are still encountering issues when using SharinPix components on Salesforce Site after applying the above points, contact us using the following email address: [support@sharinpix.com](mailto:support@sharinpix.com)
{% endhint %}
