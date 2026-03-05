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

# I got an error message 'Please verify if SharinPix Sync Setting is active'. What should I do?

If you encounter an error message similar to <mark style="color:$danger;">`Please verify if SharinPix Sync Setting is active`</mark>, this means that the Image Sync entry for the object is not active.

To reactivate the Image Sync setting for the object, follow the steps below:

* From the _Setup_, go to the **Custom Metadata Types** page.
* Next, click on **Manage Records** next to _SharinPix Sync Setting_.
* Click on **Edit** next to the object's Image Sync setting.
* Then, check the **Active** field and click save.&#x20;

![](<.gitbook/assets/image (12).png>)

{% hint style="warning" %}
**Note:**

If the **Active** field is not available on the custom setting layout, follow the steps below to add the same:

* Go to the **Custom Metadata Types** page and click on **SharinPix Sync Setting**.
* Scroll down to the _Page Layouts_ section and click on **Edit** next to **SharinPix Sync Setting Layout**.
* Add the **Active** field on the layout and save.
* Then, go to the object's Image Sync settings and verify if the _Active_ field has been checked.
{% endhint %}
