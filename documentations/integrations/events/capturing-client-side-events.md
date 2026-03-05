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

# Capturing Client-side events

What can you capture from an event:

* **name** : the name of the event occurring.
* **payload** : the payload of the event occurring.
* **albumId** : the album Id of the album that triggered the event.
* **componentId** : the component Id of the component that triggered the event

## SharinPix Events in a Lightning Component

SharinPix Events emitted from a SharinPix Album( displayed within a Lightning Component) can be captured using the code snippet below.

* The markup of the Lightning component.

```html
    <aura:component implements="flexipage:availableForRecordHome,force:hasRecordId" access="global" >
        <aura:attribute name="recordId" type="String" />
        <sharinpix:SharinPix aura:id="sharinpix-cmp" AlbumId="{! v.recordId }" height="500px" />
        <aura:handler event="sharinpix:Event" action="{!c.handleEvent}" />
    </aura:component>
```

* The client-side controller of the Lightning Component.

```javascript
    ({
        handleEvent : function(component, event, helper) {
            if(event.getSource().getLocalId() == "sharinpix-cmp") {
                console.log("Event name: ", event.getParam("name"));
                console.log("Payload: ", event.getParam("payload"));
            }
        }
    })
```

As seen from the above code snippet, the name of the emitted event is detected using `event.getParam("name")` and the event's payload is captured using `event.getParam("payload")`.

## SharinPix Events in a Visualforce Component

SharinPix Events emitted from a SharinPix Album( displayed within a Visualforce Component) can be captured using the code snippet below.

```html
    <apex:page StandardController="Account" standardStylesheets="false">
        <sharinpix:SharinPix parameters="{'Id' : '{! $CurrentPage.Parameters.Id }', 'abilities':{ '{! $CurrentPage.Parameters.Id }':{'Access':{'image_delete':true,'image_upload':true,'image_list':true,'see':true}}}}" 
        height="500px"/>
        <script>
            var eventMethod = window.addEventListener ? "addEventListener" : "attachEvent";
            var eventer = window[eventMethod];
            var messageEvent = eventMethod == "attachEvent" ? "onmessage" : "message";
            eventer(messageEvent, function(e) {
                if(e.origin !== "https://app.sharinpix.com") return;
                console.log(e.data.name);
            });
        </script>
    </apex:page>
```

## SharinPix Events in a Canvas App

SharinPix Events emitted from a SharinPix Album( displayed within a Canvas App) can be captured using the code snippet below.

```html
    <apex:page StandardController="Account">
        <sharinpix:SharinPix parameters="{'Id' : '{! $CurrentPage.Parameters.Id }', 'abilities':{ '{! $CurrentPage.Parameters.Id }':{'Access':{'image_delete':true,'image_upload':true,'image_list':true,'see':true}}}}" 
            height="500px"/>
        <script>
            var eventMethod = window.addEventListener ? "addEventListener" : "attachEvent";
            var eventer = window[eventMethod];
            var messageEvent = eventMethod == "attachEvent" ? "onmessage" : "message";
            eventer(messageEvent, function(e) {
                if(e.origin !== "https://app.sharinpix.com") return;
                console.log(e.data.name);
            });
        </script>
    </apex:page>
```

After performing a specific action on the SharinPix Album, the name of the event will be output onto the browser's console:

* The name of the event is accessed with `e.data.name`.
* The payload of the event is accessed with `e.data.payload`.

{% hint style="info" %}
**Info:**

The **payload** of the event contains useful information relative to the action being performed on the SharinPix Album.
{% endhint %}
