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

# Force Image Sync using Apex Code or Developer console

SharinPix Image Sync could be also forced by code.

This could be called from either your own Apex Code (in a trigger as an example) or from the developer console if you need to resync some albums.

Here is the syntax for a specific ID that you can use in your code/console:

```javascript
sharinpix.ImageSyncMigration.resyncAlbum('0011t00000H8mtfAAB');
```
