---
description: >-
  Tasks and Events don’t allow the lookup field required for Image Sync. This
  article explains how to use a mirror object so Image Sync functions as if
  attached directly to Activities.
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

# How to set up Image Sync for SharinPix Albums on Events and Tasks

## How Image Sync Works and Why Activities Are Different

Image Sync is a SharinPix feature that creates **SharinPix Image records** containing metadata about images, such as:

* Date taken
* Width and height
* Format
* Filename

For Image Sync to work, the following elements are required:

1. SharinPix Component with Image Sync enabled&#x20;
2. **SharinPix Image Lookup field** - Each SharinPix Image record needs a field that identifies the **parent record** (the album where the image belongs).
3. SharinPix Custom Metadata > SharinPix Sync Setting - This tells the SharinPix package which lookup field stores the parent record ID.
4. SharinPix Image Sync Permission Set – Allows users to create, edit, and delete SharinPix Image records.

{% hint style="info" icon="question" %}
## Why Activities (Tasks and Events) Are Different

Tasks and Events are part of Salesforce’s **Activity model**, which behaves differently from standard objects.

Key differences:

* Custom fields for **Tasks and Events are created on the shared Activity object**
* Activities **do not support lookup relationships in the same way as standard objects**

Because of this limitation, **Image Sync cannot directly store image records against Activities**.
{% endhint %}

## Solution Overview

To work around this limitation, the recommended approach is to create a **custom object that acts as the image host for each Activity**.

The architecture works like this:

1. When a **Task or Event is created**, a Flow automatically creates a corresponding record in a custom object (for example, **Activity Album**).
2. The Activity stores a **lookup to that custom record**.
3. The SharinPix **Album and Launcher components operate on the custom object record instead of the Activity itself**.

{% hint style="info" %}
**Note:** \
\
This is a suggested approach. Consider how it fits with your existing Salesforce data model, automation, and data cleanup processes, and test the configuration in a sandbox before deploying to production.
{% endhint %}

## Components of the Solution

1. [Custom Object ](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#create-the-custom-object)- A custom object that supports Image Sync and stores one record per Activity.
2. [Activity Lookup field](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#create-the-activity-lookup-field) - A lookup field on Task/Event pointing to the custom object.
3. [Flows](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#flows)
   1. [Record-triggered flow](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#record-triggered-flow) - Creates the custom object record when a Task/Event is created.
   2. [Screenflow for SharinPix Album](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#screen-flow-for-sharinpix-album) - Displays the album stored on the custom object.
   3. [Screenflow for Launchers](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#screen-flow-for-launchers) - Ensures images are captured and stored in the custom object album.
4. [Setup Image Sync](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#setup-image-sync) - configure Image Sync for the custom Object
5.  [Add Screen Flows to the Task/Event's Lightning Page](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#add-screen-flows-to-the-task-events-lightning-page)



### Create the Custom Object

This object stores one record per Event or Task and hosts the SharinPix Album for the Activity.

*   Create a custom Object: ⚙️Setup > Object Manager > Create > Custom Object

    (e.g., "Activity Album")

<p align="right">Salesforce Trail: <a href="https://trailhead.salesforce.com/content/learn/modules/create-a-custom-object-quick-look/create-a-custom-object">Create a Custom Object </a></p>

### Create the Activity Lookup Field

A custom lookup field on the Activity (Task/Event) that relates it to its corresponding custom object record.

*   Create a custom lookup field: ⚙️Setup > Object Manager > Fields and Relationships > New

    * _Related to:_ [_custom Object_](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#custom-object)



    Configuration example:

    * **Field Type:** Lookup Relationship
    * **Related To:** Activity Album
    * **Label:** Related Activity Album

<p align="right">Salesforce Trail: Data-modeling > <a href="https://trailhead.salesforce.com/content/learn/modules/data_modeling/object_relationships#create-a-lookup-relationship">Create a Lookup Relationship</a></p>

### Flows

Create new flows: ⚙️Setup > Quick Find "Flows" > "New Flow"

#### Record-triggered Flow

Automatically creates the related custom object record when a new Event or Task is created.

<figure><img src=".gitbook/assets/DOC SF - 1920 x 1080 (14).png" alt=""><figcaption></figcaption></figure>

* Configure Start
  * _Object_: Task or Event
  * _Trigger_: “A record is created”
  * _Entry Conditions_: None
  * &#x20;_Optimize for_: Actions and Related Records
* Create Records
  * _How to set record field values_: Manually
  * _Object_:  [custom Object](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#custom-object)
    * _Set field values_: None required. Salesforce automatically generates the record ID when the record is created. The flow will use that ID in the "Update Triggering Record" step.
* Update Triggering Record
  * _How to Find_: Use the record that triggered the Flow
  * _Conditions_: None – Always Update Record
  *   _Set Field Values_

      * Triggering Record > [Activity Lookup Field](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#activity-lookup-field) = _Record Id from Create Record_



#### Screen Flow for SharinPix Album

Replaces the standard SharinPix Album component on the Event page and displays the Album from the related custom object record instead.

<figure><img src=".gitbook/assets/DOC SF - 1920 x 1080 (15).png" alt=""><figcaption></figcaption></figure>

1.  Create New Resource (Element panel)

    1. _Resource Type_: “Variable”
    2. _API Name_: “recordId”
    3. _Data Type_: Text
    4. ✅ _Available for Input_

    Salesforce expects "recordId" as the name of the input variable when a screen flow is launched from a record page
2. Get Records - get Triggering Record
   1. Object: _Event or Task_
   2. Conditions: _Activity Id_ = recordId
   3. How many Records: "Only the first record"
   4. How to Store: "Automatically store all the fields"
3. Screen Element
   1. ✅ _Hide Header_
   2. ✅ _Hide Footer_
   3. Add SharinPix Album Component
      1. _API Name: e.g., "Activity Album"_
      2. _Album Id_: Task/Event from get Triggering Record > [Activity Lookup Field](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#activity-lookup-field) > _Record ID_
      3. _Enable Image Sync_: TRUE
      4. _Other preferred parameters_



#### Screen Flow for Launchers

Replace any existing SharinPix launch components so captured images are saved to the [custom Object](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#custom-object) record, not directly to the Task or Event.

Repeat steps 1 - 3b from [Screen Flow for SharinPix Album](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#screen-flow-for-sharinpix-album)

3c. Add the SharinPix Mobile Launcher component instead of the SharinPix Album

* _API Name: your desired value_
* _Button Label: your desired value_
* _Album Id_: Task/Event from get Triggering Record > [Activity Lookup Field](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#activity-lookup-field) > Record ID
* _Other preferred parameters_

### Setup Image Sync

Use the instructions from the [Setup Image Sync article](https://docs.sharinpix.com/documentation/image-sync/setup-sharinpix-image-sync) to configure Image Sync for your [custom Object](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#custom-object).

### Add Screen Flows to the Task/Event's Lightning Page

Use the screen flows created above instead of a SharinPix Album component or SharinPix Launcher components on your page so they operate from your image-sync-enabled [custom Object](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#custom-object).



1. On the Task or Event record page, ⚙️Setup > Edit Page. &#x20;
2. Add standard Flow components to the page and specify the Flow to use as the [Screen Flow for SharinPix Album](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#screen-flow-for-sharinpix-album) or the [Screen Flow for Launchers](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#screen-flow-for-launchers) as desired.
3. OPTIONAL - Add a “Related List – Single” to your Related tab, set the Parent record as [Custom Object](how-to-set-up-image-sync-for-sharinpix-albums-on-events-and-tasks.md#custom-object).  Edit the columns to display on the Custom Objects' Page Layout > Related Lists.

<figure><img src=".gitbook/assets/DOC SF - 1920 x 1080 (16).png" alt=""><figcaption></figcaption></figure>

## Migrating Existing Images

If images were previously uploaded directly to Tasks or Events, they will remain attached to those records.

To move them into the new custom object albums, use the [SharinPix Merge Album](https://docs.sharinpix.com/documentation/lightning-web-component/sharinpix-merge-album) component to merge the Activity album into the corresponding custom object album.
