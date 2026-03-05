# Images on generated PDF document

SharinPix addresses a lot of hitches when it comes to the addition of images to a PDF document.

![](/broken/files/9hkV4bct3vF0TgJE50pb)

## Using SharinPix Image Sync to resize images for your PDF

To resize your images, you should always make use of [SharinPix Image Sync](../image-sync/setup-sharinpix-image-sync.md) so as to automatically create [SharinPix Image records](../image-sync/the-sharinpix-image-object.md) for each image uploaded using SharinPix.

Those records can be personalized to handle different versions of the uploaded images using [SharinPix Transformation](../image-sync/sharinpix-transformation-get-your-images-automatically-resized.md). It's important to choose the right image size depending on your scenario.

**Best Practice when merging image in documents is to use a personalized image resolution so as to avoid any PDF generation size limit in Salesforce.**

A smaller image resolution will use less memory and help break the 30 MB limit for the generated PDFs. Such limitations can be reached when using original image resolutions (6 to 10 images captured by modern smartphone cameras can be sufficient to reach these limits).

In a document you don't need a very high image resolution. Only 250 pixels per inch for a printed document is enough to have an acceptable image resolution.

## Use resized image versions in your Doc Generation app/tool

There are mainly 3 different ways to display merged images onto a generated PDF document :

* as an image Table, using the SharinPix Image related List and either Formula or Rich Text field available on those records
* merging a Rich Text Field which can be populated with images using the [SharinPix To Rich Text Area](../lightning-web-component/sharinpix-to-rich-text-area.md) component
* using the [SharinPix to PDF](../lightning-web-component/sharinpix-to-pdf.md) component which relies on an easy configuration to generate PDF document with an optimized table of images, personalized first and last pages and a comment/description before and/or after the image table

## What is the best option to merge images?

There are 2 parameters to consider when choosing between using SharinPix Image records or content of a Rich Text Area field.

**1) Automated vs Manual selection of images**

Automated: [SharinPix Image records](../image-sync/the-sharinpix-image-object.md) permit to rely on the existing records and doesn't require a user to select images

Manual Selection of images: Can either be done by a selection of images and the use of [SharinPix To PDF](../lightning-web-component/sharinpix-to-pdf.md) component to populate a Rich Text field OR use of SharinPix Image records filtered by a tag added by users on each image to merge in the document (such as ServiceReport tag). As the tags field in SharinPix Image record reflects the tags added to the image it's easy to filter SharinPix Image records containing specific values.

**2) PDF generation tool or implementation used**

Based on Salesforce Template: If you are relying on Salesforce templates (such as Quote/Service Report/...) then you can either, use the related list of SharinPix Image records (as described here [Display Images in Service Report (Salesforce Field Service / FSL)](https://github.com/SharinPix/documentation/blob/main/documentations/sharinpix-integration-with-salesforce-field-service/display-images-in-service-report-salesforce-field-service-fsl.md)) or a Rich Text area field populated using the SharinPix To Rich Text component.

Using 3rd party tool such as Conga: You can implement a Conga Query to filter on SharinPix Image records in a similar way that you add a table in a template. Merging a Rich Text area populated using the SharinPix To Rich Text component will also work.\
(SharinPix works with many other PDF generation tools from the AppExchange, you can check this article with tips on how to integrate with any of those tools [How SharinPix can help with Images in PDF?](https://github.com/SharinPix/documentation/blob/main/FAQ/l/969916-how-sharinpix-can-help-with-images-in-pdf/README.md) )

Using SharinPix To PDF option: This allows you to simply implement a document generator in a click from a selection of images and requires very few steps of configuration. You can check how to make this happen here: [SharinPix To PDF](../lightning-web-component/sharinpix-to-pdf.md) (this option is only available with the [SharinPix Enterprise Plan](https://github.com/SharinPix/documentation/blob/main/FAQ/l/890710-what-is-the-difference-between-the-basic-plan-premium-plan-and-enterprise-plan/README.md)).
