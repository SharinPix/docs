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

# Customizing your SharinPix Global Settings

The Global Settings allow you to set specific permissions for everybody in your organization. First, we'll walk through getting to the Global Settings, via the SharinPix Administration Dashboard. Then we'll check out some of the basic features that you can enable through the Global settings.

For notification recipients, see [Notification settings](notification-settings.md).

{% hint style="danger" %}
**Note:**

The SharinPix Album abilities available on the Global Settings can also be configured using [SharinPix Permissions](sharinpix-permission-object-how-to-create-and-assign-custom-permission.md).

The SharinPix Global Settings configuration is applied on albums by default **unless** a SharinPix Permission has been assigned to the album.

**However, for security reasons, we strongly advise using a SharinPix Permission to control album abilities instead of the SharinPix Global Settings.**
{% endhint %}

## Access and configure the SharinPix Global Settings

To access the _SharinPix Global Settings_ from your Organization, proceed as follows:

* Click on the **App Launcher**
* Enter SharinPix Settings in the search bar and select **SharinPix Settings**
* On the SharinPix Settings page, click on the **Go to administration dashboard** button

![](../.gitbook/assets/0594671b-d305-436c-9802-8de13f288234.png)

* _You may have to sign in again to authenticate your credentials._
* Next, click on the **Settings** tab to access the Global Settings

![](<../.gitbook/assets/Screenshot 2023-11-20 at 4.39.32 PM.png>)

To configure the Global Settings, click on the **Edit Organization** button.

![](<../.gitbook/assets/Screenshot 2023-11-20 at 4.42.08 PM.png>)

Example of the User Interface in the SharinPix Settings:

![](<../.gitbook/assets/0a274cb2-196b-4034-a4a0-3cb13d455cf3 (1).png>)

* To enable/disable album abilities, check/uncheck the checkboxes accordingly.
* Click on the **Update Organization** button located at the bottom of the page to save the changes.

## Overview of the SharinPix Global Settings parameters

Global Settings give users access to the settings below:

* Add Button - for all users
* Display Images from all Users
* Add a tag function
* Delete button

<figure><img src="../.gitbook/assets/asimg101.jpg" alt=""><figcaption></figcaption></figure>

Adding tags to the photos:

<figure><img src="../.gitbook/assets/asimg102.jpg" alt=""><figcaption></figcaption></figure>

Add a tag Icon:

![](../.gitbook/assets/7a577d0f-7ad8-474c-86b5-3e6c5cf8696a.jpg)

Tag List with Add a Tag link:

![](../.gitbook/assets/09ed4069-4913-4120-bbf4-f4940ff57512.jpg)

Add a Tag:

![](../.gitbook/assets/e6de187d-c0f0-434b-a974-1fbbb1c10e10.jpg)

Create and Display Tags:

![](../.gitbook/assets/68c04c06-5f0f-4f8e-a6cc-e00751863c78.jpg)

Photo with Tags:

<figure><img src="../.gitbook/assets/asimg103.jpg" alt=""><figcaption></figcaption></figure>

**In fullscreen, all the tool icons are visible:**

1\. Tag the image

2\. Download the image

3\. Open the image in fullscreen on another tab

4\. & 5. Rotate the image

6\. & 7. Flip the image

8\. Duplicate the image

9\. Crop the image

10\. Hide/display the image annotations

11\. Annotate the image

12\. Set the image quality

13\. View image information

14\. Close the fullscreen view

15\. Image zoom slider

![](<../.gitbook/assets/Screenshot 2023-11-13 at 4.31.06 PM.png>)

**Edit Tools - have some fun here**

1. Erase
2. Size of mark
3. Color of mark
4. Text box
5. Marker
6. Line
7. Save
8. Exit
9. Rectangle
10. Circle
11. Arrow
12. Double Arrow

![](../.gitbook/assets/s2.png)

## Menu Command

The **Menu Command** section provides some options as depicted in the images below:

![](../.gitbook/assets/ab11.png)

These options are available in the **Thumbnail Menu** as shown below:

![](../.gitbook/assets/ab7.png)

{% hint style="info" %}
For more information about how to access the **Thumbnail Menu** , refer to the following article: [**Thumbnail View - The menu**](../features/user-interface/thumbnail-view-the-menu.md)
{% endhint %}

## Album Images Sort

The **Album Images Sort** section provides options that can be used to apply sorting on the images found in an album.

<figure><img src="../.gitbook/assets/asimg110.png" alt=""><figcaption></figcaption></figure>

## Privacy Settings

The **Privacy** section permits you to set whether to ask the user to access the geolocation or not.

<figure><img src="../.gitbook/assets/asimg109.png" alt=""><figcaption></figcaption></figure>

## Miscellaneous

<figure><img src="../.gitbook/assets/asimg108.png" alt=""><figcaption></figcaption></figure>

This section provides the following options:

* No image selection after upload
  * By default, after the first upload to an album, all the images uploaded are selected. After applying the **No images selection after upload** options, the images will not be selected after the first upload.
* Download zip
  * The **Download zip** option enables the user to download the images in a zip file.

![](../.gitbook/assets/ab14.png)

* Salesforce field on sObject SharinPixImage\_\_c with custom image filename for zip download
  * This parameter allows us to download the image with a custom filename. The value of the custom filename should be stored in a Salesforce field on the **SharinPixImage\_\_c** sObject.
  * The **Salesforce field API name** should then be used as the value for the parameter **download\_custom\_filename**, for example: download\_custom\_filename: 'CustomFilename\_\_c', where _CustomFilename\_\_c_ refers to the API name of the Salesforce field storing the value for the custom filename.
* Autosave annotations
  * By default, the save button has to be clicked to save annotations on the image. After applying the **Autosave annotations** option, annotations are saved automatically as they are added.
* Handle to duplicate annotations
  * The **Handle to duplicate annotations** allows duplication of an annotation.
* Zoom slider
  * The **Zoom slider** provides a slider to zoom in and zoom out of the image.

<figure><img src="../.gitbook/assets/asimg107.png" alt=""><figcaption></figcaption></figure>

* Image color adjustment
  * The **Image color adjustment** option enables the **color\_adjustment** ability which allows the user to adjust the brightness, contrast and saturation.

<figure><img src="../.gitbook/assets/asimg106.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Information:**

Global Settings allow the system administrators to choose which features to be made available for every organizational user by default. After that, you can restrict "who sees what" using [SharinPix Permission records](sharinpix-permission-object-how-to-create-and-assign-custom-permission.md) or [SharinPix Permission Parameters](sharinpix-permission.md).
{% endhint %}
