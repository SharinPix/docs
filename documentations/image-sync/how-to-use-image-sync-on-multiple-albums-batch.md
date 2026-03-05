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

# How to use image sync on multiple albums (batch)?

In this section, we will discuss how to perform image sync on multiple albums in a single command.

There are 2 ways to make batch image sync migrations:

1. By passing an SOQL scope with at least the album's ID;
2. By passing a list of object IDs (album IDs).

## 1. By passing an SOQL scope with at least the album's ID

Below is an example whereby we will perform image syncs on all Accounts.

```javascript
sharinpix.ImageSyncMigration.resyncAlbumsFromSoql('Select Id From Account');
```

Once successfully executed, this command will start a batch and perform image sync on each album in the provided scope.

## 2. By passing a list of object IDs (album IDs)

Below is an example whereby we will perform image sync on all the album IDs provided.

```
sharinpix.ImageSyncMigration.resyncAlbumsFromIds(new List<Id> {
  '001SaleforceID1',
  '001SaleforceID2',
  '001SaleforceID3',
  '001SaleforceID4',
  '001SaleforceID5'
});
```

Once successfully executed, this command will start a batch and perform image sync on each album in the provided list of IDs.

{% hint style="danger" %}
**Alert:**\
\
All Record IDs in the list must be of the same SObject type.

Take note of Salesforce Limitations.
{% endhint %}
