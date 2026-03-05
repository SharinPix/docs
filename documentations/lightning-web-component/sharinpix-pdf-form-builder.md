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

# SharinPix PDF Form Builder

SharinPix PDF Form Builder allows users to upload and create a PDF form. This component will allow a user to add **Text** fields, **Signature** fields, **Checkbox** fields, **Radio Button** fields, **List Box** fields, and **Combo Text** fields, and **save** the PDF. The user will be able to view the modified PDF in Salesforce immediately after it is saved.

This article consists of:

* [Getting Started](sharinpix-pdf-form-builder.md#getting-started)
* [How Does It Work?](sharinpix-pdf-form-builder.md#demo)
* [Revert To Previous PDF Template](sharinpix-pdf-form-builder.md#revert-to-previous-pdf-template-version-1)
* [Update PDF And Keep Existing Fields](sharinpix-pdf-form-builder.md#change-pdf-and-keep-existing-fields)

{% hint style="info" %}
This feature is only available on Lightning. It can be used:

* **On Page Builder**
* **On Desktop**
* **On Mobile**
* **In your own Lightning Component development**
{% endhint %}

{% hint style="warning" %}
**Note:**

SharinPix PDF Form Builder is only available on the object **Pdf Template.**

You should ensure the following:

* The user should have the "**SharinPix PDF Form Builder**" permission set.
* User Profile should have **read/write** on the object **Pdf template.**
* **Tab Setting** should be set to **Default On**.
{% endhint %}

### Getting Started <a href="#getting-started" id="getting-started"></a>

To use the SharinPix PDF Form Builder component, you simply need to drag and drop the component from the Lightning App Builder onto your page layout and activate the page.

<figure><img src="../.gitbook/assets/SharinPix PDF Form Builder-1.png" alt=""><figcaption></figcaption></figure>

The Lightning Parameter **Height specifies the height of the SharinPix PDF Form Builder**. The default height is **700** (**px**).

### How Does It Work? <a href="#demo" id="demo"></a>

Click on the Add button or drag and drop a PDF onto the Lightning Web Component. Once uploaded, you will have access to various tools for the PDF.

<figure><img src="../.gitbook/assets/SharinPix PDF Form Builder-2.png" alt=""><figcaption></figcaption></figure>

The following tools are available and can be used on the PDF Template:

1. **Text Field**
2. **Signature Field**
3. **Checkbox** **Field**
4. **Radio** **Button** **Field**
5. **List** **Box** **Field**
6. **Combo** **Box** **Field**
7. **History**
8. **Upload New PDF**
9. **Delete**
10. **Save**

{% hint style="success" %}
**Tip:**

Press and hold the Alt or Option (⌥) key while dragging an element to duplicate it.
{% endhint %}

<figure><img src="../.gitbook/assets/SharinPix PDF Form Builder-3.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tip:**

**Text** field, **Checkbox** field, **Radio** **Button** field, **List** **Box** field, and **Combo** **Box** field can display values retrieved from a Salesforce record where the component [SharinPix Mobile PDF Form Launcher](sharinpix-mobile-pdf-form-launcher.md) is used with the corresponding **SharinPix PDF Template URL**.
{% endhint %}

{% hint style="warning" %}
**Note:**

The exact Field API Name can be added in Field Name to pre-fill fields when using the SharinPix Mobile PDF Form Launcher Lightning Component.
{% endhint %}

Fields can be added to the PDF as shown below:

<figure><img src="../.gitbook/assets/SharinPix PDF Form Builder-4.png" alt=""><figcaption></figcaption></figure>

Once you save the PDF, it will be displayed on the screen as follows:

<figure><img src="../.gitbook/assets/SharinPix PDF Form Builder-5.png" alt=""><figcaption></figcaption></figure>

The link of the saved PDF can be copied using the link button (last button) as shown below:

<figure><img src="../.gitbook/assets/SharinPix PDF Form Builder-6.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tip:**

The link of the template can be used on the Lightning Component [SharinPix Mobile PDF Form Launcher](sharinpix-mobile-pdf-form-launcher.md)**.**
{% endhint %}

### Revert To Previous PDF Template Version <a href="#revert-to-previous-pdf-template-version-1" id="revert-to-previous-pdf-template-version-1"></a>

If you want to return to your previous PDF versions, click the History button (the first one in the header). This will show you all the versions you've saved, in case you want one of the previous versions. You can download any version you wish or delete it.

<figure><img src="../.gitbook/assets/SharinPix PDF Form Builder-7.png" alt=""><figcaption></figcaption></figure>

### Update PDF And Keep Existing Fields <a href="#change-pdf-and-keep-existing-fields" id="change-pdf-and-keep-existing-fields"></a>

To update the background PDF while keeping the existing fields, click the Upload button (the second one in the header) and upload your new PDF. Then click on Save to save the changes and upload the updated PDF to SharinPix.

<figure><img src="../.gitbook/assets/SharinPix PDF Form Builder-8.png" alt=""><figcaption></figcaption></figure>

The following shows the result after saving the updated PDF:

<figure><img src="../.gitbook/assets/SharinPix PDF Form Builder-9.png" alt=""><figcaption></figcaption></figure>
