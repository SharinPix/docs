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

# Using on a Web Form

## Use SharinPix in your own webform

The present demo intends to demonstrate the flexibility of the SharinPix Album and how it can be easily added to any Visualforce Page and fulfill your relevant use case.

{% hint style="info" %}
Resources:

For a sample case scenario, please refer to the Apex Class and Visualforce Page used by following this link:

[https://github.com/SharinPix/demo-apex/tree/case\_webform](https://github.com/SharinPix/demo-apex/tree/case_webform)
{% endhint %}

## Structure of the Webform

The **webform** will be present inside a **Visualforce Page** and it will make use of an **iframe** element to display the SharinPix Album. An **Apex Controller** will also be used to generate a **SharinPix URL** which in turn will be fed to the **src** attribute of the iframe **element**.

### Visualforce Page

The specific code line shown below, indicates the **iframe** element and the value passed to the **src** attribute. This value is represented as a merge-field which is found on the Apex Controller as implemented in the next section: [Apex Controller](using-on-a-web-form.md#apex-controller). Within this iframe, the SharinPix Album is displayed.

```html
<iframe src="{! url }" height="400px" width="100%" style="border: 0"/>
```

### Apex Controller

The piece of code below shows how the **SharinPix URL** is generated using **SharinPix Abilities**. The **SharinPix URL** is then assigned to the **src** attribute of the iframe as mentioned above.

{% hint style="info" %}
To know more about **SharinPix Abilities**, refer to the following article: [SharinPix abilities](../../access-and-security/sharinpix-abilities.md)
{% endhint %}

```apex
Map<String, Object> claims = new Map<String, Object> {
            'abilities' => new Map<String, Object> {
                albumId => new Map<String, Object> {
                    'Access'  => new Map<String, Object> {
                        'see' => true,
                        'image_list' => true,
                        'image_upload' => true,
                        'image_delete' => true,
                        'image_crop' => true,
                        'image_rotate' => true,
                        'image_annotate' => true
                    }
                }
            }
        };
        url = 'https://app.sharinpix.com/pagelayout/' + albumId + '?token=' + sharinpix.Client.getInstance().token(claims);
    }
```

The iframe is rendered and displayed as shown below.

![](<../../.gitbook/assets/image (27) (1).png>)
