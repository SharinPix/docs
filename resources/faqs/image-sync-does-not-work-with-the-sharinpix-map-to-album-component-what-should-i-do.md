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

# Image Sync does not work with the SharinPix Map to Album component. What should I do?

If the SharinPix Image Sync feature does not work on the SharinPix Map to Album component, despite having[ configured the Image Sync properly on the object](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/setup-sharinpix-image-sync), this is probably due to a missing configuration on the Map to Album component and the relating SharinPix Album preventing the Image Sync.

To enable the Image Sync feature when using the Map to Album component to upload a picture on a SharinPix Album, you should ensure that the same value is specified as the **Component Id** parameter on both components.

Here is an example of how you should proceed:

* On the Lightning App Builder, access the SharinPix Map to Album's parameters
* Enter a value for the **Component Id** parameter as demonstrated below:

<figure><img src=".gitbook/assets/test (7).png" alt=""><figcaption></figcaption></figure>

* Next, access the parameters of the SharinPix Album on which you want to upload the map images
* For the SharinPix Album's **Component Id** parameter, enter the same value used for the Map to Album's **Component Id** parameter:

<figure><img src=".gitbook/assets/test (8).png" alt=""><figcaption></figcaption></figure>

* Once you are done, save the changes and test the Image Sync feature again using the Map to Album component to upload a map image to the album
