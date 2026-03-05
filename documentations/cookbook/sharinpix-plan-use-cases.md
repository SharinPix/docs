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

# SharinPix Plan Use Cases

This article demonstrates how to use the [SharinPix Plan](../lightning-web-component/sharinpix-plan.md) component on parent and child records.

## Using the SharinPix Plan on parent and child objects

Modifications made to the SharinPix Plan component on child records can be reflected on the parent record.

This section demonstrates how to configure the plan component on the custom object _Room_ (child object) and the _Account_ (parent object) object so that modifications made to the child records' plan component (Room records) are reflected on the parent's plan (Account record).

For this configuration, you should:

1\. Create \_SharinPix Plan Settings \_for the parent object using the Custom Metadata Settings.

For detailed steps on how to create \_SharinPix Plan Settings \_for the Account object, click on this [link](../lightning-web-component/sharinpix-plan.md#sharinpix-plan-setting).

![](<../.gitbook/assets/test (6).png>)

2\. Create \_SharinPix Plan Settings \_for the child object using the Custom Metadata Settings.

For detailed steps on how to create _SharinPix Plan Settings_ , click on this [link](../lightning-web-component/sharinpix-plan.md#sharinpix-plan-setting).

![](<../.gitbook/assets/test (1) (1).png>)

3\. On the Account page layout (the parent's page layout), add a SharinPix Plan component and configure the same using the Lightning Page Builder.

This step is documented [in this article,](../lightning-web-component/sharinpix-plan.md#configurations) but for quick reference, here are the mandatory parameters to be populated on the parent's SharinPix Plan component:

* **Plan Data Field API Name**: Name of the plan data field created on the parent object.
* **Background Image Tag** : Tag to be used to identify the plan image. The image can be uploaded and tagged on a SharinPix Album.
* **Height** : Height of the component.
* **Mode** : The parent plan component should preferably be on _Geocode_ or _ReadOnly_ mode. If you want to enable users to add markers on this component, the mode should be set to _Edit_.
* **SharinPix Plan Setting** : The object’s SharinPix Plan Setting name (as created in the Custom Metadata Setting).
* **Marker Label Field API Name** : The field API name stores the marker label. This field should be created on the SharinPix Plain Item object. For example, _Name_ or _sharinpix\_\_Title\_\_c_

<figure><img src="../.gitbook/assets/test (2) (1).png" alt=""><figcaption></figcaption></figure>

4\. On the Opportunity page layout (the child's page layout), add a SharinPix Plan component and configure the same using the Lightning Page Builder.

Here are the mandatory parameters to be populated in the child Plan component:

* **Plan Data Field API Name** : Name of the plan data field created on the child object.
* **Background Image Album Field API Name** : The parent lookup API name (as created on the child object). This will display the parent’s plan image on all child records.
* **Background Image Tag**: Tag to be used to identify the plan image. This value should be the same as the parent’s Background Image Tag (i.e., the same tag value should be used on both parent and child plan components).
* **Height** : Height of the component.
* **Mode** : The parent plan component should be in **Edit** mode.
* **SharinPix Plan Setting** : The object’s SharinPix Plan Setting name (as created in the Custom Metadata Setting).
* **Marker Label Field API Name** : The field API name stores the marker label. This field should be created on the SharinPix Plan Item object. For example, _Name_ or \_ _sharinpix\_\_Title\_\_c_\_

<figure><img src="../.gitbook/assets/test (3) (1).png" alt=""><figcaption></figcaption></figure>

5\. Once the Plan components have been set up on both parent and child page records, create an automation that will trigger (example: a Record-Triggered Flow) on every related SharinPix Plan Item record created at the child level.

Once the automation is triggered, it should update the parent lookup field on the newly-created SharinPix Plan Item record to the desired parent record. This final part will ensure that all markers added to child records are displayed on the parent record.

![](<../.gitbook/assets/test (4) (1).png>)

### DEMO: Using the SharinPix Plan on parent and child objects

The screenshot below shows the SharinPix Plan on the parent record before adding markers to the child records.

![](<../.gitbook/assets/test (5) (1).png>)

The screenshot below depicts the SharinPix Plan component on the parent record after adding markers on the child records.

![](<../.gitbook/assets/test (6) (1).png>)
