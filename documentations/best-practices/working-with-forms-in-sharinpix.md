# Working with Forms in SharinPix

SharinPix offers different level of Form integration :

* You can build forms using **Salesforce native capabilities** (Flow Screen) and use SharinPix Components on top of this experience
* You can build forms using **SharinPix PDF Form** to fill out an existing PDF with values, photos, sketches and signature
* You can also build form with the **SharinPix Offline mobile Form** , which offers offline form capabilities with dynamic questions and all the power of SharinPix as Elements for this form

## SharinPix Form in Flow Screen or other Salesforce native capabilities

As part of any flow screens you can use the SharinPix component to view visual, upload or capture visual or even trigger action (such as the one supported by the SharinPix mobile app).

Please check in the list of components here the ones available in flow screens : [SharinPix Components](https://github.com/SharinPix/documentation/blob/main/documentations/..../sharinpix-lightning-components/overview-of-the-sharinpix-lightning-components.md).

## SharinPix PDF Form

As part of the features available with SharinPix, you can start with a specific PDF and build a form on top of it.

This will require you to upload the PDF in the [SharinPix PDF Form Builder](working-with-forms-in-sharinpix.md), draw areas that will be actionable to enter data, and make it uploaded as a new PDF file in Salesforce.

## SharinPix Offline mobile Forms

Using [SharinPix offline mobile forms](https://github.com/SharinPix/documentation/blob/main/documentations/..../sharinpix-form/welcome-to-sharinpix-forms.md), you can build a form by drag-and-drop using informative elements, inputs or actions.

SharinPix offline mobile forms support default values from Salesforce, conditional visibility, formulas to calculate values from input, repeated sections to input multiple rooms, assets, or even deficiencies, sections to group information when your form is too long, and more!

In that way, you will be able to provide your field users with a way to document their jobs by answering questions, capturing photos or videos (and more), and gathering signatures.

As a result of this, you will get the form submission in your Salesforce, offering quick access to the data as a read-only version, as a PDF generated with your branding, or even as Answers records in Salesforce representing all the submitted values.
