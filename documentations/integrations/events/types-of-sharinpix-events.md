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

# Types of SharinPix Events

## What are SharinPix Events ?

SharinPix Events are particular events which are emitted when a specific action is performed on a SharinPix Album.

## Types of Events

### Client-side Events

**Client-side events** refers to SharinPix events emitted and used within an in-browser context.

| <p>Event Name<br></p>                          | <p>Trigger Action<br></p>                                                                                                                                                          |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><code>image-new</code><br></p>              | Triggered for each new image added to an album.                                                                                                                                    |
| <p><code>image-processed</code><br></p>        | <p>Triggered after upload when the exifs have been extracted from the uploaded image.<br></p>                                                                                      |
| <p><code>upload-done</code><br></p>            | Triggered when one or more images have already been added to an album.                                                                                                             |
| <p><code>image-deleted</code><br></p>          | Triggered for each image deleted from an album.                                                                                                                                    |
| <p><code>tag-image-new</code><br></p>          | Triggered for each new tag applied to an image.                                                                                                                                    |
| <p><code>tag-image-deleted</code><br></p>      | <p>Triggered for each tag removed from an image.<br></p>                                                                                                                           |
| <p><code>viewer-image-viewed</code><br></p>    | Triggered when the Large View mode is activated.                                                                                                                                   |
| <p><code>viewer-closed</code><br></p>          | <p>Triggered when the Large View mode is deactivated.<br></p>                                                                                                                      |
| <p><code>images-selected</code><br></p>        | Triggered for each image being selected.                                                                                                                                           |
| <p><code>image-annotated</code> <br></p>       | Triggered for each annotation created and applied to an image.                                                                                                                     |
| <p><code>action</code><br></p>                 | Triggered whenever an action, which has been specified in the Apex Parameters, is executed.                                                                                        |
| <p><code>restricted-file-error</code> <br></p> | Triggered when uploading a restricted file type using the [upload\_accept parameter](https://docs.sharinpix.com/m/documentation/l/1649097-restrict-uploads-using-file-extensions). |

```javascript
    // Capture in Javascript code
    window.addEventListener('message', (event) => {
    	if (event.data.name == 'image-new') {
        	console.log(event.data.payload);    
        }
    })
```

### Server-side Events

**Server-side events** refer to specific emitted events that either:

* execute predefined Apex methods or,
* make an HTTP POST request (**Webhook**) to predefined endpoints.

| Event name                                      | Trigger Action                                                                                                                                                            |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p><code>New Image</code><br></p>               | Triggered for each new image added to an album.                                                                                                                           |
| <p><code>Processed image</code><br></p>         | <p>Triggered after upload when the exifs have been extracted from the uploaded image.<br></p>                                                                             |
| <p><code>New publication</code><br></p>         | Triggered when a new Chatter Post is created through the SharinPix Chatter Component.                                                                                     |
| <p><code>New tag image</code><br></p>           | Triggered when a new tag is applied to an image.                                                                                                                          |
| <p><code>Delete image</code><br></p>            | Triggered when an image is deleted from an album.                                                                                                                         |
| <p><code>Delete tag image</code><br></p>        | Triggered when a Tag is deleted from an image.                                                                                                                            |
| <p><code>Upload done</code><br></p>             | <p>Triggered once all images have been uploaded.<br>Note that if more than 50 images are uploaded at once, multiple events will be sent, each with at most 50 images.</p> |
| <p><code>New Einstein prediction</code><br></p> | Triggered when a request for an Einstein prediction has been made and a response obtained in return.                                                                      |
