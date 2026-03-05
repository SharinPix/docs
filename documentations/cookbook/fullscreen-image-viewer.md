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

# Fullscreen Image Viewer

{% hint style="warning" %}
**Note:** The present example is only relevant to the Lightning Experience.
{% endhint %}

The **Fullscreen Image Viewer** is a parameter found on the **SharinPix Album** component that generates space around the fullscreen viewer of an image. This value is used to avoid hidden elements when alerts are shown.

{% hint style="info" %}
**Information:**

The **SharinPix Album** component was previously named **SharinPix**.
{% endhint %}

* The default value for the **Fullscreen Image Viewer** is <mark style="color:red;">`90px 0 0 0`</mark>. This value adopts the CSS syntax for **Padding** property. Each value corresponds to the amount of space to be generated between the fullscreen viewer and those starting positions:
  * <mark style="color:red;">`top`</mark> - 90px
  * <mark style="color:red;">`right`</mark> - 0
  * <mark style="color:red;">`bottom`</mark> - 0
  * <mark style="color:red;">`left`</mark> - 0

{% hint style="success" %}
More information on these CSS Padding values can be found here: [ https://www.w3schools.com/Css/css\_padding.asp](https://www.w3schools.com/Css/css_padding.asp)
{% endhint %}

### Lightning App Builder <a href="#edit-page" id="edit-page"></a>

* Access the lightning page of the record of your choice.
* Click on the **Setup** icon and then select **Edit Page.**&#x20;
* The configuration details of the SharinPix Album component can be accessed inside the **Lightning App Builder**.

<figure><img src="../.gitbook/assets/test (7).jpg" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Note:

Not all image sync abilities are available for the fullscreen feature.&#x20;
{% endhint %}
