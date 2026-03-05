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

# Using in your own mobile app

It is possible to use SharinPix both in the **online** and **offline** experience.

* [Online usage](using-in-your-own-mobile-app.md#online-usage)
* [Offline usage](using-in-your-own-mobile-app.md#offline-usage)

## Online usage

Throughout the online experience, which evidently requires a constant and consistent internet connectivity, one approach arise:

* [SharinPix inside Webform](using-in-your-own-mobile-app.md#sharinpix-inside-webform)

### SharinPix inside Webform

* It is possible to use an **Iframe** html element that displays the SharinPix Album within an web form Page.
* The SharinPix URL fed to the **src** attribute of the Iframe element should have the following structure:

```
https://app.sharinpix.com/pagelayout/album_id?token=token_value
```

where,

* **album\_id** corresponds to the album you intend to display
* **token\_value** corresponds to the abilities of the SharinPix Album

The screenshot below shows how the album should appear:

![](<../../.gitbook/assets/image (20) (1).png>)

## Offline usage

{% hint style="warning" %}
**Note:** To use SharinPix in an offline context, it is mandatory to use the **SharinPix mobile application.**
{% endhint %}

Throughout the offline experience, which in this case presents an absence of internet connectivity, one main main approach to use SharinPix arise:

* Use a custom deeplink to launch the SharinPix Mobile Application from your own Mobile Application.
* For example, the custom deeplink for upoading images should be in the follow form:

```
sharinpix://upload?token=token_value
```

where,

* **token\_value** corresponds to the abilities of the SharinPix Album where the images are to be uploaded to.
