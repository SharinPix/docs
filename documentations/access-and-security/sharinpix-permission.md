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

# SharinPix permission

The code snippet below demonstrates the structure of the **SharinPix Permissions** as implemented in an Apex Controller.

```apex
public class SharinPixActionDemoCtrl {
    public String parameters {get; set;}
    
    public SharinPixActionDemoCtrl(ApexPages.StandardController controller) {
        Id accId = controller.getId();
        
        Map<String, Object> params = new Map<String, Object> {
            'exp' => 1528281766,
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

{% hint style="warning" %}
**Note:** The key **exp** represents the **expiration time** in UNIX timestamp format measured in milliseconds. For more information on this value, refer to this article: [https://jwt.io/introduction/](https://jwt.io/introduction/)
{% endhint %}

* The keys that make up the **params** Map structure are:
  * **SharinPix Abilities**, to put in simpler terms, are designations that have the possibility to expand or restrict the features enabled on the SharinPix Album.
  * The **Access** key represents the rights to specific SharinPix features.
  * **Tags** - Labels along with their corresponding translations in English (en) and in French (fr).
  * The **Action** key accepts a **SharinPix Action** as value.
