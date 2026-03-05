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

# Overview of the SharinPix Lightning Components

{% hint style="info" %}
The SharinPix Lightning Components are categorized into the following:

* [Album components](overview-of-the-sharinpix-lightning-components.md#album-components)
* [Button components](overview-of-the-sharinpix-lightning-components.md#button-components)
* [Search components](overview-of-the-sharinpix-lightning-components.md#search-components)
* [Other components](overview-of-the-sharinpix-lightning-components.md#rendering-components)

This article elaborates and provides examples of the SharinPix components available for each category.
{% endhint %}

<figure><img src="../.gitbook/assets/test (44).png" alt=""><figcaption></figcaption></figure>

### Album Components <a href="#album-components" id="album-components"></a>

The album components provide users with an album-like interface that enables management and manipulation of images.

The components available for this category are:

* **SharinPix Album:** This component allows you to upload, delete, display, download, edit as well as tag images. For more information about the SharinPix Album component, click [here](sharinpix-album.md).
* **SharinPix Album with Chatter:** In addition to the features provided by the SharinPix Album component, this component allows users to start a Chatter discussion on a specific image. For more information about the SharinPix Album with Chatter component, click [here](sharinpix-album-with-chatter.md).
* **SharinPix WebForm:** This component can be used to restrict internal and external users from submitting files that do not conform to a set of requirements. For more information on how to implement the SharinPix WebForm component, click [here](../features/upload-images/upload-using-webforms.md).

### Button Components <a href="#button-components" id="button-components"></a>

The button components are simply button-like lightning components that can be easily added to a page layout to carry out their specific tasks.&#x20;

The components available are:

* **SharinPix Copy To Clipboard:** When this component is triggered, previously selected images from a SharinPix Album are copied to the clipboard. The same images can then be pasted in a Rich Text field. For more information about the SharinPix Copy To Clipboard component, click [here](sharinpix-copy-to-clipboard.md).
* **SharinPix Mobile Launcher:** This component is used inside the Salesforce mobile app to launch the SharinPix mobile app to upload photos. For more information about this component, click [here](sharinpix-mobile-launcher.md).
* **SharinPix Rich Text To PDF:** When triggered, this component permits the conversion of images found in a specified Rich Text field into a PDF. For more information, click [here](sharinpix-rich-text-to-pdf.md).
* **SharinPix To Album:** This component permits to load images from a specific SharinPix Album into another album. For more information about the SharinPix To Album component, click [here](sharinpix-to-album.md).
* **SharinPix To PDF:** When this component is triggered, previously selected images from a SharinPix Album are used to generate a PDF. For more information, click [here](sharinpix-to-pdf.md).
* **SharinPix To Rich Text Area:** This component permits to send and display a list of images selected from the SharinPix Album component into a Rich Text Field. For more information about this component, click [here](sharinpix-to-rich-text-area.md).
* **SharinPix Upload Button:** This component is used to upload an image into a specific SharinPix Album. You can find more information about the SharinPix Upload Button component [here](sharinpix-upload-button.md).
* **SharinPix Map To Album:** This component works alongside the [SharinPix Map](sharinpix-map.md) component and is used to extract a Map as an image from the SharinPix Map component and save it in a specific SharinPix album. For more information about this component, click [here](sharinpix-map-to-album.md).
* **SharinPix Collage:** This component permits users to combine and save **two** images from a SharinPix Album into a single image. You can find more information about the SharinPix Collage component [here](sharinpix-collage.md).
* **SharinPix Share Selection:** This component allows users to share pre-selected images from a SharinPix component such as the SharinPix Album or SharinPix Search.  You can find more information about the SharinPix Collage component [here](sharinpix-share-selection.md).
* **SharinPix Import Files:** This component is used to import Salesforce files onto a SharinPix album. You can find more information about the SharinPix Import Files [here](sharinpix-import-files.md).
* **SharinPix Album Resync:** This component is used to perform Image Sync on images in a SharinPix Album. You can find more information about the SharinPix Album Resync [here](sharinpix-album-resync.md).
* **SharinPix Merge Album:** This component permits the merging of images from a specific SharinPix Album to another album. You can find more information about the SharinPix Merge Album [here](sharinpix-merge-album.md).
* **SharinPix Mobile PDF Form Launcher:** This component is used inside the Salesforce mobile app to open a PDF form on the SharinPix mobile app. For more information about this component, click [here](sharinpix-mobile-pdf-form-launcher.md).
* **SharinPix Plan Share Link:** This component permits the user to generate and share a SharinPix Plan URL. For more information about the SharinPix Plan Share Link, click [here](sharinpix-plan-share-link.md).
* &#x20;**SharinPix Plan To Album:** This component works alongside the [SharinPix Plan](sharinpix-plan.md) component and permits users to extract a Plan as an image from the SharinPix Plan component and save it in a specific SharinPix Album. For more information on this component, click [here](sharinpix-plan-to-album.md).

{% hint style="warning" %}
The **SharinPix Mobile Launcher, SharinPix Rich Text To PDF** and **SharinPix To PDF** components are only available in the Enterprise license plan of SharinPix. For more info, please contact [support@sharinpix.com](mailto:support@sharinpix.com)
{% endhint %}

### Search Components <a href="#search-components" id="search-components"></a>

The search components permit to search for images uploaded on specified records. These components also allow users to filter the search by tags.

The components available are:

* **SharinPix Search:** This component is used to search for all images that correspond to records available in a specified report. For more information about the SharinPix Search component, click [here](sharinpix-search.md).
* **SharinPix Related Search:** This component permits to search for images that were uploaded on a related child object. You can find more information about the SharinPix Related Search component [here](sharinpix-related-search.md).
* **SharinPix Related Record Albums:** This component is used to display a list of related records along with their corresponding SharinPix Albums on the parent record. For more information about the SharinPix Related Record Albums component, click [here](sharinpix-related-record-albums.md).

### Other Components <a href="#rendering-components" id="rendering-components"></a>

The other components can be used in various situations.

The components available are:

* **SharinPix Single Image:** The SharinPix Single Image component is used to upload or display an image having a specific tag. You can find more details about this component [here](sharinpix-single-image.md).&#x20;
* **SharinPix Single Image Grid:** This component embeds multiple **Single Image Grid components** to render a grid of the SharinPix Single Image component. Click [here](sharinpix-single-image-grid.md) for more details about the Single Image Grid component.
* **SharinPix Map:** This component can be used to load, annotate, modify, and save Google Maps configuration on a record. You can click [here](sharinpix-map.md) for more information about the SharinPix Map component.
* **SharinPix Plan:** This component is suitable to load, personalize and edit plans. For more information about the SharinPix Plan component, click [here](sharinpix-plan.md).
* **SharinPix Plan Items Related List:** This component enables users to select specific SharinPix Plan Item added to the SharinPix Plan component. For more information about the SharinPix Plan Items Related List, click [here](sharinpix-plan-items-related-list.md).
* **SharinPix PDF Form Builder:** This component allows users to upload and create a PDF form. For more information about the SharinPix Plan Items Related List, click [here](sharinpix-pdf-form-builder.md).
* **SharinPix Token Viewer:** This component allows the user to open any component using a token. For more information about the SharinPix Plan Items Related List, click [here](sharinpix-token-viewer.md).

{% hint style="warning" %}
The **SharinPix Map** and **SharinPix Plan** components are only available in the Enterprise license plan of SharinPix. For more info, please contact [support@sharinpix.com](mailto:support@sharinpix.com)
{% endhint %}
