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
---

# SharinPix Mobile App: Global Configuration

The SharinPix mobile app has 3 configuration levels:

* By making use of [Deeplink](sharinpix-mobile-app-deeplink-syntax.md) parameters.
* By making use of the [Settings screen](sharinpix-mobile-app-settings-screen.md) on the SharinPix mobile app itself.
* By configuring the mobile app's global parameters as described in the following sections.

The SharinPix Mobile app global parameters enable the customization of the SharinPix mobile app. The parameters currently available are:

* [checklist\_order](sharinpix-mobile-app-global-configuration.md#configure-the-checklist_order-parameter)
* [checklist\_reload](sharinpix-mobile-app-global-configuration.md#configure-the-checklist_reload-parameter)
* [auto\_destroy\_after](sharinpix-mobile-app-global-configuration.md#configure-the-auto_destroy_after-parameter)
* [incomplete\_checklist\_alert\_text](sharinpix-mobile-app-global-configuration.md#configure-the-incomplete_checklist_alert_text-parameter)
* [incomplete\_form\_alert\_text](sharinpix-mobile-app-global-configuration.md#configure-the-incomplete_form_alert_text-parameter)
* [team](sharinpix-mobile-app-global-configuration.md#configure-the-team-parameter)
* [exit\_page\_text\_ios](sharinpix-mobile-app-global-configuration.md#configure-the-exit_page_text_ios-parameter) (This parameter only applies to iOS devices)
* [compression](sharinpix-mobile-app-global-configuration.md#configure-the-compression-parameter)
* [await\_upload](sharinpix-mobile-app-global-configuration.md#configure-the-await_upload-parameter)
* [confirm](sharinpix-mobile-app-global-configuration.md#configure-the-confirm-parameter)
* [watermark](sharinpix-mobile-app-global-configuration.md#configure-the-watermark-parameter)
* [aspect\_ratio](sharinpix-mobile-app-global-configuration.md#configure-the-aspect_ratio-parameter)
* [target\_size](sharinpix-mobile-app-global-configuration.md#configure-the-target_size-parameter)
* [scan\_as](sharinpix-mobile-app-global-configuration.md#configure-the-scan_as-parameter)
* [units](sharinpix-mobile-app-global-configuration.md#configure-the-units-parameter)
* [roll\_limit](sharinpix-mobile-app-global-configuration.md#configure-the-roll_limit-parameter)
* [allow\_file\_export](sharinpix-mobile-app-global-configuration.md#configure-the-allow_file_export-parameter)
* [allow\_auto\_file\_export](sharinpix-mobile-app-global-configuration.md#configure-the-allow_auto_file_export-parameter)
* [required](sharinpix-mobile-app-global-configuration.md#configure-the-required-parameter)
* [snapsay\_language](sharinpix-mobile-app-global-configuration.md#configure-the-snapsay_language-parameter)
* [submit\_after](sharinpix-mobile-app-global-configuration.md#configure-the-submit_after-parameter)
* [annotation\_config](sharinpix-mobile-app-global-configuration.md#configure-the-annotation_config-parameter)

This article explains how to configure the above parameters in your Organization.

{% hint style="warning" %}
**Note:**

Changes to the SharinPix mobile app global configuration can take some time to be deployed to your device when offline.

The SharinPix app will keep its current configuration in the cache for at least an hour. So, if you open the app with a token while you're online, the new configuration will be automatically applied if it has been more than an hour since the last update. You can force the app to update its local configuration by going to the Settings page (tap on the top-right cog icon when you open the app).

You can ensure the app settings have been updated by looking at the last updated date and time at the bottom of the Settings page.
{% endhint %}

## Set up the parameters on your Organization

The SharinPix mobile parameters can be configured on the SharinPix Global Settings as explained in the following steps.

1\. To access the SharinPix Global Settings, from your Org:

* Using App Launcher, search for **SharinPix Settings**
* On the SharinPix Settings tab, click on the **Go to administration dashboard** button to open the global settings

2\. Once on the SharinPix Global Settings:

* click on **Settings** from the top menu bar
* Next, click on the **Edit Organization** button
* The SharinPix mobile app parameters can be viewed and edited in the **Mobile app config** section as shown below:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -1.png" alt=""><figcaption></figcaption></figure>

* To add a parameter, select the action menu icon then, click on **Append** as depicted below:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration - 2 (1).png" alt=""><figcaption></figcaption></figure>

The example below depicts how the mobile app config section looks like after the parameters have been added:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration - 3.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

The maximum number of images that can be added to a batch (a capture session) is usually 100, after which you will see an error message. You can add another 100 if you open the app again after submitting the previous one.

It is not recommended to add more than 100 images per batch. However, if you really wish to do so, please contact us and we will increase the limit.
{% endhint %}

### Configure the checklist\_order parameter

The **checklist\_order** parameter can be used to preserve the checklist order. This parameter takes two values:

* **auto:** Applying this value does not preserve the checklist's order. In this case, when a tag is applied from the checklist, the corresponding row is sent to the bottom of the list on the SharinPix app.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -4.jpg" alt=""><figcaption></figcaption></figure>

* **preserve:** This value is used to preserve the checklist order. Here, when a tag is applied from the checklist, the tag entry in the checklist remains in place, it is not sent to the bottom of the list.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -5.jpg" alt=""><figcaption></figcaption></figure>

The following code snippet shows how to configure the **checklist\_order** parameter to **preserve** or **auto** in the **Mobile app config** section:

* preserve: <mark style="color:red;">`"checklist_order": "preserve"`</mark>
* auto: <mark style="color:red;">`"checklist_order": "auto"`</mark>

Here's an example of how the **checklist\_order** parameter should look in the **Mobile app config** section:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -6.png" alt=""><figcaption></figcaption></figure>

### Configure the checklist\_reload parameter

This parameter can be used when using a [**checklist with form features**](sharinpix-mobile-app-checklist-with-form-features.md) if [**checklist\_order**](sharinpix-mobile-app-global-configuration.md#configure-the-checklist_order-parameter) is not set to **preserve**. When filling form fields in a checklist with form features, the checklist is not automatically reordered when an item changes from **incomplete** to **complete** or from **complete** to **incomplete**. To reorder the checklist, the user needs to click a reorder button. To reorder the checklist automatically, set the **checklist\_reload** parameter to **auto**. When set to **auto** the reload button is not displayed anymore.

Example:

<mark style="color:red;">`"checklist_reload": "auto"`</mark>

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -7.png" alt=""><figcaption></figcaption></figure>

### Configure the auto\_destroy\_after parameter

The **auto\_destroy\_after** parameter automatically deletes your images and form checklist data from the mobile app once they are marked as processed after a pre-defined amount of time. The Job record, which groups all media to upload to a specific Salesforce record, will still be available for an additional eight hours; however, it will be empty. New images can still be uploaded using the same job until it expires. Adding new media will extend the lifespan of the job record.

By default, if this parameter is not set, the images and form checklist data will be deleted **10 days** after they are marked as processed.

The value used for this parameter should be equal to the **number of seconds** before the images and form checklist data are removed. For example, if you want your images and form checklist data removed after 5 minutes, the auto\_destroy parameter should be configured as follows: <mark style="color:red;">`"auto_destroy_after": 300`</mark>.

The auto\_destroy\_after parameter also accepts the following special values:

* **0:** When using **0** as the value, the images and form checklist data are removed once they are marked as processed. Here, no lapse of time is given for the deletion. The syntax is as follows:

<mark style="color:red;">`"auto_destroy_after": 0`</mark>

* **-1:** A value of **-1** means that the images and form checklist data will not be deleted. Here is the syntax is:

<mark style="color:red;">`"auto_destroy_after": -1`</mark>

Here's an example of how the **auto\_destroy\_after** parameter should look in the **Mobile app config** section:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -8.png" alt=""><figcaption></figcaption></figure>

### Configure the incomplete\_checklist\_alert\_text parameter

The **incomplete\_checklist\_alert\_text** parameter can be used to add a personalized alert in cases where users attempt to submit images without completing a checklist.

The following code snippet shows how to configure the **incomplete\_checklist\_alert\_text** parameter with your own personalized text:

<mark style="color:red;">`"incomplete_checklist_alert_text": "Please fill the missing task(s) before submission"`</mark>

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -9.jpg" alt=""><figcaption></figcaption></figure>

The following placeholders can also be used with the **incomplete\_checklist\_alert\_text** parameter:

*   **\<COUNT>**: The **\<COUNT>** will be replaced by the **number of tags** with less images than the **minimum count** specified for the tag.

    Example:

<mark style="color:red;">`"incomplete_checklist_alert_text": "Missing <COUNT> tasks. Please fill the task(s)."`</mark>

will be displayed as follows on the SharinPix mobile app:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -10.jpg" alt=""><figcaption></figcaption></figure>

* **\<LIST\_INCOMPLETE>**: This value will be replaced by a list of tags which has **either** less images than the minimum count specified for the tag **or** an unfilled required field for the tag.

Example:

<mark style="color:red;">`"incomplete_checklist_alert_text": "Missing <COUNT> tasks. Please fill the following task(s). <LIST_INCOMPLETE>"`</mark>

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -11.png" alt=""><figcaption></figcaption></figure>

* **An empty string:** Inserting an empty string will omit the alert message when attempting to submit an incomplete checklist. For example, configuring the **incomplete\_checklist\_alert\_text** parameter as follows: <mark style="color:red;">`"incomplete_checklist_alert_text": ""`</mark> will not display any alert message when submitting an incomplete checklist.

### Configure the incomplete\_form\_alert\_text parameter

The **incomplete\_form\_alert\_text** parameter can be used to add a personalized alert in cases where users attempt to submit a [**checklist with form features**](sharinpix-mobile-app-checklist-with-form-features.md) without filling any required **form-field** for any tag.

Example:

<mark style="color:red;">`"incomplete_form_alert_text": "Please fill all form fields before submitting."`</mark>

will be displayed as follows on the SharinPix mobile app:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -12.png" alt=""><figcaption></figcaption></figure>

The following placeholders can also be used for the **incomplete\_form\_alert\_text** parameter:

* **\<LIST\_INCOMPLETE>**: This value will be replaced by a list of tags which has **either** less images than the minimum count specified for the tag **or** an unfilled required field for the tag.

Example:

<mark style="color:red;">`"incomplete_form_alert_text": "<COUNT> fields are unfilled. Please fill the following before submitting. <LIST_INCOMPLETE>"`</mark>

* **\<COUNT>**: The **\<COUNT>** value refers to the number tags with an unfilled required form-field in the checklist. For example, the following configuration

Example:

<mark style="color:red;">`"incomplete_form_alert_text": "<COUNT> fields are unfilled. Please fill to submit."`</mark>

### Configure the team parameter

The **team** parameter allows the user to view images already uploaded to the album the checklist relates to. This includes images uploaded live to the same record and checklists by other users.

The following code snippet shows how to configure the **team** parameter:

<mark style="color:red;">`"team": true`</mark>

This parameter takes two values:

* <mark style="color:red;">true:</mark> Used to show the user to see the online images on the checklist page

<mark style="color:red;">`"team": true`</mark>

* **false:** Default behaviour - will only show the images present locally on the device.

<mark style="color:red;">`"team": false`</mark>

{% hint style="success" %}
**Tips:**

* To retrieve the images you should make sure your token has at least the abilities: "**see**", "**image\_list** " and "**tags >read**".
* The necessary ability is required in the token so that it can access those tag images in the album.
* To configure the team checklist token abilities, you can either:
  * Create a SharinPix Permission with all required team checklist abilities and assign it to your component as explained [here](../access-and-security/sharinpix-permission-for-sharinpix-mobile-launcher-component.md) (admin-friendly method).
  * Programmatically configure the token as demonstrated in the code snippet available [in this article](sharinpix-mobile-app-team-checklist.md) (developer-oriented method) if you are using a custom component. _**Note:**_ _For some custom components, you can directly pass a SharinPix Permission ID to provide the correct Team Checklist token abilities._
{% endhint %}

### Configure the exit\_page\_text\_ios parameter

The **exit\_page\_text\_ios** parameter can be used to personalize and associate a text to the SharinPix mobile app's back button on **iOS** devices. Since iOS does not allow us to close the app automatically, this text can guide the user on the way to proceed.

The following code snippet shows how to configure the **exit\_page\_text\_ios** parameter with your own personalized text:

<mark style="color:red;">`"exit_page_text_ios": "Use <Salesforce above to return to Account."`</mark>

It will be displayed as follows on the SharinPix mobile app:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -13.jpg" alt=""><figcaption></figcaption></figure>

Here's an example of how it looks like in the **Mobile app config** section:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -14.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Information:**

The **ret\_url** parameter allows users to return to a specific external app (for example, Salesforce app or Salesforce Field Service app) from the SharinPix mobile app. This parameter can be configured in deeplinks.

For more information on the **ret\_url** parameter and on how it is configured, refer to the following article: [Deeplink syntax](sharinpix-mobile-app-deeplink-syntax.md)
{% endhint %}

### Configure the compression parameter

The **compression** parameter can be used to dictate the SharinPix mobile app to compress the captured images or not. Compressing the images taken by the SharinPix mobile app accelerates the upload and does not impact on the image quality.

The following code snippet shows how to configure the **compression** parameter:

<mark style="color:red;">`"compression": false`</mark>

This parameter accepts two values:

* **true:** When set to **true**, the SharinPix mobile app will perform the compression of images. (Note: The compression is set to true **by default**. Therefore, if not specified, image compression will take place.)

<mark style="color:red;">`"compression": true`</mark>

* **false:** When set to **false**, the mobile app will not compress the captured images.

<mark style="color:red;">`"compression": false`</mark>

### Configure the await\_upload parameter

The **await\_upload** parameter can be used to show the upload progress after submitting images captured using the SharinPix mobile app or after submitting a [checklist with form features](sharinpix-mobile-app-checklist-with-form-features.md).

The values that this parameter can take are as follows:

*   **checklist**: Used to show the image upload progress and wait for completion before exiting when submitting a **checklist with form features**

    <mark style="color:red;">`"await_upload: "checklist"`</mark>
* **batch:** Used to show the image upload progress and wait for completion before exiting when submitting a batch \
  <mark style="color:red;">`"await_upload": "batch"`</mark>
* **form:** Used to show medias upload progress and wait for completion before exiting when submitting a form containing batch or batches \
  <mark style="color:red;">`"await_upload": "form"`</mark>
* **none:** Default behaviour - uploads will be done in the background \
  <mark style="color:red;">`"await_upload": "none"`</mark>

<figure><img src="../.gitbook/assets/await_upload doc.png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tips:**

The **await\_upload** parameter can also be configured in deeplinks. For more information on how to configure this parameter in a deeplink, refer to the following article:

[SharinPix mobile App : Deeplink syntax](sharinpix-mobile-app-deeplink-syntax.md)
{% endhint %}

### Configure the confirm parameter

The **confirm** parameter is used to request confirmation from the user before the actual submission. A screen is shown with details of media to be submitted and the user can modify his input before finalizing the submission. The value for this parameter can be:

<mark style="color:red;">`"confirm": "batch"`</mark>

for showing the confirmation screen before batch submission.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -15.jpg" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tip:**

The **confirm** parameter can also be configured in deeplinks. For more information on how to configure this parameter in a deeplink, refer to the following article:

[SharinPix mobile App : Deeplink syntax](sharinpix-mobile-app-deeplink-syntax.md)
{% endhint %}

### Configure the watermark parameter

The **watermark** parameter is used to set up and display watermarks on images captured from the SharinPix mobile app.

The following code snippet shows how to configure the **watermark** parameter:

<mark style="color:red;">`"watermark": "Hello World"`</mark>

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -16.png" alt=""><figcaption></figcaption></figure>

The watermark is also available on the image when uploaded to the SharinPix album as depicted below:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -17.png" alt=""><figcaption></figcaption></figure>

#### Watermark Configuration with Date/Time and Location

The watermark parameter can be configured so as to also display the date/time and location at which the image was captured as demonstrated below:

<mark style="color:red;">`watermark: "Job-1 taken at <TIMESTAMP><LF>Location: <LAT>, <LON>"`</mark>

The date/time and location can be configured using the following syntax:

* **< TIMESTAMP>** **:** Returns the datetime in the format **yyyy-MM-dd HH:mm:ss Z**
* **\<LF>:** Referring to Line Feed and used to add a new line.
* **\<LAT>:** Returns the latitude.
* **< LON> :** Returns the longitude.

The picture below depicts a photo captured using the SharinPix mobile app with the following watermark parameter:

<mark style="color:red;">`watermark: "Job-12 taken at <TIMESTAMP><LF>Location: <LAT>, <LON>"`</mark>

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -18.png" alt=""><figcaption></figcaption></figure>

In the above example:

* The **\<TIMESTAMP>** returned the date/time 2022-07-03 22:17:13-0400.
* The **\<LAT>** returned the latitude 43.6699136.
* The **\<LON>** returned the longitude -79.3903104.

{% hint style="success" %}
**Tip:**

The **watermark** parameter can also be configured in deeplinks. For more information on how to configure this parameter in a deeplink, refer to the following article:

[SharinPix mobile App : Deeplink syntax](sharinpix-mobile-app-deeplink-syntax.md)
{% endhint %}

{% hint style="warning" %}
**Note:**

* Configuring the watermark parameter at this level, that is, at the SharinPix Global Settings, will be applied by default to all images captured by the SharinPix mobile app. This configuration will override all watermark configurations performed at the deeplink level.
* If images are selected from the roll while the watermark parameter is enabled, only **jpeg** images will preserve their exifs.
{% endhint %}

### Configure the aspect\_ratio parameter

The **aspect\_ratio** parameter can be used to open the camera with the specified aspect ratio.&#x20;

The available options are :

* 3:4
* 9:16

The following code snippet shows how to configure the **aspect\_ratio** parameter:

<mark style="color:red;">`"aspect_ratio": "9:16"`</mark>

### Configure the target\_size parameter

The **target\_size** parameter can be used to dictate the SharinPix mobile app to capture images with a specific image resolution. Capturing images with low resolution does affect the image quality but can reduce the storage size and accelerate the upload of images.

The following code snippet shows how to configure the **target\_size** parameter:

<mark style="color:red;">`"target_size": 1920`</mark>

Using this parameter does not mean that the resolution of the images will be exactly what you have specified when configuring.&#x20;

iOS will choose the resolution based on the specified **target\_size** and **aspect ratio**. It will select the resolution whose width has the smallest absolute difference from the specified target size.

The available resolution options for each aspect ratio are:

For an aspect Ratio of 3:4, the options are:

* 352 x 288
* 640 x 480

While for an aspect Ratio of 9:16, the options are:

* 3840 x 2160
* 1920 x 1080
* 1280 x 720

Unlike iOS, different Android phones have different possible resolutions that can be used to capture images. It is up to the mobile system to choose the resolution closest to the **target\_size** specified. In some cases, it may be higher than the **target\_size** specified.

### Configure the scan\_as parameter

The **scan\_as** parameter can be used to save the output for the scan files as images or pdf. As the default behaviour, one scan will be saved as an image and multiple scans will be saved as a pdf.

The following code snippet shows how to configure the **scan\_as** parameter:

<mark style="color:red;">`"scan_as": "image"`</mark>

The parameter scan\_as takes two values:

* **image** - Setting the value to image will save the scan files as images on the SharinPix mobile app.

<mark style="color:red;">`"scan_as": "image"`</mark>

* **pdf** - Setting the value to pdf will save the scan files as images on the SharinPix mobile app.

<mark style="color:red;">`"scan_as": "pdf"`</mark>

{% hint style="success" %}
The **scan\_as** parameter can also be configured in deeplinks. For more information on how to configure this parameter in a deeplink, refer to the following article:

[SharinPix mobile App : Deeplink syntax](sharinpix-mobile-app-deeplink-syntax.md#scan_as)
{% endhint %}

### Configure the units parameter

The **units** parameter is used to configure the measurement units that are available when annotating images with numerical values. This is available on arrows and double arrows. They can be used to automatically add SI units (e.g. ft and in) to the numbers users type. If the **units** parameter is not configured in the Global Settings, the default units will be as shown in the screen capture below.

The following code snippet shows an example of how to configure the **units** parameter:

<mark style="color:red;">`"units": ["m","mm","cm"]`</mark>

The parameter **units** take the measurement units as an array of values.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Global Configuration -19.png" alt=""><figcaption></figcaption></figure>

### Configure the roll\_limit parameter

The **roll\_limit** parameter is used to configure the maximum number of images that can be chosen from the roll. The value of the **roll\_limit** parameter cannot exceed 100, which is the maximum possible number of images per batch or capture session.

If the **roll\_limit** parameter is not configured, the maximum number of images that can be chosen from the roll is 30 by default.

The following code snippet shows an example of how to configure the **roll\_limit** parameter: <mark style="color:red;">`"roll_limit": 50`</mark>

{% hint style="success" %}
**Tip:**

If you wish to have a higher limit than 100, [contact us](../getting-started-with-sharinpix/how-to-contact-support.md) to discuss the use case.
{% endhint %}

{% hint style="warning" %}
**Warning:**

* Increasing the roll\_limit may affect the performance of the application on some devices.
* On **Android** , device manufacturers impose their **own limits** on the number of images that can be chosen in a single selection. If the **roll\_limit** exceeds the device’s restriction, the device’s limit will take priority, and users will only be able to select up to the maximum allowed by their device.
{% endhint %}

### Configure the allow\_file\_export parameter

The **allow\_file\_export** parameter allows the export of images or media files from the SharinPix app to the device's storage. For more information on different export options, refer to the following article: [Export media to internal storage](export-media-to-internal-storage.md).

This parameter accepts two values:

* **true:** When set to **true** , the export functionality becomes accessible.

<mark style="color:red;">`"allow_file_export": true`</mark>

* **false:** When set to **false** , the export functionality is unavailable. (If no value is specified, the flag defaults to false.)

<mark style="color:red;">`"allow_file_export": false`</mark>

### Configure the allow\_auto\_file\_export parameter

The **allow\_auto\_file\_export** parameter is used to export all images or media files from the SharinPix app including those selected from the roll to the device's storage. For more information on allow\_auto\_file\_export, refer to the following article: [Automatic file export](export-media-to-internal-storage.md#automatic-file-export)

This parameter accepts two values:

* **true:** When set to **true** , all images or media files will be automatically exported to the device's storage.

<mark style="color:red;">`"allow_auto_file_export": true`</mark>

* **false:** When set to **false** , no images or media files will be exported. (If no value is specified, the flag defaults to false.)

<mark style="color:red;">`"allow_auto_file_export": false`</mark>

{% hint style="warning" %}
**WARNING:**

if the auto\_destroy\_after parameter is set to zero, the ability to export files is restricted. The [**auto\_destroy\_after**](sharinpix-mobile-app-global-configuration.md#configure-the-auto_destroy_after-parameter) parameter controls the automatic deletion of files from the mobile app media once they are marked as processed after a specified period. If this parameter is configured to retain files only until needed (set to zero), the **allow\_file\_export** or **allow\_auto\_file\_export** functionality will be disabled to prevent unauthorized file export.
{% endhint %}

### Configure the required parameter

The **required** parameter allows a user to set a field as mandatory on a media record from the SharinPix mobile app. For example, the _title_ can be required on the each image taken on the SharinPix mobile app. The following code snippet shows an example of how to configure the **required** parameter for _title_ field.

<mark style="color:red;">`"required": ["title"]`</mark>

This **required** parameter takes an array of string, representing the fields to be set as mandatory. For example:

<mark style="color:red;">`"required": ["title", "description"]`</mark>

This parameter accepts the following values:

* title
* description

### Configure the snapsay\_language parameter

The **snapsay\_language** parameter forces the [**Snap & Say**](sharinpix-mobile-app-snap-say.md) language on **iOS**. This parameter accepts a language code as its value.

The following code snippet shows how to configure the **snapsay\_language** parameter:

<mark style="color:red;">`"snapsay_language": "en-US"`</mark>

{% hint style="warning" %}
**Note:**

For more information on the _Snap & Say_ supported languages and language codes, please refer to this link: [**Supported languages**](sharinpix-mobile-app-snap-say.md)
{% endhint %}

### Configure the submit\_after parameter

The **submit\_after** parameter automatically submits a batch once a defined number of media items is reached. The value specified for this parameter sets the threshold at which the SharinPix app submits the batch without manual intervention.

This parameter accepts a numerical value representing the number of media items required to trigger automatic submission.

The following code snippet demonstrates how to configure the **submit\_after** parameter:

<mark style="color:red;">`"submit_after": 10`</mark>

In the above example, with **submit\_after** set to 10, the batch will be automatically submitted once 10 media items have been added. When this threshold is reached, the batch is submitted without any further user action.

{% hint style="warning" %}
**Note:**

* If a multi-page PDF is scanned as a PDF, the whole PDF will be considered as one media item. Otherwise if it is scanned as images, each page will count as a separate media item.
* If the number of images/documents exceeds **submit\_after** , remaining media items will still be submitted.
* Note that once the number of media items is reached, the submission will start without allowing the user to view, annotate or add a title and description.
{% endhint %}

### Configure the annotation\_config parameter

The **annotation\_config** parameter allows you to specify a pre-defined annotation setup—tools, colors, and other engine settings—that the SharinPix app will load for your media. The value is the URL of an annotation configuration you’ve created in the SharinPix Annotations Configurator.

This parameter accepts a string URL pointing to your annotation config.

The following code snippet demonstrates how to configure the **annotation\_config** parameter:

<mark style="color:red;">`"annotation_config": "https://app.sharinpix.com/o/7d32/annotation_configs/e52d148b-081d-46b0-bb0c-ca8ae8f682a4"`</mark>

In the above example, with **annotation\_config** set to that URL, the SharinPix annotation engine will load your custom tools, color palette, and other settings defined in that configuration.

{% hint style="warning" %}
**Note:**

For details on how to create and customize your own annotation configuration, please check the SharinPix documentation on [Creating an Annotation Config](../features/user-interface/annotations-configurator.md#creation-of-an-annotation-config).
{% endhint %}

{% hint style="success" %}
**Tips:**\
For additional parameters, you can refer to the documentation below: [SharinPix Mobile App URL Parameters](sharinpix-mobile-app-deeplink-syntax.md#deeplink-url-parameters)
{% endhint %}
