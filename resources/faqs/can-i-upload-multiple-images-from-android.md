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

# Can I upload multiple images from Android?

SharinPix has different way to upload images from mobile:

* using the online integration with our components in Salesforce mobile app
* using the offline integration with our SharinPix mobile App



Uploading multiple images from the roll works with:

* Any ways on iOS
* Only the SharinPix mobile App on Android



So when you are using the components on Salesforce mobile app under Android, you can't upload multiple images from the roll.

This is due to the webkit use in the current version of the Salesforce mobile App and its a known limitation of Salesforce mobile app as described here:

[https://help.salesforce.com/articleView?id=000332906\&type=1\&mode=1](https://help.salesforce.com/articleView?id=000332906\&type=1\&mode=1)

In a coming version, Salesforce should update the webkit integrated in Salesforce mobile app and get rid of this limitation at the same time.

{% hint style="success" %}
if you have this need under android, please consider using the SharinPix mobile App integration which correct this problem:

[SharinPix mobile App integration on Salesforce mobile app](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/main-integration/using-on-lightning-with-sharinpix-mobile-launcher-lightning-component-admin-friendly)
{% endhint %}
