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

# Using on Chatter

## Overview

In this article, we will see the steps to integrate the SharinPix Album with the Salesforce Chatter Feed.

## Add SharinPix Chatter Publisher Action

* Go to **Setup.** Enter "**Global Actions**" in the **Quick Find Box.**
* Under **Global Actions** , select **Publisher Layouts**.
* Click on the **Edit** as shown in the screenshot below.

![](<../../.gitbook/assets/image (28) (1).png>)

* Drag and Drop the action **Share an Album** onto the **Quick Actions in the Salesforce Classic Publisher.** The **Share an Album** action is already included in the SharinPix Package.

![](<../../.gitbook/assets/image (29) (1).png>)

* Click on **save** when you are done.
* Navigate to **Salesforce Chatter.** As it can be seen on the Chatter Publisher, the action **Share an Album** is present.

![](<../../.gitbook/assets/image (30) (1).png>)

{% hint style="warning" %}
**Note:** If publisher action is not showing in chatter publisher on Salesforce, ensure Actions are enabled in Publisher:

* Navigate to: App Setup > Customize > Chatter > Settings
* Check “Enable Actions in the Publisher”
{% endhint %}
