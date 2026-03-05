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

# SharinPix Custom Translation

SharinPix allows you to create your own custom label with the custom language.

{% hint style="success" %}
1\. To make this work you have to add this in your token.

for example:

**translations: ' <<**&#x4C;in&#x6B;**> >' (**&#x49;nsert link towards JSON fil&#x65;**).**

**locale: ko (** Mandatory to add in the token else default translation will be applie&#x64;**)**

2\. The URL (JSON File ) should be a public link.
{% endhint %}

Example how to configure your SharinPix token:

```json
{
  "path": "/pagelayout/003240000046yLAWWW",
  "abilities": {
    "003240000046yLAWWW": {
      "Access": {
        "see": true,
        "image_list": true,
        "image_delete": true,
        "image_upload": true
      }
    }
  },
  "translations": "https://sharinpix-documentation.s3.amazonaws.com/translation_example.json",
  "locale": "ko"
}
```

Below is an example of the JSON:

```json
{
    "fr": {
        "fallback": "fr-fr",
        "data": {
          "pagelayout.dropzone": "Glissez vos fichiers ici ou cliquez pour en ajouter.",
          "pagelayout.add": "Ajouter"
        }
    },
    "en": {
        "fallback": "en-us",
        "data": {
          "pagelayout.dropzone": "Drop files here or click to upload.",
          "pagelayout.add": "Add"
        }
    },
    "it": {
        "fallback": "en-us",
        "data": {
          "pagelayout.dropzone": "Trascina qui il file oppure clicca su upload.",
          "pagelayout.add": "Aggiungi"
        }
    },
    "ko": {
        "fallback": "en-us",
        "data": {
          "pagelayout.dropzone": "여기에 파일을 놓거나 클릭하여 업로드하세요.",
          "pagelayout.add": "추가하기"
        }
    }
    
}
```

{% hint style="success" %}
fallback is reverting to the translation if in case there is missing data.
{% endhint %}

## Demo

In the demo example we are translating the language to french

Before we apply the JSON:

![](<../../.gitbook/assets/image (15) (1).png>)

```json
{
    "fr": {
        "fallback": "fr-fr",
        "data": {
          "pagelayout.dropzone": "Glissez vos fichiers ici ou cliquez pour en ajouter.",
          "pagelayout.add": "Ajouter"
        }
    }
}
```

After we applied the JSON:

![](<../../.gitbook/assets/image (16) (1).png>)
