# How to Launch a SharinPix Form

[**SharinPix Forms**](../sharinpix-form/welcome-to-sharinpix-forms.md) allow users to capture structured data and images directly within Salesforce. They are designed for both online and offline usage, making them ideal for inspections, audits, field operations, and any scenario requiring seamless data collection.

Users can capture images on the spot as they fill out forms and benefit from a wide range of integrated **tools,** including sketching capabilities, advanced formulas, spacers, image capture, repeated sections, and many other features. This combination allows teams to streamline data collection, improve accuracy, and provide a smoother experience for both field users and administrators managing the information within Salesforce.

You can launch a SharinPix Form in different ways:

* From Salesforce on a Web Browser
* From the Salesforce Mobile App to the SharinPix Mobile App
* From the Salesforce Field Service App (SFS)
* Through a Universal Link
* Through the SharinPix Form Lightning Web Component (LWC)

**Prerequisites:**

Before using **SharinPix Forms** , ensure that each user has the appropriate [permission set](../access-and-security/sharinpix-permission-sets.md) assigned:

* **SharinPix Forms Admin** is required for creating and managing form templates.
* **SharinPix Forms User** is required for filling out forms and capturing data.

Make sure you have the **latest** **SharinPix Package Version** Installed. Refer to [_this documentation_](https://docs.sharinpix.com/m/FAQ/l/1236928-how-to-update-sharinpix-package-from-the-appexchange) to update your package.

## Launching a Form from Salesforce on a Web Browser

To open a SharinPix Form in a web browser, the form URL must include:

`form_online_mode=true`

There are two recommended ways to do this:

### Option A — Generate a Universal Link

Create a universal link that includes the parameter `form_online_mode=true`. The format for **universal links** (URL) to open a form on the Web browser is as follows:

`https://app.sharinpix.com/native_app/form?token=_**< sharinpix-form-token>&**_form_online_mode=true`

### Option B — Use the Form Launcher LWC

* Add the [**SharinPix Form Launcher LWC**](../lightning-web-component/sharinpix-form-launcher.md) to the desired Salesforce record page.
* Enable the **“Open in Online Mode”** property within the component settings.
* The form will then launch directly in the browser when the user opens it as shown below.

![](<../.gitbook/assets/How to launch SPX form (2).png>)

![](<../.gitbook/assets/How to launch SPX form (3) (1).png>)

## Launching a Form from the Salesforce Mobile App to the SharinPix Mobile App

To automatically open forms inside the SharinPix Mobile App when starting from Salesforce Mobile:

There are two recommended ways to do this:

### Option A — Generate a universal link

The format for **universal links** (URL) to open a form in the SharinPix app is as follows:

`https://app.sharinpix.com/native_app/form?token=_**< sharinpix-form-token>**_`

### Option B — Use the Form Launcher LWC

* Add the Form Launcher to the record page.
* **Uncheck** the “Open in Online Mode” property.

Once configured, tapping the Form Launcher\*\*\*\* button from Salesforce Mobile automatically opens the selected form in the SharinPix Mobile App, allowing users to complete and submit it natively.

For detailed setup instructions, refer to the [Form Launcher](../lightning-web-component/sharinpix-form-launcher.md) documentation.

![](<../.gitbook/assets/How to launch SPX form (2).png>)

## Launching a Form from the Salesforce Field Service (SFS) App

Another way to launch a **SharinPix Form** is through the **Salesforce Field Service (SFS) App** by creating an **App Extension**.

The **App Extension** can embed a URL that directly opens to a **SharinPix Form** within the **SharinPix Mobile App** , allowing the user to fill and submit the form from within the SFS workflow.

For detailed setup instructions, refer to the documentation on [**Integration of SharinPix Form with SFS App using App Extension**](../sharinpix-form/integration-of-sharinpix-form-with-sfs-app-using-app-extension.md).

![](<../.gitbook/assets/DOC Mobile - 1920 x 1080 (1) (2).png>)

## Launching a Form Using a Universal Link

A universal link is the most flexible way to trigger a SharinPix Form. The format for **universal links** (URL) to open a form in the SharinPix app is as follows:

`https://app.sharinpix.com/native_app/form?token=_**< sharinpix-form-token>**_`

It can be generated in a Salesforce Flow using one of three invocable Apex actions:

### Option A — GenerateFormUrlAutomation

* Produces the **full universal link** , ready to use in flows, buttons, or external systems.
* Recommended for most use cases.\
  For detailed configuration steps, refer to the documentation on [Automatic Form URL Generation using Flow](../sharinpix-form/automatic-form-url-generation-using-flow-admin-oriented.md).

### Option B — GenerateFormTokenAutomation (Token for a Specific Form)

* Generates **only the secure token**.
* You manually construct the universal link using formulas or external logic.
* Useful when the link must be constructed outside Salesforce for security or integration reasons.\
  For detailed configuration steps, refer to the documentation on [Automatic Form Token Generation using Flow](../sharinpix-form/automatic-form-token-generation-using-flow-admin-oriented.md).

### Option C — TokenGeneration (Token for Multiple Forms)

You can generate a single token and reuse it across multiple form templates. In this approach, the token remains the same, and the specific form to open is defined using the parameter `form=<SharinPix Form Template URL>` in the universal link.

For example:

`https://app.sharinpix.com/form?token=<Token>&form=<Form Template URL 1>`\
`https://app.sharinpix.com/form?token=<Token>&form=<Form Template URL 2>`

This method is especially useful when you need to launch several forms from the same record. For instance, on an Inspection object, you may have multiple related forms such as Health & Safety, Compliance Review, Equipment Check, and more—all accessible using a single token.

For detailed configuration steps, refer to the documentation on [Automatic Token Generation using Flow](../mobile-app/sharinpix-automatic-mobile-upload-token-generation-admin-friendly.md).

## Launching a Form from the SharinPix Form LWC

You can also fill a **SharinPix Form** directly within Salesforce by using the _**SharinPix Form LWC**_.

To use it:

1. Add the **SharinPix Form LWC** to the desired Salesforce record page.
2. In the component’s property **“SharinPix Form Template ID or Name”** , specify the name or ID of the SharinPix Form Template you want to load.

Once configured, the selected form automatically loads inside the record page. Users can complete and submit the form directly within Salesforce.

![](<../.gitbook/assets/How to launch SPX form (1) (1).png>)
