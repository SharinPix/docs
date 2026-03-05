# Setup Custom Lookup For SharinPix Form Response

## Overview

{% hint style="info" %}
In this article, we will demonstrate how to setup the SharinPix Form Response Sync. To do so we will:

1. [Create a lookup relationship field on the SharinPix Form Response object](setup-custom-lookup-for-sharinpix-form-response.md#creation-of-a-lookup-relationship-field)
2. [Configure the SharinPix Form Response Setting custom metadata](setup-custom-lookup-for-sharinpix-form-response.md#configure-the-custom-metadata)
{% endhint %}

{% hint style="warning" %}
**Prerequisite:**

* The **SharinPix Form Response Sync Setting** component works alongside the **SharinPix Form** feature. Therefore, before configuring this Sync Settin&#x67;**,** ensure that the **SharinPix Form** feature has been configured properly. For more information on how to configure the SharinPix Form, please refer to the following article: [SharinPix Form](sharinpix-forms.md)
* The SharinPix Package with version **1.340** (or later) should be installed; refer to the article below to upgrade your current package: [How to upgrade SharinPix package](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)
* The **SharinPix Forms Admin** or **SharinPix Forms User** permission set should be assigned to all users to ensure they have the right to create, edit, and delete the SharinPix Form Response record through the SharinPix Form Response Sync Setting. For more information on these two permission sets, check [SharinPix Permission Sets](../access-and-security/sharinpix-permission-sets.md).
{% endhint %}

## Creation of a Lookup Relationship Field

Depending on the Object you want to use SharinPix Form Response Sync on, you must create a lookup relationship field on the SharinPix Form Response Object which links to the parent object. This demo will make use of the **SharinPix Visit** object.

Follow the steps below:

* Go to **Setup,** then access **Object Manager**
* Type form in the search bar, press Enter, and click **SharinPix Form Response**
* On the left menu, click on **Fields and Relationships** and then click on **New**

For the new field:

* Select **Lookup Relationship** as **Data Type** then click **Next**
* For the field **Related To**, select **SharinPix Visit** then click **Next**

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (5).png" alt=""><figcaption></figcaption></figure>

* On the next page, the field **Field Label** will be auto-populated
* Enter a **Field Name;** as an example **Visit\_Lookup\_\_c**
* Leave the other fields as default

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (1) (3).png" alt=""><figcaption></figcaption></figure>

* Proceed to the next steps and finally save the new relationship.

When you take a look back at the **Fields & Relationships** section, you should see the new relationship displayed as shown in the figure below.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (2) (2).png" alt=""><figcaption></figcaption></figure>

* Copy the field name: **Visit\_Lookup\_\_c** as we will need this in our next step.

{% hint style="warning" %}
**Warning:**

Ensure that you provide at least read access to the lookup field (**Visit\_Lookup\_\_c** in this case) for all users viewing/creating SharinPix Form Response records.
{% endhint %}

## Configure the Custom Metadata

This section demonstrates how to configure the SharinPix Form Response Setting custom metadata.

To do so, follow the steps below:

* Go to **Setup** and type metadata, then click on **Custom Metadata Types**
* Select the **Manage Records** action next to the label **SharinPix Form Response Setting**

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (3) (2).png" alt=""><figcaption></figcaption></figure>

* Create a new record.
* For the field **Label**, as an example, enter **Form Sync on Visit**
* The field **SharinPix Form Response Setting Name** is auto-populated when clicking anywhere outside the text box.
* For the field **Parent Object Name**, enter the **object API name;** in our case it is **sharinpix\_\_Visit\_\_c**
* For the field **Parent Field Name**, enter the field name of the lookup relationship field created in the previous section, that is **Visit\_Lookup\_\_c** (Remember the field name we asked you to copy? You can now paste it here)
* Click **Save** when done.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (5) (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Warning:**

You should be careful when entering values for the fields **Parent Object Name** and **Parent Field Name**.

* The field **Parent Object Name** refers to the object's API Name. In case you are using a custom object, you should ensure that the API name is correctly entered. For example, if you are using a custom object named **My Custom Object**, the value to be entered for the field **Parent Object Name** will be **My\_Custom\_Object\_\_c**.
* The field **Parent Field Name** on the other hand refers to the field name of the lookup relationship. You should ensure that the value entered for the field **Parent Field Name** matches the corresponding field name value in the lookup relationship.
{% endhint %}
