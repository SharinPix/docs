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
  actions:
    visible: true
  anchors:
    visible: true
---

# How to Launch a SharinPix Form

[**SharinPix Forms**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/overview-and-getting-started/welcome-to-sharinpix-forms) allow users to capture structured data and images directly within Salesforce. They are designed for both online and offline usage, making them ideal for inspections, audits, field operations, and any scenario requiring seamless data collection.

Users can capture images on the spot as they fill out forms and benefit from a wide range of integrated **tools,** including sketching capabilities, advanced formulas, spacers, image capture, repeated sections, and many other features. This combination allows teams to streamline data collection, improve accuracy, and provide a smoother experience for both field users and administrators managing the information within Salesforce.

{% hint style="info" %}
You can launch a SharinPix Form in different ways:



* [From Salesforce on a Web Browser](how-to-launch-a-sharinpix-form.md#launching-a-form-from-salesforce-on-a-web-browser)
* [From the Salesforce Mobile App to the SharinPix Mobile App](how-to-launch-a-sharinpix-form.md#launching-a-form-from-the-salesforce-mobile-app-to-the-sharinpix-mobile-app)
* [From the Salesforce Field Service App (SFS)](how-to-launch-a-sharinpix-form.md#launching-a-form-from-the-salesforce-field-service-sfs-app)
* [Through a Universal Link](how-to-launch-a-sharinpix-form.md#launching-a-form-using-a-universal-link)
* [Through the SharinPix Form Lightning Web Component (LWC)](how-to-launch-a-sharinpix-form.md#launching-a-form-from-the-sharinpix-form-lwc)
{% endhint %}

{% hint style="warning" %}
**Prerequisites:**

Before using **SharinPix Forms** , ensure that each user has the appropriate [permission set](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/sharinpix-permission-sets) assigned:

* **SharinPix Forms Admin** is required for creating and managing form templates.
* **SharinPix Forms User** is required for filling out forms and capturing data.

Make sure you have the **latest version of the SharinPix package** installed. Refer to [_this documentation_](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange) to update your package.
{% endhint %}

## Launching a Form from Salesforce on a Web Browser

To open a SharinPix Form in a web browser, the form URL must include:

<mark style="color:red;">`form_online_mode=true`</mark>

There are two recommended ways to do this:

### Option A — Use the Form Launcher LWC

* Add the [**SharinPix Form Launcher LWC**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-form-launcher) to the desired Salesforce record page.
* Enable the **“Open in Online Mode”** property within the component settings.
* The form then opens directly in the browser when the user selects the launcher, as shown below.

<figure><img src=".gitbook/assets/SPX Form Launcher.jpg" alt=""><figcaption></figcaption></figure>

![](<.gitbook/assets/How to launch SPX form (3) (1).png>)

### Option B — Generate a Share Link

Create a [share link](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/salesforce-integration/generate-sharinpix-shareable-form-links-automatically) that opens a SharinPix Form directly.

## Launching a Form from the Salesforce Mobile App to the SharinPix Mobile App

To automatically open forms inside the SharinPix Mobile App when starting from Salesforce Mobile:

There are two recommended ways to do this:

### Option A — Generate a universal link

Use the following Universal Link format to open a form in the SharinPix mobile app:

<mark style="color:red;">`https://app.sharinpix.com/native_app/form?token=`</mark>_<mark style="color:red;">**`<sharinpix-form-token>`**</mark>_

### Option B — Use the Form Launcher LWC

* Add the Form Launcher to the record page.
* **Uncheck** the “Open in Online Mode” property.

Once configured, tapping the Form Launcher button from Salesforce Mobile automatically opens the selected form in the SharinPix Mobile App, allowing users to complete and submit it natively.

For detailed setup instructions, refer to the [Form Launcher](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-form-launcher) documentation.

![](<.gitbook/assets/Form Launcher Mobile.jpg>)

## Launching a Form from the Salesforce Field Service (SFS) App

Another way to launch a **SharinPix Form** is through the **Salesforce Field Service (SFS) App** by creating an **App Extension**.

The **App Extension** can embed a URL that directly opens to a **SharinPix Form** within the **SharinPix Mobile App**, allowing the user to fill and submit the form from within the SFS workflow.

For detailed setup instructions, refer to the documentation on [**Integration of SharinPix Form with SFS App using App Extension**](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/form-mobile-integration/integration-of-sharinpix-form-with-sfs-app-using-app-extension).

![](<.gitbook/assets/DOC Mobile - 1920 x 1080 (1).png>)

## Launching a Form Using a Universal Link

A Universal Link is the most flexible way to launch a SharinPix Form in the mobile app. Use this format:

<mark style="color:red;">`https://app.sharinpix.com/native_app/form?token=`</mark>_<mark style="color:red;">**`<sharinpix-form-token>`**</mark>_

You can generate the link in a Salesforce Flow using one of three invocable Apex actions:

### Option A — GenerateFormUrlAutomation

* Produces the full Universal Link, ready to use in flows, buttons, or external systems.
* Recommended for most use cases.\
  For detailed configuration steps, refer to the documentation on [Automatic Form URL Generation using Flow](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/salesforce-integration/automatic-form-url-generation-using-flow-admin-oriented).

### Option B — GenerateFormTokenAutomation (Token for a Specific Form)

* Generates **only the secure token**.
* You manually construct the universal link using formulas or external logic.
* Useful when the link must be constructed outside Salesforce for security or integration reasons.\
  For detailed configuration steps, refer to the documentation on [Automatic Form Token Generation using Flow](https://app.gitbook.com/s/rRD1Xcn9HtKcyfQ9Ghyk/salesforce-integration/automatic-form-token-generation-using-flow-admin-oriented).

### Option C — TokenGeneration (Token for Multiple Forms)

Generate one token and reuse it across multiple forms. To identify the exact version to open, add <mark style="color:red;">`form=<SharinPix Form Version Template  URL>`</mark>to the Universal Link. Use the URL of a Form Version Template here—not the Main Form Template name used by the LWC.

Example: <mark style="color:red;">`https://app.sharinpix.com/native_app/form?token=TOKEN&form=FORM_VERSION_TEMPLATE_URL`</mark>

This method is especially useful when you need to launch several forms from the same record. For instance, on an Inspection object, you may have multiple related forms such as Health & Safety, Compliance Review, Equipment Check, and more—all accessible using a single token.

For detailed configuration steps, refer to the documentation on [Automatic Token Generation using Flow](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-automatic-mobile-upload-token-generation-admin-friendly).

## Launching a Form from the SharinPix Form LWC

You can also fill a **SharinPix Form** directly within Salesforce by using the _**SharinPix Form LWC**_.

To use it:

1. Add the **SharinPix Form LWC** to the desired Salesforce record page.
2. In the Main Form Template Name property, enter the name of the Main Form Template to load. The component automatically opens its active version.

Once configured, the selected form automatically loads inside the record page. Users can complete and submit the form directly within Salesforce.

![](<.gitbook/assets/Form template Editor Doc (2).jpg>)
