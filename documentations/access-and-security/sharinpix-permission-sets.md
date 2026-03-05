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

# SharinPix Permission Sets

**Overview**

The SharinPix package provides some ready-made Permission Sets that can be used to address access rights issues for specific users (specially non-admin users and users with custom profiles).

This article provides an overview of the Permission Sets provided by SharinPix.

* **SharinPix Lightning Components:** This permission set should be assigned to users that need access to the required SharinPix components' related Apex classes.
* **SharinPix Image Sync Permission:** This permission set should be assigned to users needing access to create, edit, or delete the SharinPix Image record. It is used for the [SharinPix Image Sync feature](../image-sync/what-is-sharinpix-image-sync.md).
* **SharinPix Image Sync for Community Users:** This permission set should be used to provide Community users access to the [SharinPix Image Sync feature](../image-sync/what-is-sharinpix-image-sync.md).

{% hint style="warning" %}
**Warning**

* For cases in which community users need access to a SharinPix component that uses a SharinPix Permission record you also need to change the value of the **Default External Access** from **Private** to **Public Read Only** for the **SharinPix Permission** object in **Sharing Settings** as depicted below to allow access to the component on the community.
* For a Community Guest User Profile that does not have access to delete any records, you can clone the "**SharinPix Image Sync for Community Users**" permission set, remove the delete permissions for SharinPix Images, and then assign the modified permission set to the guest users.
{% endhint %}

<figure><img src="../.gitbook/assets/image (12) (4).png" alt=""><figcaption></figcaption></figure>

* **SharinPix Chatter Record Permission:** This permission set should be assigned to users to give them proper read, write, edit, and delete access to the **SharinPix Chatter** object. It is used for the functionality of the [SharinPix Chatter](../lightning-web-component/sharinpix-chatter.md).
* **SharinPix Visit:** This permission set should be assigned to users to give them proper read, write, edit, and delete access to the **Visit** and **Visit Report** objects.
* **SharinPix Share Permission** : This permission set should be assigned to users to give them proper read, write, edit, and delete access to the **SharinPix Share** object. It is used for the [SharinPix Share](../lightning-web-component/sharinpix-share.md) Feature.
* **SharinPix Checklist Result Permission:** This permission set should be assigned to users to give them read, write, edit, and delete access to the **SharinPix Checklist Result** object. It is used for the functionality of the [SharinPix Checklist with Form Features](../mobile-app/sharinpix-mobile-app-checklist-with-form-features.md).
* **SharinPix Sketch Permission:** This permission set should be assigned to users who need access to give them read, write, edit, and delete access to the **SharinPix Sketch** and **SharinPix Sketch Template** objects. It is used for the functionality of the [SharinPix Sketcher](../lightning-web-component/sharinpix-sketcher.md).
* **SharinPix Media Import:** This permission set should be assigned to users to give them read, write, edit, and delete access to the **SharinPix Media Import** object. It is used for the [SharinPix Media Import Feature](../cookbook/sharinpix-media-import-feature.md).
* **SharinPix AI Connect Permission:** This permission set should be assigned to users who need access to the [SharinPix AI Connect feature](../cookbook/sharinpix-generative-ai-analysis-extract-image-capabilities.md), allowing them to leverage **AI-driven image analysis** , tagging, and other automated processes provided by SharinPix AI Connect.
* **SharinPix Forms Admin Permission:** This permission set should be assigned to users who require full administrative access to [SharinPix Forms features](../sharinpix-form/welcome-to-sharinpix-forms.md). It grants the necessary permissions to create, edit, and manage [**SharinPix Forms Templates**](../sharinpix-form/sharinpix-form-template-editor.md) as well as the related **SharinPix Form Responses** and **SharinPix Forms In Progress** within Salesforce.
* **SharinPix Forms Users Permission**: This permission set should be assigned to users who need access to [SharinPix Forms features](../sharinpix-form/welcome-to-sharinpix-forms.md) but do **not** require the ability to build or modify **SharinPix Form Templates**. It allows users to fill in, save or submit, and manage their own SharinPix Form Responses or Forms in Progress, and to use other available form-related features.
* **SharinPix PDF Form Builder Permission:** This permission set should be assigned to users who need to use the [SharinPix PDF Form Builder](../lightning-web-component/sharinpix-pdf-form-builder.md). It grants access to features related to building, editing, and managing **SharinPix PDF forms** generated or imported via SharinPix.
* **SharinPix Plan Permission:** This permission set should be assigned to users who require access to the [SharinPix Plan](../lightning-web-component/sharinpix-plan.md) feature. It grants permissions to create, view, and manage **SharinPix Plans** and related **SharinPix Plan Settings** within the SharinPix package.

{% hint style="warning" %}
**Note:**

The permission set, **SharinPix Einstein**, has been deprecated.
{% endhint %}
