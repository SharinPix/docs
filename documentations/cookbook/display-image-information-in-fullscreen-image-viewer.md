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

# Display image information in fullscreen image viewer

This article demonstrates the use of **viewer\_infos** option in **Code Generator** to display **image information** when viewed in fullscreen mode.

The information displayed are:

1. Image filename
2. Upload date and time
3. Tags

## Enabling viewer\_infos

* Access **Code Generator** from the top navigation bar of the **Administration DashBoard**.
* Check **"Display image information in the viewer"** checkbox in the **Display** section of the Code Generator.
* Optional: Add tags to the user's set of permissions for image tagging.

![](<../.gitbook/assets/screenshot-localhost_5000-2019.09.12-14_06_00(1) (1).png>)

* Notice that **viewer\_infos** option has been **enabled** in the user's set of permissions.

![](<../.gitbook/assets/screenshot-localhost_5000-2019.09.13-09_13_58(1) (1).png>)

## Testing viewer\_infos

* Upload an image in the **Preview** section.

![](<../.gitbook/assets/screenshot-localhost_5000-2019.09.13-09_12_48 (1).png>)

* Click on the image to access it in fullscreen mode.
* Notice that the **image information** are displayed at the **top left corner** of the fullscreen image viewer.

![](<../.gitbook/assets/selection (1).png>)
