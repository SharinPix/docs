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

# SharinPix Community users access rights

In this article, we will demonstrate how to give proper access rights to Community users using SharinPix components, objects or SharinPix Image Sync.

By default, Community users do not have all access rights to SharinPix.

Access rights issues regarding the usage of SharinPix by Community users occur mainly when:

* Community users trying to apply the SharinPix Image Sync feature.
* Community users trying to access SharinPix components.
* Community users trying to access SharinPix objects.
* Community users trying to access SharinPix components on Salesforce objects to which they do not have Read/Write access leading to an 'Access Denied' error.

We will address these issues in the following sections.

## Give Community users access to SharinPix Image Sync

The SharinPix package includes the **Permission Set** named **SharinPix Image Sync for Community Users** that provides proper access rights to the **SharinPix Image** object which is used by the SharinPix Image Sync feature.

Therefore, to enable Community users to perform Image Sync, the **SharinPix Image Sync for Community Users** should be assigned to them.

{% hint style="success" %}
For more information about the Permission Sets provided by SharinPix, please to the following article:

[SharinPix Permission Sets](sharinpix-permission-sets.md)
{% endhint %}

## Give Community users access to SharinPix components

To give Community users access to SharinPix components, the **SharinPix Lightning Components** Permission Set should be assigned to them.

## Give Community users access to SharinPix records

In some cases, Community users need access to SharinPix objects such as **SharinPix Permission**. In such situations, you should proceed as follows:

* Go to **Setup** and search for **Sharing Settings**.
* Once on the Sharing Settings page, click on the **Edit** button.
* Next search for the object you intend to give access to Community users. We will use the **SharinPix Permission** object for this demo.
* Under the **Default External Access** column for the SharinPix Permission object, change the value from **Private** to **Public Read/Write**.
* Click on **Save** when done.

<figure><img src="../.gitbook/assets/image (11) (4).png" alt=""><figcaption></figcaption></figure>

## Give Community users external access to Salesforce objects

In some cases where SharinPix components are added to Salesforce standard or custom objects, Community users cannot access the components and receive an 'Access Denied' error instead.&#x20;

This is most probably because the users do not have the required external Read/Write access to the object permitting them to use the SharinPix components.&#x20;

To provide the required external Read/Write access to the object, you should proceed as follows:

* Go to **Setup** and search for **Sharing Settings.**
* Once on the Sharing Settings page, click on the **Edit** button.
* Next search for the object you intend to give access to Community users.
* Under the **Default External Access** column for the SharinPix Permission object, change the value from **Private** to **Public Read/Write**. **Note:** You may also need to provide **Public Read/Write** access under the **Default Internal Access** column if that's not already the case to be able to proceed.
* Click on **Save** when done
