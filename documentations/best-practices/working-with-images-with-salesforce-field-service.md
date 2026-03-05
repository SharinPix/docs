# Working with Images with Salesforce Field Service

## Upload Images from Field Service mobile App

Salesforce Field Service has its own mobile app with very few capabilities to integrate with 3rd Party Apps.

SharinPix uses all the available possibilities at this time and will keep on integrating the new capacities as soon as they will be delivered by Salesforce.

To work with Salesforce Field Service mobile App, users will have to install the SharinPix mobile App on their mobile device and either use:

* an integration that includes the usage of an App Extension (this will appear as a menu item in the central bolt menu)
* or an integration including a clickable item in a flow (which appear as a clickable text in the flow screens)

![](<../.gitbook/assets/screenshot-docs.google.com-2022.08.23-17_27_13 (1).png>)

In both cases, it will open the SharinPix mobile App and offer direct access to the camera to take pictures and have them uploaded in the background.

The SharinPix mobile App can fully work offline and give access to all the SharinPix features including annotation, tagging and addition of Title & Description on images.

This integration uses a deeplink URL which can be personalized with different parameters as described here: [SharinPix mobile App - Deeplink syntax](../mobile-app/sharinpix-mobile-app-deeplink-syntax.md).

**The Best Practice is to personalize the deeplink URL to prohibit access to the roll, to force tags to be automatically added to images or even to add a checklist to show areas or actions to fill with images.**

## Merge images in generated Service Report PDF

![](<../.gitbook/assets/rsz_1skype_picture_2022_08_23t21_40_48_906z (1).jpg>)

If [SharinPix Image Sync is setup](../image-sync/setup-sharinpix-image-sync.md), each picture uploaded to SharinPix will have a corresponding [SharinPix image record](../image-sync/the-sharinpix-image-object.md) created accordingly.

A webhook is required by the Field Service implementation in order to make SharinPix Image Sync work for images uploaded from the SharinPix mobile App. This could be done by following the steps described in this article: [Image Sync for pictures uploaded via SharinPix Mobile App](../image-sync/image-sync-for-pictures-uploaded-via-sharinpix-mobile-app.md).

Once done, [those images could be used as a list in the Service Report template](https://github.com/SharinPix/documentation/blob/main/documentations/sharinpix-integration-with-salesforce-field-service/display-images-in-service-report-salesforce-field-service-fsl.md). These images will then be available in the generated PDF.

![](/broken/files/SRbsH1Sbw3NH7TSiyKJv)

You can also read the following articles to setup usage of SharinPix for Salesforce Field Service :

* [Using on Salesforce Field Service App (Field Service Lightning)](../features/main-integration/using-on-salesforce-field-service-app-field-service-lightning.md)
* [Integration of SharinPix App with SFS (FSL) App using App Extension](https://github.com/SharinPix/documentation/blob/main/documentations/sharinpix-integration-with-salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-app-extension.md)
* [Integration of SharinPix App with SFS (FSL) App using Flows](https://github.com/SharinPix/documentation/blob/main/documentations/sharinpix-integration-with-salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-flows.md)
* [Display Images in Service Report (Salesforce Field Service / FSL)](https://github.com/SharinPix/documentation/blob/main/documentations/sharinpix-integration-with-salesforce-field-service/display-images-in-service-report-salesforce-field-service-fsl.md)

Please note that if you are using SharinPix in a flow on a newly created record, you may have to use a specific configuration as the token value (which is an important security configuration required to make SharinPix work on Field Service mobile App) is only available on existing records.

In that case you should follow those steps :

[Add Photos on a Newly-Created Record Using Field Service Mobile Flow and SFS (FSL) Mobile (Developer-Oriented)](https://github.com/SharinPix/documentation/blob/main/documentations/sharinpix-integration-with-salesforce-field-service/add-photos-on-a-newly-created-record-using-field-service-mobile-flow-and-sfs-mobile-developer-oriented.md)
