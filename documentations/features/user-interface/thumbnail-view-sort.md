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

# Thumbnail View - Sort

SharinPix supports 3 different sortings:

* [Sort by Date Taken](thumbnail-view-sort.md#sort-by-date-taken)
* [Sort by Date Uploaded](thumbnail-view-sort.md#sort-by-date-uploaded)
* [Custom Sort](thumbnail-view-sort.md#custom-sort)

{% hint style="warning" %}
**Warning:**

If the album contains more than 200 images, sorting cannot be performed.
{% endhint %}

## Sort by Date Taken

The date taken is the one provided on the image metadata. If the file format doesn't support date taken, the creation date of the file is used.

* Below is an example of the sorting by Date Taken in ascending Order

![](<../../.gitbook/assets/image (67) (2).png>)

* Below is an example of the sorting by Date Taken in descending order

![](<../../.gitbook/assets/image (68) (3).png>)

## Sort by Date Uploaded

* Sort by Date Uploaded in ascending order.

![](<../../.gitbook/assets/image (69) (1).png>)

* Sort by uploaded date in descending order.

![](<../../.gitbook/assets/image (70) (2).png>)

## Custom Sort

* The customized sort enable by using the SharinPix Permission.

You can check the documentation on [Search Thumbnail View - Sort](search-thumbnail-view-sort.md) for more info.

![](<../../.gitbook/assets/image (71) (1).png>)

![](<../../.gitbook/assets/image (65) (2).png>)

### Edit Position

* With Edit Position you can drag and drop images to change the order.

![](<../../.gitbook/assets/image (66) (3).png>)

Note that if you have a lot of images and are in pagination mode, you should better go full screen before using the edit customized sort mode as scroll is working in a better way with drag and drop than pagination.

**Note:** If the current album hosts a significant number of images while you are in pagination mode, it is recommended to the activate the **fullscreen mode** before activating the **edit mode.**

{% hint style="success" %}
Sort is also available on SharinPix Search Component. Click [here](search-thumbnail-view-sort.md) to see how to set up sort on Search Component.
{% endhint %}
