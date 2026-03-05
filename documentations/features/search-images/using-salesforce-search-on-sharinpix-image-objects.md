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

# Using Salesforce Search on SharinPix Image objects

The present article shows how it is possible to search for **SharinPix Image** records from the Salesforce user interface.

{% hint style="warning" %}
It is assumed that SharinPix Image Sync has been activated and SharinPix Image records are present on the current org that you are using.
{% endhint %}

## Allow Search

* Go to **Setup**
* Access the **Object Manager**
* Go to the **SharinPix Image** object
* On **Details,** click on **Edit**
* Check the checkbox **Allow Search** as shown below.

<figure><img src="../../.gitbook/assets/Image from Gradio (19).png" alt=""><figcaption></figcaption></figure>

## Associate with Custom Tab

{% hint style="info" %}
**NOTE:** Custom object records are searchable in the Salesforce user interface only if the custom object is associated with a custom tab.
{% endhint %}

* Create a **Custom Object Tab** for the **SharinPix Image** object.

## Search SharinPix Images

After following the configurations as mentioned in the previous sections, you will now be able to search for SharinPix Image Records from the Salesforce user interface. It should be noted that the **Record Name** of SharinPix Image records follow the given format: **SI-0000, SI-0001.** ​​​​

* The screenshot below shows a search being performed.

<figure><img src="../../.gitbook/assets/Image from Gradio (20).png" alt=""><figcaption></figcaption></figure>
