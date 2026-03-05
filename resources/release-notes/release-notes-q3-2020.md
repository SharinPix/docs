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

# Release Notes - Q3 2020

## Known Bug with correction

* [Utils methods](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/cookbook/utils-methods) : resyncAlbum utils method don't handle deleted images
* Einstein Vision : metrics component fails for certain models
* WebHook : trouble due to Salesforce instance URL update
* Photo distorsion issue for HEIC format
* Image Sync : SharinPix Image records related to the wrong parent
* Image Search : Access Error clicking on Info icon

## Features

* [Component : Album](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-album) - Title is now available on thumbnails
* [Component : Upload Button](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-upload-button) now available in flows
* [Component : Single Image](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-single-image) - Remove Button
* [Component - Map](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-map) - better error messages (instead of error saving map message)
* [Component : To Album](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-to-album) can auto tag
* NEW [Component : Related Record Albums](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-related-record-albums)
* [SharinPix Permission sets](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/sharinpix-permission-sets) for easier security settings for apex class, community usage and more
* Einstein Vision : Review sets better models support
* SharinPix mobile App : Show media infos
* SharinPix mobile App : Display warning on old version of the mobile App
* SharinPix mobile App : Keep Tags in same order than URL for CheckList and Menu
* Crop : [select crop ratio from a list](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/user-interface/large-view-toolbar-crop-with-aspect-ratios)
* Annotation : new handles and Shift / Alt keyboard shortcuts to resize/rotate only
* Annotation : ALT and drag copy the element
* Optimized upload : Upload Multipart
* New Upload UI for all components (support Folder Drag and Drop)
