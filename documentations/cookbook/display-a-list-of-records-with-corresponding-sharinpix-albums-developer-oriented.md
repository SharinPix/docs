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

# Display a list of records with corresponding SharinPix albums (Developer-oriented)

{% hint style="info" %}
In this article, we will demonstrate how to implement a Lightning component that will:

* Display a list of records
* Display the corresponding SharinPix album of the record selected from the list

You can rely on the following GitHub entry to deploy and try the given sample on your Salesforce organisations: [https://github.com/SharinPix/demo-apex/tree/list\_case\_album](https://github.com/SharinPix/demo-apex/tree/list_case_album)
{% endhint %}

{% hint style="info" %}
**Information:**

We will use the **Case** object throughout this demo.
{% endhint %}

The component presented in this article displays a list of Case records available on your organisation. By selecting a record entry from the list, the corresponding SharinPix album will be made available as shown in the example below:

![](<../.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed.lightning.force.com-2020.05.27-11_02_36 (1).png>)

For this implementation, you will need:

1. an [Apex Class Controller](display-a-list-of-records-with-corresponding-sharinpix-albums-developer-oriented.md#apex-class-controller) that will query the Case records as well as generate the album's parameters and URL.
2. a [Lightning Component ](display-a-list-of-records-with-corresponding-sharinpix-albums-developer-oriented.md#lightning-component)to display the list of Case records and use an Iframe to embed the SharinPix album.

## Apex Class Controller

The Apex Class Controller's implementation can be found below:

```apex
public class SharinPixCaseAlbumController {
    @AuraEnabled
    public static List<Case> getCaseRecords() {
        return [SELECT Id, CaseNumber FROM Case];
    }
    
    @AuraEnabled
    public static String getAlbumParams(String albumId) {
         Map<String, Object> albumParams = new Map<String, Object> {
            'abilities' =>  new Map<String, Object> {
                albumId => new Map<String, Object> {
                    'Access' =>  new Map<String, Object> {
                        'see' => true,
                        'fullscreen' => true,
                        'image_list' => true,
                        'image_upload' => true,
                        'image_delete' => true,
                        'image_copy' => true,
                        'image_tag' => true
                    },
                    'Display' => new Map<String, Object> {
                        'tags' => true
                    }
                },
                'tags'=> new Map<String, Object> {
                    'create' => true,
                    'read'=> true,
                    'filter_any_of'=> true
                }
            },
            'download' => true,
            'Id' => albumId,
            'path' => '/pagelayout/' + albumId
        };

        sharinpix.Client clientInstance = sharinpix.Client.getInstance();
        return clientInstance.getAppHost() + '?token=' + clientInstance.token(albumParams);
    }
}
```

The method below (extracted from the Apex Class Controller) demonstrates how the album's parameters and URL are generated:

```apex
	public static String getAlbumParams(String albumId) {
         Map<String, Object> albumParams = new Map<String, Object> {
            'abilities' =>  new Map<String, Object> {
                albumId => new Map<String, Object> {
                    'Access' =>  new Map<String, Object> {
                        'see' => true,
                        'fullscreen' => true,
                        'image_list' => true,
                        'image_upload' => true,
                        'image_delete' => true,
                        'image_copy' => true,
                        'image_tag' => true
                    },
                    'Display' => new Map<String, Object> {
                        'tags' => true
                    }
                },
                'tags'=> new Map<String, Object> {
                    'create' => true,
                    'read'=> true,
                    'filter_any_of'=> true
  				}
            },
            'download' => true,
            'Id' => albumId,
            'path' => '/pagelayout/' + albumId
        };

        sharinpix.Client clientInstance = sharinpix.Client.getInstance();
        return clientInstance.getAppHost() + '?token=' + clientInstance.token(albumParams);
    }
```

## Lightning Component

The Lightning Component's implementation is found below:

```html
<aura:component access="GLOBAL"
                implements="force:appHostable,flexipage:availableForAllPageTypes,force:lightningQuickAction"
                controller="SharinPixCaseAlbumController">
    
    <aura:attribute name="recordID" type="Id"/>
    <aura:attribute name="albumURL" type="String"/>
    <aura:attribute name="listCase" type="Case[]" description="The list of Cases."/>
    <aura:attribute name="noSelectedCase" type="Boolean" default="false" description="No selected Case message."/>
    <aura:attribute name="showAlbum" type="Boolean" default="false"/>
    
    <aura:handler name="init" value="{!this}" action="{! c.doInit }"/>
     
    <article class="slds-card">
        <div class="slds-grid gutters">
            <div class="slds-col slds-size_1-of-3  slds-scrollable" style="height: 536px;">
                <div class="slds-card slds-has-bottom-magnet">
                    <ul>
                        <aura:iteration items="{! v.listCase }" var="case">
                            <button type="button" id="{! case.Id }" 
                                    class="slds-p-around_small slds-button slds-button_neutral" 
                                    style="width: 100%; border-radius: 0 !important;" 
                                    onclick="{! c.loadAlbum }">
                                Case Number: {! case.CaseNumber }
                            </button>
                            <br/>
                        </aura:iteration>
                    </ul>                    
                </div>
            </div>
            <div class="slds-col slds-size_2-of-3 slds-box slds-theme_shade" style="border-radius: 0 !important;">
                <aura:if isTrue="{! v.noSelectedCase }">
                    <div class="slds-grid slds-grid_align-center slds-grid_vertical-align-center"
                		 style="width: 100%; height: 500px;">
                        <div class="slds-text-heading_large">
                            Select a Case Number to display its corresponding album.
                        </div>
            		</div>
                </aura:if>
                <aura:if isTrue="{! v.showAlbum }">
                    <iframe id="sharinpix-album" src="{! v.albumURL }" height="500px" width="100%" style="border: 0"></iframe>
                </aura:if>
            </div>
        </div>
    </article> 
</aura:component>
```

The following code snippet demonstrate how the SharinPix album's URL is embedded inside an Iframe:

```html
<iframe id="sharinpix-album" src="{! v.albumURL }" height="500px" width="100%" style="border: 0"></iframe>
```

The Lightning Component Controller's is found below:

```javascript
({
    doInit: function(component, event, helper) {
        component.set("v.noSelectedCase", true);
        
        var action = component.get('c.getCaseRecords');
        action.setCallback(this, function(response) {
            var state = response.getState();
            if (state === "SUCCESS") {
                component.set('v.listCase', response.getReturnValue());
            }
        });
        $A.enqueueAction(action);
    },
    
    loadAlbum: function(component, event, helper) {
        component.set("v.noSelectedCase", false);
        component.set("v.showAlbum", true);
        
        var caseId = event.currentTarget.id;
        component.set('v.recordID', caseId);
        
        var action = component.get('c.getAlbumParams');
        action.setParams({ albumId : component.get('v.recordID') });
        action.setCallback(this, function(response) {
            var state = response.getState();
            if (state === "SUCCESS") {
                component.set('v.albumURL', response.getReturnValue());       
            }
        });
        $A.enqueueAction(action);
    },    
})
```

Once the implementation is done on your Salesforce organisation, go ahead and try the component by adding the same on any page record.
