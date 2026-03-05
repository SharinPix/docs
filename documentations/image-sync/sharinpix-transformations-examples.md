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

# SharinPix Transformations Examples

This article demonstrates the different types of transformations that can be applied to an image in a SharinPix Album.

## Fill to Size

* Create an image with the exact given width and height while retaining the original aspect ratio. (height = width = 250 pixels)

<figure><img src="../.gitbook/assets/test (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Fit to Size

* The image is resized so that it takes up as much space as possible within a bounding box defined by the given width and height values. (height = width = 250 pixels)

<figure><img src="../.gitbook/assets/test (5) (1) (1).png" alt=""><figcaption></figcaption></figure>

## Pad to Size

* Resize the image to fill the given width and height while retaining the original aspect ratio and with all of the original image visible. (height = width = 200 pixels)

<figure><img src="../.gitbook/assets/test (1).jpg" alt=""><figcaption></figcaption></figure>

## Scale to Size

* Change the size of the image exactly to the given width and height without necessarily retaining the original aspect ratio. (height = width = 150 pixels)

<figure><img src="../.gitbook/assets/test (2).jpg" alt=""><figcaption></figcaption></figure>

## Limit to size

* Limit the image's width and height to a specific value. If the image dimensions exceed the specified value(s), the image is down scaled to match the same. Else the image dimensions are retained. In the example below, the **Limit to size** value has been set to 250 pixels (height=width = 250 pixels) and the original image size is 300x300. Therefore, the image has been down scaled to a height and width of 250 pixels.

<figure><img src="../.gitbook/assets/test (3).jpg" alt=""><figcaption></figcaption></figure>

