# Automatic Sync Captures to Newly Created Child Records using Flow (Admin-Oriented)

## Overview

If a SharinPix Form has sections or repeated sections configured to generate new Salesforce records upon submission, Salesforce Admins can configure a Salesforce Flow to sync images captured in those sections to the SharinPix Albums of the newly created records.&#x20;

This documentation explains how to configure your Flow accordingly. It covers the following :

1. Flow Configuration Guide

* [#step-1-configure-a-record-triggered-flow](automatic-sync-captures-to-newly-created-child-records-using-flow-admin-oriented.md#step-1-configure-a-record-triggered-flow "mention")
* [#step-2-add-a-get-records-to-retrieve-form-sections-with-the-created-records](automatic-sync-captures-to-newly-created-child-records-using-flow-admin-oriented.md#step-2-add-a-get-records-to-retrieve-form-sections-with-the-created-records "mention")
* [#step-3-add-a-loop-to-go-through-each-section](automatic-sync-captures-to-newly-created-child-records-using-flow-admin-oriented.md#step-3-add-a-loop-to-go-through-each-section "mention")
* [#step-4-add-a-get-records-to-capture-answers-in-the-sections](automatic-sync-captures-to-newly-created-child-records-using-flow-admin-oriented.md#step-4-add-a-get-records-to-capture-answers-in-the-sections "mention")
* [#step-5-add-a-loop-to-go-through-every-answer-in-the-section](automatic-sync-captures-to-newly-created-child-records-using-flow-admin-oriented.md#step-5-add-a-loop-to-go-through-every-answer-in-the-section "mention")
* [#step-6-add-apex-action-sharinpix-duplicate-album](automatic-sync-captures-to-newly-created-child-records-using-flow-admin-oriented.md#step-6-add-apex-action-sharinpix-duplicate-album "mention")

2. Demo of the flow

{% hint style="warning" %}
**Prerequisites**

Before configuring this automation, ensure the following:

* You have the latest **SharinPix Package** installed. You can follow this [guide ](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)to upgrade your SharinPix Managed Package to the newest version.&#x20;
* Users must have the **SharinPix Forms Admin or SharinPix Forms User** permission set assigned. For more information on these two permission sets, check [SharinPix Permission Sets. ](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/sharinpix-permission-sets)
{% endhint %}

## Flow Configuration Guide

The following flow setup uses a **Record-Triggered Flow** to automatically sync media captured to its related record's album when a form response is submitted.&#x20;

### Step 1: Configure a Record-Triggered Flow

1. Go to **Setup** > **Flows** > Click **New Flow**
2. Choose **Start From Scratch** and click **Next**&#x20;
3. Choose **Record-Triggered Flow** and click **Create**
4. Set the following values:

| Setting               | Value                          |
| --------------------- | ------------------------------ |
| Object                | Sharinpix Form Response        |
| Trigger               | A record is created or updated |
| Set Entry Conditions  | All Conditions Are Met (AND)   |

Set Entry Conditions configuration:

| Field               | Operator | Value   |
| ------------------- | -------- | ------- |
| ProcessedAt         | Is Null  | `False` |
| Image Synced At     | Is Null  | `False` |
| Records Created At  | Is Null  | `False` |

| Setting                                  | Value                                                              |
| ---------------------------------------- | ------------------------------------------------------------------ |
| When to run the flow for updated records | Only when a record is updated to meet the condition requirements.  |
| Optimize the Flow for                    | Actions and Related Records                                        |

<figure><img src="../.gitbook/assets/Form Component Doc  (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Form Component Doc  (2).png" alt=""><figcaption></figcaption></figure>

### Step 2: Add a Get Records to retrieve Form Sections with the created records.

Set the following values:

<table><thead><tr><th width="286.89453125">Setting</th><th width="481.21875">Value</th></tr></thead><tbody><tr><td>Object</td><td>SharinPix Form Answer</td></tr><tr><td>Filter SharinPix Form Answer Records</td><td><p>All conditions are met (AND) </p><p>(see table below for condition requirements configurations)</p></td></tr><tr><td>Sort Order</td><td>Not Sorted</td></tr><tr><td>How many records to store</td><td>All records </td></tr><tr><td>How to store record data </td><td>Automatically store all fields</td></tr></tbody></table>

Condition Requirements:

<table><thead><tr><th width="216.97265625">Field</th><th width="108.43359375">Operator</th><th>Value</th></tr></thead><tbody><tr><td>SharinPix Form Response</td><td>Equals</td><td><code>Triggering sharinpix__FormResponse__c > Record ID</code></td></tr><tr><td>Linked RecordId</td><td>Is Null</td><td><code>False</code></td></tr></tbody></table>

<figure><img src="../.gitbook/assets/Form Component Doc  (4).png" alt=""><figcaption></figcaption></figure>

### Step 3: Add a Loop to go through each section&#x20;

| Setting                                         | Value                                                                                                                                                                                                                                                        |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Collection variable                             | `Get Records > SharinPix Form Answers from Get Sections With A Created Record (`[`Step 2`](automatic-sync-captures-to-newly-created-child-records-using-flow-admin-oriented.md#step-2-add-a-get-records-to-retrieve-form-sections-with-a-created-records)`)` |
| Specify direction for iterating over collection | First item to last item                                                                                                                                                                                                                                      |

<figure><img src="../.gitbook/assets/Form Component Doc  (5) (1).png" alt=""><figcaption></figcaption></figure>

### Step 4: Add a Get Records to capture answers in the sections

Set the following values:&#x20;

| Setting                              | Value                                                     |
| ------------------------------------ | --------------------------------------------------------- |
| Object                               | SharinPix Form Answer                                     |
| Filter SharinPix Form Answer Records | See table below for condition requirements configurations |
| Sort Order                           | Not Sorted                                                |
| How many records to store            | All records                                               |
| How to store record data             | Automatically store all fields                            |

Condition Requirements:&#x20;

| Setting                | Value                         |
| ---------------------- | ----------------------------- |
| Condition Requirements | Custom condition logic is met |
| Conditional Logic      | (1 OR 2) AND 3 AND 4          |

Condition logic:

<table><thead><tr><th width="102.30078125" data-type="number"></th><th width="224.89453125">Field</th><th width="157.44921875">Operator</th><th width="274.76171875">Value</th></tr></thead><tbody><tr><td>1</td><td>SharinPix Form Section</td><td>Equals</td><td><code>Current item from loop for each section with a created record > Record Id</code></td></tr><tr><td>2</td><td>Form Repeated Answer</td><td>Equals</td><td><code>Current item from loop for each section with a created record > Record Id</code></td></tr><tr><td>3</td><td>InputType</td><td>Equals</td><td><code>sharinpix-app</code></td></tr><tr><td>4</td><td>Image URL </td><td>Is Null</td><td><code>False</code></td></tr></tbody></table>

<figure><img src="../.gitbook/assets/Form Component Doc  (6) (1).png" alt=""><figcaption></figcaption></figure>

### Step 5: Add a Loop to go through every answer in the section

| Setting                                         | Value                                                                                                                                                                                                                  |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Collection Variable                             | SharinPix Form Answers from Get Capture Answers in Section ([Step 4](automatic-sync-captures-to-newly-created-child-records-using-flow-admin-oriented.md#step-4-add-a-get-records-to-capture-answers-in-the-sections)) |
| Specify direction for iterating over collection | First item to last item                                                                                                                                                                                                |

<figure><img src="../.gitbook/assets/Form Component Doc  (7) (1).png" alt=""><figcaption></figcaption></figure>

### Step 6: Add Apex Action SharinPix Duplicate Album

Add the Apex action `sharinpix__DuplicateAlbum` to the flow. For more information regarding this Apex action, refer to this documentation[Duplicate a SharinPix album using a Flow (Admin-Oriented)](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/cookbook/duplicate-a-sharinpix-album-using-a-flow-admin-oriented "mention").

| Setting               | Value                                                                                                                                                                                                                                   |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Destination Album ID  | `Current Item from Loop For Each Section With A Created Record (`[`Step 3`](automatic-sync-captures-to-newly-created-child-records-using-flow-admin-oriented.md#step-3-add-a-loop-to-go-through-each-section)`) > Linked RecordId`      |
| Source Album ID       | `Current Item from Loop For Each Capture Answer In Section (`[`Step 5`](automatic-sync-captures-to-newly-created-child-records-using-flow-admin-oriented.md#step-5-add-a-loop-to-go-through-every-answer-in-the-section)`) > Record ID` |
| Include Tags          | `True` or `False`                                                                                                                                                                                                                       |

The final Flow should look like this:

<figure><img src="../.gitbook/assets/Form Component Doc  (8).png" alt=""><figcaption></figcaption></figure>

## Demo

In this demo, the SharinPix Form is configured with a repeating section 'On-Site Workers' that creates new contact records. Any images uploaded via the embedded capture element in those sections will automatically be duplicated to the albums of the newly created contacts.&#x20;

<figure><img src="../.gitbook/assets/Form Component Doc  (9) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tip**\
Add a [SharinPix Album LWC](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-album-lwc) to the record page layout so you can view images on the records you create.
{% endhint %}

Upon Form submission, the Flow automatically triggers and duplicates any images uploaded in the section directly to the related contact record's album.

<figure><img src="../.gitbook/assets/Form Component Doc  (10).png" alt=""><figcaption></figcaption></figure>
