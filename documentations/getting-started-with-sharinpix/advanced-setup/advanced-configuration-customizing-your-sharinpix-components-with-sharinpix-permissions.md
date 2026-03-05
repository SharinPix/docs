# Advanced Configuration - Customizing your SharinPix components with SharinPix Permissions

SharinPix Permission records are used to enable or restrict [abilities](../../access-and-security/sharinpix-abilities.md) on SharinPix components.

This article demonstrates how to:

1. Create a SharinPix Permission record for an album component.
2. Configure the component abilities on the SharinPix Permission record.
3. Assign the permission to an album component.
4. Overview of the main album abilities.

**Note:**

The SharinPix Album abilities available in the SharinPix Permission record are also available on the [SharinPix Global Settings](../../access-and-security/customizing-your-sharinpix-global-settings.md).

When no SharinPix Permission is assigned, the abilities set in the SharinPix Global Settings will be applied to all album components by default.

**However, for security reasons, we strongly advise using a SharinPix Permission to control album abilities instead of the SharinPix Global Settings.**

## 1. Create a SharinPix Permission record for an album component

To create a new SharinPix Permission record, follow the steps below:

* From App Launcher, type **SharinPix Permission**
* Then click on the button **New**
* Next, in the **Information** section, enter the name of the permission. The SharinPix best practice is to name the permission **All** to indicate that this permission provides all basic album abilities.
* You can leave the description blank since it is optional.

![](<../../.gitbook/assets/Screenshot 2023-10-20 at 2.21.40 PM (1) (1).png>)

* Ensure that the \*\*Album \*\*option is selected as we are creating a permission record for an album component.

![](<../../.gitbook/assets/Screenshot 2023-10-20 at 2.21.40 PM (1) (1).png>)

## 2. Configure the component abilities on the SharinPix Permission record

All basic album abilities are set to true by default when creating a new SharinPix Permission record. You can, therefore, save the permission right away if you want to keep the default parameters.

You can still review the abilities and modify them as desired as depicted below.

![](<../../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.04.12-14_13_24 (1) (1) (1).png>)

Please note that each checkbox has 3 states:

* \*\*True: \*\*When a checkbox is selected, this will enable the ability on the component.
* \*\*False: \*\*When a checkbox is left blank, this will disable the ability on the component.
* \*\*Default value: **When a dash is present in the checkbox. This means that the ability value will reflect the value set in** SharinPix Global Settings \*\*by default.

## 3. Assign the permission to an album component

To assign the SharinPix Permission to an album component:

* Save the permission record.
* Copy the permission's name (**All** in our case).
* Go to the **Lightning App Builder** page on any record page containing the SharinPix Album component.
* On the album component, paste the permission's name in the \*\*Custom Permission Id or Name \*\*parameter.
* Save the changes when done.

![](<../../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2021.04.12-15_43_49 (1) (1).png>)

## 4. Overview of the main album abilities and how to configure them using a SharinPix Permission record

### Standard Album Abilities

SharinPix Permission records can provide users access to the following album features:

1. Display images
2. Upload photos
3. View the album in fullscreen
4. Delete images
5. Access deleted images in the trash for 30 days after deletion

![](<../../.gitbook/assets/Screenshot 2023-11-13 at 3.07.55 PM (1) (1).png>)

### Standard Tag Abilities

SharinPix Permissions can also allow users to:

1. Tag Images
2. View tags on images

![](<../../.gitbook/assets/Screenshot 2023-11-13 at 3.28.14 PM (1) (1).png>)

The tags abilities are also available when opening an image in fullscreen.

![](<../../.gitbook/assets/Screenshot 2023-11-13 at 3.38.08 PM (1) (1).png>)

### The Image Fullscreen View in a Nutshell

To open an image in fullscreen, click on the image thumbnail on the album component.

The following tools can be made available in the image fullscreen view.

![](<../../.gitbook/assets/Screenshot 2023-11-13 at 4.31.06 PM (1) (1).png>)

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

### The Image Annotation Menu

The annotation menu is available in the fullscreen view and provides the following options:

![](<../../.gitbook/assets/s2 (1) (1).png>)

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

### The Album Menu Command

Common album menu abilities are:

1. Copy images
2. Download selected images in a zipped file
3. Share pre-selected images outside of Salesforce

![](<../../.gitbook/assets/Screenshot 2023-11-13 at 4.48.49 PM (1) (1).png>)

Tip:

For more information about how to access the **Thumbnail Menu** , refer to the following article:\*\* \*\*[Thumbnail View - The menu](../../features/user-interface/thumbnail-view-the-menu.md)

### Image Sorting Abilities

Using SharinPix Permission records, the images uploaded to albums can be sorted:

* By uploaded date
* Date taken
* Or can be sorted in a custom way by dragging and dropping the images

![](<../../.gitbook/assets/Screenshot 2023-11-13 at 4.52.40 PM (1) (1).png>)

![](<../../.gitbook/assets/Screenshot 2023-11-13 at 4.53.25 PM (1) (1).png>)
