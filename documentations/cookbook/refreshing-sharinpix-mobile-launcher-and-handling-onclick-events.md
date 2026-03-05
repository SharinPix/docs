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

# Refreshing SharinPix Mobile Launcher and Handling OnClick Events

In this article, we will demonstrate how to:

* [Capture the OnClick event in the SharinPix Mobile Launcher.](refreshing-sharinpix-mobile-launcher-and-handling-onclick-events.md#id-1.-capturing-the-button-click-event)
* [Refresh the SharinPix Mobile Launcher component effectively.](refreshing-sharinpix-mobile-launcher-and-handling-onclick-events.md#id-2.-reloading-the-sharinpix-mobile-launcher-component)

## 1. Capturing the Button Click Event

The event to be captured is <mark style="color:$danger;">`sharinpix-mobile-launcher-clicked`</mark>. An example use case may be to show the user a message when returning to the Salesforce mobile app after taking pictures with the SharinPix mobile app.

To capture this event in LWC, you must listen for the custom Javascript event using the <mark style="color:$danger;">`addEventListener`</mark> method. Here’s an example of how to handle this event in LWC.

**Javascript:**

```javascript
import { LightningElement } from 'lwc';
export default class MobileLauncherParent extends LightningElement {
    connectedCallback() {
        window.addEventListener('sharinpix-mobile-launcher-clicked', this.handleCustomEvent);
    }
    handleCustomEvent(event) {
        // your own logic
    }
}
```

**Explanation:**

* **Event Listener:** The <mark style="color:$danger;">`window.addEventListener`</mark> method listens for the <mark style="color:$danger;">`sharinpix-mobile-launcher-clicked`</mark> event, triggered when the mobile launcher button is clicked.
* **Event Handler:** The <mark style="color:$danger;">`handleCustomEvent`</mark> function is executed once the event is triggered. You can add custom logic to this function, such as updating elements or logging event details.

This setup ensures that your LWC component efficiently handles the <mark style="color:$danger;">`sharinpix-mobile-launcher-clicked`</mark> event.

## 2. Reloading the SharinPix Mobile Launcher Component

To reload the SharinPix Mobile Launcher component, you must invoke the <mark style="color:$danger;">`reload()`</mark> method. The component state (such as tags, roll, or custom parameters) **must** be updated dynamically before reloading to ensure the changes are applied.

Below is an example illustrating how to call the <mark style="color:$danger;">`reload()`</mark> method on the SharinPix Mobile Launcher component.

**Template :**

```html
<template>
    <sharinpix-mobile-launcher
        lwc:ref="mobileLauncher"
        tags={dynamicTags}
        button-label="Mobile Launcher Test"
        record-id={recordId}
        roll={roll}
        flash={flash}
        show-overlay={showOverlay}
        checklist={checklist}
        custom-parameters={customParameters}
    ></sharinpix-mobile-launcher>
    <button onclick={reloadMobileLauncher}>Reload URL</button>
</template>
```

**Javascript :**

```javascript
import { LightningElement, api } from 'lwc';

export default class MobileLauncherParent extends LightningElement {
    @api dynamicTags = 'before'
    @api recordId
    @api roll = false
    @api showOverlay = false
    @api checklist = 'Tag1|Tag2|Tag3'
    @api customParameters

    reloadMobileLauncher() {
        this.dynamicTags = 'After'
        this.roll = true
        this.showOverlay = true
        this.checklist = 'Test1|Test2'
        const childComponent = this.refs.mobileLauncher;
        if (childComponent) {
            // this timeout is important for the change to be applied in the LWC lifecyle.
            setTimeout(() => {
                childComponent.reload();
            }, 0)
        }
    }
}
```

**Explanation:**

* **LWC Component Properties:** This component has properties like <mark style="color:$danger;">`dynamicTags`</mark>, <mark style="color:$danger;">`roll`</mark>, <mark style="color:$danger;">`showOverlay`</mark>, and <mark style="color:$danger;">`checklist`</mark> that **must** be updated dynamically before the component reloads to ensure real-time changes are applied.
* **Reload Method:** In the example, we use a button to trigger the reload. When the "Reload URL" button is clicked, the <mark style="color:$danger;">`reloadMobileLauncher`</mark> method is invoked. This method updates the component state and then calls the <mark style="color:$danger;">`reload()`</mark> method on the child component (<mark style="color:$danger;">`mobileLauncher`</mark>) to refresh it. You can also automate this reload process, depending on your specific logic, without using a button.
