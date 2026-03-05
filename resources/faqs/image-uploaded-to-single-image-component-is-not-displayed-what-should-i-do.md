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

# Image uploaded to Single Image component is not displayed. What should I do?

If the image uploaded to the **SharinPix Single Image** component is not displayed or disappears after a page refresh, this might be because the tag used in the component is marked unlisted.

Unlisted tags are 'unavailable tags' and cannot be used on SharinPix components. Therefore, if you applied an unlisted tag to a Single Image component, the images will not show up on the same due to the tag unavailability.

To resolve the above issue, that is to mark the tag as listed so that it can be used on the component, follow the steps below:

* Access the [SharinPix Global Settings](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/overview-of-the-sharinpix-administration-dashboard) by searching for **SharinPix Settings** using the **App Launcher**
* Next, click on the **Go to administration dashboard** button. This will open the global settings
* Once on the global settings, click on **Tags** on the top menu bar
* Click on the **Unlisted** button located on the top left:

![](.gitbook/assets/screenshot-app.sharinpix.com-2021.08.11-10_06_34.png)

* Search for the desired tag and click on **Edit**

![](.gitbook/assets/screenshot-app.sharinpix.com-2021.08.11-10_07_57.png)

**Note:** _If you cannot see the tag in the list at this point, go back to the **Listed** section and ensure that the tag is marked as listed from there._

* Once on the Edit Tag page, check the **Listed** checkbox to mark the tag as listed:

![](.gitbook/assets/screenshot-app.sharinpix.com-2021.08.11-10_11_25.png)

* Click on **Update Tag** when done and test the component again
