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

# Low resolution picture displayed

## Problem analysis

When you click on SharinPix thumbnail it display the image in large view.

This view can happen to show a lower resolution version of the image than expected, most of the time this could be corrected/enhanced easily depending on the use case.

## Case 1 : Display in large screen

If you are using the high resolution screen, you may want the very high resolution version of the image to be displayed in large view.

To do so you can use the engine icon from the Toolbar and choose HR version.

## Case 2 : Zoom in picture is needed

If you want to see some details, you may want to zoom in the picture.

This could be done by just double click (or double tap on a touch device).

## Case 3 : Vectorial file is rendered into low resolution

When submitting a vectorial file to SharinPix, we render the image as a raster (webp, png or jpeg) format.

The size and resolution of the picture is depending on parameters included in the original file.

As example, for an AI file we use the artboard size parameter from Adobe Illustrator parameters.\
if you get a 500x500 pixels artboard size in your AI file it will be so rendered into a 500x500 pixels raster version in SharinPix.

To modify this, you should get into the original file and change this value. This is how to do it for AI [https://www.wikihow.com/Change-Artboard-Size-in-Adobe-Illustrator](https://www.wikihow.com/Change-Artboard-Size-in-Adobe-Illustrator)
