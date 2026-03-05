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

# Image Sync not working when using Salesforce mobile app to upload photos. What should I do?

If you are encountering issues with SharinPix Image Sync when uploading photos via the **Salesforce mobile app** , here are some configurations that need to be looked into:

* **Check if option Enable Image Sync has been applied to the SharinPix Album**\
  \
  The first thing that needs to be checked is whether the option **Enable Image Sync** has been applied to the SharinPix Album component on which images are being uploaded.\
  \
  If you need help to verify this part, please refer to the following article:\
  [Enable Image Sync for Lightning](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/enable-image-sync-for-lightning)
* **Check if Image Sync has been set up properly for the object on which photos are being uploaded**\
  \
  Another configuration that should be verified is the Image Sync setup for the object on which photos are being uploaded via the Salesforce mobile app.\
  \
  One step that can be easily missed here is the assignment of the SharinPix Image Sync's permission set (that is, **SharinPix Image Sync Permission**) to the user uploading the photos. For more information about the setting up of the SharinPix Image Sync, you can refer to the article that follows:\
  [Setup SharinPix Image Sync](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/setup-sharinpix-image-sync)
