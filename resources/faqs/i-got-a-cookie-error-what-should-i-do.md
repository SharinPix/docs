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

# I got a cookie error, what should I do?

Some devices may encounter a cookie error which never stops displaying the "click here to allow cookies" as depicted in the image below:

<figure><img src=".gitbook/assets/I got a cookie error, what should I do1.png" alt=""><figcaption></figcaption></figure>

When you encounter this error, it might be because of:

* Old version of the SharinPix app used

SharinPix latest package version is correcting this problem most of the time. You just have to go to the AppExchange ( [http://bit.ly/SharinPixAppExchange](http://bit.ly/SharinPixAppExchange) ) and use the Get It Now button, just like if you were installing this for the first time. The AppExchange will detect the existing installation and will just update the code without any impact on your implementation.\
That should correct the problem, if not, please check the other solutions below.

*   Incorrect security settings

    SharinPix relies on external URLs to upload, display and manage images.

    You may have to whitelist those URLs in order to correct this problem.

    The list of those URLs can be find here: [SharinPix Endpoints to Authorize](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/sharinpix-endpoint-urls-to-authorize-or-whitelist)
*   Incorrect implementation of an Iframe

    If you are using an Iframe, its implementation might be incorrect.

    To overcome this issue, SharinPix adopted the use of the **postMesssage** method in the Iframe implementation. For more detailed information about how to use the postMessage method to bypass the error, click on the link that follows:

[http://docs.sharinpix.com/m/documentation/l/1193053-using-a-sharinpix-component-in-an-iframe-developer-oriented](http://docs.sharinpix.com/m/documentation/l/1193053-using-a-sharinpix-component-in-an-iframe-developer-oriented)

{% hint style="info" %}
If the problem still persists or if you require assistance, you can contact us [here](http://www.sharinpix.com/#contact).
{% endhint %}
