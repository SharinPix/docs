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

# Generate token from SharinPix Permission with Apex

In this article, you will learn how to generate a token for the SharinPix Album component from a SharinPix Permission.

The article also demos how to extend the album's permissions/abilities using code.

Create a [SharinPix Permission record](../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md#creation-of-a-sharinpix-permission-record) to be used to generate the token.

{% hint style="warning" %}
**Note:**

If you want to remove or add any permission to your album, you will simply need to modify the SharinPix Permission record on Salesforce, no need to modify the corresponding code.
{% endhint %}

## Generating token

The code snippet below demonstrates how to generate a SharinPix online token in an Apex method:

```apex
public String generateToken(String recordId) {
  sharinpix.Client clientInstance = sharinpix.Client.getInstance();
  String token = clientInstance.token( 
    sharinpix.SharinPixPermission.mergeAlbumAbilities( 
      recordId, 
      'SharinPixPermissionName', 
      new Map<String, Object> {
          'Id' => recordId
        }
     )
  );
  return token;
}
```

{% hint style="warning" %}
**Note:**

* The _**SharinPixPermissionName**_ highlighted above should be replaced with the name of the SharinPix Permission you created before.
* _**mergeAlbumAbilities**_ highlighted above is a global method. Below is a more detailed description of the method.
{% endhint %}

### mergeAlbumAbilities

_global static Map \<String, Object> **mergeAlbumAbilities**(String **albumId** , String **permissionNameOrId** , Map\<String, Object> **options**)_

The _mergeAlbumAbilities_ method is used to create a map of permissions using a SharinPix Permission, and extending the abilities by adding other permissions on top of the SharinPix Permission.

```apex
Map<String, Object> permission = 
    sharinpix.SharinPixPermission.mergeAlbumAbilities(
    	'0011t00001KBq8mAAD', 
        'SharinPixPermissionName', 
        new Map<String, Object> {'exp' => 0}
    );

system.debug(permission);
```

## Get token Parameter inside Lightning Component

* The sample code below shows how the token value is used to display the **SharinPix Album** inside the markup of a Lightning Component.

```html
<aura:component controller="ClassName"
implements="force:hasRecordId,flexipage:availableForAllPageTypes >
    <aura:attribute name="recordId" type="String"/>
    <aura:attribute name="token" type="String"/>

    <aura:handler name="init" value="{! this }" action="{! c.doInit }"/>

    <iframe src="{! v.token }" width="100%" height="500px"></iframe>
</aura:component>
```

_**ClassName**_ highlighted above should be replaced with the name of your apex class, where you have the generateToken method.

```javascript
({    
    doInit : function(component) {
        var recordId = component.get("v.recordId");
        var action = component.get("c.generateToken");           
        action.setParams({ recordId: recordId });          
        action.setCallback(this, function(response) {       
            if (response.getState() === "SUCCESS") {
                component.set('v.token', 
                "app.sharinpix.com/pagelayout/album_id?token=" 
                + response.getReturnValue());
            } else if (response.getState() === "ERROR"){ 
                console.log("Error");
            }
        });
        $A.enqueueAction(action);
    }
})
```

The method **generateToken** is the apex method shown below, it should be _**@AuraEnabled**_ to be able to access it in the aura component.

```apex
public class className  {    
    @AuraEnabled    
    public static String generateToken(String recordId) { 
        sharinpix.Client clientInstance = sharinpix.Client.getInstance();        
        String token = clientInstance.token(
            sharinpix.SharinPixPermission.mergeAlbumAbilities(
                recordId,
                'SharinPixPermissionName',
                new Map<String, Object> {
                    'Id' => recordId
                }
            )
        );
        return token;
    }
}
```
