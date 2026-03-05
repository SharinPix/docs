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

# SharinPix security token

The SharinPix security token represents an essential element for using SharinPix.

* [Structure of SharinPix Parameters](sharinpix-security-token.md#structure-of-sharinpix-parameters)
* [Using the SharinPix security token](sharinpix-security-token.md)

## Structure of SharinPix Parameters

{% hint style="success" %}
**Note**: To see the effect of each **SharinPix Ability** on the album, please refer to the following article: [SharinPix abilities](sharinpix-abilities.md)
{% endhint %}

The code snippet below demonstrates the structure of the SharinPix Parameters as implemented in an Apex Controller.

```apex
public class SharinPixActionDemoCtrl {
    public String parameters {get; set; }
    
    public SharinPixActionDemoCtrl(ApexPages.StandardController controller ) {
        Id accId = controller.getId();
        
        Map<String, Object> params = new Map<String, Object> {
            'exp' => 1000,
            'abilities' => new Map<String, Object> {
                accId => new Map<String, Object> {
                    'Access' => new Map<String, Object> {
                        'see' => true,
                        'image_list' => true,
                        'image_upload' => true,
                        'image_tag' => true,
                        'image_delete' => true
                    },
                    'Tags' => new Map<String, Object> {
                        'car' => new Map<String, String> {
                            'en' => 'car',
                            'fr' => 'voiture'
                        }        
                    },
                    'Action' => new List<String> {
                    	'Add to description'        
                    }
                }
            } 
        };
        parameters = JSON.serialize(params);
    }
    
}
```

* The keys that make up the **params** Map structure are explained below.

### SharinPix Abilities (abilities)

* **SharinPix Abilities** , to put in simpler terms, are designations that have the possibility to expand or restrict the features enabled on the SharinPix Album.

```apex
'abilities' => new Map<String, Object> {
    accId => new Map<String, Object> {
        'Access' => new Map<String, Object> {
            'see' => true,
            'image_list' => true,
            'image_upload' => true,
            'image_tag' => true,
            'image_delete' => true
        },
        'Tags' => new Map<String, Object> {
            'car' => new Map<String, String> {
                'en' => 'car',
                'fr' => 'voiture'
            }        
        },
        'Action' => new List<String> {
        	'Add to description'        
        }
    }
} 
```

### SharinPix Access (access)

* The **Access key**  represents the rights to specific SharinPix features.

```apex
'Access' => new Map<String, Object> {
    'see' => true,
    'image_list' => true,
    'image_upload' => true,
    'image_tag' => true,
    'image_delete' => true
},
```

### SharinPix Tags (Tags)

* **Tags** - Labels along with their corresponding translations in english(en) and in french(fr).

```apex
'Tags' => new Map<String, Object> {
    'car' => new Map<String, String> {
        'en' => 'car',
        'fr' => 'voiture'
    }        
},
```

### SharinPix Actions (Action)

The **Action** key accepts a **SharinPix Action** as value.

```apex
'Action' => new List<String> {
    	'Add to description'        
}
```
