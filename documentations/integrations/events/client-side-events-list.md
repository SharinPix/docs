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

# Client-side Events List

Client-side events are the unsung heroes that bring web pages to life, reacting precisely to user input. They occur from a simple mouse click to a complex drag-and-drop operation.

The following SharinPix components can raise client-side events:

* The [SharinPix Album component ](/broken/spaces/Hhhsz8OAg6xcF0k0DJhg/pages/LWOdV9eWz0NXM3QUjTmP)(which displays images stored at a record level)
* The [SharinPix Single Image component ](/broken/spaces/Hhhsz8OAg6xcF0k0DJhg/pages/KspOsiej3fTtx6q3PtcI)(which displays an image having a specific tag stored at a record level)
* The [SharinPix Search component](/broken/spaces/Hhhsz8OAg6xcF0k0DJhg/pages/hoaqhCz87wLZu1pyTMFv) (which displays images searched across different records)

Each has its own set of events.

## Album Component events

* **image-new** – when an image is uploaded
* **images-selected** – when an image check box is checked (or unchecked)
* **image-processed** – After the completion of processing a large file.
* **image-deleted** – when an image has been deleted
* **image-undeleted** – when an image has been undeleted
* **image-rotated** – when an image is rotated
* **image-cropped** – when an image is cropped
* **image-annotated** – when an image is annotated
* **tag-image-new** – when a tag is added to an image
* **tag-image-deleted** – when a tag is removed from an image
* **viewer-image-viewed** – when an image is clicked to be viewed in the large view
* **viewer-closed** – when the large view is closed
* **image-sort-completed** – when custom sorting has been applied to images
* **image-sync-completed** – when an image has been synchronized
* **restricted-file-error** - when uploading a restricted file type using the [upload\_accept parameter](../../features/upload-images/restrict-uploads-using-file-extensions.md).

## Single Image Component events

* **image-new** – when an image is uploaded
* **images-selected** – when an image check box is checked (or unchecked)
* **image-processed** – After the completion of processing a large file.
* **image-deleted** – when an image has been deleted
* **image-undeleted** – when an image has been undeleted
* **image-rotated** – when an image is rotated
* **image-cropped** – when an image is cropped
* **image-annotated** – when an image is annotated
* **tag-image-new** – when a tag is added to an image
* **tag-image-deleted** – when a tag is removed from an image

## Search Component events

* **search-ready** – when the component is opening and fully loaded
* **images-selected** – when an image check box is checked (or unchecked)
* **viewer-image-viewed** – when an image is clicked to be viewed in the large view
* **viewer-closed** – when the large view is closed
