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

# SharinPix Webhook Payload

{% hint style="info" %}
This article gives examples of the different payloads available for events specified in SharinPix Webhook. These events are:

* [New image](sharinpix-webhook-payload.md#new-image)
* [Processed image](sharinpix-webhook-payload.md#processed-image)
* [New tag image](sharinpix-webhook-payload.md#new-tag-image)
* [Delete image](sharinpix-webhook-payload.md#delete-image)
* [Delete tag image](sharinpix-webhook-payload.md#delete-tag-image)
* [Upload done](sharinpix-webhook-payload.md#upload-done)
* [New einstein prediction](sharinpix-webhook-payload.md#new-einstein-prediction)
{% endhint %}

{% hint style="success" %}
**Tip:**

For more information about the events listed above, please refer to the following:

[Server-side Events](../integrations/events/types-of-sharinpix-events.md#server-side-events)
{% endhint %}

## New image

The SharinPix Webhook Payload for the **New image** event is as shown below:

```yaml
id: f37e01b7-942c-4179-bfd0-0cccf4700328
public_id: f37e01b7-942c-4179-bfd0-0cccf4700328
metadatas: {}
width: 3786
height: 4733
rotation: 0
gps: 
size: 1526906
format: jpg
original_url: <Image's original URL>
filename: NorthBuilding
created_at: '2020-08-12T08:18:57.549+02:00'
taken_at: 
infos:
  format: jpg
page: 1
group_id: 
exifs:
  DateTimeOriginal: 
processed: true
processing_error: 
album_id: 0WOB0000000YsjGOAS
thumbnails:
  full: <URL displaying image in full format>
  large: <URL displaying image in large format>
  mini: <URL displaying image in mini format>
```

In the payload above, information regarding the newly added image is given such as, its ID, dimensions, format, album ID as well as related thumbnail URLs.

## Processed image

The SharinPix Webhook Payload for the **Processed image** event is as shown below:

```yaml
 id: 26e19efc-5bdf-4534-890e-df44e26975f8
 public_id: 26e19efc-5bdf-4534-890e-df44e26975f8
 metadatas:  
    sharinpix_mobile_app_url: <Mobile app URL> 
    sharinpix_mobile_app_job_id: <Mobile app job ID>
    sharinpix_mobile_app_batch_id: <Mobile app batch ID>  
    sharinpix_mobile_app_media_id: <Mobile app media ID>  
    sharinpix_mobile_app_device_id: <Mobile app device ID>
 width: 3024
 height: 4032
 rotation: 0
 gps:
 - -20.30993611111111
 - 57.486961111111114
 size: 2771157
 format: jpg
 original_url: <Image's original URL>
 filename: 4C1D0F5B-4F40-40FB-9C23-0B56B3DAB8D7
 created_at: '2021-11-12T13:23:15.327+01:00'
 taken_at: '2021-11-12T17:21:55.000+01:00'
 infos:
    format: jpg
 page: 1
 group_id: 
 exifs:  
    DateTimeOriginal: '2021-11-12T16:21:55.000Z'
 processed: true
 processing_error: 
 album_id: <Album ID>
 thumbnails:  
    full: <Image full URL>
    large: <Image large URL>
    mini: <Image mini URL>
```

## New tag image

The **New tag image** event is triggered when images are tagged with either pre-defined tags or any tags. The payload is as follows:

```yaml
  id: da40f34c-5e88-454c-bfe0-d69411261602
  tag:
    id: '09078003-4dd2-4ad8-ae8c-536aaa7017b3'
    name: Villa
    label: '{"en":"Villa","fr":"Villa"}'
  image:
    id: 8399c579-c037-451f-88ad-4d03e2aa02cd
    public_id: 8399c579-c037-451f-88ad-4d03e2aa02cd
    metadatas: {}
    width: 4288
    height: 2848
    rotation: 0
    gps: 
    size: 1412814
    format: jpg
    original_url: <Image's original URL>
    filename: NorthBuilding
    created_at: '2020-06-30T09:19:25.882+02:00'
    taken_at: 
    infos:
      format: jpg
    page: 1
    group_id: 
    exifs:
      DateTimeOriginal: 
    processed: true
    processing_error: 
    album_id: 001B000001KKHZeIAP
    thumbnails:
      full: <URL displaying image in full format>
      large: <URL displaying image in full format>
      mini: <URL displaying image in full format>
  user:
    public_id: <User's public ID>
    fullname: <User's fullname>
    email: <User's email>
    username: <Username>
    sfid: <User's Salesforce ID>
```

The above payload provides information about the tag, the tagged image and the user who applied the tag.

## Delete image

The **Delete image** event's payload provides information about the deleted image as shown below:

```yaml
id: f37e01b7-942c-4179-bfd0-0cccf4700328
public_id: f37e01b7-942c-4179-bfd0-0cccf4700328
metadatas: {}
width: 3786
height: 4733
rotation: 0
gps: 
size: 1526906
format: jpg
original_url: <Image's original URL>
filename: NorthBuilding
created_at: '2020-08-12T08:18:57.549+02:00'
taken_at: 
infos:
  format: jpg
page: 1
group_id: 
exifs:
  DateTimeOriginal: 
processed: true
processing_error: 
album_id: 0WOB0000000YsjGOAS
thumbnails:
  full: <URL displaying image in full format>
  large: <URL displaying image in large format>
  mini: <URL displaying image in mini format>
```

## Delete tag image

The **Delete tag image** event's payload provides information about the removed tag, the image for which tag has been omitted as well as information about the user who performed the action. The payload is presented below:

```yaml
  id: 3f5d46b6-bdf0-4cd5-aa00-a7b4cb590857
  tag:
    id: 9c3ba3d4-9c45-414d-99ce-43dabf845ae7
    name: main
    label: '{"en":"main","fr":"main"}'
  image:
    id: 8399c579-c037-451f-88ad-4d03e2aa02cd
    public_id: 8399c579-c037-451f-88ad-4d03e2aa02cd
    metadatas: {}
    width: 4288
    height: 2848
    rotation: 0
    gps: 
    size: 1412814
    format: jpg
    original_url: <Image's original URL>
    filename: NorthBuilding
    created_at: '2020-06-30T09:19:25.882+02:00'
    taken_at: 
    infos:
      format: jpg
    page: 1
    group_id: 
    exifs:
      DateTimeOriginal: 
    processed: true
    processing_error: 
    album_id: 001B000001KKHZeIAP
    thumbnails:
      full: <URL displaying image in full format>
      large: <URL displaying image in large format>
      mini: <URL displaying image in mini format>
  user:
    public_id: <User's public ID>
    fullname: <User's fullname>
    email: <User's email>
    username: <Username>
    sfid: <User's Salesforce ID>
```

## Upload done

An example of the **Upload done** event's payload for image upload via a mobile device is given below:

```yaml
app_url: sharinpix://upload?token=<The SharinPix Token>
count: 1
platform: mobile
album_id: 0WOB0000000YsjGOAS
image_ids: 59d6ec21-617a-438b-8913-b0d598f88850
```

The payload consists of:

* **app\_url:** Provides the deeplink to the SharinPix app
* **count:** Gives the number of images captured
* **platform:** Indicates whether the images were captured from the **web** or a **mobile** device. In this case the image was uploaded using a mobile device
* **album\_id:** Gives the album ID
* **image\_ids:** Gives the public IDs of the images captured

The payload obtained for an Upload Done event when images are uploaded via the **web** differs slightly as shown below:

```yaml
count: 1
platform: web
album_id: 003B000000HhRRnIAN
image_ids: 153ac9da-3a3f-4e74-a839-3e5515349a9b
```

### New einstein prediction <a href="#new-einstein-prediction" id="new-einstein-prediction"></a>

The **Einstein prediction** event's payload is as shown below:

```yaml
einstein_model_id: 3c0a9f99-3f4a-4951-bc7a-6bdcd46cfd13
probability:
- probability: 0.99653995
  label: car
- probability: 0.0034591604
  label: truck
- probability: 9.0841826e-07
  label: moto
status: completed
image_id: 89919357-7324-4abe-8982-ca48fa2bd327
model_id: a042400000Ns4HdAAJ
type: image-classification
message: 
```

The payload provides information about the model, the image ID as well as the calculated probabilities.
