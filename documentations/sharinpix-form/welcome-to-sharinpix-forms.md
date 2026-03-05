# Welcome to SharinPix Forms

SharinPix Forms offers the capability of asking users questions in a structured way on the field, including asking them to capture or fill out information in a visual way.

For example, you can ask a technician in the field to fill out a name, a phone number, or a serial number, but also to document any questions with notes, photos, Videos, scanned documents, personalised sketches (supporting all the visual features for which SharinPix has been known for years).

All that working fully offline!

You can learn more [here](sharinpix-forms.md), or you can just read further below for a quick overview.

{% hint style="success" %}
Currently we offer a **free form implementation as part of the SharinPix Form 14-Day trial** , just reach us here to ask for this : [Ask SharinPix For a FREE Form Implementation](mailto:sales@sharinpix.com?subject=FREE%20Form%20Implementation%20as%20part%20of%20FREE%20TRIAL)
{% endhint %}

## How it works?

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (6) (2).png" alt=""><figcaption></figcaption></figure>

Everything starts with a [Form template,](sharinpix-form-template-editor.md) which can be edited to build and optimize the form as it will be used by field users (learn more about the [SharinPix Form Template Builder here](sharinpix-form-template-editor.md)).

This Form template is then saved under a specific name. It can be associated with an action triggered by a Salesforce user or even provided as a link to external users without Salesforce access.

This action or link, once clicked, opens the SharinPix mobile app to run the form in an offline mode (read more about [SharinPix Form Launcher](/broken/spaces/Hhhsz8OAg6xcF0k0DJhg/pages/Nt8NRMnhV6xJ29Cqi1dY) and SharinPix Form Links here).

Once filled, this form can be submitted by the field user and will be uploaded in the background or instantaneously (provided you have a mobile data connection at the time of submission).

Once the upload is finalized (depending on the length of the form and/or the number of media associated with it, it can take seconds or minutes to load), it will appear in Salesforce as a SharinPix Form Response.

A configuration can be added to associate a Form Response to the parent from which it must be started, so you can have, for example, multiple Inspection forms associated with a specific property (the name of this configuration is the [SharinPix Form Response Sync Setting](setup-custom-lookup-for-sharinpix-form-response.md)).

The Form Response gives access to the Form Data either visually (so the desktop user can see the form in the same way it has been filled by the field user), in PDF format (a PDF can be automatically generated to reflect the form data so it can be shared with external users), or as an Answers record and field in Salesforce (so as an admin, you can apply any Salesforce logic, automation, query, report, or view it).

## SharinPix Form Template

From the [SharinPix Form Templates](sharinpix-form-template-editor.md) tab, you can create a Form template by adding any desired elements to it. The elements can be either a decoration (Title, description, visual guidance), a question (asking for some values to be picked or filled out) or even a visual action (capture photos, videos, sketching, and more).

The Form template can be previewed and tested (but for the photo/video capture) directly from there.

<figure><img src="../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2022.04.29-16_48_15 (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## SharinPix Form Launcher or Link

A component (name [SharinPix Form Launcher](/broken/spaces/Hhhsz8OAg6xcF0k0DJhg/pages/Nt8NRMnhV6xJ29Cqi1dY)) can be used on Salesforce mobile app to trigger the associated SharinPix Form from the mobile. This component can be added to any Record Page or Flow Screen on that purpose.

The SharinPix Form can also be exposed as a link, which can be used either on Salesforce Field Service (as a flow action or an app extension) or provided through any means (WhatsApp, text, email, agenda entries, and more) so that any external users can open the SharinPix form associated with it, fill it out, and update the right record in Salesforce.

If the [SharinPix mobile App](../mobile-app/where-to-find-the-sharinpix-mobile-app.md) is not installed prior to trigger any of those actions, the user will be prompted to install it from AppStore or GooglePlay (no extra fees needed there).

## SharinPix Form Response

The SharinPix Form Response is the container of all the submitted form data.

It gets a summary of the response as provided by the user, which can be quickly accessed to view the answer to any questions.

It is also available as a view-only version and can be printed out as a personalised PDF by the provided SharinPix automation.

Answers also exist as SharinPix Answers records related to the Form Response, to parse with Salesforce logic and are available for any Salesforce implementation.

If you have implemented the SharinPix Form Response Sync Setting, the SharinPix Form Response will be associated automatically as a related list of the parent record from which it has been triggered.
